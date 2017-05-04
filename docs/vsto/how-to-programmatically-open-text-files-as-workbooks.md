---
title: "如何：以程式設計方式將文字檔開啟為活頁簿 | Microsoft Docs"
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
  - "文字 [Visual Studio 中的 Office 程式開發], 文字檔"
  - "文字檔, 開啟為活頁簿"
  - "活頁簿, 開啟文字檔"
ms.assetid: 056ae3d0-7fe7-4c28-a2a5-5a948baee0e6
caps.latest.revision: 47
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 46
---
# 如何：以程式設計方式將文字檔開啟為活頁簿
  您可以將文字檔當做活頁簿來開啟。  您必須傳入要開啟的文字檔案名稱。  您可以指定幾個選擇性參數，例如從哪個資料列編號開始剖析，以及檔案中的資料行格式等參數。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## 範例  
 [!code-csharp[Trin_VstcoreExcelAutomation#80](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#80)]
 [!code-vb[Trin_VstcoreExcelAutomation#80](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#80)]  
  
## 編譯程式碼  
 這個範例需要下列元件：  
  
-   名為 `Test.txt` 的逗號分隔文字檔，其中至少包含三行文字。  
  
-   要儲存在 C 磁碟中的 `Test.txt` 文字檔案。  
  
## 請參閱  
 [使用活頁簿](../vsto/working-with-workbooks.md)   
 [如何：以程式設計方式開啟活頁簿](../vsto/how-to-programmatically-open-workbooks.md)   
 [如何：以程式設計方式建立新活頁簿](../vsto/how-to-programmatically-create-new-workbooks.md)   
 [如何：以程式設計方式儲存活頁簿](../vsto/how-to-programmatically-save-workbooks.md)   
 [如何：以程式設計方式關閉活頁簿](../vsto/how-to-programmatically-close-workbooks.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)  
  
  