===================
Track and bill time
===================

*Helpdesk* provides teams with the ability to track the amount of hours spent working on a ticket,
and to bill a customer for that time. Through integrations with the *Sales*, *Timesheets*,
*Project*, and *Accounting* applications, customers can be charged once the work is completed, or
before it has even begun.

.. warning::
   Since the *Track & Bill Time* features require integration with other applications, enabling them
   may result in the installation of additional modules or applications.

   Installing a new application on a *One-App-Free* database triggers a 15-day trial. At the end of
   the trial, if a paid subscription has not been added to the database, it will no longer be active
   or accessible.

Track and bill time features configuration
==========================================

Before a customer can be invoiced for support services, the *Track & Bill Time* features **must** be
enabled on each *Helpdesk* team individually.

Enable track and bill time on a team
------------------------------------

To view and enable the *Track & Bill Time* features on a *Helpdesk* team, first navigate to
:menuselection:`Helpdesk app --> Configuration --> Helpdesk Teams`. Then, select a team from the
list, or create a :doc:`new Helpdesk team <../overview/getting_started>`. This reveals a team's
settings page.

On the team's settings page, click :guilabel:`Edit`, then scroll to the :guilabel:`Track & Bill
Time` section. Tick the boxes labeled :guilabel:`Timesheets` and :guilabel:`Time Billing`.

Once the :guilabel:`Timesheets` box is checked, a new field appears, labeled :guilabel:`Project`.

.. note::
   If this is the first time this feature has been enabled on this database, the page may need to be
   manually saved and refreshed before the :guilabel:`Project` field appears.

The project selected in this field represents where all the timesheets for this team's tickets are
recorded. Click into the :guilabel:`Project` drop-down menu to select a project.

To create a new project where the timesheets are recorded, click into the :guilabel:`Project`
drop-down menu, type a name for the project, and then click :guilabel:`Create` from the drop-down
menu beneath.

Click :guilabel:`Save` at the top-left of the page to save any changes.

.. image:: track_and_bill/track-bill-enable-settings.png
   :align: center
   :alt: The settings page of a Helpdesk team with the track and bill time settings enabled.

.. _helpdesk/configure-service-products:

Configure service products
~~~~~~~~~~~~~~~~~~~~~~~~~~

When the :guilabel:`Time Billing` feature is enabled, a new product is created in the *Sales* app
called, *Service on Timesheet*. This product can be found under :menuselection:`Sales app-->
Products --> Products`. Then, search for `Service on Timesheet` in the :guilabel:`Search...` bar.
This is the product that is used when invoicing for *post-paid support services* **after** they have
been completed.

Select :guilabel:`Service on Timesheet` from the :guilabel:`Products` page. This reveals the product
detail form. The product is configured with the :guilabel:`Product Type` set to :guilabel:`Service`,
and the :guilabel:`Invoicing Policy` set to :guilabel:`Based on Timesheets`. Click :guilabel:`Edit`
to make any necessary changes to the product record, such as the :guilabel:`Cost` or
:guilabel:`Sales Price`, then click :guilabel:`Save`.

.. image:: track_and_bill/track-bill-product-based-on-timesheets.png
   :align: center
   :alt: The Service on Timesheet product with emphasis on the invoicing policy field.

In order to invoice for support services *before* the work has been completed, also known as
*prepaid support services*, a separate product with a different invoicing policy must be created.

To create a new service product, go to :menuselection:`Sales app --> Products --> Products`, and
click :guilabel:`Create`. This reveals a blank product detail form.

On the new product form, add a :guilabel:`Product Name`.

.. tip::
   Try to use a name that identifies the purpose of the product, for example, `Prepaid Services`.
   This makes it easier when adding it to a sales order later.

Set the :guilabel:`Product Type` to :guilabel:`Service`. Then, set the :guilabel:`Invoicing Policy`
to :guilabel:`Prepaid/Fixed Price`. This means an invoice can be generated and payment can be
received for this product, before any timesheet entries have been recorded for these services.

.. image:: track_and_bill/track-bill-product-prepaid-fixed.png
   :align: center
   :alt: The Service on Timesheet product with emphasis on the invoicing policy field.

Finally, set the :guilabel:`Sales Price`, and confirm that the :guilabel:`Unit of Measure` is set to
:guilabel:`Hours`. Then, click :guilabel:`Save` to save those configurations.

Invoice prepaid support services
================================

When support services are billed on a fixed price, an invoice can be created before any work is
completed on the issue. In this case, a service product with the *Invoicing Policy* set to
*Prepaid/Fixed Price* would be used, just like the one created in the :ref:`Configure service
products <helpdesk/configure-service-products>` section.

Create prepaid product sales order
----------------------------------

To invoice a customer for prepaid support services, first create a sales order (SO) with the support
services product. To do this, go to :menuselection:`Sales app --> Orders --> Quotations`. Then,
click :guilabel:`Create` to reveal a blank quotation form.

Then, fill out the quotation form with the customer information.

Go to the :guilabel:`Order Lines` tab of the quotation, and click :guilabel:`Add a Product`. Then,
select the *prepaid services product* configured in the steps :ref:`above
<helpdesk/configure-service-products>`. Update the :guilabel:`Quantity` field with the number of
hours.

After updating any other necessary information, :guilabel:`Confirm` the quotation. This converts the
quotation into a :abbr:`SO (sales order)`.

Create/send invoice for prepaid services
----------------------------------------

Once the :abbr:`SO (sales order)` has been confirmed, click the :guilabel:`Create Invoice` button on
the sales order form. This opens a :guilabel:`Create invoices` pop-up window.

If no down payment is collected, the :guilabel:`Create Invoice` type can remain as
:guilabel:`Regular invoice`. If a :doc:`down payment <../../../sales/sales/invoicing/down_payment>`
is collected, choose between either :guilabel:`Down payment (percentage)` or :guilabel:`Down payment
(fixed amount)`.

When the necessary information has been entered, click :guilabel:`Create and View Invoice` or
:guilabel:`Create Invoice`.

.. tip::
   Invoices are created in draft mode, so they can be reviewed and edited, if necessary.

The invoice can then be :doc:`sent to the customer <../../../finance/accounting/customer_invoices>`
for payment.

Create helpdesk ticket for prepaid services
-------------------------------------------

To create a *Helpdesk* ticket for prepaid services, navigate to :menuselection:`Helpdesk app`, and
click the :guilabel:`Tickets` button on the desired team's card, to reveal that specific team's
pipeline. Click :guilabel:`Create` to create a new ticket.

On the blank ticket form, enter a ticket :guilabel:`Title` and the :guilabel:`Customer`
information.

When the customer name is added, the :guilabel:`Sales Order Item` field automatically populates with
the most recent prepaid sales order item that has time remaining.

If a customer has more than one sales order item with remaining time, click the :guilabel:`Sales
Order Item` field, and select the correct item from the drop-down list.

After entering all of the necessary information, click :guilabel:`Save`.

Track hours on helpdesk ticket
------------------------------

Time spent working on a *Helpdesk* ticket is tracked on the *Timesheets* tab on the specific ticket.

On the ticket detail form, click on the :guilabel:`Timesheets` tab, and click :guilabel:`Add a
line`. Choose an :guilabel:`Employee`, add a :guilabel:`Description` of the task, and enter the
number of :guilabel:`Hours Spent` working on the task.

As new lines are added to :guilabel:`Timesheets` tab, the :guilabel:`Remaining Hours on SO` field,
at the bottom-right of the tab, is automatically updated.

.. image:: track_and_bill/track-bill-remaining-hours-total.png
   :align: center
   :alt: The timesheets tab of a Helpdesk ticket keeping track of the number of hours remaining on a
       sales order.

.. note::
   If the number of hours on the :guilabel:`Timesheets` tab exceeds the number of hours sold, the
   :guilabel:`Remaining Hours of SO` turns red.

As hours are added to the :guilabel:`Timesheets` tab, they are automatically updated in the
:guilabel:`Delivered` field on the :abbr:`SO (sales order)`, as well.

Invoice post-paid support services
==================================

When support services are billed based on the amount of time spent on an issue, an invoice
**cannot** be created before the total number of hours required to solve the problem have been
entered on a timesheet. In this case, a service product with the *Invoicing Policy* set to *Based on
Timesheets* would be used, like the one created :ref:`above <helpdesk/configure-service-products>`.

Create time-tracked product sales order
---------------------------------------

To invoice a customer for post-paid support services, first create a sales order (SO) with the
:guilabel:`Service on Timesheet` product. To do this, go to :menuselection:`Sales app --> Orders
--> Quotations`. Then, click :guilabel:`Create` to reveal a blank quotation form.

Fill out the quotation with the customer information.

On the :guilabel:`Order Lines` tab, click :guilabel:`Add a Product`. Select the :guilabel:`Service
on Timesheet` product configured :ref:`above <helpdesk/configure-service-products>`. After updating
any other necessary information, :guilabel:`Confirm` the quotation.

.. important::
   Unlike with the prepaid service quotations, Odoo does **not** allow an invoice to be created at
   this time. That is because no services have been performed; in other words, nothing has been
   delivered, therefore, there is nothing to invoice.

Create a helpdesk ticket for time-tracked services
--------------------------------------------------

To record a *Timesheet* entry for time-tracked services, go to the :menuselection:`Helpdesk app`,
and select the appropriate team for which these services apply.

If there is already an existing ticket for this issue, select it from the Kanban view to open it. If
there is no existing ticket for this customer issue, click :guilabel:`Create` to create a new
ticket, and enter the necessary customer information on the blank ticket detail form.

After selecting or creating a ticket, go to the :guilabel:`Sales Order Item` drop-down menu. Select
the :abbr:`SO (sales order)` created in the previous step.

Track support hours on a ticket
-------------------------------

In order to create an invoice for a product based on timesheets, hours need to be tracked and
recorded. At this point, the service is considered *delivered*. To record hours for this support
service, click on the :guilabel:`Timesheets` tab of the ticket.

Click :guilabel:`Add a Line` to record a new entry. Select an :guilabel:`Employee` from the
drop-down menu, and record the time spent in the :guilabel:`Hours Spent` column.

Repeat these steps, as needed, until all time spent on the issues has been recorded. Then, click
:guilabel:`Save`.

Create invoice for hours tracked on a ticket
--------------------------------------------

After the customer's issue has been solved, and it is determined no new timesheet entries need to be
made, an invoice can be created, and the customer can be billed.

To do this, return to the :abbr:`SO (sales order)` by clicking on the :guilabel:`Sales Order` smart
button at the top of the ticket.

Before creating the invoice, confirm that the number in the :guilabel:`Delivered` column matches the
total number of :guilabel:`Hours Spent` listed in the :guilabel:`Timesheets` tab on the ticket.

Then, click :guilabel:`Create Invoice`. This opens a :guilabel:`Create invoices` pop-up window.

If no down payment is collected, the :guilabel:`Create Invoice` type can remain as
:guilabel:`Regular invoice`. If a down payment is collected, choose between either :guilabel:`Down
payment (percentage)` or :guilabel:`Down payment (fixed amount)`.

.. important::
   Use the :guilabel:`Timesheets Period` field if this invoice should **only** include timesheets
   from a certain time period. If this field is left blank, **all** applicable timesheets that have
   not yet been invoiced will be included.

When the necessary information has been entered, click :guilabel:`Create and View Invoice` or
:guilabel:`Create Invoice`. The invoice can then be :doc:`sent to the customer
<../../../finance/accounting/customer_invoices>` for payment.

.. seealso::
   - :doc:`../../../inventory_and_mrp/inventory/management/products/uom`
   - :doc:`../../../sales/sales/invoicing/down_payment`
