---
title: "Office 文件上的密碼保護 | Microsoft Docs"
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
  - "Office 文件 [Visual Studio 中的 Office 程式開發], 受限制的使用權限"
  - "密碼 [Visual Studio 中的 Office 程式開發], 文件保護"
  - "使用權限 [Visual Studio 中的 Office 程式開發]"
  - "活頁簿 [Visual Studio 中的 Office 程式開發], 受限制的使用權限"
ms.assetid: 9cee99c8-73c6-4f89-9d5e-7912c876ff96
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Office 文件上的密碼保護
  您可以在 Microsoft Office Word 文件和 Microsoft Office Excel 活頁簿中設定密碼，以防止不知道密碼的人開啟。  這個選項稱為 \[**密碼開啟**\]。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 您可以使用已啟用 \[**密碼開啟**\] 的現有文件和活頁簿，建立文件層級專案。  在 Visual Studio 中，已啟用 \[**密碼開啟**\] 的 Word 和 Excel 文件的行為並不相同。  
  
 如需啟用 \[**密碼開啟**\] 的詳細資訊，請參閱 Word 或 Excel 中的 \[說明\]。  
  
## Excel 和 Word 的行為  
 每次在 Visual Studio 中開啟已啟用 \[**密碼開啟**\] 的 Excel 活頁簿時，Excel 都會提示您輸入密碼。  建置方案時會再次提示您輸入密碼，因為文件在建置期間是處於開啟的狀態。  
  
 第一次在 Visual Studio 中開啟已啟用 \[**密碼開啟**\] 的 Word 文件時，Word 會提示您輸入密碼。  順利輸入密碼以後，就會從文件中移除 \[**密碼開啟**\]，此後不需要密碼就能開啟文件。  若要讓方案中的文件要求密碼後再開啟，必須在最後建置以後、在部署方案以前，啟用 \[**密碼開啟**\]。  
  
## 請參閱  
 [文件層級方案的文件保護](../vsto/document-protection-in-document-level-solutions.md)   
 [資訊版權管理和 Managed 程式碼擴充概觀](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [如何：允許程式碼在具有限制使用權限的文件背後執行](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)  
  
  