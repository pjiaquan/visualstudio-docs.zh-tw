---
title: "如何：建立及修改自訂文件屬性 | Microsoft Docs"
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
  - "自訂文件屬性"
  - "文件 [Visual Studio 中的 Office 程式開發]，屬性"
  - "文件屬性 [Visual Studio 中的 Office 程式開發]"
ms.assetid: 99d9dfaf-891f-4f3b-a580-67362afdaf34
caps.latest.revision: 47
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 46
---
# 如何：建立及修改自訂文件屬性
  上列 Microsoft Office 應用程式提供與文件一起儲存的內建屬性。 此外，如果您有想要與文件一起儲存的其他資訊，則可以建立和修改自訂文件屬性。  
  
 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]  
  
 請使用文件的 `Value` 屬性來處理自訂屬性。 例如，在 Microsoft Office Excel 的文件層級專案中，請使用  類別的 `Value` 屬性。 在 Excel 的 VSTO 增益集專案中，則請使用  物件的 `Value` 屬性。 這些屬性會傳回 `Value` 物件，它是  物件的集合。 您可以按照名稱或集合內的索引，使用該集合的 `Value` 屬性擷取特定的屬性。  
  
 下列範例示範如何在 Excel 的文件層級自訂中加入自訂屬性，並指派該屬性的值。  
  
 `Value` 如需相關的示範影片，請參閱[如何：存取和操作 Microsoft Word 中的自訂文件屬性？](http://go.microsoft.com/fwlink/?LinkId=136772)。  
  
## 範例  
 [!code-csharp[Trin_VstcoreProgramming#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/CS/ThisWorkbook.cs#6)]
 [!code-vb[Trin_VstcoreProgramming#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/VB/ThisWorkbook.vb#6)]  
  
## 穩固程式設計  
 嘗試存取未定義之屬性的 `Value` 屬性將會引發例外狀況。  
  
## 請參閱  
 [VSTO 增益集程式設計](../vsto/programming-vsto-add-ins.md)   
 [文件層級自訂程式設計](../vsto/programming-document-level-customizations.md)   
 [如何：從文件屬性中讀取及寫入](../vsto/how-to-read-from-and-write-to-document-properties.md)  
  
  