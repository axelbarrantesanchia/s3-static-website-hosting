# Proyecto: Hosting de sitio web estático en Amazon S3

Este proyecto guía paso a paso cómo alojar un sitio web estático utilizando Amazon S3. Aprenderás a crear un bucket, subir archivos, habilitar el hosting, y aplicar políticas de seguridad avanzadas.

<!-- -------------------------------------------------- -->

## Paso 1: Buscar S3 en la consola de AWS

Ingresa a la consola de AWS y busca "S3" en la barra superior.

![Paso 1](s3-pasos/paso1.png)
<!-- -------------------------------------------------- -->
Paso 2: Crear un nuevo bucket
<!-- -------------------------------------------------- -->
Haz clic en el botón Create bucket.

![Paso 2](s3-pasos/paso2.png)
<!-- -------------------------------------------------- -->
Paso 3: Configurar nombre, ACLs y propietario
<!-- -------------------------------------------------- -->
Escribe un nombre para el bucket siguiendo el formato: nextwork-website-project-tu-nombre.
<!-- -------------------------------------------------- -->
Habilita ACLs.
<!-- -------------------------------------------------- -->
Selecciona Bucket owner preferred.
<!-- -------------------------------------------------- -->
![Paso 3](s3-pasos/paso3.png)
💡 ¿Qué son las ACLs (Access Control Lists)?
<!-- -------------------------------------------------- -->
Son listas de control de acceso que definen qué usuarios o cuentas pueden acceder a objetos específicos dentro del bucket.
<!-- -------------------------------------------------- -->
Paso 4: Configurar acceso público y versionado
<!-- -------------------------------------------------- -->
Desmarca la opción Block all public access.
<!-- -------------------------------------------------- -->
Marca la casilla de confirmación.
<!-- -------------------------------------------------- -->
Activa Bucket Versioning.
<!-- -------------------------------------------------- -->
![Paso 4](s3-pasos/paso4.png)
<!-- -------------------------------------------------- -->
Paso 5: Habilitar S3 Encryption y Bucket Key
<!-- -------------------------------------------------- -->
Asegúrate de que esté habilitada la cifrado del lado del servidor (SSE-S3).
<!-- -------------------------------------------------- -->
Activa la opción Bucket Key para reducir costos de cifrado.
<!-- -------------------------------------------------- -->
![Paso 5](s3-pasos/paso5.png)
💡 S3 Encryption protege automáticamente tus archivos almacenados en S3 usando claves gestionadas por AWS.
<!-- -------------------------------------------------- -->
💡 Bucket Key permite usar una sola clave del KMS para cifrar múltiples objetos, optimizando costos.

<!-- -------------------------------------------------- -->
Paso 6: Crear el bucket
<!-- -------------------------------------------------- -->
Haz clic en Create bucket para finalizar la creación.
<!-- -------------------------------------------------- -->
![Paso 6](s3-pasos/paso6.png)
<!-- -------------------------------------------------- -->
Paso 7: Iniciar subida de archivos
<!-- -------------------------------------------------- -->
Entra al bucket recién creado y selecciona Upload.
<!-- -------------------------------------------------- -->
![Paso 7](s3-pasos/paso7.png)
<!-- -------------------------------------------------- -->
Paso 8: Subir archivos HTML
<!-- -------------------------------------------------- -->
Selecciona los archivos index.html y about.html.
<!-- -------------------------------------------------- -->
![Paso 8](s3-pasos/paso8.png)
![Paso 9](s3-pasos/paso9.png)

<!-- -------------------------------------------------- -->
Paso 9: Subir carpetas de assets y styles
<!-- -------------------------------------------------- -->
Selecciona las carpetas descomprimidas: assets/ y styles/.
<!-- -------------------------------------------------- -->
![Paso 10](s3-pasos/paso10.png)

<!-- -------------------------------------------------- -->
Paso 10: Confirmar subida
<!-- -------------------------------------------------- -->
Haz clic en Upload para comenzar la transferencia.
<!-- -------------------------------------------------- -->
![Paso 11](s3-pasos/paso11.png)

<!-- -------------------------------------------------- -->
Paso 11: Éxito en la subida
<!-- -------------------------------------------------- -->
Verifica el mensaje de éxito: Upload succeeded.
<!-- -------------------------------------------------- -->
![Paso 12](s3-pasos/paso12.png)
<!-- -------------------------------------------------- -->
![Paso 13](s3-pasos/paso13.png)
<!-- -------------------------------------------------- -->
Paso 12: Ir a Properties
<!-- -------------------------------------------------- -->
Desde el bucket, haz clic en la pestaña Properties.
<!-- -------------------------------------------------- -->
![Paso 14](s3-pasos/paso14.png)
<!-- -------------------------------------------------- -->
Paso 13: Ir a configuración de Static Website Hosting
<!-- -------------------------------------------------- -->
Desplázate hasta la sección Static website hosting y selecciona Edit.
<!-- -------------------------------------------------- -->
![Paso 15](s3-pasos/paso15.png)
<!-- -------------------------------------------------- -->
Paso 14: Activar hosting de sitio estático
<!-- -------------------------------------------------- -->
Habilita el hosting estático.
<!-- -------------------------------------------------- -->
Elige Host a static website.
<!-- -------------------------------------------------- -->
En Index document, coloca: index.html.
<!-- -------------------------------------------------- -->
![Paso 16](s3-pasos/paso16.png)
<!-- -------------------------------------------------- -->
Paso 15: Probar el sitio - Error 403
<!-- -------------------------------------------------- -->
Haz clic en el Bucket website endpoint y notarás un 403 Forbidden.
<!-- -------------------------------------------------- -->
![Paso 17](s3-pasos/paso17.png)
<!-- -------------------------------------------------- -->
💡 Esto ocurre porque los objetos todavía son privados por defecto.

<!-- -------------------------------------------------- -->
Paso 16: Hacer públicos los objetos con ACL
<!-- -------------------------------------------------- -->
Ve a la pestaña Objects, selecciona todos los archivos y carpetas, luego elige Make public using ACL.
<!-- -------------------------------------------------- -->
![Paso 18](s3-pasos/paso18.png)
<!-- -------------------------------------------------- -->
💡 ACL vs Bucket Policy
<!-- -------------------------------------------------- -->
ACLs: Controlan acceso a nivel de objeto.
<!-- -------------------------------------------------- -->
Bucket Policies: Se aplican a todo el bucket, y permiten definir reglas más avanzadas.
<!-- -------------------------------------------------- -->
En este caso, usamos ACLs para mostrar cómo dar permisos por objeto.

<!-- -------------------------------------------------- -->
Paso 17: Confirmación de visibilidad
<!-- -------------------------------------------------- -->
Verifica el mensaje de éxito tras hacer los objetos públicos.
<!-- -------------------------------------------------- -->
![Paso 19](s3-pasos/paso19.png)
<!-- -------------------------------------------------- -->
![Paso20](s3-pasos/paso20.png)
<!-- -------------------------------------------------- -->
Paso 18: Probar nuevamente la página
<!-- -------------------------------------------------- -->
Recarga el enlace del bucket website endpoint. ¡Tu sitio ya está visible!
<!-- -------------------------------------------------- -->
![Paso 20](s3-pasos/Paginarecargada.png)
<!-- -------------------------------------------------- -->
Paso 19: Ir a la sección Permissions
<!-- -------------------------------------------------- -->
Haz clic en la pestaña Permissions de tu bucket.
<!-- -------------------------------------------------- -->
![Paso 21](s3-pasos/paso21.png)
<!-- -------------------------------------------------- -->
Paso 20: Ir a Bucket Policy
<!-- -------------------------------------------------- -->
En Permissions, ve a Bucket Policy y haz clic en el botón para usar el generador de políticas.
<!-- -------------------------------------------------- -->
![Paso 22](s3-pasos/paso22.png)
<!-- -------------------------------------------------- -->
Paso 21: Seleccionar tipo de política
<!-- -------------------------------------------------- -->
Selecciona S3 bucket policy como tipo de política en el generador.
<!-- -------------------------------------------------- -->
![Paso 23](s3-pasos/paso23.png)
<!-- -------------------------------------------------- -->
Paso 22: Copiar ARN del objeto
<!-- -------------------------------------------------- -->
Puedes copiar el ARN desde Properties o desde la consola del objeto específico.
<!-- -------------------------------------------------- -->
![Paso 24](s3-pasos/paso24.png)
<!-- -------------------------------------------------- -->
Paso 23: Configurar política Deny
<!-- -------------------------------------------------- -->
En el generador, configura los siguientes campos:
<!-- -------------------------------------------------- -->
Effect: Deny
<!-- -------------------------------------------------- -->
Principal: *
<!-- -------------------------------------------------- -->
Action: s3:DeleteObject
<!-- -------------------------------------------------- -->
Resource: arn:aws:s3:::nextwork-website-project-tu-nombre/index.html
<!-- -------------------------------------------------- -->
SID: BucketPutDelete
<!-- -------------------------------------------------- -->

![Paso 25](s3-pasos/paso25.png)
<!-- -------------------------------------------------- -->
Paso 24: Generar la política
<!-- -------------------------------------------------- -->
Haz clic en Add Statement y luego en Generate Policy.
<!-- -------------------------------------------------- -->
![Paso 26](s3-pasos/paso26.png)
<!-- -------------------------------------------------- -->
Paso 25: Copiar el JSON
<!-- -------------------------------------------------- -->
El generador te mostrará el JSON listo para copiar.
<!-- -------------------------------------------------- -->
![Paso 27](s3-pasos/paso27.png)
<!-- -------------------------------------------------- -->
Paso 26: Pegar el JSON
<!-- -------------------------------------------------- -->
Pega el JSON en la sección de Bucket Policy en la consola de S3.
<!-- -------------------------------------------------- -->
![Paso 28](s3-pasos/paso28.png)
<!-- -------------------------------------------------- -->
Paso 27: Guardar cambios
<!-- -------------------------------------------------- -->
Haz clic en Save changes para aplicar la política.
<!-- -------------------------------------------------- -->
![Paso 29](s3-pasos/paso29.png)
<!-- -------------------------------------------------- -->
Paso 28: Política aplicada con éxito
<!-- -------------------------------------------------- -->
Verifica que aparezca el mensaje de éxito tras aplicar la política.
<!-- -------------------------------------------------- -->
![Paso 30](s3-pasos/paso30.png)
<!-- -------------------------------------------------- -->
Paso 29: Intentar eliminar index.html
<!-- -------------------------------------------------- -->
Intenta eliminar index.html desde la consola. Verás que no es posible, gracias a la política aplicada.
<!-- -------------------------------------------------- -->
![Paso 31](s3-pasos/paso31.png)

✨ Autor
<!-- -------------------------------------------------- -->
**Axel Andres Barrantes Anchia**
<!-- -------------------------------------------------- -->
📍 Santa Ana, San José
<!-- -------------------------------------------------- -->
📧 [axelbarrantesanchia@gmail.com](mailto:axelbarrantesanchia@gmail.com)
