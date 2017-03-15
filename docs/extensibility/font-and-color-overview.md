---
title: "字型和色彩概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "編輯器 [Visual Studio SDK]、 字型和色彩"
  - "字型和色彩控制項 [Visual Studio SDK] 編輯器"
ms.assetid: 2203e4e7-8b7f-44ec-8884-6ff718d4f278
caps.latest.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 22
---
# 字型和色彩概觀
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本主題將討論文字的字型和色彩設定，在[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]整合式的開發環境 \(IDE\)。  也介紹類別和顯示項目\] 的概念，並且說明如何 VSPackages 和核心編輯器\] 中使用的文字屬性。  
  
## 字型和色彩\] 屬性頁  
 您可以管理屬性中的顯示文字的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]透過整合式的開發環境 \(IDE\) **字型和色彩**屬性頁。  若要尋找**字型和色彩** 屬性頁，在 **工具** \] 功能表中，按一下 **選項**。  展開 \[**環境**\]，然後按一下 \[**字型和色彩**\]。  
  
## 分類和顯示的項目  
 字型和色彩會組織成**類別** 和 **顯示項目**。  
  
-   A **類別** 是一種邏輯或功能的容器，將多個 **顯示項目**。  
  
     一份**類別** 在 **顯示設定為** 下拉式方塊中的 **字型和色彩**屬性頁。  
  
-   A **的顯示項目**是妥善定義的文字實體，例如註解、 字串或顯示時以色彩標示，是一個控制結構。  
  
 每個**的顯示項目** 內唯一定義 **類別**包含該控制項。  因此，一個以上**類別** 能 **的顯示項目**具有相同的名稱。  
  
## VSPackage 控制字型和色彩  
 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]允許 VSPackages 至：  
  
-   定義字型和色彩**類別**。  
  
-   指定的字型和色彩用來呈現**顯示項目**。  
  
-   互動**字型和色彩**屬性頁。  
  
-   彙總的多重**類別**成群組。  
  
-   保存在 \[預設值的變更。  
  
 有兩種方法中的字型和色彩選取項目與互動[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]。  
  
-   其中一個方法就是*語法色彩*。  它由自訂現有的 VSPackage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]實作語言服務，並建立來源編輯器的編輯器。  
  
     只能有一個**類別** 支援這項機制，也就是， **文字編輯器**。  
  
-   更廣泛的另一種方式可支援其他所有**類別**和顯示文字時，在原始檔編輯器以外的使用者介面元件。  如需詳細資訊，請參閱 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>。  
  
## 核心編輯器的文字設定  
 語言服務物件的核心編輯器的字型和色彩設定由**文字編輯器類別顯示設定為** 下拉式方塊中的 **字型和色彩**屬性頁。  
  
 當使用編輯器，您應該使用特殊的字型和色彩控制機制語言服務所提供控制和擴充**文字編輯器**設定。  此機制稱為 「 *語法色彩* ，並提供：  
  
-   簡化的技術，來管理字型和色彩顯示項目。  
  
     如需詳細資訊，請參閱 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>和 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>。  
  
-   定義良好而且通用最佳化的顏色標示的機制。  
  
     如需詳細資訊，請參閱 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>。  
  
-   兩者都可以使用內建顯示項目，從**文字編輯器類別** ，並將其擴充。  
  
     如需詳細資訊，請參閱 [如何: 使用內建可設定色彩的項目](../extensibility/internals/how-to-use-built-in-colorable-items.md)和 [自訂色彩的項目](../extensibility/internals/custom-colorable-items.md)。  
  
-   自動的永續性的目前狀態包括內建的自訂顯示的項目**文字編輯器**類別。  
  
 如需有關語法色彩請參閱[語法著色在舊版語言服務](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)。  
  
## 請參閱  
 [在編輯器中的傳統介面](../extensibility/legacy-interfaces-in-the-editor.md)   
 [語法著色在舊版語言服務](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)