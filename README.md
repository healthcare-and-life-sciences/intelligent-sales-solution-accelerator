![](/images/ahlsbanner.png)

# A-HLS Intelligent Sales Solutions Accelerator Documentation

## Overview

The Accelerator for Intelligent Sales Solutions delivers a pre-configured app to enable your liaisons to maintain and expand their network of referring physicians. The pre-built app is available for download into your Salesforce org free of charge using the controls to the right.

---

## Business Objective

Add Accelerator Objective

## Business Value and Benefits

-    Add
-    Add

-    Add
-    Add

---

## Industry Focus and Workflow

### Primary Industry:

-    Provider

### Primary User Persona:

-    Physician Liaison

### User Workflow:

-    Add
-    Add

---

## Package Includes:

### **OmniScript (#)**

-    Add
-    Add
-    Add

### **DataRaptor (#)**

-    Add
-    Add
-    Add

### **Custom Components (#)**

-    Add
-    Add
-    Add

---

## Configuration Requirements

### Pre-Install Configuration Steps:

#### These steps must be completed before installing the unmanaged package (Estimated time: 10 minutes)

1. **Ensure the following licenses are installed in your Salesforce org:**
     1. Health Cloud Sales - Enterprise Edition
     2. Salesforce Maps
     3. To confirm which licenses are installed in your org, please refer to this Help Article: [_https://help.salesforce.com/s/articleView?id=sf.distribution_assigning_user_licenses.htm&type=5_](https://help.salesforce.com/s/articleView?id=sf.distribution_assigning_user_licenses.htm&type=5)
2. **Enable “Send Email” and Allow Activities**
     1. Setup > Search for “Deliverability”
     2. Select “Deliverability”
     3. Set Send Email Access to “All Email”
     4. Refer to this Help Article for more information: [_https://help.salesforce.com/s/articleView?id=sf.data_sandbox_email_deliverability.htm&type=5_](https://help.salesforce.com/s/articleView?id=sf.data_sandbox_email_deliverability.htm&type=5)
3. **Set the Organization-Wide Email Address**
     1. Setup > Email > Organization-Wide Addresses
     2. Add a new User Selectable Organization-Wide Email Addresses and choose a Display Name of your choosing.
     3. Verify the email address set by opening the link sent to the email address.
4. **Enable Email-to-Case**
     1. Setup a Default User if one is not already specified in your settings.
     2. Turn on Email-To-Case.
     3. Refer to this Help Article for step-by-step instructions: [_https://help.salesforce.com/s/articleView?id=sf.customizesupport_enabling_email_to_case.htm&language=en_US_](https://help.salesforce.com/s/articleView?id=sf.customizesupport_enabling_email_to_case.htm&language=en_US&r=https%3A%2F%2Fwww.google.com%2F&type=5#:~:text=From%20Setup%2C%20enter%20Email%2Dto,%2DCase%2C%20and%20click%20Save)

### Installion Steps:

#### These steps must be completed to install the unmanaged package of pre-built components for PRM

1. Navigate to the following website and complete the Download Now workflow: [_https://hlsaccelerators.developer.salesforce.com/s/bundle/a9E5f000000PKvwEAG/solution-accelerator-for-provider-relationship-management_](https://hlsaccelerators.developer.salesforce.com/s/bundle/a9E5f000000PKvwEAG/solution-accelerator-for-provider-relationship-management)
     1. You will be prompted to acknowledge the Terms of Service, after which please enter your email address to receive a one-time confirmation code.
     2. Enter the confirmation code in the next step. After entering the code, you will have a chance to open these same instructions in your browser.
     3. On the final step, you will be presented with “Install In My Org” which will bring you to the Salesforce login screen. Enter your credentials for the org in which you wish to install the accelerator.
     4. Choose “Install for all users” when prompted. The installation process may take a few minutes. You will receive an email with installation confirmation when completed.
     5. If you have any issues with installation, please contact the HLS Accelerator team at [_lchristenbury@salesforce.com_](mailto:lchristenbury@salesforce.com).

### Post-Install Configuration Steps:

#### These steps must be completed to enable the included components (Estimated Time: 1-2 hours)

**Enable Path to support the visual Path flow on the Case Lightning Record Page**

1. Follow these steps to enable the Path: [_https://help.salesforce.com/s/articleView?id=sf.path_enable.htm&type=5_](https://help.salesforce.com/s/articleView?id=sf.path_enable.htm&type=5)

**Configure Salesforce Maps**

1. Create a Field Set named "Salesforce Maps Check Out" on the "Task" object. For help on how to create a Field Set, go to [https://help.salesforce.com/s/articleView?id=sf.fields_editing_field_sets.htm&type=5](https://help.salesforce.com/s/articleView?id=sf.fields_editing_field_sets.htm&type=5).
     1. Field Set Label: Salesforce Maps Check Out
     2. Field Set Name: Salesforce_Maps_Check_Out
     3. Where is this used?: Salesforce Maps
     4. Click Save.
     5. Add the following fields to the Field Set: Call Result, Comments, Check Out Date.
2. Please follow these steps to set up Salesforce Maps: [_https://help.salesforce.com/s/articleView?id=sf.salesforce_maps_setup_maps.htm&type=5_](https://help.salesforce.com/s/articleView?id=sf.salesforce_maps_setup_maps.htm&type=5)
3. The package contains predefined custom fields for the Check-In Activity Fields. Please follow the steps in this Help Article: [_https://help.salesforce.com/s/articleView?id=sf.salesforce_maps_setup_check_in_activity_fields_select.htm&type=5_](https://help.salesforce.com/s/articleView?id=sf.salesforce_maps_setup_check_in_activity_fields_select.htm&type=5)
4. At the bottom of the Activity Settings, click “Suggest” to auto-assign the custom fields.
5. In the Field Set dropdown in Activity Settings, Select the Field Set “Salesforce Maps Check Out”.

![](/images/prm1.png)

**Configure Recommendation Record -** This Recommendation will show as a Next Best Action to your liaisons as they review contact records in Salesforce. If the custom field “Enrolled in Provider Portal?” on the Contact Record is Unchecked, then this recommendation will show.

1. Download the recommendation_1.csv file in the GitHub repository here: https://github.com/healthcare-and-life-sciences/intelligent-sales-solution-accelerator
2. Use DataLoader to import the CSV file into the Recommendation object in your Salesforce org. When importing, you may leave the following fields unmapped:
     1. ID
     2. ISACTIONACTIVE
     3. ISDELETED

**Meeting Reminder Flow and Email Template**

1. This will enable the system to automatically send prospects or contacts an email reminder of an upcoming meeting 1 day before the meeting date. This helps decrease the no-show rate of prospects or contacts of liaison meetings.
2. Create a new Record-Triggered Flow titled “Meeting Reminder”
3. Configure the Flow Start as outlined below:
     1. Object: Event
     2. Trigger the Flow When: A record is created or updated
     3. Entry Conditions:
          1. Condition Requirements: Formula Evaluates to True
          2. Formula: `{!$Record.ActivityDate} > TODAY()`
          3. When to Run the Flow for Updated Records: Only when a record is updated to meet the condition requirements.
          4. Click Done.

![](/images/prm2.png)

1. Click on Start on the Flow path, then click "Add Scheduled Paths (Optional)":
     1. Set the Schedule Path to be “1 Day Before Event: Date”
     2. Time Source: Event: Due Date Only
     3. Offset Number: 1
     4. Offset Options: Day Before

![](/images/prm3.png)

1. Add a Flow Action of the following type: Email Alert
     1. NOTE: If you don’t already have an email template created to use, create the template first. For additional information on how to create an email template, refer to this Help Article: https://help.salesforce.com/s/articleView?id=sf.email_create_a_template.htm&type=5
          1. Once you have created an email template, you will need to create an Email Alert. For more information on creating email alerts, go to https://help.salesforce.com/s/articleView?id=sf.customize_wfalerts.htm&type=5.
          2. When creating the Email Alert, attach it to the Event object.
     2. Type = Email Alert
     3. Email Template = the Email template record of your choosing.
     4. Label = Meeting Reminder
     5. RecordID = `{!$Record.ActivityDate}`
2. Save and Debug your Flow to validate that it meets your business requirements
3. Once you are satisfied with the Flow, Activate the Flow.

**Add “Confirm Meeting” Quick Action to your users’ Publisher Layout**

1. The package contains a Quick Action labeled “Confirm Meeting” which enables your Physician Liaison user to send a templated email to a contact/lead to confirm an upcoming meeting in one click.
2. To enable this Quick Action, add the Quick Action to the active Publisher Layout assigned to the Physician Liaison Profile, or your Global Publisher Layout.
3. Refer to this Help Article for more information on how to edit a Publisher Layout: [_https://help.salesforce.com/s/articleView?id=sf.working_with_global_publisher_layouts.htm&type=5_](https://help.salesforce.com/s/articleView?id=sf.working_with_global_publisher_layouts.htm&type=5)

**Create a Physician Liaison Profile**

1. Navigate to Setup > Profiles > New Profile
2. Ensure the Profile is aligned to the Salesforce License Type
3. Name the Profile “Physician Liaison”
4. Ensure to align the Profile to these components:

| **Component Type**               | **Component Name**           |
| -------------------------------- | ---------------------------- |
| Lightning App                    | Intelligent Sales            |
| Default Home Page - IntSales App | Intelligent_Sales_Home_Page  |
| Case Record Type                 | IntSales Request             |
| Case Page Layout                 | IntSales Request             |
| Case Path                        | IntSales Path                |
| Case Lightning Page              | IntSales_Case_Page           |
| Task Record Type                 | IntSales Task                |
| Contact Page Layout              | Intelligent Sales            |
| Contact Lightning Page           | Contact_Record_Page_IntSales |
| Contact Compact Layout           | Intelligent Sales Layout     |
| Lead Record Type                 | Intelligent Sales            |
| Lead Page Layout                 | Intelligent Sales            |
| Lead Lightning Page              | Lead_Record_Page_IntSales    |
| Lead Compact Layout              | Intelligent Sales Layout     |
| Account Page Layout              | Account Layout - IntSales    |
| Account Lightning Page           | Account_Record_Page_IntSales |
| Account Compact Layout           | Intelligent Sales Layout     |

## Unmanaged Package Component Inventory

| Resources:                 |                                                             |                   |                                  |                                |
| -------------------------- | ----------------------------------------------------------- | ----------------- | -------------------------------- | ------------------------------ |
| **Action**                 | **Component Name**                                          | **Parent Object** | **Component Type**               | **Installation Notes**         |
| Create                     | NewEventIntSales                                            | Global            | Action                           | This is a brand new component. |
| Create                     | Account Layout - IntSales                                   | Account           | Page Layout                      | This is a brand new component. |
| Create                     | NewCaseIntSales                                             | Global            | Action                           | This is a brand new component. |
| Create                     | SendEmailIntSales                                           | Global            | Action                           | This is a brand new component. |
| Create                     | My Accounts Without Recent Activity                         |                   | Report                           | This is a brand new component. |
| Create                     | Task.Defer_Change_Date                                      | Task              | Action                           | This is a brand new component. |
| Create                     | Screen_Shot_20220215_at_45040_PM1                           |                   | Asset File                       | This is a brand new component. |
| Create                     | IntSales Request                                            | Case              | Page Layout                      | This is a brand new component. |
| Create                     | NewNoteIntSales                                             | Global            | Action                           | This is a brand new component. |
| Create                     | Intelligent Sales Performance Dashboard                     |                   | Dashboard                        | This is a brand new component. |
| Create                     | IntSales_Path                                               |                   | Path Assistant                   | This is a brand new component. |
| Create                     | Intelligent Sales                                           | Lead              | Business Process                 | This is a brand new component. |
| Create                     | My Check Ins                                                |                   | Report                           | This is a brand new component. |
| Create                     | IntSales Task                                               | Task              | Page Layout                      | This is a brand new component. |
| Create                     | SampleHealthcarePractitionerFacilityContactConfigurationPRM |                   | UI Object Relation Configuration | This is a brand new component. |
| Create                     | Intelligent Sales                                           | Lead              | Record Type                      | This is a brand new component. |
| Create                     | Intelligent Sales                                           | Lead              | Page Layout                      | This is a brand new component. |
| Create                     | Confirm Meeting                                             | Global            | Action                           | This is a brand new component. |
| Create                     | IntSales Request                                            | Case              | Business Process                 | This is a brand new component. |
| Create                     | My Completed Activities                                     |                   | Report                           | This is a brand new component. |
| Create                     | Intelligent Sales Reports                                   |                   | Report Folder                    | This is a brand new component. |
| Create                     | Intelligent Sales Layout                                    | Account           | Compact Layout                   | This is a brand new component. |
| Create                     | Case.SendEmailCase                                          | Case              | Action                           | This is a brand new component. |
| Create                     | Intelligent Sales Layout                                    | Contact           | Compact Layout                   | This is a brand new component. |
| Create                     | LogACallIntSales                                            | Global            | Action                           | This is a brand new component. |
| Create                     | IntSales Task                                               | Task              | Record Type                      | This is a brand new component. |
| Create                     | My Avg Check-In Distance from Account (f                    |                   | Report                           | This is a brand new component. |
| Create                     | NewTaskIntSales                                             | Global            | Action                           | This is a brand new component. |
| Create                     | Intelligent Sales                                           | Contact           | Page Layout                      | This is a brand new component. |
| Create                     | Salesforce Maps Check Out                                   | Task              | Field Set                        | This is a brand new component. |
| Create                     | Referral Trend Report                                       |                   | Report                           | This is a brand new component. |
| Create                     | Task.UpdatePriority_IntSales                                | Task              | Action                           | This is a brand new component. |
| Create                     | General                                                     | Task              | Record Type                      | This is a brand new component. |
| Create                     | My New Leads                                                | Lead              | List View                        | This is a brand new component. |
| Create                     | NewContactIntSales                                          | Global            | Action                           | This is a brand new component. |
| Create                     | IntSales Request                                            | Case              | Record Type                      | This is a brand new component. |
| Create                     | My Meeting Quality                                          |                   | Report                           | This is a brand new component. |
| Create                     | My Time Spent On Site                                       |                   | Report                           | This is a brand new component. |
| Create                     | SampleHealthcarePractitionerFacilityAccountConfigurationPRM |                   | UI Object Relation Configuration | This is a brand new component. |
| Create                     | Intelligent Sales Layout                                    | Lead              | Compact Layout                   | This is a brand new component. |
| Create                     | Intelligent Sales Dashboards                                |                   | Dashboard Folder                 | This is a brand new component. |
| Create                     | New_Task_IntSales                                           | Global            | Action                           | This is a brand new component. |
| Create                     | Task.UpdateStatusIntSales                                   | Task              | Action                           | This is a brand new component. |
|                            |                                                             |                   |                                  |                                |
| Apps:                      |                                                             |                   |                                  |                                |
| **Action**                 | **Component Name**                                          | **Parent Object** | **Component Type**               | **Installation Notes**         |
| Create                     | Intelligent Sales                                           |                   | App                              | This is a brand new component. |
|                            |                                                             |                   |                                  |                                |
| Flows:                     |                                                             |                   |                                  |                                |
| **Action**                 | **Component Name**                                          | **Parent Object** | **Component Type**               | **Installation Notes**         |
| Create                     | Reminder to Enroll in Provider Portal                       |                   | Flow Version                     | This is a brand new component. |
|                            |                                                             |                   |                                  |                                |
| Fields:                    |                                                             |                   |                                  |                                |
| **Action**                 | **Component Name**                                          | **Parent Object** | **Component Type**               | **Installation Notes**         |
| Create                     | Check Out Distance From Record (mi)                         | Activity          | Custom Field                     | This is a brand new component. |
| Create                     | Check Out Date/Time                                         | Activity          | Custom Field                     | This is a brand new component. |
| Create                     | Meeting Quality                                             | Activity          | Custom Field                     | This is a brand new component. |
| Create                     | Check In Date/Time                                          | Activity          | Custom Field                     | This is a brand new component. |
| Create                     | Enrolled in Provider Portal?                                | Contact           | Custom Field                     | This is a brand new component. |
| Create                     | Time on Site Minutes                                        | Activity          | Custom Field                     | This is a brand new component. |
| Create                     | Days Since Last Visit                                       | Account           | Custom Field                     | This is a brand new component. |
| Create                     | Check Out Date                                              | Activity          | Custom Field                     | This is a brand new component. |
|                            |                                                             |                   |                                  |                                |
| Recommendation Strategies: |                                                             |                   |                                  |                                |
| **Action**                 | **Component Name**                                          | **Parent Object** | **Component Type**               | **Installation Notes**         |
| Create                     | Referring Providers                                         |                   | Recommendation Strategy          | This is a brand new component. |
|                            |                                                             |                   |                                  |                                |
| Pages:                     |                                                             |                   |                                  |                                |
| **Action**                 | **Component Name**                                          | **Parent Object** | **Component Type**               | **Installation Notes**         |
| Create                     | Intelligent_Sales_UtilityBar                                |                   | Lightning Page                   | This is a brand new component. |
| Create                     | Lead_Record_Page_IntSales                                   |                   | Lightning Page                   | This is a brand new component. |
| Create                     | Intelligent_Sales_Home_Page                                 |                   | Lightning Page                   | This is a brand new component. |
| Create                     | IntSales_Case_Page                                          |                   | Lightning Page                   | This is a brand new component. |
| Create                     | Contact_Record_Page_IntSales                                |                   | Lightning Page                   | This is a brand new component. |
| Create                     | Account_Record_Page_IntSales                                |                   | Lightning Page                   | This is a brand new component. |

---

## Assumptions

1. A customer has licenses for Industry Cloud and Salesforce Maps. These solutions have all been installed and are functional.
2. A customer is assuming Salesforce Lightning Experience — not Classic.
3. The Accelerator uses the Lightning Design System standards and look. Customers may want to apply their own branding which can be achieved.

---

## Revision History

-    **Revision Short Description (Month Day, Year)**

-    -    Add
     -    Add

-
