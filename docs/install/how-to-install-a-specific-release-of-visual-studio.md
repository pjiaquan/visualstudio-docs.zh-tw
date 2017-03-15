---
title: "如何：安裝特定版本的 Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "安裝特定版本, Visual Studio"
ms.assetid: d69ad0f8-f0a0-438e-a0ef-777c4868f139
caps.latest.revision: 20
caps.handback.revision: 11
author: "TerryGLee"
ms.author: "tglee"
manager: "ghogen"
---
# 如何：安裝特定版本的 Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

我們時常更新 Visual Studio 安裝程式，以便讓您取得最新且最佳化版本的選擇性功能。  但如果您想安裝舊版 Visual Studio 2015 \(例如包括 iOS 支援，且在 Update 1 之前版本的 Visual Studio 2015\)，則必須強制 Visual Studio 安裝程式使用舊版的功能資訊清單檔案。 本文說明如何執行這項操作。  
  
## 安裝目前版本  
 自 Visual Studio 2015 的初始版本之後，我們已更新一次安裝程式引擎、至少五次資訊清單檔案。  這表示，如果您在乾淨且已連線到網際網路的電腦上[立即下載與執行 Visual Studio 安裝程式](https://www.visualstudio.com/downloads/download-visual-studio-vs)，安裝程式就會安裝 Visual Studio 2015 Update 1，其中包含最新的產品改善，以及較新的選擇性功能和工具最近版本。  
  
## 安裝舊版  
 您可以建立並掛接 ISO 映像，也可以下載並直接啟動 Web 安裝程式，然後以其他命令列參數 \(例如 \/CustomInstallPath、\/Full、\/InstallSelectableItems、\/NoRestart 等\) 附加 .exe 檔。 控制安裝 Visual Studio 的方式。  
  
 下表包含一些特定時間點的情節，以及您必須傳遞給 Enterprise 版本 Web 安裝程式的必要命令列參數。 \(Community 或 Professional 版的 Web 安裝程式也都可以使用相同參數\)  
  
|Visual Studio 2015 版本|要執行的項目|要使用的命令列|安裝程式的動作|  
|---------------------------|------------|-------------|-------------|  
|Visual Studio Enterprise \(最新的公開版本\)|Visual Studio Enterprise Update 1 \(可從 [VisualStudio.com](https://www.visualstudio.com/en-us/products/vs-2015-product-editions.aspx) 取得\)|`vs_enterprise.exe` **Note:**  此安裝的預設行為可提供最新的選擇性功能，因此不需要任何命令列參數。|Visual Studio 安裝程式會使用最新的 feed.xml 並安裝最新的檔案|  
|Visual Studio Enterprise \(原始 RTM，但包含 Update 1 前的更新\)|Visual Studio Enterprise RTM \(可從 [MSDN 訂用帳戶下載頁面](https://msdn.microsoft.com/en-us/subscriptions/downloads/)取得\)|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/3/6/1/36188D5F-479F-4A46-BF55-6AE5928D1EBB/20151102.3/enu/feed.xml`|Visual Studio 安裝程式將使用在 Update 1 發行前現用的 feed.xml|  
|Visual Studio Enterprise Update 1 \(沒有其他 Update 1 時期更新的原始 Update 1\)|Visual Studio Enterprise Update 1 \(可從 [MSDN 訂用帳戶下載頁面](https://msdn.microsoft.com/en-us/subscriptions/downloads/)取得\)|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/3/2/A/32A1974F-D236-43C1-8981-97DDCBAEF14A/20151201.1/enu/feed.xml`|Visual Studio 安裝程式將使用 Update 1 提供的 feed.xml|  
|Visual Studio Enterprise \(沒有更新的原始 RTM\)|Visual Studio Enterprise RTM \(可從 [MSDN 訂用帳戶下載頁面](https://msdn.microsoft.com/en-us/subscriptions/downloads/)取得\)|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/5/7/B/57BF5016-E4F0-4EB5-BE27-2BFA87E7723F/20150713.1/enu/feed.xml`|Visual Studio 安裝程式將使用 RTM 提供的 feed.xml|  
  
> [!IMPORTANT]
>  請根據您想要使用的語言，以下列其中一個值取代 "enu"\(英文\)：  
>   
>  -   chs \(中文 \(簡體\)\)  
> -   cht \(中文 \(繁體\)\)  
> -   csy \(捷克文\)  
> -   deu \(德文\)  
> -   esn \(西班牙文\)  
> -   fra \(法文\)  
> -   ita \(義大利文\)  
> -   jpa \(日文\)  
> -   kor \(韓文\)  
> -   plk \(波蘭文\)  
> -   ptb \(葡萄牙文\)  
> -   rus \(俄文\)  
> -   trk \(土耳其文\)  
  
## 請參閱  
 [安裝 Visual Studio](../Topic/Installing%20Visual%20Studio%202015.md)