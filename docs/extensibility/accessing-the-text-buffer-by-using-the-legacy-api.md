---
title: "使用舊版 API 存取文字緩衝區 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "編輯器 [Visual Studio SDK]，舊版-文字緩衝區"
ms.assetid: cd6cf4ae-fff5-4e23-b293-7cbafdb8aed2
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# 使用舊版 API 存取文字緩衝區
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

文字會負責管理文字資料流與檔案的保存性的。  雖然緩衝區可以讀取或寫入其他格式，所有的一般通訊與緩衝區藉由使用 Unicode。  在傳統的 Api，文字緩衝區可以使用一位或二維的座標系統以找出在緩衝區中的字元位置。  
  
## 一個和兩個維度的座標系統  
 一維的座標位置根據第一個字元的字元位置，例如 147 的緩衝區中。  您使用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>存取一維的位置在緩衝區中的介面。  二維的座標系統是以行和索引組為基礎。  比方說，43 緩衝區中的字元，5 就會在行 43 右邊的那一行的第一個字元的五個字元。  您在存取二維諸塞州緩衝區使用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>介面。  這兩個<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>介面由文字緩衝區物件實作 \(<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>\)，藉由存取彼此`QueryInterface`。  下圖顯示上述和其他重要的介面上<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>。  
  
 ![文字緩衝區物件](~/extensibility/media/vstextbuffer.gif "vsTextBuffer")  
文字緩衝區物件  
  
 不論是哪一種座標系統的運作方式文字緩衝區中，雖然它被最佳化，可以使用二維座標。  為一維的座標系統造成的效能負荷。  因此，使用二維座標系統在可能的情況。  
  
 文字緩衝區的第二個責任是檔案的保存性。  若要這樣做，文字緩衝區物件實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> ，並做為專案項目的文件資料物件的元件和其他環境元件參與持續性。  如需詳細資訊，請參閱 [開啟並儲存專案項目](../extensibility/internals/opening-and-saving-project-items.md)。  
  
## 本章節內容  
 [使用舊版 API 來變更檢視設定](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 說明如何變更使用舊版 API 的檢視設定。  
  
 [使用文字管理員監控全域設定](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 說明如何使用 \[文字管理員\]，請以監視通用設定。.  
  
## 請參閱  
 [核心編輯器內](../extensibility/inside-the-core-editor.md)