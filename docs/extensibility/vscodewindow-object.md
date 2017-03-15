---
title: "VSCodeWindow 物件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VSCodeWindow"
helpviewer_keywords: 
  - "檢視 [Visual Studio SDK]，VSCodeWindow 物件"
  - "VsCodeWindow 物件"
ms.assetid: cf5fe926-e784-4098-bc01-cac49c7c55c6
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# VSCodeWindow 物件
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

程式碼視窗是一種特殊的文件視窗，通常包含一或多個文字檢視 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> 物件。  
  
 在架構上，程式碼\] 視窗是會在視窗內的文件視窗。 在功能上，程式碼視窗會直接與其他功能的文件視窗。 在多重文件介面 \(MDI\) 模式中，程式碼視窗會是 MDI 子框架。 如需詳細資訊，請參閱[使用舊版 API 的自訂程式碼視窗](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)。  
  
 下表包含的介面 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> 物件。  
  
|方法|描述|  
|--------|--------|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|提供一般存取機制來尋找全域唯一識別碼 \(GUID\) 識別的服務。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|代表多個文件介面 \(MDI\) 子系包含一個或多個程式碼檢視。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|填滿視窗框架。|  
  
## 請參閱  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>   
 [Figures Edit](http://msdn.microsoft.com/zh-tw/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)