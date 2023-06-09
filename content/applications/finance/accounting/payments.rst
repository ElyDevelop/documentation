:show-content:

========
Pagos
========

En Odoo, los pagos pueden vincularse automáticamente a una factura o recibo o ser registros independientes
para su uso en una fecha posterior.

Si un pago está **vinculado a una factura o recibo**, se reduce el importe adeudado de la factura. Puedes
tener varios pagos relacionados con la misma factura.

Si un pago **no está vinculado a una factura o recibo**, el cliente tiene un crédito pendiente con
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
la factura del proveedor está marcada como :guilabel:`En pago`. Luego, cuando se concilie la cuenta pendiente
con una línea de extracto bancario, la factura o factura de proveedor cambia al estado :guilabel:`Pagado`.

El icono de información junto a la línea de pago muestra más información sobre el pago. Puede 
acceder a información adicional, como el diario relacionado, haciendo clic en :guilabel:`Ver`.

.. image:: payments/information-icon.png
   :alt: See detailed information of a payment

.. note::
   - La factura del cliente o la factura del proveedor deben estar en el estado :guilabel:`Publicada` para 
     registrar el pago.
   - Al hacer clic en :guilabel:`Registrar pago`, Puede seleccionar la cantidad a pagar y hacer un
     pago parcial o total.
   - Si su cuenta bancaria principal está configurada como :ref:`Cuenta pendiente
     <bank/outstanding-accounts>`, y el pago se realiza en Odoo (no relacionado con un
     extracto bancario), las facturas se registran directamente en el estado :guilabel:`Pagado`.
   - Si ha desconciliado un pago, seguirá apareciendo en sus libros, pero ya no estará vinculado a la
     factura.
   - Si (des)concilia un pago en una moneda diferente, automáticamente se crea una entrada contable para 
     registrar las ganancias o pérdidas de cambio de divisas (revisión).
   - Si (des)concilia un pago y una factura que tiene impuestos en efectivo, una entrada de diario es
     creado automáticamente para contabilizar el importe del impuesto sobre la base de efectivo (reversión).

.. seealso::
   - :doc:`bank/reconciliation`

Registrar pagos no vinculados a una factura o recibo
====================================================

Cuando se registra un nuevo pago a través del menú :menuselection:`Clientes / Proveedores --> Pagos`,
no está directamente vinculado a una factura. En su lugar, la cuenta por cobrar o la cuenta por pagar
se emparejan con la cuenta pendiente hasta que se emparejan manualmente con su factura relacionada.

Coincidir facturas y recibos con pagos
-----------------------------------------

Un banner azul aparece cuando se valida una nueva factura o recibo y hay un pago pendiente para este 
cliente o proveedor específico. Puede coincidirse fácilmente desde la factura o el recibo haciendo 
clic en :guilabel:`Añadir` debajo de :guilabel:`Créditos por cobrar` o :guilabel:`Débitos por pagar`.

.. image:: payments/add-option.png
   :alt: Shows the ADD option to reconcile an invoice or a bill with a payment

La factura o recibo ahora está marcado como :guilabel:`En pago` hasta que se concilie con el estado 
de cuenta bancaria.

.. seealso::
   - :doc:`bank/reconciliation`

Pago por lotes
--------------

Los pagos por lotes le permiten agrupar diferentes pagos para facilitar la :doc:`conciliación
<bank/reconciliation>`. También son útiles cuando deposita cheques en el banco o para Pagos SEPA. 
Para hacerlo, vaya a :menuselection:`Contabilidad --> Clientes --> Pagos por lotes` o
:menuselection:`Contabilidad --> Proveedores --> Pagos por lotes`. En la vista de lista de pagos, 
puede seleccionar varios pagos y agruparlos en un lote haciendo clic 
en :menuselection:`Acción --> Crear pago por lotes`.

.. seealso::
  - :doc:`payments/batch`
  - :doc:`payments/batch_sdd`

.. _payments-matching:

Coincidencias de pagos
----------------------

La herramienta :guilabel:`Coincidencias de pagos` abre todas las facturas de clientes o recibos 
de proveedores no conciliados y le brinda la oportunidad de procesarlos uno por uno, haciendo 
la coincidencia de todos sus pagos y facturas a la vez. Puede acceder a esta herramienta desde 
:menuselection:`Dashboard Contabilidad -->Facturas Clientes / Facturas Proveedores`, y hacer click 
en :guilabel:`⋮` y selecciona :guilabel:`Coincidencia de pagos`, o yendo 
a :menuselection:`Contabilidad --> Conciliación`.

.. note::
   Durante la :doc:`conciliación <bank/reconciliation>`, si la suma de los débitos y créditos no 
   coincide, queda un saldo pendiente. Este saldo pendiente debe conciliarse en una fecha posterior 
   o, en su defecto, debe amortizarse directamente.

Coincidencias de pagos por lotes
--------------------------------

Para conciliar varios pagos o facturas pendientes de una vez, para un cliente o proveedor específico, 
se puede utilizar la función de conciliación por lotes. Vaya a :menuselection:`Contabilidad --> Informes -->
Cuentas por cobrar vencidas / Cuentas por pagar vencidas`. Ahora puede ver todas las transacciones 
que aún no han sido conciliadas, y cuando selecciona un cliente o proveedor, se muestra la 
opción :guilabel:`Conciliar`.

.. image:: payments/reconcile-option.png
   :alt: See the reconcile option

Conciliación de pagos con extractos bancarios
=============================================

Una vez que se ha registrado un pago, el estado de la factura o recibo es :guilabel:`En pago`. El siguiente 
paso es conciliarlo con la línea correspondiente del estado de cuenta bancario para finalizar la transacción 
y marcar la factura o recibo como :guilabel:`Pagado`

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
