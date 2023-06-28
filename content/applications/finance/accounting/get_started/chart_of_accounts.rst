=================
Plan de cuentas
=================

El plan de cuentas es la lista de todas las cuentas que se utilizan para
registrar transacciones financieras en el libro mayor de una organización.

Normalmente, las cuentas se listan en el orden en que aparecen en los
reportes financieros. La mayoría de las veces se listan así:

- Cuentas del balance general:

  - Activos
  - Pasivos
  - Capital

- Estado de resultados:

  - Ingresos
  - Gastos

En su plan de cuentas puede filtrar las cuentas por su número en la columna de
la izquierda, y también agruparlas por tipo de cuenta.

.. image:: chart_of_accounts/chart-of-accounts.png
   :align: center
   :alt: Group the accounts by type in Odoo Accounting

Configuración de una cuenta
===========================

El país que seleccione en la creación de su base de datos (o la empresa adicional en su base de datos)
determina qué paquete de localización fiscal se instala de forma predeterminada. Este paquete incluye
un plan de cuentas estándar ya configurado de acuerdo con la normativa del país. Puede utilizarlo
directamente o configurarlo según las necesidades de su empresa.

.. Advertencia::
   No es posible modificar la localización fiscal de una empresa una vez que se haya
   registrado un asiento contable.

Para crear una nueva cuenta, vaya a Contabilidad ‣ Configuración ‣ Plan de cuentas,
haga clic en crear y conplete el formulario.

Código y nombre
---------------

Cada cuenta se identifica con su código y nombre, los cuales también indican el objetivo de la cuenta.

.. _chart-of-account/type:

Tipo
----

Es muy importante configurar de forma correcta el tipo de cuenta. Hacerlo tiene varios objetivos:

- Información del propósito y comportamiento de la cuenta
- Generar reportes legales y financieros específicos del país
- Establecer las reglas para cerrar el año fiscal
- Generar asientos de apertura

Para configurar un tipo de cuenta, abra el selector desplegable del campo tipo y elija el más adecuado de la siguiente lista:

+---------------+--------------+-------------------------+
| Report        | Category     | Account Types           |
+===============+==============+=========================+
| Balance Sheet | Assets       | Receivable              |
|               |              +-------------------------+
|               |              | Bank and Cash           |
|               |              +-------------------------+
|               |              | Current Assets          |
|               |              +-------------------------+
|               |              | Non-current Assets      |
|               |              +-------------------------+
|               |              | Prepayments             |
|               |              +-------------------------+
|               |              | Fixed Assets            |
|               +--------------+-------------------------+
|               | Liabilities  | Payable                 |
|               |              +-------------------------+
|               |              | Credit Card             |
|               |              +-------------------------+
|               |              | Current Liabilities     |
|               |              +-------------------------+
|               |              | Non-current Liabilities |
|               +--------------+-------------------------+
|               | Equity       | Equity                  |
|               |              +-------------------------+
|               |              | Current Year Earnings   |
+---------------+--------------+-------------------------+
| Profit & Loss | Income       | Income                  |
|               |              +-------------------------+
|               |              | Other Income            |
|               +--------------+-------------------------+
|               | Expense      | Expense                 |
|               |              +-------------------------+
|               |              | Depreciation            |
|               |              +-------------------------+
|               |              | Cost of Revenue         |
+---------------+--------------+-------------------------+
|Other          | Other        | Off-Balance Sheet       |
+---------------+--------------+-------------------------+

Automatización de activos y gastos e ingresos diferidos
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Algunos tipos de cuentas cuentan con un nuevo campo para automatizar la creación de asientos de activos,
así como asientos de gastos diferidos y de ingresos diferidos.

Hay tres opciones para el campo automatización:

#. :guilabel:`No`: es el valor predeterminado. No pasa nada.
#. :guilabel:`Crear en borrador`: cuando se registra una transacción en la cuenta, se crea un borrador de asiento,
    pero no se valida. Primero debe completar el formulario correspondiente.
#. :guilabel:`Crear y validar`: también debe seleccionar un modelo. Cuando se registra una transacción en la cuenta,
    se crea un asiento y se valida de inmediato.

Impuestos predeterminados
-------------------------

Seleccione un **impuesto predeterminado** que se aplicará cuando esta cuenta se use para la venta o compra de un producto.

Etiquetas
---------

Algunos reportes contables requieren que se establezcan **etiquetas** en las cuentas relevantes. De forma predeterminada, puede escoger entre las etiquetas que utiliza el *Estado de cuenta de flujos de efectivo*.

Grupos de cuentas
-----------------

Los **grupos de cuentas** sirven para listar múltiples cuentas como *subcuentas* de una cuenta más grande y,
por lo tanto, consolidar reportes como la **Balanza de Comprobación**. De forma predeterminada, los grupos se
gestionan según el código del grupo.  Por ejemplo, una nueva cuenta `131200` será parte del grupo `131000`.

Crear grupos de cuentas de forma manual
---------------------------------------

.. note::
  Los usuarios normales no deberían necesitar crear grupos de cuentas de forma manual. La siguiente sección solo
  está pensada para casos de uso poco frecuentes y avanzados.

Para crear un nuevo grupo de cuentas debe activar el :ref:`developer mode <developer-mode>` y acceder a la aplicación
:menuselection:`Contabilidad --> Configuración --> Grupo de cuentas`. Cree un nuevo grupo, agregue su
:guilabel:`nombre, prefijo de nombre, y empresa` para la cual el grupo estará disponible.
Tome en cuenta que debe introducir el mismo prefijo de código en los campos :guilabel:`De` and :guilabel:`A`.

.. image:: chart_of_accounts/account-groups.png
   :align: center
   :alt: Account groups creation.

Para visualizar sus grupos de cuentas en el reporte de **balanza de comprobación**, vaya a la aplicación
:menuselection:`Contabilidad-->Reportes-->Balanza de comprobación`, luego abra el menú :guilabel:`Optiones` y seleccione
:guilabel:`Jerarquía y subtotales`.

.. image:: chart_of_accounts/trial-balance.png
   :align: center
   :alt: Account Groups in the Trial Balance in Odoo Accounting

Permitir conciliaciones
-----------------------

Algunas cuentas, como las que registran transacciones de un método de pago, se pueden usar para conciliar los asientos contables.

Por ejemplo, una factura que se pagó con una tarjeta de crédito puede marcarse como :guilabel:`pagada` si se concilia con 
el pago correspondiente. Por lo tanto, la cuenta que se utiliza para registrar pagos con tarjeta de crédito se debe configurar
para **permitir conciliaciones**.

Para hacerlo, seleccione la casilla :guilabel:`permitir conciliaci'on` en los ajustes de la cuenta y guarde los cambios.

Obsoleta
--------

No es posible eliminar una cuenta una vez que se haya registrado una transacción en ella. Puede hacerla inutilizable
al usar la función **Obsoleta**.

Para hacerlo, seleccione la casilla :guilabel:`Obsoleta` en los ajustes de la cuenta y guarde los cambios.

.. seealso::
   * :doc:`cheat_sheet`
   * :doc:`../vendor_bills/assets`
   * :doc:`../vendor_bills/deferred_expenses`
   * :doc:`../customer_invoices/deferred_revenues`
   * :doc:`../../fiscal_localizations`
