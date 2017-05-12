---
title: "資訊版權管理和 Managed 程式碼擴充概觀"
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
  - "文件 [Visual Studio 中的 Office 程式開發], 受限制的使用權限"
  - "資訊版權管理 [Visual Studio 中的 Office 程式開發]"
  - "IRM [Visual Studio 中的 Office 程式開發]"
  - "Office 文件 [Visual Studio 中的 Office 程式開發], 受限制的使用權限"
  - "版權管理 [Visual Studio 中的 Office 程式開發]"
  - "活頁簿 [Visual Studio 中的 Office 程式開發], 受限制的使用權限"
ms.assetid: 9728f5fe-9122-48e7-b0a3-9f5e0a16164f
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# 資訊版權管理和 Managed 程式碼擴充概觀
  Microsoft Office Word 和 Microsoft Office Excel 提供了資訊版權管理 \(IRM\)，這項功能可以協助您防止未經授權的人員檢視或更改敏感的資訊。  如需資訊版權管理如何運作的詳細資訊，請參閱特定 Office 應用程式中的說明。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## 以受限的使用權限執行文件的後置程式碼  
 如果方案包含使用 IRM 的文件或活頁簿，根據預設，Word 和 Excel 不允許執行任何程式碼。  如果您是文件的作者或者具有「完全控制」存取權限，您可以變更這個預設值，讓您的方案能夠執行。  如需詳細資訊，請參閱[如何：允許程式碼在具有限制使用權限的文件背後執行](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)。  
  
 IRM 可防止使用 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ServerDocument>，擷取或操作文件中的快取資料。  
  
## 使用者對使用 Managed 程式碼擴充的文件限制使用權限  
 對方案中文件或活頁簿具有「完全控制」存取權限的任何人都可以使用 IRM 限制使用權限。  例如，如果會計部門的某位使用者使用了一個會自動從資料庫將資料填入工作表的方案，這位使用者可能會希望只對自己部門的人員授與「變更」存取權限，其他人則授與「讀取」存取權限。  當使用者加入受限的使用權限時，根據預設，工作表的後置程式碼將無法執行，而且工作表也不會填入資料。  
  
 若要修正這個問題，必須由對這個文件或活頁簿具有「完全控制」存取權限的人變更預設的使用權限設定，允許以程式的方式存取物件模型。  如需詳細資訊，請參閱[如何：允許程式碼在具有限制使用權限的文件背後執行](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)。  
  
## 請參閱  
 [文件層級方案的文件保護](../vsto/document-protection-in-document-level-solutions.md)   
 [Office 文件上的密碼保護](../vsto/password-protection-on-office-documents.md)   
 [保護 Office 方案](../vsto/securing-office-solutions.md)   
 [部署 Office 方案](../vsto/deploying-an-office-solution.md)   
 [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)  
  
  