---
title: "Office 方案安全性疑難排解"
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
  - "安全性 [Visual Studio 中的 Office 程式開發], 疑難排解"
ms.assetid: 6f85dd61-31f5-47da-8409-21ad827eb2dd
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# Office 方案安全性疑難排解
  本主題包含解決常見問題的秘訣，您可能會在設定 Office 方案的安全性時遇到這些問題。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## 無法從限制的網站安裝受信任的方案  
 如果這個網站在 Internet Explorer 限制的網站區域，列出使用者無法安裝從 Web 位置的方案。  即使方案是以受信任的憑證簽署，仍無法安裝。  
  
 部署資訊清單的 URL 可分類成系列五個區域的其中一個：  
  
-   我的電腦  
  
-   網際網路  
  
-   近端內部網路  
  
-   信任的網站  
  
-   限制的網站  
  
 如果部署資訊清單的位置已指派至限制的網站區域，則 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 不會安裝方案。  如果位置已知且可信任，則使用者可從限制的網站區域中移除該位置，並安裝方案。  如需如何管理區域的詳細資訊，請參閱[設定 ClickOnce 信任的發行者](http://msdn2.microsoft.com/zh-tw/library/ms996418.aspx)。  
  
## 已安裝 Internet Explorer 增強式安全性設定或 Internet Explorer 7 時，無法從網路檔案共用或 Web 位置安裝方案  
 Internet Explorer 增強式 Windows Server 啟動的安全設定 \(IEESC\) 和較高，因此，、Internet Explorer \(含\) 以上版本，大幅限制使用者可以瀏覽網際網路。  當使用者嘗試安裝時從網路的 Office 方案檔案共用或 Web 位置，可能會顯示下列錯誤訊息:，因為用來的憑證來簽署 *SolutionName* 的部署資訊清單不受信任， 「本應用程式中的自訂的功能無法運作。  請連絡您的系統管理員，以取得進一步協助」。  
  
 IEESC 和 Internet Explorer Explorer \(含\) 以上版本，則為，如果部署資訊清單 URL 在網際網路區域中的分類，資訊清單必須有來自信任的發行者的憑證或方案無法安裝。  未使用 IEESC 時，預設行為是提示使用者做出信任決策。  
  
 若要管理 IEESC 和 Internet Explorer 精確度的效果與較高，請識別您信任並將它們加入至其中一個受信任的安全性區域的網站和通用命名慣例 \(UNC\) 路徑 \(近端內部網路或信任網站\)。如需如何管理區域的詳細資訊， [設定 ClickOnce 信任發行者](http://go.microsoft.com/fwlink/?LinkId=94774)請參閱  
  
## 請參閱  
 [保護 Office 方案](../vsto/securing-office-solutions.md)  
  
  