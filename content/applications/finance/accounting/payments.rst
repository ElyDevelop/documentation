:show-content:

========
Pagos
========

En Odoo, los pagos pueden vincularse automáticamente a una factura o factura o ser registros independientes
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

Registro del pago de una factura
===========================================

Al hacer clic en :guilabel:`Registrar pago` En una factura de cliente o factura de proveedor, genera un
nueva entrada en el diario y cambia el importe adeudado según el importe del pago. La contraparte
se refleja en una cuenta de recibos o pagos pendientes. En este punto, la factura del cliente o
la factura del proveedor está marcada como :guilabel:`En pago`. Luego, cuando se concilie la cuenta pendiente
con una línea de extracto bancario, la factura del proveedor cambia a estado:guilabel:`Pagada`.

El icono de información cerca de la línea de pago muestra más información sobre el pago. Puedes
acceder a información adicional, como el diario relacionado, haciendo clic en :guilabel:`Ver`.

.. image:: payments/information-icon.png
   :alt: See detailed information of a payment

.. note::
   - La factura del cliente o la factura del proveedor debe estar en estado :guilabel:`Publicado` para registar el pago.
   - Al hacer click en :guilabel:`Registrar pago`, puedes seleccionar la cantidad a pagar y para hacer un pago parcial o un pago total.
   - If your main bank account is set as :ref:`outstanding account
     <bank/outstanding-accounts>`, and the payment is made in Odoo (not related to a
     bank statement), invoices and bills are directly registered in the status :guilabel:`Paid`.
   - If you unreconciled a payment, it still appears in your books but is no longer linked to the
     invoice.
   - If you (un)reconcile a payment in a different currency, a journal entry is automatically
     created to post the currency exchange gains/losses (reversal) amount.
   - If you (un)reconcile a payment and an invoice having cash basis taxes, a journal entry is
     automatically created to post the cash basis tax (reversal) amount.

.. seealso::
   - :doc:`bank/reconciliation`

Registering payments not tied to an invoice or bill
===================================================

When a new payment is registered via the menu :menuselection:`Customers / Vendors --> Payments`, it
is not directly linked to an invoice or bill. Instead, the account receivable or the account payable
are matched with the outstanding account until they are manually matched with their related invoice
or bill.

Matching invoices and bills with payments
-----------------------------------------

A blue banner appears when you validate a new invoice or bill and there is an outstanding payment
for this specific customer or vendor. It can easily be matched from the invoice or the bill by
clicking on :guilabel:`ADD` under :guilabel:`Outstanding Credits` or :guilabel:`Outstanding Debits`.

.. image:: payments/add-option.png
   :alt: Shows the ADD option to reconcile an invoice or a bill with a payment

The invoice or bill is now marked as :guilabel:`In payment` until it is reconciled with the bank
statement.

.. seealso::
   - :doc:`bank/reconciliation`

Batch payment
-------------

Batch payments allow you to group different payments to ease :doc:`reconciliation
<bank/reconciliation>`. They are also useful when you deposit checks to the bank or
for SEPA Payments. To do so, go to :menuselection:`Accounting --> Customers --> Batch Payments` or
:menuselection:`Accounting --> Vendors --> Batch Payments`. In the list view of payments, you can
select several payments and group them in a batch by clicking on :menuselection:`Action --> Create
Batch Payment`.

.. seealso::
  - :doc:`payments/batch`
  - :doc:`payments/batch_sdd`

.. _payments-matching:

Payments matching
-----------------

The :guilabel:`Payments matching` tool opens all unreconciled customer invoices or vendor bills and
gives you the opportunity to process them all one by one, doing the matching of all their payments
and invoices at once. You can reach this tool from the :menuselection:`Accounting Dashboard -->
Customer Invoices / Vendor Bills`, and click on :guilabel:`⋮` and select :guilabel:`Payments
Matching`, or by going to :menuselection:`Accounting --> Reconciliation`.

.. note::
   During the :doc:`reconciliation <bank/reconciliation>`, if the sum of the debits
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
