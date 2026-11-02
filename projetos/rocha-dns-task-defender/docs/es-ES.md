# Rocha DNS & Task Defender - guía rápida

Desarrollado por Alexandre Rocha. Extraiga todos los archivos y ejecute Setup.exe como administrador. Seleccione el idioma y acepte la política. El instalador permite personalizar título, mensaje, contacto y QR; la vista previa se actualiza mientras escribe y el botón de previsualización abre la ventana real.

Adjuntos: PDF (primera página), PNG, JPEG/JPG, BMP, GIF y TIFF. Se convierten localmente a PNG. Guarde para completar; cancelar antes de guardar no instala el programa.

El icono A.R es verde cuando no hay pendientes, amarillo al verificar o pausar y rojo si requiere atención. Botón derecho: Abrir, Activar, Pausar, Editor, donaciones y Salir. Cerrar o minimizar oculta la ventana y mantiene la aplicación. Salir la detiene.

Comprueba cada 15 segundos y corrige DNS IPv4 a 8.8.8.8 / 8.8.4.4 con copia y aviso. Crea HOSTS limpio y conserva hosts_old_DDMMAAAA. Mientras haya hosts_old_* en etc, el aviso se repite cada 60 segundos. También elimina entradas legítimas; los DNS públicos pueden afectar nombres internos. No modifica IPv6, proxy o DNS seguro del navegador.

Inicia inmediatamente y al entrar la cuenta administradora que instaló el programa. No es un servicio y no inicia antes de entrar ni para otros usuarios. Desinstale primero la versión Soma anterior.

En %ProgramFiles%\RochaDefender: MessageEditor.exe edita avisos y Uninstall.exe desinstala en el idioma elegido. También hay accesos en Inicio y Aplicaciones instaladas. Se conservan ajustes, QR, registros/copias, hosts_old_* y configuración de red. Registros: %LOCALAPPDATA%\RochaDefender.

Donaciones voluntarias: Pix alexandre.dirck@gmail.com; Santander Brasil, sucursal 1071, cuenta corriente 01011741-4, SWIFT/BIC BSCHBRSP. No se requiere donar. Para transferencias internacionales confirme instrucciones completas y corresponsal según moneda: https://www.santander.com.br/cambio/transferencia-internacional/

Binarios sin firma digital; el código privado no debe publicarse. El empaquetado compilado no impide ingeniería inversa ni protege frente a un administrador. Homologue instalación, desinstalación y reinicio en una VM antes de distribuir. Consulte README.md para detalles y límites.
