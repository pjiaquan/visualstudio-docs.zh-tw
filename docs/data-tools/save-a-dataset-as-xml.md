---
title: "如何：將資料集儲存為 XML | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "資料 [Visual Studio], 另存為 XML"
  - "資料集 [Visual Basic], 另存為 XML"
  - "儲存資料"
  - "XML [Visual Basic], 資料集"
ms.assetid: 68b8327c-ae05-49ff-b9ba-99183e70b52c
caps.latest.revision: 11
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：將資料集儲存為 XML
您可以藉由呼叫資料集上可用的 XML 方法，存取資料集中的 XML 資料。  如需以 XML 格式儲存資料，您可以呼叫 <xref:System.Data.DataSet> 的 <xref:System.Data.DataSet.GetXml%2A> 方法或 <xref:System.Data.DataSet.WriteXml%2A> 方法。  
  
 呼叫 <xref:System.Data.DataSet.GetXml%2A> 方法時，就會傳回一個字串，其中含有資料集的所有資料表中格式化成 XML 的資料。  
  
 呼叫 <xref:System.Data.DataSet.WriteXml%2A> 方法時，則會將 XML 格式的資料傳送至您所指定的檔案中。  
  
### 若要將資料集中的資料當做 XML 儲存至變數中  
  
-   由於 <xref:System.Data.DataSet.GetXml%2A> 方法會傳回 <xref:System.String>，所以請宣告 <xref:System.String> 型別的變數並將 <xref:System.Data.DataSet.GetXml%2A> 方法的結果指派給它。  
  
     [!code-vb[VbRaddataSaving#12](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_1.vb)]
     [!code-cs[VbRaddataSaving#12](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_1.cs)]  
  
### 若要將資料集中的資料當做 XML 儲存至檔案中  
  
-   <xref:System.Data.DataSet.WriteXml%2A> 方法含有多項多載。  下列程式碼將示範如何將資料儲存至檔案中，因此請宣告變數並將要儲存檔案的有效路徑指派給它。  
  
     [!code-vb[VbRaddataSaving#13](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_2.vb)]
     [!code-cs[VbRaddataSaving#13](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_2.cs)]  
  
## 請參閱  
 [DataSet、DataTable 及 DataView](../Topic/DataSets,%20DataTables,%20and%20DataViews.md)   
 [Visual Studio 中的 XML 工具](../xml-tools/xml-tools-in-visual-studio.md)   
 [準備您的應用程式以接收資料](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [連接至 Visual Studio 中的資料](../data-tools/connecting-to-data-in-visual-studio.md)   
 [準備您的應用程式以接收資料](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [將資料擷取至您的應用程式中](../data-tools/fetching-data-into-your-application.md)   
 [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [在您的應用程式中編輯資料](../data-tools/editing-data-in-your-application.md)   
 [驗證資料](../Topic/Validating%20Data.md)   
 [儲存資料](../data-tools/saving-data.md)