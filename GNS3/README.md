# 🖥️ Agregar una Máquina Windows en GNS3

Guía paso a paso para configurar y ejecutar una máquina virtual Windows dentro de GNS3 usando QEMU y TigerVNC.

---

## 📋 Requisitos Previos

- GNS3 instalado y funcionando (con servidor local)
- QEMU instalado (`qemu-system-x86_64`)
- TigerVNC instalado (`tigervnc-viewer`)
- Imagen ISO de Windows (en este ejemplo: `Win11_25H2_Spanish_x64_v2.iso`)

### Instalar TigerVNC (si no está instalado)

```bash
sudo apt install tigervnc-viewer
```

> **Nota:** Sin TigerVNC instalado, GNS3 mostrará el error:
> `Could not start VNC program with command 'vncviewer localhost:5901': [Errno 2] No such file or directory: 'vncviewer'`

---

## 📥 Paso 1: Obtener la Imagen de Windows

Puedes descargar imágenes compatibles con QEMU/KVM desde sitios especializados. Algunos formatos disponibles son:

| Archivo | Tipo |
|---|---|
| win-10-x64-20H2v2.tgz | Windows 10 x64 |
| win-11-x64-DEV.tgz | Windows 11 x64 Dev |
| winserver-2019-R2-x64-rev3.tgz | Windows Server 2019 |
| win10rs5-ltsc-kvm-ttys3.zip | Windows 10 LTSC KVM |

En este manual se usa la ISO oficial: `Win11_25H2_Spanish_x64_v2.iso`

---

## ⚙️ Paso 2: Crear la Plantilla QEMU en GNS3

1. Abre GNS3 y ve a **Edit → Preferences → QEMU → Qemu VMs**
2. Haz clic en **New** para crear una nueva plantilla
3. Configura los parámetros generales:

| Parámetro | Valor |
|---|---|
| Template name | Windows |
| Console type | **vnc** |
| CPUs | 1 |
| Memory | 2048 MB (mínimo) |
| QEMU binary | qemu-system-x86_64 |
| Linked base VM | True |

> ⚠️ **Importante:** Asegúrate de que el `Console type` sea **vnc** (no `telnet`). Con `telnet` la consola se conecta pero no muestra nada gráfico.

---

## 💾 Paso 3: Configurar el Disco Duro (HDD)

### 3.1 Asignar la ISO de instalación

En la pestaña **HDD** de la plantilla:

- **HDA → Disk image:** selecciona la ISO de Windows (`Win11_25H2_Spanish_x64_v2.iso`)
- **HDA → Disk interface:** `virtio`

### 3.2 Crear un disco virtual QCOW2 para la instalación

1. En la pestaña HDD, haz clic en **Create...** junto a HDB (o HDA si deseas reemplazar)
2. Se abrirá el **Qemu image creator**:
   - **Qemu-img binary:** `/bin/qemu-img (v8.2.2)`
   - **Image format:** `Qcow2` ✅
3. En la siguiente pantalla (Qcow2 options):
   - **Preallocation:** `off`
   - **Cluster size:** `<default>`
   - **Lazy refcounts:** desactivado
4. En la pantalla final (Size and location):
   - **File location:** `Windows-hda.qcow2`
   - **Disk size:** `30,000 MiB` (30 GB recomendado para Windows 11)
5. Haz clic en **Finish**

---

## 🌐 Paso 4: Configurar la Red

En la pestaña **Network** de la plantilla:

| Parámetro | Valor |
|---|---|
| Adapters | 1 |
| Name format | Ethernet{0} |
| Type | e1000 |

---

## ▶️ Paso 5: Agregar y Arrancar la VM en un Proyecto

1. En tu proyecto de GNS3, arrastra el nodo **Windows** desde el panel de dispositivos
2. Haz clic derecho sobre el nodo → **Start**
3. Una vez iniciado, haz clic derecho → **Console**

> ⚠️ Si abres la consola antes de iniciar el nodo, verás el mensaje:
> `This node must be started before a console can be opened`

---

## 🖥️ Paso 6: Conectarse por VNC

Cuando el nodo esté corriendo, GNS3 abrirá automáticamente **TigerVNC** y verás el arranque de Windows:

```
QEMU (Windows-1) - TigerVNC
```

Aparecerá el logo de Windows 11 durante el proceso de instalación/arranque.

---

## 🔧 Solución de Problemas

| Error | Causa | Solución |
|---|---|---|
| `vncviewer: No such file or directory` | TigerVNC no instalado | `sudo apt install tigervnc-viewer` |
| `This node must be started before a console can be opened` | La VM no está encendida | Clic derecho → Start primero |
| Consola muestra texto pero no gráficos | Console type en `telnet` | Cambiar a `vnc` en la plantilla |
| La VM no arranca la ISO | Disco interface incorrecto | Usar `virtio` en HDA |

---

## 📝 Notas Adicionales

- La primera vez que se ejecuta, Windows realizará el proceso de instalación completo desde la ISO
- Se recomienda al menos **4 GB de RAM** en el host por VM de Windows activa
- El disco QCOW2 usa espacio dinámico: solo ocupa lo que realmente se escribe
- Puedes ver el consumo de recursos en `htop` — cada VM de Windows consume ~24% de CPU y ~3.8 GB de RAM durante el uso

---

## 🗂️ Estructura de Archivos

```
/home/francis/GNS3/images/QEMU/
├── Win11_25H2_Spanish_x64_v2.iso   ← ISO de instalación
└── Windows-hda.qcow2                ← Disco virtual (generado en paso 3.2)
```
