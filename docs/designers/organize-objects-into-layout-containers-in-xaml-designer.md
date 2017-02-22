---
title: "在 XAML 設計工具中將物件組織在版面配置容器中 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 29c80c38-0fa3-48d6-b3a8-3b864f482e44
caps.latest.revision: 15
caps.handback.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 在 XAML 設計工具中將物件組織在版面配置容器中
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

想像一下您想讓物件 \(例如影像、按鈕和視訊等物件\) 出現在頁面的什麼地方。  或許您想讓物件出現在資料列和資料行中、在垂直或水平的單一行中，或在固定位置中。  
  
 在利用此機會思考頁面可能會如何出現之後，請選擇版面配置面板。  所有頁面都會以此開始，因為您需要一些項目來加入物件。  預設是 \[方格\]，但可以變更。  
  
 版面配置面板可協助您在頁面上排列物件，但不僅僅如此。  此面板還可協助您針對不同螢幕大小和解析度進行設計。  當使用者執行您的應用程式時，版面配置面板中的所有項目會調整大小以符合他們裝置的實際螢幕面積。  當然，如果您不想要讓版面配置這麼做，可以對某部分版面配置或整個版面配置覆寫該行為。  您可以使用高度和寬度屬性來控制該行為。  
  
 本頁面描述版面配置面板和控制項，然後會引導您觀賞短片，協助您開始使用。  
  
> [!NOTE]
>  某些影片可能會參考 Blend 或 Expression Blend，這些工具使用與 Visual Studio 和 Blend for Visual Studio 相同的 XAML 設計工具。  
  
## 版面配置面板  
 選擇這些版面配置面板的其中一個，開始您的頁面。  您可以有一個以上的頁面。  例如，您著手開始的是 \[方格\] 版面配置面板，然後將 \[堆疊面板\] 加入至 \[方格\] 中的區域，以便可以在該項目中垂直排列控制項。  
  
 下列版面配置面板只是最普遍使用的面板，除此之外還有其他面板。  您可以在 \[資產\] 面板中找到所有控制項。  
  
-   [格線](#Grid)  
  
-   [同型方格](#Uniform)  
  
-   [Canvas](#Canvas)  
  
-   [StackPanel](#Stack)  
  
-   [WrapPanel](#Wrap)  
  
-   [DockPanel](#Dock)  
  
###  <a name="Grid"></a> 格線  
 將物件排列成資料列和資料行。  
  
 **觀看短片：** ![設定已安裝的功能](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [使用 Grid](http://www.popscreen.com/v/6A4hj/Microsoft-Expression-Blend-Using-Grids)  
  
###  <a name="Uniform"></a> 同型方格  
 將物件排列成相等或同型的方格區域。  此面板適合用來排列影像清單。  
  
 \(僅適用於 WPF 專案\)  
  
 **觀看短片：** ![設定已安裝的功能](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [使用 UniformGrid](http://www.popscreen.com/v/6A4iq/Microsoft-Expression-Blend-Working-with-a-UniformGrid)  
  
###  <a name="Canvas"></a> Canvas  
 以任何想要的方式排列物件。  當使用者執行您的應用程式時，這些項目在螢幕上會具有固定位置。  
  
 **觀看短片：** ![設定已安裝的功能](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [使用 Canvas](http://www.popscreen.com/v/6A4hT/Microsoft-Expression-Blend-Working-with-the-Canvas)  
  
###  <a name="Stack"></a> StackPanel  
 水平或垂直排列單一行中的物件。  
  
 **觀看短片：** ![設定已安裝的功能](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [使用 StackPanel 和 WrapPanel](http://www.popscreen.com/v/6A4i5/Microsoft-Expression-Blend-Using-the-StackPanel-and-WrapPanel)  
  
###  <a name="Wrap"></a> WrapPanel  
 以循序方式從左到右排列物件。  若面板的最右側邊緣沒有足夠空間時，會將內容*「換行」*\(wrap\) 到下一行，從左到右、從上到下依此類推。  您也可以讓換行面板變成垂直方向，讓物件從上到下、從左到右地流動。  
  
 \(僅適用於 WPF 專案\)  
  
 **觀看短片：** ![設定已安裝的功能](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [使用 StackPanel 和 WrapPanel](http://www.popscreen.com/v/6A4i5/Microsoft-Expression-Blend-Using-the-StackPanel-and-WrapPanel)  
  
###  <a name="Dock"></a> DockPanel  
 排列物件，使其停留或*「停駐」*\(dock\) 在面板的一個邊緣。  
  
 \(僅適用於 WPF 專案\)  
  
 **觀看短片：** ![設定已安裝的功能](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [WPF \- DockPanel](https://www.youtube.com/watch?v=EBH_OIM-zPo)  
  
## 版面配置控制項  
 您也可以將物件加入至版面配置控制項。  控制項不像板面配置面板一樣具有豐富的功能，但會發現控制項在特定情況下很有幫助。  
  
 下列版面配置控制項只是最普遍使用的控制項，除此之外還有其他控制項。  您可以在 \[資產\] 面板中找到所有控制項。  
  
-   [框線](#Border)  
  
-   [快顯](#Popup)  
  
-   [ScrollViewer](#Scroll)  
  
-   [同型方格](#Uniform)  
  
-   [Viewbox](#View)  
  
###  <a name="Border"></a> 框線  
 在物件周圍建立框線、背景或兩者。  您可以只將一個將物件加入至 \[框線\]。  如果您要對一個以上的物件套用框線或背景，請將版面配置面板加入至 \[框線\]。  然後，將物件加入至該面板或控制項。  
  
 **觀看短片：** ![設定已安裝的功能](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [使用 Border](http://www.popscreen.com/v/6A4hB/Microsoft-Expression-Blend-Working-with-Borders)  
  
###  <a name="Popup"></a> 快顯  
 在視窗中向使用者顯示資訊或選項。  您可以只將一個將物件加入至 \[快顯\]。  根據預設，\[快顯\] 包含 \[方格\]，但您可以加以變更。  
  
###  <a name="Scroll"></a> ScrollViewer  
 可用來向下捲動頁面或頁面的區域。  您可以只將一個物件加入至 \[捲動檢視器\]，以便可以更合理地加入版面配置面板，例如 \[方格\] 或 \[堆疊面板\]。  
  
###  <a name="View"></a> Viewbox  
 縮放物件的作用就像是使用縮放控制項一樣。  您可以只將一個將物件加入至 **Viewbox**。  如果您要將該效果套用至多個物件，請將版面配置面板加入至 **ViewBox**，然後將控制項加入至該版面配置面板。  
  
 \(僅適用於 WPF 專案\)  
  
## 請參閱  
 [使用 XAML 設計工具中的項目](../designers/working-with-elements-in-xaml-designer.md)   
 [使用 XAML 設計工具建立 UI](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)