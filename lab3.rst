Lab 3: LTM+APM Per Request Policies
==========================================

.. toctree::
   :maxdepth: 1
   :glob:

The purpose of this lab is to familiarize the Student with Per Request Policies.
The F5 Access Policy Manager (APM) provides two types of policies.

Access Policy - The access policy runs when a client initiates a session.   Depending
on the actions you include in the access policy, it can authenticate the user
and perform group or class queries to populate session variables with data for
use throughout the session.

Per-Request Policy - After a session starts, a per-request policy runs each time
the client makes an HTTP or HTTPS request.  A per-request policy can include a
subroutine, which starts a subsession.  Multiple subsessions can exist at one
time. One access policy and one per-request are specified within a virtual server.

**It's important to note that APM first executes a per-session policy when a client
attempts to connect to a resource.   After the session starts then a per-request
policy runs on each HTTP/HTTPS request.  Per-Request policies can be utilized in a
number of different scenarios; however, in the interest of time this lab will only
demonstrate one method of leveraging Per-Request policies**

This lab will only focus on configuring Per-Request policies for controlling access
to external URL categories.


Objective:

-  Gain an understanding of Per Request policies

-  Gain an understanding of use for Per Request Policy


Lab Requirements:

-  All lab requirements will be noted in the tasks that follow

Estimated completion time: 10 minutes

Lab 1 Tasks:
-----------------

TASK 1: Create Per Session Policy
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Refer to the instructions and screen shots below:

+----------------------------------------------------------------------------------------------+
| 1. Login to your lab provided **Virtual Edition BIG-IP**                                     |
|     - On your jumphost launch Chrome and click the bigip1 link from the app shortcut menu    |
|     - Login with credentials admin/admin                                                     |
|                                                                                              |
| 2. Begin by selecting: **Access -> Profiles/Policies -> Per Session Policies** ->            |
|                                                                                              |
| 3. Click the **Create** button (far right)                                                   |
+----------------------------------------------------------------------------------------------+
| |image001|                                                                                   |
+----------------------------------------------------------------------------------------------+

+----------------------------------------------------------------------------------------------+
| 4. Enter the name of the policy, profile type, and profile scope                             |
|                                                                                              |
|    -  **Name**: **app.acme.com-PSP**                                                         |
|                                                                                              |
|    -  **Profile Type**: **All**                                                              |
|                                                                                              |
|    -  **Profile Scope**: **Profile**                                                         |
|                                                                                              |
|    -  **Accept Languages**: **English (en)**                                                 |
|                                                                                              |
|    *Note: You will need a per session policy and a per request policy but we will be         |
|           leaving the per session policy blank and performing our auth in per Request*       |
+----------------------------------------------------------------------------------------------+
| |image002|                                                                                   |
+----------------------------------------------------------------------------------------------+

+----------------------------------------------------------------------------------------------+
| 5. On the app.acme.com-PSP policy click **Edit**                                             |
|                                                                                              |
| 6. Click on the **Deny** and change the Select Ending to **Allow**                           |
|                                                                                              |
| 7. Click **Save**                                                                            |
|                                                                                              |
| 8. Click Apply policy                                                                        |
|                                                                                              |
|   *Note:  Nothing will be set in this policy we will simply establish a session and manage   |
|           all the authentication in the Per-Request Policy*                                  |
+----------------------------------------------------------------------------------------------+
| |image003|                                                                                   |
|                                                                                              |
| |image004|                                                                                   |
+----------------------------------------------------------------------------------------------+

TASK 2: Configure SAML Per Request Policy
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Refer to the instructions and screen shots below:

+----------------------------------------------------------------------------------------------+
| In Lab 1 we created all the SAML SP objects and bound them to an IdP.  Now we will           |
| leverage those objects to create our SAML Per-Request Policy                                 |
|                                                                                              |
| 1. Begin by selecting: **Access -> Profiles/Policies -> Per Request Policies** ->            |
|                                                                                              |
| 2. Click the **Create** button (far right)                                                   |
+----------------------------------------------------------------------------------------------+
| |image005|                                                                                   |
+----------------------------------------------------------------------------------------------+

+----------------------------------------------------------------------------------------------+
| 4. In the **Create New SAML IdP Connector** dialogue box, click **Browse** and select        |
|                                                                                              |
|    the **idp.acme.com_metadata.xml** file from the C:\Labfiles\SAML Metadata jump host.      |
|                                                                                              |
| 5. In the **Identity Provider Name** field enter the following: **idp.acme.com**             |
|                                                                                              |
| 6. Click **OK** on the dialogue box.                                                         |
|                                                                                              |
| *Note: The idp.acme.com_metadata.xml was created previously. Oftentimes, iDP*                |
|                                                                                              |
| *providers will have a metadata file representing their IdP service. This can be*            |
|                                                                                              |
| *imported to save object creation time as it has been done in this lab*                      |
+----------------------------------------------------------------------------------------------+
| |image005|                                                                                   |
+----------------------------------------------------------------------------------------------+

.. |image001| image:: media/Lab3/image001.png
   :width: 4.5in
   :height: 0.74in
.. |image002| image:: media/Lab3/image002.png
   :width: 4.5in
   :height: 3.37in
.. |image003| image:: media/Lab3/image003.png
   :width: 4.5in
   :height: 3.38in
.. |image004| image:: media/Lab3/image004.png
   :width: 4.5in
   :height: 0.73in
.. |image005| image:: media/Lab3/image005.png
   :width: 4.5in
   :height: 3.37in
.. |image006| image:: media/Lab3/image006.png
   :width: 4.5in
   :height: 1.15in
.. |image007| image:: media/Lab3/image007.png
   :width: 4.5in
   :height: 2.28in
.. |image008| image:: media/Lab3/image008.png
   :width: 4.5in
   :height: 0.96in
.. |image009| image:: media/Lab3/image009.png
   :width: 4.5in
   :height: 1.69in
.. |image010| image:: media/Lab3/image010.png
   :width: 4.5in
   :height: 2.94in
.. |image011| image:: media/Lab3/image011.png
   :width: 4.5in
   :height: 0.80in
.. |image012| image:: media/Lab3/image012.png
   :width: 4.5in
   :height: 1.12in
.. |image013| image:: media/Lab3/image013.png
   :width: 4.5in
   :height: 4.00in
.. |image014| image:: media/Lab3/image014.png
   :width: 4.5in
   :height: 1.48in
.. |image015| image:: media/Lab3/image015.png
   :width: 4.5in
   :height: 1.12in
.. |image016| image:: media/Lab3/image016.png
   :width: 4.5in
   :height: 1.54in
.. |image017| image:: media/Lab3/image017.png
   :width: 4.5in
   :height: 1.29in
.. |image018| image:: media/Lab3/image018.png
   :width: 4.5in
   :height: 5.46in
.. |image019| image:: media/Lab3/image019.png
   :width: 4.5in
   :height: 2.13in
.. |image020| image:: media/Lab3/image020.png
   :width: 4.5in
   :height: 1.01in
.. |image021| image:: media/Lab3/image021.png
   :width: 4.5in
   :height: 1.93in
