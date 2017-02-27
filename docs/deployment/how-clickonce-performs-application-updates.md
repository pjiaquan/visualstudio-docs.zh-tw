---
title: "ClickOnce 執行應用程式更新的方式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "部署應用程式 [ClickOnce], 應用程式更新"
  - "更新, ClickOnce"
ms.assetid: d54313c2-cf0c-420d-b151-99953a95f0bb
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 9
---
# ClickOnce 執行應用程式更新的方式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ClickOnce 會使用應用程式部署資訊清單內所指定的檔案版本資訊，以決定是否要更新應用程式的檔案。  在更新開始之後，ClickOnce 會使用「*檔案修補*」\(File Patching\) 技術來避免應用程式檔案的多餘下載。  
  
## 檔案修補  
 在更新應用程式時，除非檔案已變更，否則 ClickOnce 不會下載應用程式新版本的所有檔案。  它會比較目前應用程式之應用程式資訊清單內所指定之檔案的雜湊簽章以及新版本資訊清單內的簽章。  如果檔案的簽章不同，則 ClickOnce 會下載新版本。  如果簽章相符，表示檔案未變更版本。  在這種情形下，ClickOnce 會複製現有的檔案，並用於應用程式的新版本中；  這種方法可避免 ClickOnce 在可能只有一兩個檔案變更時，必須再次下載整個應用程式。  
  
 檔案修補也適用於使用 <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A> 和 <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroupAsync%2A> 方法視需要下載的組件上。  
  
 如果您使用 Visual Studio 編譯應用程式，則會針對所有檔案產生新的雜湊簽章，而不管您是否重建整個專案。  在這種情形下，雖然可能只有幾個組件已變更，也會將所有的組件下載到用戶端。  
  
 檔案修補不適用於標記為資料並儲存在資料目錄中的檔案，  一定會下載這些檔案，無不論檔案的雜湊簽章為何。  如需資料目錄的詳細資訊，請參閱[在 ClickOnce 應用程式中存取本機和遠端資料](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)。  
  
## 請參閱  
 [選擇 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)   
 [選擇 ClickOnce 部署策略](../deployment/choosing-a-clickonce-deployment-strategy.md)