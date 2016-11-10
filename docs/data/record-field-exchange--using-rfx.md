---
title: "Record Field Exchange: Using RFX"
ms.custom: na
ms.date: "10/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: na
ms.suite: na
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: na
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RFX (ODBC), implementing"
ms.assetid: ada8f043-37e6-4d41-9db3-92c997a61957
caps.latest.revision: 8
ms.author: "mblome"
manager: "ghogen"
translation.priority.ht: 
  - "cs-cz"
  - "de-de"
  - "es-es"
  - "fr-fr"
  - "it-it"
  - "ja-jp"
  - "ko-kr"
  - "pl-pl"
  - "pt-br"
  - "ru-ru"
  - "tr-tr"
  - "zh-cn"
  - "zh-tw"
---
# Record Field Exchange: Using RFX
This topic explains what you do to use RFX in relation to what the framework does.  
  
> [!NOTE]
>  This topic applies to classes derived from [CRecordset](../mfcref/crecordset-class.md) in which bulk row fetching has not been implemented. If you are using bulk row fetching, bulk record field exchange (Bulk RFX) is implemented. Bulk RFX is similar to RFX. To understand the differences, see [Recordset: Fetching Records in Bulk (ODBC)](../data/recordset--fetching-records-in-bulk--odbc-.md).  
  
 The following topics contain related information:  
  
-   [Record Field Exchange: Working with the Wizard Code](../data/record-field-exchange--working-with-the-wizard-code.md) introduces the main components of RFX and explains the code that the MFC Application Wizard and **Add Class** (as described in [Adding an MFC ODBC Consumer](../mfcref/adding-an-mfc-odbc-consumer.md)) write to support RFX and how you might want to modify the wizard code.  
  
-   [Record Field Exchange: Using the RFX Functions](../data/record-field-exchange--using-the-rfx-functions.md) explains writing calls to the RFX functions in your `DoFieldExchange` override.  
  
 The following table shows your role in relation to what the framework does for you.  
  
### Using RFX: You and the Framework  
  
|You|The framework|  
|---------|-------------------|  
|Declare your recordset classes with a wizard. Specify names and data types of field data members.|The wizard derives a `CRecordset` class and writes a [DoFieldExchange](../Topic/CRecordset::DoFieldExchange.md) override for you, including an RFX function call for each field data member.|  
|(Optional) Manually add any needed parameter data members to the class. Manually add an RFX function call to `DoFieldExchange` for each parameter data member, add a call to [CFieldExchange::SetFieldType](../Topic/CFieldExchange::SetFieldType.md) for the group of parameters, and specify the total number of parameters in [m_nParams](../Topic/CRecordset::m_nParams.md). See [Recordset: Parameterizing a Recordset (ODBC)](../data/recordset--parameterizing-a-recordset--odbc-.md).||  
|(Optional) Manually bind additional columns to field data members. Manually increment [m_nFields](../Topic/CRecordset::m_nFields.md). See [Recordset: Dynamically Binding Data Columns (ODBC)](../data/recordset--dynamically-binding-data-columns--odbc-.md).||  
|Construct an object of your recordset class. Before using the object, set the values of its parameter data members, if any.|For efficiency, the framework prebinds the parameters, using ODBC. When you pass parameter values, the framework passes them to the data source. Only the parameter values are sent for requeries, unless the sort and/or filter strings have changed.|  
|Open a recordset object using [CRecordset::Open](../Topic/CRecordset::Open.md).|Executes the recordset's query, binds columns to field data members of the recordset, and calls `DoFieldExchange` to exchange data between the first selected record and the recordset's field data members.|  
|Scroll in the recordset using [CRecordset::Move](../Topic/CRecordset::Move.md) or a menu or toolbar command.|Calls `DoFieldExchange` to transfer data to the field data members from the new current record.|  
|Add, update, and delete records.|Calls `DoFieldExchange` to transfer data to the data source.|  
  
## See Also  
 [Record Field Exchange (RFX)](../data/record-field-exchange--rfx-.md)   
 [Record Field Exchange: How RFX Works](../data/record-field-exchange--how-rfx-works.md)   
 [Recordset: Obtaining SUMs and Other Aggregate Results (ODBC)](../data/recordset--obtaining-sums-and-other-aggregate-results--odbc-.md)   
 [CRecordset Class](../mfcref/crecordset-class.md)   
 [CFieldExchange Class](../mfcref/cfieldexchange-class.md)   
 [Macros, Global Functions, and Global Variables](../Topic/Macros,%20Global%20Functions,%20and%20Global%20Variables.md)