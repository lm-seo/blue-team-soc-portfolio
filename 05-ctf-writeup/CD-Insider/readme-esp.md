# CyberDefenders – Insider Lab (DFIR Forensics)  
Repositorio con la resolución del laboratorio *Insider* de CyberDefenders: Este repositorio documenta paso a paso la investigación forense realizada sobre una imagen de disco extraída de una máquina Linux perteneciente a una empleada sospechosa. El objetivo es responder una serie de preguntas definidas en el lab usando análisis de artefactos, logs del sistema y herramientas forenses, principalmente **FTK Imager**.


## Contexto del reto

La empresa ficticia **TAAUSAI** detecta actividad interna sospechosa atribuida a *Karen*, una empleada con acceso a una estación de trabajo Linux. Se proporciona una imagen forense de su disco para que, como analista de seguridad/SOC, se identifiquen evidencias, actividades y artefactos que respondan a preguntas específicas planteadas en el laboratorio.


## Metodología general

1. **Carga de la imagen forense**  
   Se monta la imagen `.AD1` en FTK Imager como evidencia para exploración completa de directorios y análisis de artefactos.

2. **Exploración del sistema de archivos**  
   Se revisan directorios críticos como `/boot`, `/var/log`, `/root`, y archivos de configuración para encontrar respuestas.

3. **Extracción de hashes y artefactos**  
   Se obtienen hashes de archivos, se examinan logs (`auth.log`, `bash_history`) y otros artefactos relevantes.

---

### Q1 — Distribución de Linux

**Respuesta:** *Kali Linux*  
**Cómo se determinó:**  
Revisando el contenido de directorios de arranque y logs del sistema se identifica claramente información del sistema operativo incluida en los artefactos principales.

---

### Q2 — MD5 del archivo `access.log`

**Respuesta:**  
Se calculó el hash MD5 del archivo Apache `access.log` para verificar su integridad.

**Cómo se obtuvo:**  
Exportando la lista de hashes en FTK Imager se identificó el valor MD5 asociado a ese archivo de log.

---

### Q3 — Nombre de la herramienta de volcado de credenciales

**Respuesta:** `mimikatz_trunk.zip`  
**Razonamiento:**  
La carpeta de descargas del usuario *root* muestra este archivo. Su nombre concuerda con una popular herramienta de extracción de credenciales.

---

### Q4 — Ruta absoluta del archivo “super-secreto”

**Respuesta:**  
`/root/Desktop/SuperSecretFile.txt`  
**Por qué:**  
El archivo no aparece directamente, pero su creación y ruta quedan registradas en el historial de comandos de bash.

---

### Q5 — Herramienta usada con `didyouthinkwedmakeiteasy.jpg`

**Respuesta:** `binwalk`  
**Explicación:**  
El historial de shell muestra que se empleó Binwalk para examinar dicho archivo de imagen, probablemente buscando datos incrustados o código oculto.

---

### Q6 — Tercer objetivo en la lista de Karen

**Respuesta:** `Profit`  
**Cómo se confirmó:**  
El archivo de checklist ubicado en el escritorio detalla metas personales/profesionales de la investigada; la tercera es “Profit”.

---

### Q7 — Número de ejecuciones de Apache

**Respuesta:** `0`  
**Justificación:**  
Los archivos de log de Apache están vacíos, lo que indica que el servicio no fue ejecutado en la máquina.

---

### Q8 — Evidencia de ataque hacia otro sistema

**Respuesta:** `irZLAohL.jpeg`  
**Por qué:**  
Este archivo de imagen muestra evidencia visual de que la sesión se vinculó a otro equipo (captura con prompt de otro usuario), sugiriendo un uso ofensivo.

---

### Q9 — Persona a la que Karen se burlaba

**Respuesta:** `Young`  
**Cómo se dedujo:**  
En un script de bash bajo la carpeta de documentos se imprime un texto que incluye este nombre de manera provocativa.

---

### Q10 — Usuario que escaló a root a las 11:26

**Respuesta:** `postgres`  
**Evidencia:**  
El archivo de logs de autenticación (`auth.log`) muestra múltiples entradas de `su` iniciadas por este usuario en ese horario.

---

### Q11 — Directorio de trabajo actual según bash_history

**Respuesta:**  
`/root/Documents/myfirsthack`  
**Motivo:**  
Basado en la última ruta visitada registrada en el historial de shell.

---

## Herramientas utilizadas

- **FTK Imager** — Para montar y explorar la imagen forense.  
- **Exportación de hashes** — Para verificar la integridad de archivos.
