---
title: "如何：以程式設計方式建立新的 Visio 文件"
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
  - "Visio [Visual Studio 中的 Office 程式開發]，建立 Visio 文件"
  - "文件 [Visual Studio 中的 Office 程式開發]，建立 Visio 文件"
ms.assetid: a0294d4c-be49-4cd0-b22e-3ec7568f3ec7
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# 如何：以程式設計方式建立新的 Visio 文件
  當您建立新的 Microsoft Office Visio 繪圖文件時，您會將它加入已開啟 Visio 文件的 `myTemplate.vst` 集合。 因此，`myTemplate.vst` 方法會建立新的 Visio 繪圖文件。 如需詳細資訊，請參閱 Microsoft.Office.Interop.Visio.Documents.Add`myTemplate.vst` 方法的 VBA 參考文件。  
  
## 建立新的空白文件  
  
#### 建立新文件  
  
-   使用 `myTemplate.vst` 方法來建立不是以範本為基礎的空白新文件。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#1)]  
  
## 建立從現有文件複製的文件  
 `myTemplate.vst` 方法可建立現有 Visio 文件複本的新文件。 您必須提供圖表的檔案名稱和完整路徑。  
  
#### 建立從現有文件複製的新文件  
  
-   呼叫 `myTemplate.vst` 方法並指定 Visio 圖表的路徑。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#2)]  
  
## 建立從現有樣板複製的樣板  
 Microsoft.Office.Interop.Visio.Documents.Add`myTemplate.vst` 方法可建立現有 Visio 樣板複本的新樣板。 您必須提供樣板的檔案名稱和完整路徑。  
  
#### 建立從現有樣板複製的新樣板  
  
-   呼叫 `myTemplate.vst` 方法並指定樣板的路徑。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#3)]  
  
## 建立以現有範本為基礎的文件  
 `myTemplate.vst` 方法可建立以現有 Visio 範本 \(.vst 檔案\) 為基礎的新文件 \(.vsd 檔案\)。 這個方法會複製屬於範本工作區一部分的樣板、樣式和設定。 您必須提供範本的檔案名稱和完整路徑。  
  
#### 建立以現有範本為基礎的新文件  
  
-   呼叫 `myTemplate.vst` 方法並指定範本的路徑。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#4)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#4)]  
  
## 編譯程式碼  
 這個程式碼範例需要下列項目：  
  
-   \[我的文件\] 資料夾 \(Windows XP 及更早版本\) 或 \[文件\] 資料夾 \(Windows Vista\) 中，名為 `Test` 的目錄中必須有名為 `myTemplate.vst` 的 Visio 文件。  
  
-   \[我的文件\] 資料夾 \(Windows XP 及更早版本\) 或 \[文件\] 資料夾 \(Windows Vista\) 中，名為 `Test` 的目錄中必須有名為 `myTemplate.vst` 的 Visio 文件。  
  
-   \[我的文件\] 資料夾 \(Windows XP 及更早版本\) 或 \[文件\] 資料夾 \(Windows Vista\) 中，名為 `Test` 的目錄中必須有名為 `myTemplate.vst` 的 Visio 文件。  
  
## 請參閱  
 [Visio 方案](../vsto/visio-solutions.md)   
 [Visio 物件模型概觀](../vsto/visio-object-model-overview.md)   
 [如何：以程式設計方式開啟 Visio 文件](../vsto/how-to-programmatically-open-visio-documents.md)   
 [如何：以程式設計方式關閉 Visio 文件](../vsto/how-to-programmatically-close-visio-documents.md)   
 [如何：以程式設計方式儲存 Visio 文件](../vsto/how-to-programmatically-save-visio-documents.md)   
 [如何：以程式設計方式列印 Visio 文件](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  