---
title: "MSBuild 錯誤 MSB3122 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GenerateManifest.FileAssociationsApplicationNotFullTrust"
helpviewer_keywords: 
  - "MSB3122"
ms.assetid: 523e4160-f165-437a-9f19-fb2ec77d46f5
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3122
**MSB3122: 使用檔案關聯需要完全信任。**  
  
 發行設定檔案關聯的應用程式時，該應用程式必須是完全信任的應用程式。  
  
### 若要更正這個錯誤  
  
-   啟用 ClickOnce 安全性設定，並將應用程式設定為完全信任的應用程式。  如需詳細資訊，請參閱 [如何：啟用 ClickOnce 安全性設定](../deployment/how-to-enable-clickonce-security-settings.md)。  
  
## 請參閱  
 [專案設計工具、發行頁](../ide/reference/publish-page-project-designer.md)   
 [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)   
 [ClickOnce 應用程式的程式碼存取安全性](../deployment/code-access-security-for-clickonce-applications.md)