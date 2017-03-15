---
title: "圖像控制項 (原始檔控制 VSPackage) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "原始檔控制套件的圖像"
  - "原始檔控制套件圖像 (glyph)"
ms.assetid: b9413b08-b3c3-4fc3-a6e0-3dc0db3652d7
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# 圖像控制項 (原始檔控制 VSPackage)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

加入原始檔控制 VSPackages 可用的深度整合的一部分是顯示自己的圖像 \(glyph\) 表示的原始檔控制下的項目狀態的功能。  
  
## 層級的圖像 \(glyph\) 控制  
 狀態的圖像 \(glyph\) 會有圖示，表示目前的狀態顯示，例如在某個項目的**方案總管\] 中** 或 **類別檢視**。  原始檔控制 VSPackage 可以運用圖像 \(glyph\) 控制項的兩個層的級。  它會限制為一組預先定義的圖像 \(glyph\) 所提供的圖像 \(glyph\) 選擇[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 中，或者也可以定義一組自訂的 \[要顯示的圖像 \(glyph\)。  
  
### 圖像 \(glyph\) 的預設集合  
 若要判斷狀態圖像中的項目與相關聯的**方案總管\] 中**，專案從原始檔控制使用要求狀態的圖像 \(glyph\) <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.GetSccGlyph%2A>。  原始檔控制 VSPackage 可能會決定要保留的圖像 \(glyph\) 限制為預先定義的圖像 \(glyph\) 所提供的 IDE 選擇。  如此一來，VSPackage 上一步傳遞數值，代表 vsshell.idl 中所定義的圖像 \(glyph\) 列舉型別的陣列。  如需詳細資訊，請參閱<xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon> 。這是一組預先定義設定的 IDE，例如圖像 \(glyph"已簽入 」\)，以及核取記號，以"簽出"圖像鎖的圖像 \(glyph\)。  
  
### 自訂設定的圖像 \(glyph\)  
 原始檔控制 VSPackage 可以使用它自己的圖像 \(glyph\) 唯一"外觀和感覺 」 安裝時。  使用新的原始檔控制 VSPackage 時，它應該能夠開始使用它自己的圖像 \(glyph\) 即使先前的原始檔控制 VSPackage 仍載入但沒有作用。  在此模式中，原始檔控制 VSPackage 仍可以使用現有的圖示以維護一致的外觀[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]如果選擇。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>服務支援的介面， <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>，這樣可以選擇性地實作 VSPackage，這將會要求您的 ide。  當 IDE 發出要求， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]會依序嘗試從目前已登錄的原始檔控制 VSPackage 取得這個介面。  如果介面有已註冊的 VSPackage，為自訂的圖像 \(glyph\) 的 IDE 的要求就會成功。 否則， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 會使用其預設的圖像 \(glyph\)。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs.GetCustomGlyphList%2A>的方法由[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]以取得一份影像顯示不同的原始檔控制狀態。  原始檔控制 VSPackage 傳回 ide 其自訂的圖像 \(glyph\) 的影像清單的控制代碼。  IDE 會將影像清單複製到目前為止，並稍後再用它來選擇要顯示的圖像 \(glyph\)。  如果不支援新的介面或`IVsSccGlyphs::GetCustomGlyphList`方法會傳回 E\_NOTIMPL，那麼 IDE 從所提供的圖像 \(glyph\) 的 \[預設\] 清單中取得其圖像 \(glyph\) [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
## 請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>