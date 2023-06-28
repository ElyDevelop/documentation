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

Submit an expense report
------------------------

When an expense report is completed, the next step is to submit the report to a manager for
approval. Reports must be individually submitted, and cannot be submitted in batches. Open the
specific report from the list of expense reports (if the report is not already open). To view all
expense reports, go to :menuselection:`Expenses app --> My Expenses --> My Reports`.

If the list is large, grouping the results by status may be helpful since only reports that are in a
:guilabel:`Draft` mode need to be submitted, reports with an :guilabel:`Approved` or
:guilabel:`Submitted` status do not.

.. image:: expenses/expense-status.png
   :align: center
   :alt: Submit the report to the manager.

.. note::
   The status of each report is shown in the :guilabel:`Status` column on the far right. If the
   :guilabel:`Status` column is not visible, click the :guilabel:`⋮ (additional options)` icon at
   the end of the row, and check the box next to :guilabel:`Status`.

Click on a report to open it, then click :guilabel:`Submit To Manager`. After submitting a report,
the next step is to wait for the manager to approve it.

.. important::
   The :ref:`expenses/approve`, :ref:`expenses/post`, and :ref:`expenses/reimburse` sections are
   **only** for users with the *necessary rights*.

.. _expenses/approve:

Approve expenses
================

In Odoo, not just anyone can approve expense reports— only users with the necessary rights (or
permissions) can. This means that a user must have at least *Team Approver* rights for the
*Expenses* app. Employees with the necessary rights can review expense reports, and approve or
reject them, as well as provide feedback thanks to the integrated communication tool.

To see who has rights to approve, go to the main :menuselection:`Settings` app and click on
:guilabel:`Manage Users`.

.. note::
   If the *Settings* app is not available, then certain rights are not set on the account. In the
   :guilabel:`Access Rights` tab of a user's card in the :menuselection:`Settings` app, the
   :guilabel:`Administration` section is set to one of three options:

   - :guilabel:`None (blank)`: The user cannot access the *Settings* app at all.
   - :guilabel:`Access Rights`: The user can only view the :guilabel:`User's & Companies` section of
     the *Settings* app.
   - :guilabel:`Settings`: The user has access to the entire *Settings* app with no restrictions.

   Please refer to :doc:`this document </applications/general/users/manage_users>` to learn more
   about managing users and their access rights.

Click on an individual to view their card, which displays the :guilabel:`Access Rights` tab in the
default view. Scroll down to the :guilabel:`Human Resources` section. Under :guilabel:`Expenses`,
there are four options:

- :guilabel:`None (blank)`: A blank field means the user has no rights to view or approve expense
  reports, and can only view their own.
- :guilabel:`Team Approver`: The user can only view and approve expense reports for their own
  specific team.
- :guilabel:`All Approver`: The user can view and approve any expense report.
- :guilabel:`Administrator`: The user can view and approve any expense report as well as access the
  reporting and configuration menus in the *Expenses* app.

Users who are able to approve expense reports (typically managers) can easily view all expense
reports to validate. Go to :menuselection:`Expenses app --> Expense Reports  --> Reports to
Approve`. This view lists all the expense reports that have been submitted but not approved, as
noted by the :guilabel:`Submitted` tag in the status column.

.. image:: expenses/reports-to-approve.png
   :align: center
   :alt: Reports to validate are found on the Reports to Approve page.

Reports can be approved in two ways (individually or several at once) and refused only one way. To
approve multiple expense reports at once, remain in the list view. First, select the reports to
approve by clicking the check box next to each report, or click the box next to :guilabel:`Employee`
to select all reports in the list. Next, click on the :guilabel:`⚙️ Action (gear)` icon, then click
:guilabel:`Approve Report`.

.. image:: expenses/approve-report.png
   :align: center
   :alt: Approve multiple reports by clicking the checkboxes next to each report.

To approve an individual report, click on a report to go to a detailed view of that report. In this
view, several options are presented: :guilabel:`Approve`, :guilabel:`Refuse`, or :guilabel:`Reset to
draft`. Click :guilabel:`Approve` to approve the report.

If :guilabel:`Refuse` is clicked, a pop-up window appears. Enter a brief explanation for the refusal
in the :guilabel:`Reason to refuse Expense` field, then click :guilabel:`Refuse`.

.. image:: expenses/refuse-expense.png
   :align: center
   :alt: Send messages in the chatter.

Team managers can easily view all the expense reports for their team members. While in the
:guilabel:`Reports to Approve` view, click on :guilabel:`Filters`, then click :guilabel:`My Team`.
This presents all the reports for the manager's team.

.. image:: expenses/my-team-filter.png
   :align: center
   :alt: Select the My Team filter.

.. note::
   If more information is needed, such as a receipt is missing, communication is easy from the
   chatter. In an individual report, simply type in a message, tagging the proper person (if
   needed), and post it to the chatter by clicking :guilabel:`Send`. The message is posted in the
   chatter, and the person tagged will be notified via email of the message, as well as anyone
   following.

   .. image:: expenses/chatter.png
      :align: center
      :alt: Send messages in the chatter.

.. _expenses/post:

Post expenses in accounting
===========================

Once an expense report is approved, the next step is to post the report to the accounting journal.
To view all expense reports to post, go to :menuselection:`Expenses --> Expense Reports --> Reports
To Post`.

.. image:: expenses/post-reports.png
   :align: center
   :alt: View reports to post by clicking on expense reports, then reports to post.

Just like approvals, expense reports can be posted in two ways (individually or several at once). To
post multiple expense reports at once, remain in the list view. First, select the reports to post by
clicking the check box next to each report, or click the box next to :guilabel:`Employee` to select
all reports in the list. Next, click on the :guilabel:`⚙️ Action (gear)` icon, then click
:guilabel:`Post Entries`.

.. image:: expenses/post-entries.png
   :align: center
   :alt: Post multiple reports from the Post Entries view.

To post an individual report, click on a report to go to the detailed view of that report. In this
view, several options are presented: :guilabel:`Post Journal Entries`, :guilabel:`Report In Next
Payslip`, or :guilabel:`Refuse`. Click :guilabel:`Post Journal Entries` to post the report.

If :guilabel:`Refuse` is clicked, a pop-up window appears. Enter a brief explanation for the refusal
in the :guilabel:`Reason to refuse Expense` field, then click :guilabel:`Refuse`. Refused reports
can be viewed by going to :menuselection:`Expenses app --> Expense Reports  --> All Reports`. This
list shows all reports, including the refused ones.

.. note::
   To post expense reports to an accounting journal, the user must have following access rights:

   - Accounting: Accountant or Adviser
   - Expenses: Manager

.. _expenses/reimburse:

Reimburse employees
===================

After an expense report is posted to an accounting journal, the next step is to reimburse the
employee. To view all expense reports to pay, go to :menuselection:`Expenses --> Expense Reports -->
Reports To Pay`.

.. image:: expenses/reports-to-pay.png
   :align: center
   :alt: View reports to pay by clicking on expense reports, then reports to pay.

Just like approvals and posting, expense reports can be paid in two ways (individually or several at
once). To pay multiple expense reports at once, remain in the list view. First, select the reports
to pay by clicking the check box next to each report, or click the box next to :guilabel:`Employee`
to select all reports in the list. Next, click on the :guilabel:`⚙️ Action (gear)` icon, then click
:guilabel:`Register Payment`.

.. image:: expenses/register-payment.png
   :align: center
   :alt: Post multiple reports by clicking the checkboxes, clicking the gear, then post the entries.

To pay an individual report, click on a report to go to a detailed view of that report. Click
:guilabel:`Register Payment` to pay the employee.

Re-invoice expenses to customers
================================

If expenses are tracked on customer projects, expenses can be automatically charged back to the
customer. This is done by creating an expense report, then creating a sales order with the expensed
items on it. Then, managers approve the expense report, and the accounting department posts the
journal entries. Finally, the customer is invoiced.

Setup
-----

First, specify the invoicing policy for each expense product. Go to :menuselection:`Expenses app -->
Configuration --> Expense Products`. Click on the expense product to edit, then click
:guilabel:`Edit`. Under the :guilabel:`Invoicing` section, select the :guilabel:`Invoicing Policy`
and :guilabel:`Re-Invoicing Policy` by clicking the radio button next to the desired selection.

:guilabel:`Invoicing Policy`:

- :guilabel:`Ordered quantities`: Expense product will only invoice expenses based on the ordered
  quantity.
- :guilabel:`Delivered quantities`: Expense product will only invoice expenses based on the
  delivered quantity.

:guilabel:`Re-Invoicing Policy`:

- :guilabel:`No`: Expense product will not be re-invoiced.
- :guilabel:`At cost`: Expense product will invoice expenses at their real cost.
- :guilabel:`At sales price`: Expense product will invoice the price set on the sale order.

Create an expense
-----------------

First, when :ref:`creating a new expense <expenses/new>`, the correct information needs to be
entered in order to re-invoice a customer. Select the :guilabel:`Customer to Reinvoice` from the
drop-down menu. Next, select the :guilabel:`Analytic Account` the expense will be posted to.

.. image:: expenses/reinvoice-expense.png
   :align: center
   :alt: Ensure the customer to be invoiced is called out on the expense.

Create a quote and sales order
------------------------------

In the :menuselection:`Sales` app, create a quote for the customer being invoiced, listing the
expense products. First, click :guilabel:`Create` to create a new quotation. Next, select the
:guilabel:`Customer` being invoiced for the expenses from the drop-down menu.

In the :guilabel:`Order Lines` tab, click :guilabel:`Add a product`. In the :guilabel:`Product`
field, select the first item being invoiced from the drop-down menu, or type in the product name.
Then, update the :guilabel:`Quantity`, the :guilabel:`Delivered` quantity, and the :guilabel:`Unit
Price` if needed. Repeat this for all products being invoiced. When all the products have been added
to the quote, click :guilabel:`Confirm` and the quotation becomes a sales order.

.. image:: expenses/expenses-salesorder.png
   :align: center
   :alt: Create and confirm the sales order with the expenses listed as products.

Once the quote turns into a sales order, a :guilabel:`Delivered` column appears. The delivered
quantity must be updated for each item. Click on the `0.000` field for each product, and enter the
delivered quantity. When all delivered quantities have been entered, click :guilabel:`Save`.

Validate and post expenses
--------------------------

Only employees with permissions (typically managers or supervisors) can :ref:`approve expenses
<expenses/approve>`. Before approving an expense report, ensure the :guilabel:`Analytic Account` is
set on every expense line of a report. If an :guilabel:`Analytic Account` is missing, click
:guilabel:`Edit` and select the correct account from the drop-down menu, then click
:guilabel:`Approve` or :guilabel:`Refuse`.

The accounting department is typically responsible for :ref:`posting journal entries
<expenses/post>`. Once an expense report is approved, it can then be posted.

Invoice expenses
----------------

Once the quote has turned into a sales order, and the expense report has been approved, it is time
to invoice the customer. Go to :menuselection:`Sales app --> To Invoice --> Orders to Invoice` to
view the sales orders ready to be invoiced.

Next, find the sales order related to the expense report, click into it, and then click
:guilabel:`Create Invoice` and a :guilabel:`Create invoices` pop-up window appears. Select if the
invoice is a :guilabel:`Regular invoice`, :guilabel:`Down payment (percentage)`, or :guilabel:`Down
payment (fixed amount)` by clicking the radio button next to the selection. For either down payment
options, enter the amount (fixed or percentage) in the :guilabel:`Down Payment Amount` field.
Finally, click either :guilabel:`create and view invoice` or :guilabel:`create invoice`.
