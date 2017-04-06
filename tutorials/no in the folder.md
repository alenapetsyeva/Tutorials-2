---
title: no in the folder
description: Create and run an ABAP application based on tables from the sample EPM data model.
primary_tag: topic>abap-development
tags: [  tutorial>beginner, topic>abap-development ]
---

## Prerequisites  
[Create an ABAP project in Eclipse](http://www.sap.com/developer/tutorials/abap-create-project.html)


## Next Steps
 Create a global ABAP class and a DDIC structure for data retrieval (coming soon).

## Details
### You will learn  
In this tutorial you will learn how to create and run an ABAP application based on tables of the SAP NetWeaver Demo sample EPM Model (details in the SAP Community [The SAP NetWeaver Enterprise Procurement Model – An Introduction](https://archive.sap.com/documents/docs/DOC-31458). So you can reiterate the tutorial on any SAP NetWeaver 7.5 system.  


### Time to Complete
**5-10 Min**.

---

[ACCORDION-BEGIN [Step 1: ](Create New ABAP Program)]
If you can't see the **$TMP** package in the Project Explorer expand your project node and the node **Favorite Packages**. Right-click on the package **$TMP** to open the context menu. Select **New** and click on **ABAP Program**.

![create ABAP program](abap-03-1.png)

A wizard appears to create a new ABAP Program. Enter  `z_invoice_items_euro` in the name field. Enter a meaningful text in the **description field**. Click **Finish** to create the report. Afterwards an editor will be opened which shows the empty report.
