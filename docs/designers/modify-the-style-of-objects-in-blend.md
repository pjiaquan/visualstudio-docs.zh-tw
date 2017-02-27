---
title: "在 Blend 中修改物件的樣式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 31192d2c-5b84-41bc-94c0-898638c170bd
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# 在 Blend 中修改物件的樣式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

若要自訂物件，最簡單的方式就是在 \[**屬性**\] 窗格中設定屬性。  
  
 如果您要重複使用設定或多組設定，請建立可重複使用的資源。  這可能是*「樣式」*\(style\)、*「範本」*\(template\)，或一些簡單項目，例如自訂色彩。  您也可以依控制項的狀態讓控制項以不同的方式出現。  例如，按鈕會在使用者按一下時變成綠色。  
  
 **本主題內容**：  
  
-   [筆刷：修改物件的外觀](#Brushes)  
  
-   [樣式和範本：跨控制項建立一致的外觀與風格](#Styles)  
  
-   [視覺狀態：依控制項的狀態變更其外觀](#Visual)  
  
-   [資源：建立色彩、樣式和範本，之後重複使用這些項目](#Resources)  
  
##  <a name="Brushes"></a> 筆刷：修改物件的外觀  
 如果您要變更筆刷的外觀，請將筆刷套用至物件。  
  
 **觀看短片：** ![設定已安裝的功能](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [筆刷編輯器](http://www.popscreen.com/v/6A4mO/Microsoft-Expression-Blend-The-Brushes-Editor)。  
  
### 在物件上繪製重複影像或圖樣  
 使用*「拼貼筆刷」*\(tile brush\) 在物件上繪製重複影像或圖樣。  
  
 若要建立拼貼筆刷，請先建立*「影像筆刷」*\(image brush\)、*「繪圖筆刷」*\(drawing brush\)，或*「視覺筆刷」*\(visual brush\) 資源。  
  
 使用影像來建立影像筆刷。  下列圖例顯示影像筆刷、並排的影像筆刷和翻轉的影像筆刷。  
  
 使用向量繪圖 \(例如路徑或圖形\) 來建立繪圖筆刷。  下列圖例顯示繪圖筆刷、並排的繪圖筆刷和翻轉的繪圖筆刷。  
  
 從按鈕等控制項建立視覺筆刷。  下列圖例顯示視覺筆刷和並排的視覺筆刷。  
  
 **觀看短片：** ![設定已安裝的功能](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [拼貼筆刷](http://www.popscreen.com/v/6A4iM/Microsoft-Expression-Blend-Tile-Brushes)。  
  
##  <a name="Styles"></a> 樣式和範本：跨控制項建立一致的外觀與風格  
 您可以設計控制項的外觀和行為一次，並將該設計套用至其他控制項，如此就不必一一維護它們。  
  
 **您應該使用樣式嗎？**：如果您只要設定預設屬性 \(例如按鈕的色彩\)，請使用*「樣式」*\(style\)。  您可以修改控制項，即使在套用樣式後也行。  
  
 **您應該使用範本嗎？**：如果您要變更控制項的結構，請使用*「範本」*\(template\)。  想像一下將圖形或標誌轉換成按鈕。  在將範本套用至控制項之後，便無法修改控制項。  
  
### 建立範本或樣式  
 共有兩種方式可以建立範本。  您可以將畫板上的任何物件轉換成控制項，或可以讓範本以現有的控制項為基礎。  
  
 若要將任何物件轉換成控制項範本，請選取該物件，然後在 \[工具\] 功能表上選擇 \[變成控制項\]。  
  
 如果您要讓範本以現有控制項為基礎，請選取畫板上的物件。  然後，在畫板上方選擇階層連結按鈕，接著選擇 \[編輯範本\]，然後選擇 \[編輯複本\] 或 \[建立空的\]。  
  
 若要建立樣式，請選取物件，接著在 \[物件\] 功能表中選擇 \[編輯樣式\]，然後選擇 \[編輯複本\] 或 \[建立空的\]。  
  
-   選擇 \[編輯複本\] 以依照控制項的預設樣式或範本開始著手。  
  
-   選擇 \[建立空的\] 從頭開始。  
  
 \[編輯目前項目\] 選項只會在編輯已建立的樣式或範本時才會出現。  若是仍然使用預設系統範本的控制項，則不會顯示此選項。  
  
 在 \[建立樣式資源\] 對話方塊中，您可以為樣式或範本命名以便之後使用，或將樣式或範本套用至該類型的所有控制項。  
  
> [!NOTE]
>  您無法為每一個類型的控制項建立樣式或範本。  如果控制項不支援此項，階層連結按鈕就不會出現在畫板上。  
>   
>  若要回到主文件的編輯範圍，請按一下 \[將範圍傳回\] ![](../designers/media/55844eb3-ed98-4f20-aa66-a6f5b23eeb2b.png "55844eb3\-ed98\-4f20\-aa66\-a6f5b23eeb2b")。  
  
 **觀看短片：** ![設定已安裝的功能](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [建立樣式](http://www.microsoft.com/showcase/details.aspx?uuid=9b8e86e2-8e90-4d61-81af-fa5b5afb3e95)。  
  
 **觀看短片：** ![設定已安裝的功能](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [在 Expression Blend 中建立控制項範本](http://msdn.microsoft.com/expression/cc263912.aspx)。  
  
### 將樣式或範本套用至控制項  
 在 \[[物件與時間軸](http://msdn.microsoft.com/zh-tw/135a5a5e-ec6d-4f38-8827-60e284cd5f57)\] 面板中以滑鼠右鍵按一下物件，接著選擇 \[編輯範本\]，然後選擇 \[套用資源\]。  
  
### 還原控制項的預設樣式或範本  
 選取控制項，然後在 \[[屬性](http://msdn.microsoft.com/zh-tw/135a5a5e-ec6d-4f38-8827-60e284cd5f57)\] 面板中，找出 \[樣式\] 或 \[範本\] 屬性。  接著按一下 \[進階選項\] ![](../designers/media/12e06962-5d8a-480d-a837-e06b84c545bb.png "12e06962\-5d8a\-480d\-a837\-e06b84c545bb")，然後按一下捷徑功能表上的 \[重設\]。  
  
##  <a name="Visual"></a> 視覺狀態：依控制項的狀態變更其外觀  
 控制項可根據使用者互動有不同的視覺外觀。  例如，在使用者按一下按鈕時，您可以讓按鈕變成綠色或者執行動畫。  您可以使用轉場來縮短或加長視覺狀態間的時間。  
  
 **觀看短片：** ![設定已安裝的功能](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [管理 WPF 控制項的狀態](https://www.youtube.com/watch?v=m0PlkF5i6uw)。  
  
##  <a name="Resources"></a> 資源：建立色彩、樣式和範本，之後重複使用這些項目  
 您可以將專案中幾乎任何項目轉換為資源。  資源只是一個可在應用程式中不同地方重複使用的物件。  例如，您可以建立色彩一次、使它變成資源，然後在數個物件上使用該色彩。  若要變更所有這些物件的色彩，只須變更色彩資源即可。  
  
 **觀看短片：** ![設定已安裝的功能](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [資源的簡短試用](http://www.popscreen.com/v/6A4k7/Microsoft-Expression-Blend-Brief-Touch-on-Resources)。  
  
## 請參閱  
 [使用 Blend for Visual Studio 建立 UI](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)