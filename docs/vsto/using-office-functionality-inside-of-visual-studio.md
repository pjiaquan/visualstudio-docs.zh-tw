---
title: "在 Visual Studio 中使用 Office 功能 | Microsoft Docs"
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
  - "Office 應用程式 [Visual Studio 中的 Office 程式開發]"
  - "Visual Studio 中的 Office 功能"
  - "安全性 [Visual Studio 中的 Office 程式開發], 文件保護"
ms.assetid: 593fd583-57e5-4ed5-8489-89f73b886c6c
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# 在 Visual Studio 中使用 Office 功能
  建立文件層級專案時，文件和關聯的應用程式會裝載在 Visual Studio 內，讓您可以設計並且直接使用文件。  Microsoft Office 應用程式在 Visual Studio 中開啟時，通常可如往常一般運作。  但是，有些應用程式功能可能會不同或無法存取。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## 文件保護  
 Microsoft Office Word 和 Microsoft Office Excel 提供可在專案中使用的文件保護功能。  但是，如果在文件開啟於 Visual Studio 中時啟用文件保護，您可能無法做一些設計變更。  如需詳細資訊，請參閱[文件層級方案的文件保護](../vsto/document-protection-in-document-level-solutions.md)。  
  
## 資訊版權管理  
 資訊版權管理 \(IRM\) 可在 Microsoft Office Word 和 Microsoft Office Excel 中使用。  IRM 可以協助防止未經授權的人檢視或變更敏感資訊。  但是，IRM 也會使程式碼無法執行。  如需詳細資訊，請參閱[資訊版權管理和 Managed 程式碼擴充概觀](../vsto/information-rights-management-and-managed-code-extensions-overview.md)。  
  
## 密碼保護  
 您可以設定 Microsoft Office Word 文件和 Microsoft Office Excel 活頁簿，讓不知道密碼的人無法加以開啟。  Word 和 Excel 進行密碼保護的方式不同，這會影響您的開發程序。  如需詳細資訊，請參閱[Office 文件上的密碼保護](../vsto/password-protection-on-office-documents.md)。  
  
## 請參閱  
 [文件層級方案的文件保護](../vsto/document-protection-in-document-level-solutions.md)   
 [資訊版權管理和 Managed 程式碼擴充概觀](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Office 文件上的密碼保護](../vsto/password-protection-on-office-documents.md)   
 [如何：以不執行程式碼的方式開啟 Office 方案](../vsto/how-to-open-office-solutions-without-running-code.md)  
  
  