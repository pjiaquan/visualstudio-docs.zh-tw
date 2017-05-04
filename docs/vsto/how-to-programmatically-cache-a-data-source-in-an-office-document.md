---
title: "如何：以程式設計方式快取 Office 文件的資料來源 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "資料 [Visual Studio 中的 Office 程式開發], 快取"
  - "資料快取 [Visual Studio 中的 Office 程式開發], 以程式設計的方式"
  - "資料集 [Visual Studio 中的 Office 程式開發], 快取"
  - "Office 應用程式 [Visual Studio 中的 Office 程式開發], 資料"
  - "StartCaching 方法"
ms.assetid: 70b3fc06-7534-407e-898b-36f84e9a7516
caps.latest.revision: 43
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# 如何：以程式設計方式快取 Office 文件的資料來源
  您可以用程式設計方式將資料物件加入至文件的資料快取中，方法是呼叫主項目 \(例如 <xref:Microsoft.Office.Tools.Word.Document>、<xref:Microsoft.Office.Tools.Excel.Workbook> 或 <xref:Microsoft.Office.Tools.Excel.Worksheet>\) 的 `StartCaching` 方法。  透過呼叫主項目的 `StopCaching` 方法，移除資料快取中的資料物件。  
  
 雖然 `StartCaching` 方法和 `StopCaching` 方法都是私用的 \(Private\)，不過它們會出現在 IntelliSense 中。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 當您使用 `StartCaching` 方法，將資料物件加入至資料快取時，不需要使用 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> 屬性 \(Attribute\) 宣告資料物件。  不過，資料物件必須符合某些需求，才能加入至資料快取。  如需詳細資訊，請參閱[快取資料](../vsto/caching-data.md)。  
  
### 若要以程式設計方式快取資料物件  
  
1.  請在類別層級而不是在方法內宣告資料物件。  這個範例會假設您要宣告名為 `dataSet1` 的 <xref:System.Data.DataSet>，而您想以程式設計方式快取它。  
  
     [!code-csharp[Trin_VstcoreDataExcel#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#12)]
     [!code-vb[Trin_VstcoreDataExcel#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#12)]  
  
2.  執行個體化資料物件，然後呼叫文件或工作表執行個體的 `StartCaching` 方法，並傳入資料物件的名稱。  
  
     [!code-csharp[Trin_VstcoreDataExcel#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#13)]
     [!code-vb[Trin_VstcoreDataExcel#13](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#13)]  
  
### 若要停止快取資料物件  
  
1.  呼叫文件或工作表執行個體的 `StopCaching` 方法，並傳入資料物件的名稱。  這個範例會假設您有名為 `dataSet1` 的 <xref:System.Data.DataSet>，並想要停止快取它。  
  
     [!code-csharp[Trin_VstcoreDataExcel#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#14)]
     [!code-vb[Trin_VstcoreDataExcel#14](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#14)]  
  
    > [!NOTE]  
    >  請勿從文件或工作表之 `Shutdown` 事件的事件處理常式呼叫 `StopCaching`。  引發 `Shutdown` 事件時，修改資料快取就為時已晚。  如需 `Shutdown` 事件的詳細資訊，請參閱[Office 專案中的事件](../vsto/events-in-office-projects.md)。  
  
## 請參閱  
 [快取資料](../vsto/caching-data.md)   
 [如何：快取資料供離線使用或於伺服器上使用](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [如何：快取受密碼保護文件中的資料](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [存取伺服器文件中的資料](../vsto/accessing-data-in-documents-on-the-server.md)   
 [儲存資料](../data-tools/saving-data.md)  
  
  