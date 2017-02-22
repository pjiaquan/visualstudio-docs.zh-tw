---
title: "VSIX 專案範本 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "部署封裝"
  - "發行延伸模組"
ms.assetid: b6c82167-e2a5-4cff-8c8b-2d72e2a9092c
caps.latest.revision: 21
caps.handback.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
---
# VSIX 專案範本
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以使用在 VSIX 專案中，包裝一個或多個 Visual Studio 擴充功能的 VSIX 專案範本，並再將封裝發佈上 [Visual Studio 元件庫](http://go.microsoft.com/fwlink/?LinkID=123847) 網站。  
  
 VSIX 部署支援 VSPackages、 組件、 MEF 元件、 專案範本、 項目範本、 工具箱控制項和自訂延伸模組類型。  
  
> [!NOTE]
>  若要使用 VSIX 專案，您必須安裝 Visual Studio SDK。 如需 Visual Studio SDK 的詳細資訊，請參閱 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)。  
  
## 哪裡可以找到 VSIX 專案範本  
 VSIX 專案範本位於 **新的專案** 對話方塊。 展開 \[ **Visual Basic** 節點或 **Visual C\#** 節點，然後選擇 \[ **擴充性**。  
  
> [!TIP]
>  您應該確定該.NET Framework 4.5 或更新版本中頂端的下拉式清單中指定 **新的專案** 對話方塊。  
  
## VSIX 專案範本的用途  
 VSIX 專案範本有兩個主要用途:  
  
-   若要部署專案範本、 項目範本和其他還沒有 VSIX 支援的延伸模組。  
  
-   若要將多個延伸模組的輸出包裝成一個部署套件。  
  
 您沒有使用 VSIX 專案範本來部署 VSPackages 或其他類型的已支援的 VSIX 擴充功能。  
  
## 封裝中的空白 VSIX 專案的延伸模組  
 您可以將現有的延伸模組或沒有支援，藉由包裝在空白的 VSIX 專案中的 VSIX 擴充功能封裝。 要包裝的延伸模組必須是支援的型別 [VSIX 結構描述](../extensibility/vsix-extension-schema-2-0-reference.md)。  
  
#### 若要使用 VSIX 專案封裝延伸模組  
  
1.  建置專案，您的延伸模組所組成。  
  
2.  使用建立 VSIX 專案 **VSIX 專案** 範本。  
  
     在中開啟 Source.extension.vsixmanifest **資訊清單設計工具**。  
  
3.  在 **資產** 索引標籤上，選擇 \[ **新增** \] 按鈕。  
  
     **加入新資產** \] 對話方塊隨即出現。  
  
4.  在 **類型** 清單中，選擇要加入之擴充型別。  
  
5.  若要加入的擴充功能或內容的項目包含在目前的方案 \(例如，項目範本或編譯的組件\)，執行下列步驟:  
  
    1.  在 **來源** 清單中，選擇 **目前方案中的專案**。  
  
    2.  在 **專案** 清單中，選擇 \[延伸模組的名稱。  
  
    3.  在 **此資料夾中的內嵌** 方塊中，輸入要在其中內嵌資產，然後選擇 \[資料夾名稱 **確定** \] 按鈕。  
  
6.  若要加入的擴充功能或內容不包含目前方案中的項目，執行下列步驟:  
  
    1.  在 **來源** 清單方塊中，選擇 \[ **檔案系統上的**。  
  
    2.  在 **路徑** 欄位，輸入完整路徑編譯或壓縮的延伸模組檔案，或使用 **瀏覽** 按鈕瀏覽至檔案。  
  
    3.  在 **此資料夾中的內嵌** 方塊中，輸入要在其中內嵌資產，然後選擇 \[資料夾名稱 **確定** \] 按鈕。  
  
7.  如果您想您封裝可以包含其他擴充功能，加入這些相同的方式。  
  
8.  建置方案。  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 建置包含 VSIX 資訊清單檔案、 \[Content\_Types\].xml 檔案，以及所有您加入至專案的延伸模組資產.vsix 檔案。  
  
## 請參閱  
 [VSIX 擴充功能 2.0 結構描述參考](../extensibility/vsix-extension-schema-2-0-reference.md)   
 [尋找及使用 Visual Studio 擴充功能](../ide/finding-and-using-visual-studio-extensions.md)