.. _doc--workflows:

Workflow Management
===================

.. contents:: :local:
    :depth: 4

Overview
---------

A workflow is a sequence of steps or rules applied to a process from its initiation to completion. 
In OroCRM, workflows organize and direct users’ work, making them follow particular steps in a pre-defined order, or preventing them from performing actions that either contradict or conflict with the logical steps of a process.

Workflow Types
--------------

In OroCRM, there are two types of workflows: ``system`` and ``custom``.

System workflows are provided out of the box and their management from the UI is limited.

Custom workflows can be created and edited depending on your desired configurations. 

Workflow Components
-------------------

Each process or action applied to a record is called a ``workflow transition``. On the interface, transitions are usually initiated when a user clicks the corresponding button or icon. There are two types of transitions:

-	Transitions that take a user from one state to another and connect to each step in the workflow.
-	Self-transitions that do not change steps in the workflow. 

A ``workflow step`` is the state of a record before and after a transition.

Every workflow has the **Start** transition that launches the workflow.

A transition can be defined as soon as there is at least one step besides **Start**. However, it is often simpler to define all workflow steps and then all the transitions between them.  

.. image:: ../img/workflows/1_transitions_steps.png

``Attributes`` are characteristics of the record. For example, a ZIP code and a street name are attributes of an address. In the course of each transition, you can change some attributes of the processed record.

A workflow may have ``configuration parameters`` (also known as ``variables``). For example, the **Alternative Checkout** workflow includes reviewing of an order by an authorized person. This is usually required only for orders over a certain amount, so the workflow's configuration parameter enables you to set an order subtotal limit that triggers the alternative checkout.

.. image:: ../img/workflows/workflow_config_prameters.png

If enabled (see the section below), the **Workflow** widget displays the process steps defined in workflow configuration on the record view page. Multiple workflow widgets can be displayed for one record at the same time.

.. image:: ../img/workflows/2_wf_steps_new.png

.. _doc-workflows-actions-create:

Workflow Creation
-----------------

To create a workflow for an entity:

1. In the main menu, navigate to **System > Workflows**.
2. Click **Create Workflow** in the upper-right corner of the page.

   .. image:: ../img/workflows/3_create_wf_button.png

3. On the **Create Workflow** page, specify the details of your workflow in the **General** section.

   .. image:: ../img/workflows/4_create_wfpng.png

4. Once the details in the **General** section have been specified, you can add steps and transitions in the **Designer** section.


.. _doc-workflows-actions-create-general:

General Section
^^^^^^^^^^^^^^^

The **General** section of the create a workflow page contains the following information:


.. csv-table::
  :header: "Field", "Description"
  :widths: 10, 30


  "**Name**", "The name of the workflow."
  "**Related Entity**", "A related entity is the entity for which the workflow is created. When the workflow is active, it can be launched and executed on the records of its related entity."
  "**Exclusive Active Groups**","Exclusive Active Groups is a list of group names for which the current workflow should be active exclusively. Determining Exclusive Record Groups allows to set up mutually exclusive workflows in order to configure how they each correlate in the system. This makes it possible for only one workflow to be active, or for an entity record to use only one workflow from the group at a time."
  "**Exclusive Record Groups**","Exclusive Record Groups specify how workflows apply to certain sets of records in order to limit their applicability. This lets users create specific workflows for specific segments (subsets) of records. For example, no concurrent transitions are possible among workflows in same exclusive record group."
  "**Default Step**", "Specifying the default steps launches the workflow in a particular step by default. For instance, when you activate Opportunity Management Flow, a newly created opportunity will appear as **open**, if **Open** was specified as the default step.
  If no step is selected, all newly created records will have no workflow associated with them, and it must be launched with one of the starting transitions."
  "**Display Steps Ordered**", "Display Steps Ordered box is not checked by default.

   - **If checked**, all workflow steps are displayed in the workflow widget.
   - **If not checked**, only the steps that have actually been performed are displayed."


.. _doc-workflows-actions-create-designer:

Designer Section
^^^^^^^^^^^^^^^^

The **Designer** section consists of a table and an interactive chart representations of a workflow.

.. image:: ../img/workflows/5_table_chart_example.png

**Within the table**, you can perform the following actions for a **transition**:

-	**Update** (clicking the transition name opens an **Edit Transition** form).
-	**Clone** (clicking the |IcClone| **Clone** icon next to the transition name opens the **Clone Transition** dialog).
-	**Delete** (clicking the |IcDelete| **Delete** icon next to the transition launches name **Delete Confirmation** dialog).

**For a step**, you can perform the following action by clicking the corresponding icons in the **Actions** column:

- **Add a transition to a step** (clicking the **+** icon opens the **Add New Transition** dialog).
- **Update** (clicking the |IcEdit| **Edit** icon opens the **Edit Step** dialog).
- **Clone** (clicking the |IcClone| **Clone** icon opens the **Clone Step** dialog).
- **Delete** (clicking the |IcDelete| **Delete** icon launches the **Delete Confirmation** dialog).

.. image:: ../img/workflows/designer_table.gif

**Within the chart**, you can:

- **Add a transition** (clicking the **+ Add Transition** button at the top of the chart opens the **Add Transition** dialog).
- **Add a step** (clicking the **+ Add Step** button at the top of the chart opens the **Add Step** dialog).
- **Autosort** (clicking the **Auto Sort** button at the top of the chart automatically shapes your chart).
- **Rearrange the chart** for clearer workflow view (drag-and-drop transitions and steps in the chart as required, or click the |IcExpand| **Expand** button in the upper-right corner of the chart).

.. image:: ../img/workflows/auto_sort.gif

- **Zoom in/out** (click the |IcSearchPlus| **Zoom In** / |IcSearchMinus| **Zoom Out** button in the upper-right corner of the chart to zoom the chart in/out, or select zoom percent from the list).
- **Show transition labels** (select this check box in the upper-left corner of the chart to display transition labels in the chart).
- **Drag transitions from one step to another** (point to one of four corners of the step box, and when the cursor changes shape to the hand, click the corner and drag an arrow to another step).

.. image:: ../img/workflows/drag_transition.gif

- **Undo/Redo changes** (click the |IcReply| **Undo** / |IcShare| **Redo** button at the top of the cart to revert or restore changes made to the chart).
- **Edit/Clone/Delete** a step/transition (point to the step/transition button, and when the |IcCaretDown| arrow appears, click it, and then click the |IcEdit| **Edit** / |IcClone| **Clone** / |IcDelete| **Delete** icon.

.. note:: All actions available for transitions and steps in the table are available in the chart as well.

.. image:: ../img/workflows/6_manage_chart.png

Example Introduction
~~~~~~~~~~~~~~~~~~~~

As an example, we are going to create the **Opportunity Support Flow** workflow to show how a workflow is configured and visualized.

Add a Step
~~~~~~~~~~

To add a step to a workflow:

1. Click **Add Step** in the upper-right corner of the chart.

   .. image:: ../img/workflows/7_add_step.png

2. In the **Add Step** dialog, complete the following fields:

.. csv-table::
  :header: "Field", "Description"
  :widths: 10, 30

  "**Name**", "The name of the step that will be displayed on the entity record."
  "**Position**", "A number that determines the position of the step in the workflow. The higher the number, the further the step is from the start."
  "**Final**", "This option marks the step as the logical *end* or the *outcome* of the workflow. This is a purely logical property required for distinguishing steps for the funnel charts or creating reports with the workflow data. Marking the step final has no effect on the flow itself."


3. Click **Apply** to save the step.

Next, we are going to apply a transition for these steps.


Example
"""""""

For the sample **Opportunity Support Flow**, we will start off by creating two steps: **No Complaints** and **Complaint Received**.

.. image:: ../img/workflows/8_add_step_form.png

.. image:: ../img/workflows/9_add_step_form_2.png

Add a Transition
~~~~~~~~~~~~~~~~

To add a transition to a workflow:

1. Click **Add Transition** in the upper-right corner of the chart.

   .. image:: ../img/workflows/10_add_transition.png

2. In the **Add New Transition** dialog, click the **Info** tab, and provide the following information:

    .. csv-table::
      :header: "Field", "Description"
      :widths: 10, 30

      "**Name**", "The name of the transition that will be displayed on its button."
      "**From Step**", "The workflow step, for which the transition button should appear on the entity page."
      "**To Step**", "The step to which the workflow will progress after the transition is performed."
      "**View Form**", "Transition attributes can appear in one of two available forms: in the *popup window*, which is a default transition behavior suitable for most cases, or on the *separate page*, which should be used with care and only for attribute-heavy transitions."
      "**Warning Message**", "If you want to show a warning popup message to the user before a transition is executed, put the text of the warning into this field."
      "**Button Label**", "This text appears on the transition button and as the title of the transition form. If the button label is not provided, the value of the **Name** field is used."
      "**Button Title**", "This message appears when a user moves the pointer over the transition button. Use it to provide transition description or any other additional information."
      "**Button Icon**", "An icon that will appear on the transition button before the transition name."
      "**Button Style**", "This control specifies the visual style of the transition button."
      "**Button Preview**", "This is the live preview of the transition button as it will appear on the entity page."

   .. image:: ../img/workflows/workflows_addtransition_info.png

   .. important:: Self-transitions do not change steps in workflows (e.g. it can be a transition that launches an Edit form of a record within the same step).


3. Click the **Attributes** tab, and define the following fields:

.. csv-table::
  :header: "Field", "Description"
  :widths: 10, 30

  "**Entity Field**","This is the field of the workflow entity or its related entities that will appear on the view form of the transition. Use these if you want a user to add or edit some entity data in the transition."
  "**Label**", "Use the field if you want to change the way it is displayed on the user interface. The system label value of the entity is used by default."
  "**Required**","Select the **Required** check box if the definition of the attribute should be mandatory for the transition."
  "**+Add**", "Click **+Add** to add a new attribute."

4. Click **Apply** to save the transition.

.. tip:: After you have configured and saved your workflow, you can also configure sending email notification to the concerned parties when a transition is performed. For this, create an email notification rule as described in the :ref:`Notification Rules <system-notification-rules>` guide, and on the notification rule create page, specify the following:

         - From the **Entity** list, select the same entity as you have selected for your workflow.
         - From the **Event Name** list, select *Workflow transition*.
         - From the **Workflow** list, select your workflow.
         - From the **Transition** list, select the transition about which you want to notify concerned parties.

         All other fields must be configured as usual.

         .. image:: ../img/workflows/workflow_notification_rule.png

Example
"""""""

The following is an example of an attribute added for the **Register a Complaint** transition in the sample **Opportunity Support Flow**. The entity selected for the attribute is Additional Comments. Its label has been changed to **Specify the Complaint**.

.. image:: ../img/workflows/12_specify_complaint.png

.. image:: ../img/workflows/13_attribute_saved.png

In the same manner, specify steps, transitions and attributes required for your custom workflow.

The sample **Opportunity Support Flow** has been configured the following way:

.. image:: ../img/workflows/14_sample_flow_saved.png

.. _doc--workflows--actions--set-config-param:

Set a Workflow Configuration Parameters
---------------------------------------

To set a workflow configuration parameters:

1. In the main menu, navigate **System > Workflows**.
2. On the workflow list, click the required workflow.
3. If the workflow has configuration parameters, you can see the **Configuration** button in the upper-right corner of the workflow view page. Click this button.

   .. image:: ../img/workflows/workflow_set_config_param.png

4. On the workflow configuration page, set the required values to the configuration parameters.

   .. image:: ../img/workflows/workflow_set_config_param2.png

5. Click **Save and Close**.

.. important:: You cannot create new or delete existing configuration parameters via the user interface. See :ref:` <User Interface Limitations for Workflows>`.

               When you clone a workflow, pay attention that configuration parameters are cloned too and cannot be removed from the cloned item.

.. _doc--workflows--ui-limitations:

User Interface Limitations for Workflows
----------------------------------------

OroCRM workflows can be created from both the server-side and the user interface. However, there is a number of functions that can be defined for a workflow only from the server-side logics in the course of integration. More information on workflow implementation can be found `on this GitHub page <https://github.com/orocrm/platform/blob/master/src/Oro/Bundle/WorkflowBundle/Resources/doc/reference/workflow/index.md>`__   `and in the :ref:`Workflow Management for Developers <dev-doc--workflows>` guide.

Workflow Visualization
----------------------

Once the workflow has been configured and saved, you can see how it is visualized for the records:

- Transition buttons will be displayed in the upper-right corner of the entity record page.
- All the steps will be located at the top on the entity record page within the workflow widget.

Example
^^^^^^^

The sample **Opportunity Support Flow** has been saved and activated.

As you can see from the screenshots below, the opportunity is currently in the **No Complaints** step. Clicking **Register a Complaint** will prompt an attribute we have configured for this transition:

.. image:: ../img/workflows/15_osf_ui_1.png

.. image:: ../img/workflows/16_osf_ui_2.png

Submitting a complaint will launch an opportunity page with the **Resolve, Request Feedback and Close** transition buttons activated.

.. image:: ../img/workflows/17_osf_ui_3.png

Clicking each of these buttons will pass the user on to the next step specified in the workflow:

.. image:: ../img/workflows/18_osf_ui_4.png

**Completed steps** are green, **the step in progress** is white, **the step to follow** is grey. The completed workflow cycle will have all steps highlighted in green:

.. image:: ../img/workflows/19_osf_ui.png

As an illustration, we have unselected the **Display Steps Ordered** check box in the edit mode for the same workflow. Here is what the steps look like in this case:

.. image:: ../img/workflows/20_osf_ui_5.png

The workflow widget now displays only the current step that the opportunity is in.

.. image:: ../img/workflows/21_osf_ui_5.png

.. image:: ../img/workflows/22_osf_ui_5.png

The current step of a workflow is displayed in the **Step** column within the entity grid, as in the example below:

.. image:: ../img/workflows/23_open_opps_steps.png

Multiple Active Workflows
-------------------------

It is possible to have multiple active workflows for the same record. If you have more than one active workflow, you can separately activate each of them. In the following example, two workflows are available for one record:

.. image:: ../img/workflows/24_multiple_wfs.jpg

Workflow group can be expanded / collapsed, if necessary, by clicking the **+** **Expand** / **-** **Collapse** icon on the left of the workflow group, as illustrated below:

.. image:: ../img/workflows/25_collapse_flow.jpg

.. image:: ../img/workflows/26_collapse_flow_2.jpg

.. TODO: DOC-122, draft as the dev ticket is not completed.

.. The frontstore and backoffice workflows are united into separate groups, each can be expanded / collapsed individually.

.. The frontstore workflows are marked with the |IcCustoemrUser| icon. The backoffice workflows are marked with the |IcUser| icon.

.. .. image:: ../img/workflows/workflows_frontstore_backoffice.jpg

Workflow Management
-------------------
System Workflows
^^^^^^^^^^^^^^^^

Since system workflows are pre-implemented in the system, their management from the user interface is limited. From the grid, you can perform the following actions for system workflows:

- **Clone**:|IcClone| (copy the workflow to be able to customize it).
- **View**: |IcView| (Go to the view page of the workflow).
- **Activate/Deactivate**: |IcCheck| / |IcTimes| (activate/deactivate the workflow).

.. image:: ../img/workflows/27_manage_wf_2.png

Custom Workflows
^^^^^^^^^^^^^^^^

Cloned system workflows and workflows created in the UI from scratch are custom workflows.
You can perform the following actions for them:

- **Clone**: |IcClone| (copy the workflow to be able to customize it).
- **View**: |IcView| (go to the view page of the workflow).
- **Activate/Deactivate**: |IcCheck| / |IcTimes| (activate/deactivate the workflow).
- **Edit**: |IcEdit| (open the edit form of the workflow).
- **Delete**: |IcDelete| (delete the workflow from the system).

.. image:: ../img/workflows/28_manage_wf_1.png

Workflow Activation
^^^^^^^^^^^^^^^^^^^

You can activate a workflow by clicking on the corresponding button on the view page of the workflow:

.. image:: ../img/workflows/29_activate_wf.png

Optionally, you can select certain workflows to be deactivated. If you do not, leave the field empty and click **Activate**.

.. image:: ../img/workflows/30_activate_wf_2.png

Similarly, click **Deactivate** if you wish to deactivate the selected workflow:

.. image:: ../img/workflows/31_deactivate_wf.png

.. image:: ../img/workflows/32_deactivate_wf_2.png

Activating workflows does not happen automatically for all entities. Once the flow has been activated in **System > Workflows**, you need to start it manually for the required entities:

.. image:: ../img/workflows/33_start_wf_manually.png

It is possible to activate/deactivate workflows from the grid. See the previous section of this guide on Workflow Management to learn more about workflow grids.

User Permissions for Individual Workflows
-----------------------------------------

Multiple workflows functionality requires an ability to manage user permissions to run individual workflows. You can configure the following workflow permissions in **System > User Management > Roles**:

- Visibility of the entire workflow and its steps/current step.
- Ability to run workflow transactions.
- Ability to run every individual transaction.

.. image:: ../img/workflows/34_roles_wfs.png

Workflow Translations
---------------------

All workflow labels can be translated into other languages, providing better localizations for users from different countries.

.. image:: ../img/workflows/35_translations.png

To define a translation:

1. Click the |IcLanguage| **To Translations** icon next to the label that you want to translate. The translations list opens and is filtered to show only relevant translations.

   .. image:: ../img/workflows/translations_relevantlist.png

2. On the translation list, choose the language into which you want to translate a label, and point to the corresponding cell in the **Translated Value** column.
3. Using the :ref:`inline editor <doc-grids-actions-records-edit-inline>`, specify a new translation for a label.

   .. image:: ../img/workflows/translations_edit1.png

   .. image:: ../img/workflows/translations_edit2.png

.. You can find more information on translations in the :ref:`Manage Translations <> guide.

.. include:: ../../img/buttons/include_images.rst
   :start-after: begin
