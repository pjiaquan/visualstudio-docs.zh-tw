---
title: "如何：允許程式碼在具有限制使用權限的文件背後執行 | Microsoft Docs"
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
  - "程式碼 [Visual Studio 中的 Office 程式開發], 在限制的文件背後執行"
  - "文件 [Visual Studio 中的 Office 程式開發], 受限制的使用權限"
  - "資訊版權管理 [Visual Studio 中的 Office 程式開發]"
  - "IRM [Visual Studio 中的 Office 程式開發]"
  - "Office 文件 [Visual Studio 中的 Office 程式開發], 受限制的使用權限"
  - "使用權限 [Visual Studio 中的 Office 程式開發]"
ms.assetid: d037eae5-cf83-4be0-85ba-05e9f7d570e1
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# 如何：允許程式碼在具有限制使用權限的文件背後執行
  您可以使用 Microsoft Office 的資訊版權管理 \(IRM\) 功能，限制文件或活頁簿的使用權限。  預設不允許執行受限制之 Microsoft Office Word 文件或 Microsoft Office Excel 活頁簿後置的程式碼。  您可以變更這個預設值，讓 Managed 程式碼擴充可以存取物件模型，而方案也能夠執行。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 您必須是文件或活頁簿的作者或者具有「完全控制」存取權限，才可以變更使用權限設定。  
  
### 若要允許程式碼以限制的權限在文件背後執行  
  
1.  在 Word 或 Excel 中開啟文件或活頁簿。  
  
2.  按一下索引標籤， \[**檔案**\] 指向 \[**準備**\]，指向 \[**限制使用權限**\]，然後按一下 \[**受限制的存取**\]。  
  
    > [!NOTE]  
    >  第一次使用時，會提示您安裝 Windows Rights Management 用戶端。  而在安裝用戶端之後，可能就需要重複這些步驟。  
  
3.  選取 \[**使用權限**\] 對話方塊中的 \[**限制此文件的權限**\]，然後按一下 \[**更多選項**\]。  
  
4.  在 \[**使用者的其他權限**\] 之下，選取 \[**以程式存取內容**\]。  
  
 Word 或 Excel 就會允許以程式設計方式存取物件模型。  
  
## 請參閱  
 [資訊版權管理和 Managed 程式碼擴充概觀](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [文件層級方案的文件保護](../vsto/document-protection-in-document-level-solutions.md)   
 [Office 文件上的密碼保護](../vsto/password-protection-on-office-documents.md)   
 [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)   
 [保護 Office 方案](../vsto/securing-office-solutions.md)   
 [部署 Office 方案](../vsto/deploying-an-office-solution.md)  
  
  