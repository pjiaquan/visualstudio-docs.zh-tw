---
title: "授與信任給 Office 方案 | Microsoft Docs"
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
  - "安全性 [Visual Studio 中的 Office 程式開發]，信任"
  - "內含清單 [Visual Studio 中的 Office 程式開發]，關於內含清單"
  - "信任 [Visual Studio 中的 Office 程式開發]，2007 Office 系統"
  - "授與信任 [Visual Studio 中的 Office 程式開發]"
ms.assetid: 6c33e614-d367-4556-9e76-0f302ad0f929
caps.latest.revision: 37
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 36
---
# 授與信任給 Office 方案
  授與 Office 方案信任表示要修改的每個目標電腦安全性原則信任方案組件、應用程式資訊清單、部署資訊清單和文件。  信任可以授與 Office 方案由您或使用者。  
  
 您可以授與完全信任給 Office 方案透過簽署應用程式和部署資訊清單。  
  
 使用者將信任授與 Office 方案可以在 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 做出信任提示的信任決策。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
##  <a name="Signing"></a> 信任方案透過簽署應用程式和部署資訊清單  
 Office 方案的所有應用程式和部署資訊清單都必須以可識別發行者的憑證簽署。  憑證是進行信任決策的基礎。  
  
 在建置階段時，系統會為您建立暫存憑證，讓方案得以執行來供您偵錯。  如果您要簽署的暫時憑證的方案，系統就會提示使用者做出信任決策。  
  
 如果您用已知信任的憑證來簽署方案，方案會自動安裝而不提示使用者進行決策。  如需如何取得憑證進行簽署的詳細資訊，請參閱 [ClickOnce 和 Authenticode](../deployment/clickonce-and-authenticode.md)。  在取得憑證之後，憑證必須加入至 \[信任的發行者\] 清單中明確受到信任。  如需詳細資訊，請參閱[如何：新增信任發行者至 ClickOnce 應用程式的用戶端電腦](~/deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)。  
  
 如果開發人員以暫存憑證簽署方案，系統管理員可以在其中一項 Microsoft .NET Framework 工具中 \(資訊清單產生和編輯工具 mage.exe\) 中使用已知信任的憑證來重新簽署自訂。  如需簽署方案的詳細資訊，請參閱 [如何：簽署 Office 方案](../vsto/how-to-sign-office-solutions.md) 和 [如何：簽署應用程式和部署資訊清單](~/ide/how-to-sign-application-and-deployment-manifests.md)。  
  
##  <a name="TrustPrompt"></a> 信任使用 ClickOnce 信任提示的方案  
 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 會在沒有信任方案憑證的組織原則時，提示使用者進行信任決策。  如果使用者決定授與方案信任，則會建立一個內含清單項目，其中包含 URL 和儲存這項信任決策所需的公開金鑰 \(Public Key\)。  稍後執行信任的自訂時，就不再提示使用者。  
  
 系統管理員可以停用 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 信任提示，或只讓提示在方案是以 Authenticode 憑證簽署時顯示。  如需如何變更 MyComputer、LocalIntranet、Internet、TrustedSites 和 UntrustedSites 區域的這些設定之詳細資訊，請參閱 [如何：設定 ClickOnce 信任提示行為](~/deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)。  
  
## 請參閱  
 [保護 Office 方案](../vsto/securing-office-solutions.md)   
 [授與信任給文件](../vsto/granting-trust-to-documents.md)   
 [Office 方案安全性疑難排解](../vsto/troubleshooting-office-solution-security.md)   
 [指定 Office 方案的安全性考量](../vsto/specific-security-considerations-for-office-solutions.md)  
  
  