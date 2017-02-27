---
title: "如何︰ 更新 Visual Studio 擴充功能 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "更新套件"
  - "更新擴充功能"
  - "新的封裝版本"
ms.assetid: 93f79774-7b79-4dd6-94ad-13698f72c257
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# 如何︰ 更新 Visual Studio 擴充功能
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您也可以使用您的系統上更新 Visual Studio 擴充功能 **擴充功能和更新** 來安裝更新的版本。 如果您建立擴充功能的更新的版本，您可以更新 VSIX 資訊清單中的版本號碼遞增，它表示。  
  
 當連入的擴充功能的 VSIX 資訊清單具有相同的已安裝更新 `ID` 以及已安裝的其中一個較高 `Version` 數字。 如果 `Version` 數目相同或更低，無法安裝封裝。 如果 `ID` 值不相符，尚未安裝的封裝視為不同的副檔名。  
  
 為了避免衝突，在開發期間，我們建議您解除安裝舊版擴充功能，在進行中，並也解除安裝或停用任何可能發生衝突的延伸。  
  
### 若要更新您的系統上的擴充  
  
1.  在 \[工具\] 功能表上，按一下 \[擴充功能和更新\]。  
  
2.  在左窗格中，按一下 \[ **更新**。  
  
3.  在中間窗格中，按一下您想要安裝的更新。  
  
     更新的延伸模組的版本號碼會顯示在右窗格中，以及其他資訊。  
  
4.  在右窗格的底端，按一下 \[ **更新**。  
  
### 若要發行之擴充功能更新  
  
1.  在 Visual Studio 中，開啟您想要更新的擴充功能的解決方案。 進行變更。  
  
    > [!IMPORTANT]
    >  不帶正負號所有的使用者擴充功能執行不會自動取得更新。 您應一律登入您的擴充功能。  
  
2.  在 **方案總管\] 中**, ，開啟 source.extension.manifest。  
  
3.  在 \[資訊清單設計工具中，數字值增加 **版本** 欄位。  
  
4.  將方案儲存並建立該檔案。  
  
5.  新.vsix 檔案 （在專案的 \\bin\\Debug\\ 資料夾） 上傳至 [Visual Studio 元件庫](http://go.microsoft.com/fwlink/?LinkID=123847) 網站。  
  
     具有較早版本的擴充功能的使用者便會開啟 **擴充功能和更新**, ，新的版本會出現在 **更新** 清單，前提是此工具設為自動尋找更新。  
  
     您可以啟用或停用自動檢查更新底部 **更新** 窗格 \(**啟用\/停用自動偵測可用更新的**\)，哪些變更 **檢查更新** 中設定 **工具 \/ 選項 \/ 環境 \/ 擴充功能和更新**。  
  
    > [!NOTE]
    >  從 Visual Studio 2015 Update 2 開始，您可以指定 \(在 **工具 \/ 選項 \/ 環境 \/ 擴充功能和更新**\) 是否要自動更新每個使用者擴充功能、 所有的使用者擴充功能或兩個 （預設值）。  
  
## 請參閱  
 [VSIX 套件的剖析](../extensibility/anatomy-of-a-vsix-package.md)   
 [尋找及使用 Visual Studio 擴充功能](../ide/finding-and-using-visual-studio-extensions.md)