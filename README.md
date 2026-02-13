
***

## Ejercicio 1 – Automóvil configurable

- **Tipo de patrón:** Creacional.  
- **Patrón utilizado:** **Builder**.

**Justificación:**  
Un `Automovil` tiene muchos atributos opcionales (tipo de motor, color, llantas, sistema de sonido, interiores, techo solar, GPS). Usar constructores tradicionales generaría un “constructor telescópico” con muchos parámetros difíciles de leer y mantener. [refactoring](https://refactoring.guru/es/design-patterns/builder/java/example)
El patrón Builder permite construir el objeto paso a paso, haciendo obligatorios solo algunos parámetros (por ejemplo, tipo de motor y color) y agregando el resto de forma opcional mediante métodos encadenados. Esto mejora la legibilidad, evita múltiples constructores sobrecargados y facilita la inmutabilidad del objeto final. [refactoring](https://refactoring.guru/design-patterns/builder/java/example)

**Clases principales:**  
- `Automovil` (producto final, inmutable).  
- `Automovil.Builder` (clase interna que construye el automóvil).  
- `Main` (crea instancias de `Automovil` usando el Builder).

***

## Ejercicio 2 – Notificaciones en diferentes plataformas

- **Tipo de patrón:** Estructural.  
- **Patrón utilizado:** **Bridge**.

**Justificación:**  
Se requiere combinar distintos tipos de notificación (mensaje, alerta, advertencia, confirmación) con varias plataformas (web, móvil, escritorio). Si se modelara solo con herencia, habría que crear una clase por cada combinación (`NotificacionMensajeWeb`, `NotificacionAlertaMovil`, etc.), produciendo una explosión de clases difícil de mantener. [refactoring](https://refactoring.guru/es/design-patterns/bridge/java/example)
El patrón Bridge separa la jerarquía de **abstracciones** (tipos de notificación) de la jerarquía de **implementaciones** (plataformas). Cada notificación mantiene una referencia a una plataforma, lo que permite combinar libremente tipo y plataforma, agregar nuevas plataformas o nuevos tipos sin modificar las clases existentes y mantener una clara separación de responsabilidades. [gregorybrown.com](https://gregorybrown.com.br/blog/post/bridge-design-pattern)

**Clases principales:**  
- Abstracción: `Notification`, `BaseNotification`, `MessageNotification`, `AlertNotification`, `WarningNotification`, `ConfirmationNotification`.  
- Implementación: `NotificationPlatform`, `WebPlatform`, `MobilePlatform`, `DesktopPlatform`.  
- Cliente: `Main` , que crea las combinaciones y envía las notificaciones.

***

## Ejercicio 3 – Chat grupal

- **Tipo de patrón:** Comportamiento.  
- **Patrón utilizado:** **Mediator**.

**Justificación:**  
En una sala de chat grupal, si cada usuario tuviera referencias directas a todos los demás, el sistema se volvería muy acoplado: cada vez que se agregara o eliminara un usuario habría que modificar varias relaciones. [refactoring](https://refactoring.guru/es/design-patterns/mediator)
El patrón Mediator centraliza la comunicación en un objeto mediador (`ChatRoom`). Los usuarios solo conocen al mediador y le envían los mensajes; el mediador se encarga de reenviarlos al resto de usuarios. Esto reduce el acoplamiento entre usuarios, facilita el mantenimiento y hace sencillo agregar o eliminar participantes sin cambiar la lógica del resto. [softwarepatterns](https://softwarepatterns.com/java/mediator-software-pattern-java-example)

**Clases principales:**  
- Mediador: `ChatMediator` (interfaz), `ChatRoom` (implementación concreta).  
- Colegas: `Usuario` (abstracta), `UsuarioConcreto` (implementación).  
- Cliente: `Main`, que crea la sala de chat, registra los usuarios y simula el envío de mensajes.

***


