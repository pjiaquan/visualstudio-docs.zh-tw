---
title: "私用組件庫 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSIX 圖庫，私用"
  - "私用組件庫 VSIX"
ms.assetid: b6b3dee7-91c5-4556-9f69-0d56b675e83b
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# 私用組件庫
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以共用控制項、 範本和工具所開發的張貼至 *私用組件庫* 內部為您的組織，如下所示︰  
  
-   建立 Atom \(RSS\) 摘要，您的內部網路上的適當地設定中央位置 （儲存機制）。 如需詳細資訊，請參閱[如何: 建立的 Atom 摘要的私用組件庫](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md)。  
  
-   散發描述私用組件庫的.pkgdef 檔。 我們建議系統管理員想要連接到多部電腦的私用組件庫，同時此組態。  
  
## 加入擴充功能和更新 Visual Studio 中的私用組件庫  
 私用組件庫時，您可以將它加入至 **擴充功能和更新** Visual Studio 中。  
  
 ![&#91;擴充管理員&#93; 的 &#91;新增&#93; 對話方塊](~/extensibility/media/em_adddialog.png "EM\_AddDialog")  
  
#### 加入擴充功能和更新的私用組件庫  
  
1.  在功能表列上選擇 \[工具\]、\[選項\]。  
  
2.  在 **環境** 節點中，選取 **擴充功能和更新**。  
  
3.  選擇 \[**加入**\] 按鈕。  
  
4.  在 **名稱** 欄位中，輸入私用組件庫的名稱，例如 `My Gallery`。  
  
5.  在 **URL** 欄位中，輸入 Atom 摘要或裝載的私用組件庫的 SharePoint 網站的 URL。  
  
    1.  如果主機是 Atom 摘要時，連線到私用組件庫時，URL 會看起來像這樣︰ http:\/\/www.mywebsite\/mygallery\/atom.xml。  這個 URL 可以指向檔案或網路路徑。  
  
    2.  如果主機是在 SharePoint 網站，URL 會類似這樣︰ http:\/\/mysharepoint\/sites\/mygallery\/forms\/AllItems.aspx。  
  
### 管理私用組件庫  
 系統管理員可以提供私用組件庫數台電腦一次修改每一部電腦的系統登錄。 若要達成此目的，建立說明新的登錄機碼和其值的.pkgdef 檔。  此檔案的格式如下所示。  
  
```  
[$RootPath$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) … MaxInt (lowest priority) (DWORD) (uint)  
Protocol=VSGallery|Atom|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 如需詳細資訊，請參閱[如何︰ 使用登錄設定管理私人組件庫](../extensibility/how-to-manage-a-private-gallery-by-using-registry-settings.md)。  
  
## 從私用組件庫安裝擴充功能  
 您可以搜尋並安裝 Visual Studio 擴充功能中的私用庫 **擴充功能和更新**。 下列步驟使用名為私用組件庫 `My Gallery`。  
  
 ![安裝私人組件庫的 &#91;擴充管理員&#93;](~/extensibility/media/em_.png "EM\_")  
  
#### 搜尋並安裝擴充功能，從私用組件庫  
  
1.  在功能表列上，選擇 \[**工具**\]、\[**擴充功能和更新**\]。  
  
2.  在左窗格中，選取 **線上延伸**, ，然後選取 **我的組件庫**。  
  
3.  在右窗格中，選取一項擴充功能，然後選擇 **下載** \] 按鈕。  
  
## 從私用組件庫的更新延伸模組  
 新版本的 Visual Studio 擴充功能會公佈在私用組件庫中，您可以更新您已安裝的擴充功能。 下列步驟使用名為私用組件庫 `My Repository`。  
  
 ![&#91;擴充管理員&#93; 更新私人組件庫](~/extensibility/media/em_update.png "EM\_Update")  
  
#### 若要更新已安裝的擴充，從私用組件庫  
  
1.  在功能表列上，選擇 \[**工具**\]、\[**擴充功能和更新**\]。  
  
2.  在左窗格中，選取 **更新**, ，然後選取 **我的儲存機制**。  
  
3.  在右窗格中，選取一項擴充功能，然後選擇 **更新** \] 按鈕。  
  
## 請參閱  
 [尋找及使用 Visual Studio 擴充功能](../ide/finding-and-using-visual-studio-extensions.md)   
 [傳送 Visual Studio 擴充功能](../extensibility/shipping-visual-studio-extensions.md)