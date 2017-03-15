---
title: "針對測試和實際執行伺服器部署 ClickOnce 應用程式但不重新簽章 | Microsoft Docs"
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
  - "應用程式更新, ClickOnce"
  - "ClickOnce 應用程式, 部署但不重新簽章"
  - "ClickOnce 部署, 不重新簽署"
  - "deploymentProvider 標記"
  - "資料清單 [ClickOnce]"
  - "更新位置 [ClickOnce]"
ms.assetid: 1218a98d-1ad5-4eef-95dd-0e0b3c44168c
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 針對測試和實際執行伺服器部署 ClickOnce 應用程式但不重新簽章
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本主題將討論 .NET Framework 3.5 版新增的一項 ClickOnce 功能，此功能可從多個網路位置部署 ClickOnce 應用程式，而無須重新簽章或變更 ClickOnce 資訊清單。  
  
> [!NOTE]
>  不過，在部署新版本的應用程式時，最好還是重新簽章。  請盡可能使用重新簽章方法。  如需詳細資訊，請參閱[Mage.exe \(資訊清單產生和編輯工具\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)。  
  
 協力廠商開發人員和獨立軟體廠商 \(ISV，Independent Software Vendor\) 可選擇採用此功能，讓其客戶更容易更新其應用程式。  這項功能可在下列情況使用：  
  
-   更新應用程式時 \(並非第一次安裝應用程式\)。  
  
-   電腦上只有一個應用程式組態時。  例如，如果應用程式設定為指向兩個不同的資料庫，就無法使用此功能。  
  
## 從部署資訊清單排除 deploymentProvider  
 在 .NET Framework 2.0 和 .NET Framework 3.0 中，安裝在系統上以供離線可用性的任何 ClickOnce 應用程式，必須在其部署資訊清單中指定 `deploymentProvider`。  `deploymentProvider` 通常是指更新位置，這是 ClickOnce 檢查是否有任何應用程式更新的位置。  由於有此需求，再加上需要應用程式發行者簽署其部署，公司要更新來自廠商或其他協力廠商的 ClickOnce 應用程式並不容易。  此外，要從相同網路的多個位置部署同一個應用程式也變得更困難。  
  
 .NET Framework 3.5 的 ClickOnce 功能經過改進後，協力廠商就可以將 ClickOnce 應用程式提供其他組織，再由組織部署應用程式在其網路上。  
  
 為使用這項功能，ClickOnce 應用程式的開發人員必須將 `deploymentProvider` 排除在其部署資訊清單之外。  這表示，使用 Mage.exe 建立部署資訊清單時，請排除 `-providerUrl` 引數，或如果使用 MageUI.exe 產生部署資訊清單，確定將 \[**應用程式資訊清單**\] 索引標籤上的 \[**啟動位置**\] 文字方塊保留空白。  
  
## deploymentProvider 與應用程式更新  
 從 .NET Framework 3.5 開始，在部署 ClickOnce 應用程式供線上和離線使用時，不再需要在部署資訊清單中指定 `deploymentProvider`。  這可讓您封裝和簽署部署，但同時又可讓其他公司在其網路上部署應用程式。  
  
 請注意，排除 `deploymentProvider` 的應用程式清單在更新時無法變更其安裝位置，除非再提供的更新中再次加入 `deploymentProvider` 標記。  
  
 以下是說明此點的兩個範例。  在第一個範例中，您會發行一個沒有 `deploymentProvider` 標記的 ClickOnce 應用程式，並要求使用者從 http:\/\/www.adatum.com\/MyApplication\/ 安裝該應用程式。  如果您決定要從 http:\/\/subdomain.adatum.com\/MyApplication\/ 發行應用程式的下個更新，就無法在位於 http:\/\/www.adatum.com\/MyApplication\/ 的部署資訊清單反應此點。  您可進行下列任一步驟：  
  
-   告知使用者解除安裝舊版，然後從新位置安裝新版本。  
  
-   在 http:\/\/www.adatum.com\/MyApplication\/ 上加入更新，其中包含指向 http:\/\/www.adatum.com\/MyApplication\/ 的 `deploymentProvider`。  接著稍後再發行另一個更新，並加上指向 http:\/\/subdomain.adatum.com\/MyApplication\/ 的 `deploymentProvider`。  
  
 在第二個範例中，您會發行指定 `deploymentProvider` 的 ClickOnce 應用程式，稍後決定要移除它。  一旦沒有 `deploymentProvider` 的新版本下載到用戶端，您就無法重新導向更新所使用的路徑，直到發行還原 `deploymentProvider` 的應用程式版本。  如同第一個範例，`deploymentProvider` 必須在一開始指向目前的更新位置，而非新位置。  在此例中，如果您嘗試插入指向 http:\/\/subdomain.adatum.com\/MyApplication\/ 的 `deploymentProvider`，則下一個更新會失敗。  
  
## 建立部署  
 如需逐步指引以建立可以從不同的網路位置進行的部署，請參閱[逐步解說：手動部署不需要重新簽署而且會保留商標資訊的 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md)。  
  
## 請參閱  
 [Mage.exe \(資訊清單產生和編輯工具\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)   
 [MageUI.exe \(Manifest Generation and Editing Tool, Graphical Client\)](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md)