:show-content:

========
Gastos
========

Odoo **Gastos** simplifica la gestión de gastos. Después de que un empleado presenta sus gastos en Odoo, estos son revisados por los equipos de gestión y contabilidad. Una vez aprobados, los pagos pueden ser procesados y desembolsados de vuelta al empleado para su reembolso.

.. seealso::
   `Odoo Expenses: product page <https://www.odoo.com/app/expenses>`_

Establecer tipos de gastos
==========================

El primer paso para hacer un seguimiento de los gastos es configurar los diferentes *tipos de gastos* para la empresa
(administrados como *productos* en Odoo). Cada "producto" puede ser tan específico o generalizado como se necesite. Vaya a
:menuselection:`Módulo Gastos --> Configuración --> Productos de gastos` para ver los productos de gastos actuales en una vista kanban predeterminada.

.. image:: expenses/products.png
   :align: center
   :alt: Set expense costs on products.

Para crear un nuevo producto de gastos, haga clic en :guilabel:`Crear`. Aparecerá un formulario de producto. Solo se requieren dos campos, el :guilabel:`Nombre del producto` y la :guilabel:`Unidad de Medida`. Ingresa el
:guilabel:`Nombre del Producto` en el campo correspondiente, y selecciona la :guilabel:`Unidad de Medida` en el menú desplegable (la mayoría de los productos serán configurados en :guilabel:`Unidades`).

.. tip::
   El módulo de *Ventas* es donde se crean y editan las especificaciones sobre las unidades de medida (por ejemplo, unidades, 
   millas, noches, etc.). Ir a :menuselection:`Módulo Ventas --> Configuración --> Configuración` y
   asegúrese de que la opción `Unidad de Medidas` está marcada en la sección `Catálogo de productos`. Haga Click en el enlace
   interno :guilabel:`Unidades de medida` para ver, crear, y editar las unidades de medida. Consulte
   :doc:`este documento </applications/inventory_and_mrp/inventory/management/products/uom>` para
   saber más sobre las unidades de medida y cómo configurarlas.

.. image:: expenses/new-expense-product.png
   :align: center
   :alt: Set expense costs on products.

El campo :guilabel:`Cost` en el formulario de un producto está preconfigurado con un valor de `0.00` por defecto. 
Cuando un gasto específico siempre debe ser reembolsado por un precio particular, ingrese esa cantidad en el campo
:guilabel:`Costo`. De lo contrario, deje el campo :guilabel:`Costo` en `0.00`, y los empleados reportarán el costo 
real al presentar un informe de gastos.

.. Ejemplo::
   Aquí hay algunos ejemplos de cuándo establecer un :guilabel:`Costo` specífico en un producto en lugar de dejar el
   :guilabel:`Costo` en `0.00`:

   - **Comidas**: Establezca el :guilabel:`Costo` en `0.00`. Cuando un empleado registra un gasto por una comida, 
      ingresan la cantidad real de la factura y se les reembolsará por esa cantidad. Un gasto por una comida que 
      cuesta $95.23 equivaldría a un reembolso por $95.23.
   - **Millaje**: Establezca el :guilabel:`Costo` a `0.30`. Cuando un empleado registra un gasto por "millaje", 
      ingresan la cantidad de millas conducidas y se les reembolsa $0.30 por cada milla registrada. Un gasto por 
      100 millas equivaldría a un reembolso de $30.00.
   - **Estacionamiento mensual**: Establezca el :guilabel:`Costo` a `75.00`. Cuando un empleado registra un gasto 
      por "estacionamiento mensual", el reembolso sería de $75.00.
   - **Gastos**: Establezca el :guilabel:`Costo` a `0.00`. Cuando un empleado registra un gasto que no es una comida, 
      millaje o estacionamiento mensual, utilizan el producto genérico :guilabel:`Gastos`. Un gasto por una laptop que 
      cuesta $350.00 se registraría como un producto :guilabel:`Gastos`, y el reembolso sería por $350.00.

Seleccione una :guilabel:`Cuenta de gastos` si está utilizando la aplicación *Contabilidad* de Odoo. Se recomienda verificar 
con el departamento de contabilidad para determinar la cuenta correcta a la que se debe hacer referencia en este campo, 
ya que afectará los informes.

Establezca un impuesto en cada producto en los campos :guilabel:`Impuestos del Proveedor` e :guilabel:`Impuestos del Cliente`, 
si corresponde. Se considera buena práctica utilizar un impuesto que esté configurado con :ref:`Impuesto incluido en el precio 
<taxes/included-in-price>`. Los impuestos se configurarán automáticamente si se establece esta opción.

.. _expenses/new:

Registrar gastos
================

Crear un nuevo gasto de forma manual
------------------------------------

Para registrar un nuevo gasto, comience en el panel principal de la aplicación :menuselection:`Gastos`,
que presenta la vista predeterminada :guilabel:`Mis Gastos a Reportar`. Esta vista también se puede acceder
desde :menuselection:`Aplicación de Gastos --> Mis Gastos --> Mis Gastos a Reportar`.

En primer lugar, haga clic en :guilabel:`Crear`, y luego complete los distintos campos del formulario.

- :guilabel:`Descripción`: Ingrese una breve descripción para el gasto en el campo :guilabel:`Descripción`.
Esto debería ser breve e informativo, como almuerzo con el cliente o hotel para la conferencia.
- :guilabel:`Producto`: Seleccione el producto del menú desplegable que se corresponda más estrechamente con 
el gasto. Por ejemplo, un boleto de avión sería apropiado para un :guilabel:`Producto de gastos` llamado :guilabel:`Viaje en avión`.
:guilabel:`Precio unitario`: Ingrese el monto total pagado por el gasto de una de dos maneras:

   #. Si el gasto es para un solo artículo/gasto, ingrese el costo en el campo :guilabel:`Precio unitario`, y deje la 
      :guilabel:`Cantidad` en `1.00`.
   #. Si el gasto es para múltiples unidades del mismo artículo/gasto, ingrese el *precio por unidad* en el campo 
      :guilabel:`Precio unitario`, e ingrese la *cantidad de unidades* en el campo :guilabel:`Cantidad`.

     .. Ejemplo::
        En el caso de una estadía en un hotel, por ejemplo, el :guilabel:`Precio unitario` se establecería como el 
        costo *por noche*, y se establecería la :guilabel:`Cantidad` en el *número de noches* hospedadas.

- :guilabel:`Impuestos`: Si se pagaron impuestos sobre el gasto, seleccione el porcentaje de impuestos utilizando 
   el menú desplegable. Las opciones de impuestos están preconfiguradas en función de la configuración de localización
   seleccionada al crear la base de datos. La adición de nuevos impuestos solo debe hacerse cuando sea necesario.

  .. Nota::
     Cuando un impuesto es seleccionado el valor :guilabel:`Total` será actualizado en tiempo real update in real time 
     para mostrar los impuestos añadidos.

- :guilabel:`Pagado por`: Seleccione el botón de opción para indicar quién pagó el gasto y quién debe ser reembolsado. 
   Si el empleado pagó el gasto (y debe ser reembolsado), seleccione :guilabel:Empleado (para reembolsar). Si la empresa 
   pagó directamente (por ejemplo, si se usó la tarjeta de crédito de la empresa para pagar el gasto), 
   seleccione :guilabel:`Empresa`.
- :guilabel:Fecha de gasto: Utilice el módulo de calendario para ingresar la fecha en que se realizó el gasto. 
   Use las flechas :guilabel:< (izquierda) y :guilabel:> (derecha) para navegar hasta el mes correcto, y luego 
   haga clic en el día específico para ingresar la selección.
- :guilabel:Referencia de factura: Si hay algún texto de referencia que deba incluirse para el gasto, ingréselo en este campo.
- :guilabel:Cuenta: Seleccione la cuenta de gastos en la que se debe registrar este gasto del menú desplegable.
- :guilabel:Empleado: Utilizando el menú desplegable, seleccione el empleado para el que es este gasto.
- :guilabel:Cliente a Re-facturar: Si el gasto es algo que debe ser pagado por un cliente, seleccione el cliente que 
   será facturado por este gasto del menú desplegable. Por ejemplo, si un cliente desea tener una reunión en el lugar,
   y acepta pagar los gastos asociados (como viajes, hotel, comidas, etc.), entonces todos los gastos relacionados 
   con esa reunión indicarían a ese cliente como el :guilabel:Cliente a Re-facturar.
- :guilabel:Cuenta Analítica: Seleccione la cuenta en la que se debe registrar el gasto en el menú desplegable.
- :guilabel:Empresa: Si se han configurado varias empresas, seleccione la empresa para la que se debe presentar 
   este gasto del menú desplegable. Si solo hay una empresa, este campo se completará automáticamente.
- :guilabel:Notas...: Si se necesitan notas para aclarar el gasto, ingréselas en el campo de notas.

Una vez que se hayan completado todos los campos, haga clic en :guilabel:Guardar.

.. image:: expenses/expense-filled-in.png
   :align: center
   :alt: A filled in expense form for a client lunch.

Adjuntar un recibo.
~~~~~~~~~~~~~~~~~~~

Después de guardar el gasto, el siguiente paso es adjuntar un recibo. Aparece un nuevo botón :guilabel:Adjuntar 
Recibo después de guardar la entrada, debajo del anterior botón :guilabel:Guardar (que se convierte en un botón :guilabel:Editar).

.. image:: expenses/save-receipt.png
   :align: center
   :alt: Attach a receipt after saving the record.

Haga clic en el nuevo botón :guilabel:Adjuntar Recibo y aparecerá un explorador de archivos. Navegue hasta el 
recibo que desea adjuntar y haga clic en :guilabel:Abrir. Aparecerá un nuevo botón inteligente :guilabel:Recibos 
en la parte superior, y el nuevo recibo se registrará en el chatter. Se pueden adjuntar más de un recibo a un 
gasto individual, según sea necesario. El número de recibos adjuntos al gasto se indicará en el botón inteligente.

.. image:: expenses/receipt-smartbutton.png
   :align: center
   :alt: Attach a receipt after saving the record.

Crear automáticamente nuevos gastos a partir de un correo electrónico.
---------------------------------------------------------------------

En lugar de crear individualmente cada gasto en la aplicación Gastos, los gastos pueden ser creados automáticamente al 
enviar un correo electrónico a una dirección de correo electrónico específica.

Para hacerlo, primero es necesario configurar una dirección de correo electrónico. 
Vaya a :menuselection:Aplicación de Gastos --> Configuración --> Configuración. Asegúrese de que la opción
:guilabel:Correos electrónicos entrantes esté seleccionada.

.. image:: expenses/email-alias.png
   :align: center
   :alt: Create the domain alias by clicking the link.

.. note::
  Si es necesario configurar el alias de dominio, en lugar del campo de dirección de correo electrónico, 
  aparecerá el enlace :guilabel:Configura tu alias de dominio debajo de la casilla de verificación de correos 
  electrónicos entrantes. Consulte esta documentación para obtener instrucciones de configuración y más información:
  :doc:/administration/maintain/domain_names. Una vez que se haya configurado el alias de dominio, el campo de 
  dirección de correo electrónico será visible debajo de la sección de correos electrónicos entrantes.

A continuación, ingrese la dirección de correo electrónico que se utilizará en el campo de correo electrónico y 
luego haga clic en :guilabel:Guardar. Ahora que se ha ingresado la dirección de correo electrónico, se pueden 
enviar correos electrónicos a esa dirección para crear nuevos gastos sin tener que estar en la base de datos de Odoo.

Para enviar un gasto por correo electrónico, cree un nuevo correo electrónico e ingrese el código de referencia 
interna del producto (si está disponible) y el monto del gasto en el asunto del correo electrónico. A continuación, 
adjunte el recibo al correo electrónico. Odoo crea el gasto tomando la información en el asunto del correo electrónico 
y combinándola con el recibo adjunto.

Para verificar la referencia interna de un producto de gasto, vaya a :menuselection:Aplicación de Gastos --> 
Configuración --> Productos de Gastos. Si se indica una referencia interna en el producto, se mostrará en esta 
vista como :guilabel:(Ref###).

.. image:: expenses/internal-ref-numbers.png
   :align: center
   :alt: Internal reference numbers are listed in the main Expense Products view.

Para agregar una referencia interna en un producto de gasto, haga clic en el producto y luego en :guilabel:Editar.
En el modo de edición, ingrese la :guilabel:Referencia Interna en el campo correspondiente. Debajo del campo de
:guilabel:Referencia Interna, aparece la siguiente frase: :guilabel:Usar esta referencia como un prefijo del 
asunto al enviar por correo electrónico..

.. image:: expenses/meals-internal-reference.png
   :align: center
   :alt: Internal reference numbers are listed in the main Expense Products view.

.. note::
  Por motivos de seguridad, solo se aceptan correos electrónicos de empleados autenticados por Odoo al crear 
  un gasto desde un correo electrónico. Para confirmar una dirección de correo electrónico de empleado autenticada, 
  vaya a la tarjeta del empleado en la aplicación :guilabel:Empleados y consulte el campo :guilabel:Correo electrónico de trabajo.

   .. image:: expenses/authenticated-email-address.png
      :align: center
      :alt: Create the domain alias by clicking the link.

.. Ejemplo::
  Si se envía un gasto por correo electrónico por una comida de $25.00 durante un viaje de trabajo, 
  el asunto del correo electrónico sería Ref005 Comida $25.00.



 Explicación:

   - La :guilabel:Referencia Interna para el producto de gasto Comida es Ref005
   - El :guilabel:Costo del gasto es $25.00

Crear un informe de gastos
==========================

Cuando los gastos están listos para ser presentados (como al final de un viaje de negocios o una vez al mes), 
es necesario crear un informe de gastos. Vaya al panel principal de la aplicación :menuselection:Gastos, 
que muestra la vista predeterminada :guilabel:Mis Gastos,
o vaya a :menuselection:Aplicación de Gastos --> Mis Gastos --> Mis Gastos a Reportar.

En primer lugar, se deben seleccionar cada gasto individual para el informe haciendo clic en la casilla de
verificación junto a cada entrada, o seleccionar rápidamente todos los gastos en la lista haciendo clic
en la casilla de verificación junto a :guilabel:Fecha del Gasto.

.. image:: expenses/create-report.png
   :align: center
   :alt: Select the expenses to submit, then create the report.

Una vez que se hayan seleccionado los gastos, haga clic en el botón :guilabel:Crear Informe (o similar).
El nuevo informe aparece con todos los gastos listados, y el número de documentos es visible en el botón
inteligente :guilabel:Documentos.

Es recomendable agregar un breve resumen para cada informe para ayudar a mantener los gastos organizados.
Haga clic en el botón :guilabel:Editar, y aparecerá el campo :guilabel:Resumen del Informe de Gastos.
Ingrese una breve descripción para el informe de gastos (como Viaje a Cliente en NYC o Reparaciones
para Vehículo de la Empresa). A continuación, seleccione un :guilabel:Gerente en el menú desplegable
para asignar un gerente para revisar el informe.

.. image:: expenses/expense-report-summary.png
   :align: center
   :alt: Enter a short description and select a manager for the report.

Si algunos gastos no están en el informe y deberían estarlo, aún se pueden agregar. Haga clic en
:guilabel:Agregar línea en la parte inferior de la pestaña :guilabel:Gastos. Seleccione la casilla
de verificación junto a cada gasto que desea agregar y luego haga clic en :guilabel:Seleccionar.
Los elementos ahora aparecerán en el informe que acaba de crear.

.. image:: expenses/add-an-expense-line.png
   :align: center
   :alt: Add more expenses to the report before submitting.

.. note::
   El botón :guilabel:Agregar línea solo aparece cuando el documento está en modo de edición. No aparece de otra manera.

Cuando se hayan completado todas las ediciones, haga clic en :guilabel:Guardar.

Presentar un informe de gastos
------------------------------

Una vez que se completa un informe de gastos, el siguiente paso es presentar el informe a un gerente para su aprobación.
Los informes deben presentarse individualmente y no se pueden presentar en lotes. Abra el informe específico
desde la lista de informes de gastos (si el informe aún no está abierto). Para ver todos los informes de gastos,
vaya a :menuselection:Aplicación de Gastos --> Mis Gastos --> Mis Informes.

Si la lista es larga, agrupar los resultados por estado puede ser útil ya que solo se deben presentar los informes
que estén en modo :guilabel:Borrador, los informes con estado :guilabel:Aprobado o :guilabel:Presentado no necesitan ser presentados.

.. image:: expenses/expense-status.png
   :align: center
   :alt: Submit the report to the manager.

.. note::
  El estado de cada informe se muestra en la columna :guilabel:Estado en el extremo derecho. Si la columna
  :guilabel:Estado no es visible, haga clic en el icono :guilabel:⋮ (opciones adicionales) al final de la 
  fila y marque la casilla junto a :guilabel:Estado.

Haga clic en un informe para abrirlo y luego haga clic en :guilabel:Presentar al Gerente. Después de presentar
un informe, el siguiente paso es esperar a que el gerente lo apruebe.

.. important::
   Las secciones :ref:expenses/approve, :ref:expenses/post y :ref:expenses/reimburse son solo para usuarios con los permisos necesarios.

.. _expenses/approve:

Aprobación de gastos
====================

En Odoo, no cualquier usuario puede aprobar informes de gastos, solo los usuarios con los permisos necesarios pueden hacerlo.
Esto significa que un usuario debe tener al menos los permisos de Aprobador de equipo para la aplicación de Gastos.
Los empleados con los permisos necesarios pueden revisar los informes de gastos, aprobarlos o rechazarlos, así como
proporcionar comentarios gracias a la herramienta de comunicación integrada.

Para ver quiénes tienen permisos para aprobar, vaya a la aplicación principal de :menuselection:Configuración y haga clic
en :guilabel:Gestionar Usuarios.

.. note::
   Si la aplicación de Configuración no está disponible, entonces ciertos permisos no están configurados en la cuenta.
   En la pestaña :guilabel:Derechos de Acceso de la ficha de un usuario en la aplicación de :menuselection:Configuración,
   la sección de :guilabel:Administración se establece en una de tres opciones:

   - :guilabel:None (en blanco): El usuario no puede acceder en absoluto a la aplicación de Configuración.
   - :guilabel:Derechos de Acceso: El usuario solo puede ver la sección de :guilabel:Usuarios y Compañías de la aplicación de Configuración.
   - :guilabel:Configuración: El usuario tiene acceso a toda la aplicación de Configuración sin restricciones.

   Consulte :doc:este documento </applications/general/users/manage_users> para obtener más información sobre cómo
   administrar usuarios y sus derechos de acceso.

Haga clic en un individuo para ver su ficha, que muestra la pestaña :guilabel:Derechos de Acceso en la vista predeterminada.
Desplácese hacia abajo hasta la sección de :guilabel:Recursos Humanos. Bajo :guilabel:Gastos, hay cuatro opciones:

- :guilabel:None (en blanco): Un campo en blanco significa que el usuario no tiene permisos para ver o aprobar informes de gastos, y solo puede ver los     suyos propios.
- :guilabel:Aprobador de equipo: El usuario solo puede ver y aprobar informes de gastos para su equipo específico.
- :guilabel:Aprobador de todo: El usuario puede ver y aprobar cualquier informe de gastos.
- :guilabel:Administrador: El usuario puede ver y aprobar cualquier informe de gastos, así como acceder a los menús de informes y configuración en la 
  aplicación de Gastos.

Los usuarios que pueden aprobar informes de gastos (generalmente gerentes) pueden ver fácilmente todos los informes
de gastos para validarlos. Vaya a :menuselection:Aplicación de Gastos --> Informes de Gastos --> Informes por aprobar.
Esta vista lista todos los informes de gastos que se han presentado pero no aprobado, como se indica por la etiqueta
:guilabel:Presentado en la columna de estado.

.. image:: expenses/reports-to-approve.png
   :align: center
   :alt: Reports to validate are found on the Reports to Approve page.

Los informes se pueden aprobar de dos formas (individualmente o varios a la vez) y solo hay una forma de rechazarlos.
Para aprobar varios informes de gastos a la vez, permanezca en la vista de lista. Primero, seleccione los informes
que desea aprobar haciendo clic en la casilla de verificación junto a cada informe, o haga clic en la casilla junto a
:guilabel:Empleado para seleccionar todos los informes de la lista. A continuación, haga clic en el icono
:guilabel:⚙️ Acción (engranaje), luego haga clic en :guilabel:Aprobar informe.

.. image:: expenses/approve-report.png
   :align: center
   :alt: Approve multiple reports by clicking the checkboxes next to each report.

Para aprobar un informe individual, haga clic en un informe para ir a una vista detallada de ese informe.
En esta vista, se presentan varias opciones: :guilabel:Aprobar, :guilabel:Rechazar o :guilabel:Restablecer
a borrador. Haga clic en :guilabel:Aprobar para aprobar el informe.

Si se hace clic en :guilabel:Rechazar, aparecerá una ventana emergente. Ingrese una breve explicación para
el rechazo en el campo :guilabel:Motivo del rechazo del gasto, luego haga clic en :guilabel:Rechazar.

.. image:: expenses/refuse-expense.png
   :align: center
   :alt: Send messages in the chatter.

Los gerentes de equipo pueden ver fácilmente todos los informes de gastos de los miembros de su equipo.
Mientras está en la vista de :guilabel:Informes por aprobar, haga clic en :guilabel:Filtros, luego haga clic
en :guilabel:Mi equipo. Esto presenta todos los informes para el equipo del gerente.

.. image:: expenses/my-team-filter.png
   :align: center
   :alt: Select the My Team filter.

.. note::
  Si se necesita más información, como si falta un recibo, la comunicación es fácil desde el chat. En un informe
  individual, simplemente escriba un mensaje, etiquetando a la persona adecuada (si es necesario), y publíquelo
  en el chat haciendo clic en :guilabel:Enviar. El mensaje se publica en el chat y la persona etiquetada recibirá
  una notificación por correo electrónico del mensaje, así como cualquier persona que lo esté siguiendo.

   .. image:: expenses/chatter.png
      :align: center
      :alt: Send messages in the chatter.

.. _expenses/post:

Registrar gastos en contabilidad.
=================================

Una vez que se aprueba un informe de gastos, el siguiente paso es contabilizar el informe en el diario contable.
Para ver todos los informes de gastos por contabilizar, vaya a
:menuselection:Gastos --> Informes de Gastos --> Informes por contabilizar.

.. image:: expenses/post-reports.png
   :align: center
   :alt: View reports to post by clicking on expense reports, then reports to post.

Al igual que con las aprobaciones, los informes de gastos se pueden contabilizar de dos formas
(individualmente o varios a la vez). Para contabilizar varios informes de gastos a la vez, permanezca
en la vista de lista. Primero, seleccione los informes que desea contabilizar haciendo clic en la casilla
de verificación junto a cada informe, o haga clic en la casilla junto a :guilabel:Empleado para seleccionar
todos los informes de la lista. A continuación, haga clic en el icono :guilabel:⚙️ Acción (engranaje),
luego haga clic en :guilabel:Contabilizar asientos.

.. image:: expenses/post-entries.png
   :align: center
   :alt: Post multiple reports from the Post Entries view.

Para contabilizar un informe individual, haga clic en un informe para ir a una vista detallada de ese informe.
En esta vista, se presentan varias opciones: :guilabel:Contabilizar asientos, :guilabel:Informe en el próximo
recibo de pago o :guilabel:Rechazar. Haga clic en :guilabel:Contabilizar asientos para contabilizar el informe.

Si se hace clic en :guilabel:Rechazar, aparecerá una ventana emergente. Ingrese una breve explicación para el
rechazo en el campo :guilabel:Motivo del rechazo del gasto, luego haga clic en :guilabel:Rechazar. Los informes
rechazados se pueden ver yendo a :menuselection:Aplicación de Gastos --> Informes de Gastos --> Todos los informes.
Esta lista muestra todos los informes, incluidos los rechazados.

.. note::
   Para contabilizar los informes de gastos en el diario contable, el usuario debe tener los siguientes derechos de acceso:

   - Contabilidad: Contador o Asesor
   - Gastos: Gerente

.. _expenses/reimburse:

Reembolsar a los empleados.
==========================

Después de contabilizar un informe de gastos en el diario contable, el siguiente paso es reembolsar al empleado.
Para ver todos los informes de gastos para pagar, vaya a :menuselection:Gastos --> Informes de Gastos --> Informes por pagar.

.. image:: expenses/reports-to-pay.png
   :align: center
   :alt: View reports to pay by clicking on expense reports, then reports to pay.

Al igual que con las aprobaciones y la contabilización, los informes de gastos se pueden pagar de dos formas
(individualmente o varios a la vez). Para pagar varios informes de gastos a la vez, permanezca en la vista de lista.
Primero, seleccione los informes que desea pagar haciendo clic en la casilla de verificación junto a cada informe,
o haga clic en la casilla junto a :guilabel:Empleado para seleccionar todos los informes de la lista. A continuación,
haga clic en el icono :guilabel:⚙️ Acción (engranaje), luego haga clic en :guilabel:Registrar pago.

.. image:: expenses/register-payment.png
   :align: center
   :alt: Post multiple reports by clicking the checkboxes, clicking the gear, then post the entries.

Para pagar un informe individual, haga clic en un informe para ir a una vista detallada de ese informe.
Haga clic en :guilabel:Registrar pago para pagar al empleado.

Volver a facturar los gastos a los clientes.
============================================

Si los gastos se registran en proyectos de clientes, los gastos se pueden cargar automáticamente al cliente.
Esto se hace creando un informe de gastos, luego creando una orden de venta con los elementos de gastos en ella.
Luego, los gerentes aprueban el informe de gastos y el departamento de contabilidad contabiliza los asientos
del diario. Finalmente, se factura al cliente.

Configuración
-------------

En primer lugar, especifique la política de facturación para cada producto de gastos. Vaya a :menuselection:Aplicación de Gastos
--> Configuración --> Productos de Gastos. Haga clic en el producto de gastos para editarlo, luego haga clic en :guilabel:Editar.
En la sección :guilabel:Facturación, seleccione la :guilabel:Política de facturación y la :guilabel:Política de re-facturación
haciendo clic en el botón de radio junto a la selección deseada.

:guilabel:`Política de facturación`:

- :guilabel:Cantidades pedidas: el producto de gastos solo facturará los gastos según la cantidad pedida.
- :guilabel:Cantidades entregadas: el producto de gastos solo facturará los gastos según la cantidad entregada.
:guilabel:`Re-Invoicing Policy`:

- :guilabel:No: el producto de gastos no será re-facturado.
- :guilabel:Al costo: el producto de gastos facturará los gastos a su costo real.
- :guilabel:Al precio de venta: el producto de gastos facturará el precio establecido en la orden de venta.

Crear un gasto
--------------

En primer lugar, al :ref:crear un nuevo gasto <expenses/new>, es necesario ingresar la información correcta
para volver a facturar a un cliente. Seleccione el :guilabel:Cliente a volver a facturar en el menú desplegable.
A continuación, seleccione la :guilabel:Cuenta analítica en la que se registrará el gasto.

.. image:: expenses/reinvoice-expense.png
   :align: center
   :alt: Ensure the customer to be invoiced is called out on the expense.

Crear una cotización y una orden de venta
------------------------------------------

En la aplicación :menuselection:Ventas, cree una cotización para el cliente que se está facturando, que
incluya los productos de gastos. Primero, haga clic en :guilabel:Crear para crear una nueva cotización.
A continuación, seleccione el :guilabel:Cliente que se está facturando por los gastos en el menú desplegable.

En la pestaña :guilabel:Líneas de pedido, haga clic en :guilabel:Agregar un producto. En el campo :guilabel:Producto,
seleccione el primer artículo que se está facturando en el menú desplegable o escriba el nombre del producto. Luego,
actualice la :guilabel:Cantidad, la cantidad :guilabel:Entregada y el :guilabel:Precio unitario si es necesario.
Repita esto para todos los productos que se estén facturando. Cuando se hayan agregado todos los productos a la
cotización, haga clic en :guilabel:Confirmar y la cotización se convierte en una orden de venta.

.. image:: expenses/expenses-salesorder.png
   :align: center
   :alt: Create and confirm the sales order with the expenses listed as products.

Una vez que la cotización se convierte en una orden de venta, aparece una columna de :guilabel:Entregado.
La cantidad entregada debe actualizarse para cada artículo. Haga clic en el campo 0,000 para cada producto
y escriba la cantidad entregada. Cuando se hayan ingresado todas las cantidades entregadas, haga clic
en :guilabel:Guardar.

Validar y publicar un gasto
---------------------------

Solo los empleados con permisos (generalmente gerentes o supervisores) pueden :ref:aprobar gastos<expenses/approve>.
Antes de aprobar un informe de gastos, asegúrese de que se haya establecido la :guilabel:Cuenta analítica en cada línea
de gastos del informe. Si falta una :guilabel:Cuenta analítica, haga clic en :guilabel:Editar y seleccione la cuenta
correcta en el menú desplegable, luego haga clic en :guilabel:Aprobar o :guilabel:Rechazar.

El departamento de contabilidad es típicamente el responsable de :ref:contabilizar asientos de diario<expenses/post>.
Una vez que se aprueba un informe de gastos, se puede contabilizar.

Factura de gastos
-----------------

Una vez que la cotización se ha convertido en una orden de venta y se ha aprobado el informe de gastos, es
hora de facturar al cliente. Vaya a :menuselection:Aplicación de ventas --> Para facturar --> Órdenes a facturar
para ver las órdenes de venta listas para ser facturadas.

A continuación, busque la orden de venta relacionada con el informe de gastos, haga clic en ella y luego haga clic
en :guilabel:Crear factura. Aparecerá una ventana emergente de :guilabel:Crear facturas. Seleccione si la factura
es una :guilabel:Factura regular, :guilabel:Pago a cuenta (porcentaje) o :guilabel:Pago a cuenta (cantidad fija)
haciendo clic en el botón de radio junto a la selección. Para las opciones de pago a cuenta, ingrese la cantidad
(fija o porcentaje) en el campo :guilabel:Cantidad del pago a cuenta. Finalmente, haga clic en :guilabel:Crear y ver
factura o :guilabel:Crear factura.
