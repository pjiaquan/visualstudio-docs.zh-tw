---
title: "自訂 XML 組件概觀"
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
  - "自訂 XML 組件 [Visual Studio 中的 Office 程式開發]"
  - "自訂 XML 組件 [Visual Studio 中的 Office 程式開發], 關於"
  - "資料 [Visual Studio 中的 Office 程式開發], 自訂 XML 組件"
  - "文件 [Visual Studio 中的 Office 程式開發], 自訂 XML 組件"
  - "在文件中內嵌 XML 資料 [Visual Studio 中的 Office 程式開發]"
  - "Excel [Visual Studio 中的 Office 程式開發], 自訂 XML 組件"
  - "Office 文件 [Visual Studio 中的 Office 程式開發], 自訂 XML 組件"
  - "Office Open XML 格式 [Visual Studio 中的 Office 程式開發]"
  - "Word [Visual Studio 中的 Office 程式開發], 自訂 XML 組件"
  - "XML [Visual Studio 中的 Office 程式開發], 自訂 XML 組件"
  - "XML 檔案格式 [Visual Studio 中的 Office 程式開發]"
  - "XML 組件 [Visual Studio 中的 Office 程式開發]"
ms.assetid: a14119dc-59e8-4614-94f1-08c92bdf7300
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# 自訂 XML 組件概觀
  您可以將 XML 資料嵌入某些 Microsoft Office 應用程式的文件中。  當您將 XML 資料嵌入文件時，該資料就稱為*「自訂 XML 組件」*\(custom XML part\)。  
  
 您可以使用 Visual Studio 中的 VSTO 增益集或文件層級方案，建立和修改文件中的自訂 XML 組件。  您不必啟動 Microsoft Office 應用程式，即可建立和修改自訂 XML 組件。  
  
 **適用對象：**本主題資訊適用於 Excel、PowerPoint 及 Word 的文件層級專案及 VSTO 增益集專案。  如需詳細資訊，請參閱＜[依 Office 應用程式和專案類型提供的功能](../vsto/features-available-by-office-application-and-project-type.md)＞。  
  
> [!NOTE]  
>  Visual Studio 也可讓您快取文件層級自訂中的資料物件。  雖然這項功能與自訂 XML 組件有些類似，但兩者卻不相同。  如需詳細資訊，請參閱[文件層級自訂中的快取資料](../vsto/cached-data-in-document-level-customizations.md)。  
  
## 了解自訂 XML 組件  
 2007 Microsoft Office system 中加入了自訂 XML 組件以及 Open XML 格式。  這些格式包含適用於 Excel、PowerPoint 和 Word 的新 XML 檔案格式 \(例如 .xlsx、.pptx 和 .docx\)。  這些格式的文件是由 XML 檔案 \(也稱為*「XML 組件」*\(XML part\) 所組成，而這些 XML 檔會組織在 ZIP 封存的資料夾中。  大部分的 XML 組件都是用來協助定義文件結構和狀態的內建組件。  但是，文件也可包含自訂 XML 組件，您可以使用這類自訂 XML 組件在文件中儲存任意 XML 資料。  
  
 XML 檔案格式讓應用程式能夠以舊式二進位檔案格式 \(例如 .xls、.ppt 和 .doc\) 無法辦到的方式來處理文件。  即使未安裝 Microsoft Office，任何可讀取 ZIP 封存的應用程式都可以檢查和修改文件的內容。  
  
 如需 Open XML 和自訂 XML 組件之結構的詳細資訊，請參閱下列文章：  
  
-   [Office \(2007\) Open XML 檔案格式簡介](http://msdn.microsoft.com/zh-tw/96018532-f62c-4da7-bbff-16b96a483fbf)  
  
-   [如何：操作 Open XML 格式文件](http://msdn.microsoft.com/zh-tw/c989d4e2-053d-4e1f-83be-257c608b343f)  
  
-   [逐步解說：Word 2007 XML 格式](http://msdn.microsoft.com/zh-tw/fc1afcb2-27fb-4608-9f29-11b7bd23ea4a)  
  
-   [使用 Open XML 格式建置 Word 2007 文件](http://msdn.microsoft.com/zh-tw/59a46f4e-5a5a-4dac-86e5-7dfd43330766)  
  
> [!NOTE]  
>  Excel、Word 和 PowerPoint 也可讓您在以二進位檔案格式儲存的文件中使用自訂 XML 組件。  但是，如果文件是以二進位格式儲存，您就無法在未啟動 Microsoft Office 應用程式的情況下加入或修改自訂 XML 組件。  
  
## 建立和修改自訂 XML 組件  
 當文件在 Office 應用程式中開啟時，或者當文件為關閉狀態時，即使未安裝 Microsoft Office，您仍可以建立或修改自訂 XML 組件。  
  
### 在執行 Office 應用程式時修改 XML 組件  
 您可以使用文件層級自訂或 VSTO 增益集來處理自訂 XML 組件。  如果您使用文件層級自訂，則通常會在自訂的文件中處理自訂 XML 組件。  如果您使用 VSTO 增益集，則可以在任何於應用程式中開啟的文件建立或修改自訂 XML 組件。  
  
 若要使用 Visual Studio 建立自訂 XML 組件，請將新的 <xref:Microsoft.Office.Core.CustomXMLPart> 加入文件的 <xref:Microsoft.Office.Core.CustomXMLParts> 集合中。  如需詳細資訊，請參閱下列主題：  
  
-   [如何：將自訂 XML 組件加入至文件層級自訂](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)  
  
-   [如何：使用 VSTO 增益集將自訂 XML 組件加入文件中](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)  
  
### 在未啟動 Office 應用程式的情況下修改 XML 組件  
 您可以在未啟動 Excel、PowerPoint 或 Word 的情況下，加入或修改自訂 XML 組件。  如果您想要在尚未安裝 Microsoft Office 應用程式的電腦 \(例如伺服器\) 上處理文件中的 XML 資料，則這種做法會很實用。  
  
 若要在不啟動 Microsoft Office 的情況下加入自訂 XML 組件，請使用 Open XML SDK 中的類別。  這些類別是專為存取 Office 文件特有的 Open XML 內容而設計。  例如，若要將自訂 XML 組件加入 Excel 活頁簿，您可以使用 [WorkbookPart](http://msdn.microsoft.com/zh-tw/d011e6f4-77dd-d02d-66ef-dc4a9e7b26f2) 物件的 [AddNewPart\<T\>](http://msdn.microsoft.com/zh-tw/47c348c0-77ab-a504-5097-bcd6a213921a) 方法。  如需詳細資訊，請參閱 [Open XML SDK 2.0](http://msdn.microsoft.com/zh-tw/f6a9ae68-7989-4208-97f5-3c945137a0ab)。  
  
## 將自訂 XML 組件繫結至 Word 內容控制項  
 您可以將 Word 方案中的內容控制項繫結至自訂 XML 組件中的項目。  當內容控制項繫結至自訂 XML 組件時，自訂 XML 組件中的資料會顯示在內容控制項的使用者介面 \(UI\) 中。  如果使用者編輯控制項中的文字，對應的 XML 項目就會自動更新。  同樣地，如果自訂 XML 組件中的項目值變更，繫結至該 XML 項目的內容控制項就會顯示新的資料。  如需詳細資訊，請參閱[內容控制項](../vsto/content-controls.md)。  
  
## 請參閱  
 [文件層級自訂中的 XML 結構描述和資料](../vsto/xml-schemas-and-data-in-document-level-customizations.md)   
 [如何：將自訂 XML 組件加入至文件層級自訂](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)   
 [如何：使用 VSTO 增益集將自訂 XML 組件加入文件中](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)   
 [內容控制項](../vsto/content-controls.md)   
 [逐步解說：將內容控制項繫結至自訂 XML 組件](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)  
  
  