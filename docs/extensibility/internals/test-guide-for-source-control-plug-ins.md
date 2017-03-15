---
title: "原始檔控制外掛程式的測試指南 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "外掛程式，原始檔控制"
  - "原始檔控制 [Visual Studio SDK]，測試外掛程式"
  - "原始檔控制外掛程式的測試"
  - "測試，原始檔控制外掛程式"
  - "原始檔控制外掛程式，測試指南"
ms.assetid: 13b74765-0b7c-418e-8cd9-5f2e8db51ae5
caps.latest.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 26
---
# 原始檔控制外掛程式的測試指南
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

本區段說明如何測試您的原始檔控制外掛程式的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  提供廣泛的概觀最常見的測試區域，以及某些更錯綜複雜便可能發生問題的區域。  本概觀，並不適合視為完整的測試案例的清單。  
  
> [!NOTE]
>  有些錯誤修正和最新的改良功能[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 可能會發現問題的現有原始檔控制外掛程式先前不時所遇到的使用舊版的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  強烈建議您測試現有原始檔控制外掛程式的這一節中所列舉的區域，即使沒有已變更外掛程式自前一版的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
## 常見的準備工作  
 一部電腦[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ，目標原始檔控制外掛程式安裝，就需要。  第二部機器，同樣的設定後可用於 \[開啟\] 從原始檔控制的測試部分。  
  
## 術語的定義  
 這個測試 」 指南的目的使用以下的詞彙定義：  
  
 用戶端專案  
 任何專案中可用的型別[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]支援原始檔控制整合 \(比方說， [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]， [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]，或[!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)]\)。  
  
 Web 專案  
 有四種類型的 Web 專案： 檔案系統、 本機 IIS、 遠端站台，以及 FTP。  
  
-   檔案系統專案已建立的本機路徑，但它們不需要的 「 網際網路資訊服務 \(IIS\) 」，因為它們底色圖案，透過內部存取，而且可以放在 IDE 內部的與用戶端專案很類似，從原始檔控制下進行安裝。  
  
-   IIS 的本機專案是由 IIS 安裝在同一部電腦上，而且可存取的 URL，指向 \[本機電腦所使用。  
  
-   遠端站台的專案也會建立在 IIS 服務\] 下，但它們會放在原始檔控制在 IIS 伺服器電腦上，而不是從內部[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE。  
  
-   FTP 專案可以透過遠端 FTP 伺服器來存取，但不能置於原始檔控制。  
  
 登記  
 方案或專案原始檔控制之下的另一種說法。  
  
 版本儲存區  
 正在透過原始檔控制外掛程式 API 存取原始檔控制資料庫。  
  
## 本章節所包含的測試區域  
  
-   [測試區 1︰ 加入開啟從原始檔控制](../../extensibility/internals/test-area-1-add-to-open-from-source-control.md)  
  
    -   回復 1a： 將方案加入至原始檔控制  
  
    -   案例 1b： 從原始檔控制開啟方案  
  
    -   案例 1： 將方案從原始檔控制  
  
-   [取得從原始檔控制的測試區域 2:](../../extensibility/internals/test-area-2-get-from-source-control.md)  
  
-   [測試區 3︰ 簽出\/復原簽出](../../extensibility/internals/test-area-3-check-out-undo-checkout.md)  
  
    -   案例 3： 簽出\/復原簽出  
  
    -   回復 3a： 簽出  
  
    -   案例 3b： 中斷連接簽出  
  
    -   案例 3 c： 編輯查詢的查詢儲存 \(QEQS\)  
  
    -   回復 3d: 無訊息簽出  
  
    -   回復 3e： 復原簽出  
  
-   [簽入的測試區域 4:](../../extensibility/internals/test-area-4-check-in.md)  
  
    -   回復匣 4a： 修改項目  
  
    -   案例 4b: 新增檔案  
  
    -   案例 4 c： 加入專案  
  
-   [測試區 5︰ 變更原始檔控制](../../extensibility/internals/test-area-5-change-source-control.md)  
  
    -   回復 5a： 繫結  
  
    -   回復 5b： 解除繫結  
  
    -   回復 5c： 重新繫結  
  
-   [測試區域 6: 刪除](../../extensibility/internals/test-area-6-delete.md)  
  
-   [測試區域 7: 共用](../../extensibility/internals/test-area-7-share.md)  
  
-   [測試地區 8: 外掛程式切換](../../extensibility/internals/test-area-8-plug-in-switching.md)  
  
    -   回復 8a： 自動變更  
  
    -   回復 8b： 解決方案架構的變更  
  
## 請參閱  
 [原始檔控制外掛程式](../../extensibility/source-control-plug-ins.md)