---
title: "如何：匯出包含 Mipmap 的材質 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3d1ad14b-44fb-4cf0-a995-5e2f60026524
caps.latest.revision: 7
caps.handback.revision: 7
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
---
# 如何：匯出包含 Mipmap 的材質
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在專案的建置階段中，影像內容管線可以從來源影像產生 Mipmap。  當您不需要手動指定每個 MIP 層級的影像內容時 \(在您可能會想要達到某些效果時\)，於建置階段產生 Mipmap 確保 Mipmap 內容絕不變得無法同步，而且排除在執行階段產生 Mipmap 的效能成本。  
  
 本文件示範下列活動:  
  
-   設定要由影像內容管線處理的來源影像。  
  
-   設定影像內容管線，使它產生 MIP 對應。  
  
## 匯出 Mipmap  
 Mipmapping 自動為 3D 遊戲或應用程式的材質表面提供螢幕空間層次細節。  這會藉由預先計算材質的縱向取樣版本，增強遊戲或應用程式的轉譯效能，讓整個材質不必每次取樣時都進行縱向取樣。  
  
#### 若要匯出有 Mipmap 的紋理  
  
1.  從基本材質開始。  載入現有影像檔，或建立影像檔，如 [如何：建立基本材質](../Topic/How%20to:%20Create%20a%20Basic%20Texture.md)中所述。  若要支援 mipmap，請指定寬度和高度大小是相同二次方的紋理，例如，64x64、256x256 或 512x512。  
  
2.  設定您剛建立的材質檔案，以便由影像內容管線處理。  在 \[**方案總管**\] 中，開啟剛建立之材質檔案的捷徑功能表，然後選擇 \[**屬性**\]。  在 \[**組態屬性**\]、\[**一般**\] 頁面上，將 \[**項目類型**\] 屬性設定為 \[**影像內容管線**\]。  確定 \[**內容**\] 屬性已設為 \[**是**\]，而且 \[**從組建排除**\] 設為 \[**否**\]，然後選擇 \[**套用**\] 按鈕。  \[**影像內容管線**\] 組態屬性頁面隨即出現。  
  
3.  設定影像內容管線，使它產生 MIP 對應。  在 \[**組態屬性**\]、\[**影像內容管線**\]、\[**一般**\] 頁面上，將 \[**產生 Mips**\] 屬性設定為 \[**是 \(\/generatemips\)**\]。  
  
4.  選擇 \[**確定**\] 按鈕。  
  
 當您建立專案時，影像內容管線會將來源影像從工作格式轉換為您指定的輸出格式 \(包括 MIP 層級\)，而且結果複製到專案的輸出目錄。