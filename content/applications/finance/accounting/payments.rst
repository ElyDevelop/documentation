:show-content:

========
Pagos
========

En Odoo, los pagos pueden vincularse automáticamente a una factura o ser registros independientes
para su uso en una fecha posterior.

Si un pago está **vinculado a una factura**, se reduce el importe adeudado de la factura. Puedes
tienen varios pagos relacionados con la misma factura.

Si un pago **no está vinculado a una factura**, el cliente tiene un crédito pendiente con
su empresa, o su empresa tiene un débito pendiente con un proveedor. Puedes usar aquellos sobresalientes
importes para reducir facturas/facturas impagadas.

.. seealso::
   - :doc:`Internal transfers <payments/internal_transfers>`
   - :doc:`bank/reconciliation`
   - `Odoo Tutorials: Bank Configuration
     <https://www.odoo.com/slides/slide/bank-configuration-1880>`_

Registrar el pago de una factura o recibo
===========================================

Al hacer clic en :guilabel:`Registrar pago` en una factura de cliente o factura de proveedor, se genera una
nueva entrada en el diario y cambia el importe adeudado según el importe del pago. La contraparte
se refleja en una cuenta de recibos o pagos pendientes. En este punto, la factura del cliente o
aa factura del proveedor está marcada como :guilabel:`En pago`. Luego, cuando se concilie la cuenta pendiente
con una línea de extracto bancario, la factura o factura de proveedor cambia al estado :guilabel:`Pagado`.

El icono de información cerca de la línea de pago muestra más información sobre el pago. Puedes
Acceda a información adicional, como la revista relacionada, haciendo clic en :guilabel:`Ver`.

.. image:: payments/information-icon.png
   :alt: See detailed information of a payment

.. note::
   - La factura del cliente o la factura del proveedor deben estar en el estado :guilabel:`Publicada` para registrar el pago.
   - Al hacer clic en :guilabel:`Registrar pago`, Puede seleccionar la cantidad a pagar y hacer un
     pago parcial o total.
   - Si su cuenta bancaria principal está configurada como :ref:`outstanding account
     <bank/outstanding-accounts>`, y el pago se realiza en Odoo (no relacionado con un
     extracto bancario), las facturas se registran directamente en el estado :guilabel:`Pagado`.
   - Si ha desconciliado un pago, seguirá apareciendo en sus libros, pero ya no estará vinculado a la
     factura.
   - Si (des)concilia un pago en una moneda diferente, una entrada de diario se realiza automáticamente
     creado para contabilizar el importe de las ganancias/pérdidas (reversión) por cambio de moneda.
   - Si (des)concilia un pago y una factura que tiene impuestos en efectivo, una entrada de diario es
     creado automáticamente para contabilizar el importe del impuesto sobre la base de efectivo (reversión).

.. seealso::
   - :doc:`bank/reconciliation`

Registrar pagos no vinculados a una factura o recibo
===================================================

Cuando se registra un nuevo pago a través del menú :menuselection:`Customers / Vendors --> Payments`,
no está directamente vinculado a una factura. En su lugar, la cuenta por cobrar o la cuenta por pagar
se emparejan con la cuenta pendiente hasta que se emparejan manualmente con su factura relacionada.

Coincidir facturas y recibos con pagos
-----------------------------------------

Un banner azul aparece cuando se valida una nueva factura o recibo y hay un pago pendiente para este cliente o proveedor específico. Puede coincidirse fácilmente desde la factura o el recibo haciendo clic en :guilabel:`Añadir` debajo de :guilabel:`Créditos por cobrar` o :guilabel:`Débitos por pagar`.

.. image:: payments/add-option.png
   :alt: Shows the ADD option to reconcile an invoice or a bill with a payment

La factura o recibo ahora está marcado como :guilabel:`En pago` hasta que se concilie con el estado de cuenta bancario.

.. seealso::
   - :doc:`bank/reconciliation`

Pago por lotes
-------------

Los pagos por lotes le permiten agrupar diferentes pagos para facilitar :doc:`reconciliation
<bank/reconciliation>`. También son útiles cuando deposita cheques en el banco o para Pagos SEPA. Para hacerlo, vaya a :menuselection:`Contabilidad --> Clientes --> Pagos por lotes` o
:menuselection:`Contabilidad --> Proveedores --> Pagos por lotes`. En la vista de lista de pagos, puede seleccionar varios pagos y agruparlos en un lote haciendo clic en :menuselection:`Acción --> Crear pago por lotes`.

.. seealso::
  - :doc:`payments/batch`
  - :doc:`payments/batch_sdd`

.. _payments-matching:

Coincidencias de pagos
-----------------

La herramienta :guilabel:`Coincidencias de pagos` abre todas las facturas de clientes o recibos de proveedores no conciliados y le brinda la oportunidad de procesarlos uno por uno, haciendo la coincidencia de todos sus pagos y facturas a la vez. Puede acceder a esta herramienta desde :menuselection:`Dashboard Contabilidad -->
Facturas Clientes / Facturas Proveedores`, y hacer click en :guilabel:`⋮` y selecciona :guilabel:`Coincidencia de pagos`, o yendo a :menuselection:`Contabilidad --> Conciliación`.

.. note::
   Durante la :doc:`conciliación <bank/reconciliation>`, if the sum of the debits
   and credits does not match, there is a remaining balance. This either needs to be reconciled at a
   later date or needs to be written off directly.

Batch payments matching
-----------------------

To reconcile several outstanding payments or invoices at once, for a specific customer or vendor,
the batch reconciliation feature can be used. Go to :menuselection:`Accounting --> Reporting -->
Aged Receivable / Aged Payable`. You now see all transactions that have not been reconciled yet, and
when you select a customer or vendor, the :guilabel:`Reconcile` option is displayed.

.. image:: payments/reconcile-option.png
   :alt: See the reconcile option

Reconciling payments with bank statements
=========================================

Once a payment has been registered, the status of the invoice or bill is :guilabel:`In payment`. The
next step is to reconcile it with the related bank statement line to have the transaction finalized
and the invoice or bill marked as :guilabel:`Paid`.

.. seealso::
   - :doc:`bank/reconciliation`

.. toctree::
   :titlesonly:

   payments/online
   payments/checks
   payments/batch
   payments/batch_sdd
   payments/follow_up
   payments/internal_transfers
   payments/pay_sepa
   payments/pay_checks
   payments/multiple
   payments/forecast
