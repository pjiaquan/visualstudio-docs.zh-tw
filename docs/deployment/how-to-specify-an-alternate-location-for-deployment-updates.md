---
title: "如何：指定部署更新的其他位置 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ClickOnce 部署, 更新"
  - "部署更新, 替代位置"
ms.assetid: 7faacd35-2638-492d-80f6-6b57e5f820de
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 如何：指定部署更新的其他位置
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以從 CD 或檔案共用開始安裝 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式，不過應用程式必須檢查網站上的定期更新。  您可以在部署資訊清單中指定更新的替代位置，以便讓應用程式能在初始安裝過後從網站更新自己。  
  
> [!NOTE]
>  您的應用程式必須設定在本機安裝才能使用這項功能。  如需詳細資訊，請參閱[逐步解說：手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)。  此外，如果您從網路安裝 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式，設定替代位置就會讓 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 使用這個位置來進行初始安裝和所有的後續安裝。  如果由本機安裝您的應用程式 \(例如，從 CD 進行\)，就會使用原始媒體執行初始安裝，而且所有的後續更新都會使用替代的位置。  
  
### 使用 MageUI.exe \(Windows Form 公用程式\) 指定更新的替代位置  
  
1.  開啟 .NET Framework 命令提示字元並輸入：  
  
     **mageui.exe**  
  
2.  在 \[**檔案**\] 功能表上，選擇 \[**開啟**\] 以開啟應用程式的部署資訊清單。  
  
3.  選取 \[**部署選項**\] 索引標籤。  
  
4.  在名為 \[**啟動位置**\] 的文字方塊中，輸入目錄的 URL，其會包含應用程式更新的部署資訊清單。  
  
5.  儲存部署資訊清單。  
  
### 使用 Mage.exe 指定更新的替代位置  
  
1.  開啟 .NET Framework 命令提示字元。  
  
2.  使用下列命令設定更新位置。  在此範例中，**HelloWorld.exe.application** 是 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式資訊清單的路徑，始終會具有 .application 副檔名，**http:\/\/adatum.com\/Update\/Path** 則是 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 將會檢查應用程式更新的 URL。  
  
     **Mage \-Update HelloWorld.exe.application \-ProviderUrl http:\/\/adatum.com\/Update\/Path**  
  
3.  儲存檔案。  
  
    > [!NOTE]
    >  現在您需要以 Mage.exe 重新簽署檔案。  如需詳細資訊，請參閱[逐步解說：手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)。  
  
## .NET Framework 安全性  
 如果是從離線媒體如 CD 安裝您的應用程式，而且電腦位於線上，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 便會先檢查在部署資訊清單中，由 `<deploymentProvider>` 標籤指定的 URL，以決定更新位置是否含有應用程式的更新版本。  如果確實如此，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 便會從該處直接安裝應用程式，而非從初始安裝目錄進行，Common Language Runtime \(CLR\) 則會使用 `<deploymentProvider>` 判斷您應用程式的信任層級。  如果電腦離線，或是無法連接至 `<deploymentProvider>`，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 便會從 CD 安裝，CLR 則會根據安裝點授與信任；若為 CD 安裝，這表示您的應用程式會得到完整的信任。  所有的後續更新都會繼承該信任層級。  
  
 所有使用 `<deploymentProvider>` 的 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式，都應該在其應用程式資訊清單中，明確宣告其所需要的權限，如此應用程式就不會在不同的電腦上得到不同的信任層級。  
  
## 請參閱  
 [逐步解說：手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [ClickOnce 部署資訊清單](../deployment/clickonce-deployment-manifest.md)   
 [保護 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md)   
 [選擇 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)