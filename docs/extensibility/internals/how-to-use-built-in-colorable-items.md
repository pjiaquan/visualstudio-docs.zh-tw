---
title: "如何: 使用內建可設定色彩的項目 | Microsoft Docs"
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
  - "可設定色彩的項目"
  - "語言服務，內建可設定色彩的項目"
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# 如何: 使用內建可設定色彩的項目
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

使用內建的可設定色彩項目之前，您必須先通知整合式的開發環境 \(IDE\) 不提供您自己自訂可設定色彩，這些項目在此情況下會是<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>物件。  您這樣做，藉由設定語言服務的登錄項目。  
  
### 若要使用內建的可設定色彩項目  
  
1.  在 HKEY\_LOCAL\_MACHINE\\VisualStudio\\*X.Y*\\Languages\\Language Services\\*語言名稱*，其中 *X.Y* 版本的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]和*語言名稱*是名稱的程式語言中，建立名為 DWORD 登錄項目值`RequestStockColors`。  
  
2.  設定`RequestStockColors`登錄項目值為 1。  
  
     在您建立的登錄項目，您 colorizer 的後<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>方法可使用的成員<xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS>來填入陣列中的編輯器\] 中所使用的色彩屬性的列舉型別。  
  
    > [!NOTE]
    >  如果您提供的自訂的可設定色彩項目，請不要設定此登錄項目。  如需詳細資訊，請參閱 [自訂色彩的項目](../../extensibility/internals/custom-colorable-items.md)。  
  
## 請參閱  
 [語法著色中自訂編輯器](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [語法著色在舊版語言服務](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [實作語法標色](../../extensibility/internals/implementing-syntax-coloring.md)   
 [自訂色彩的項目](../../extensibility/internals/custom-colorable-items.md)   
 [註冊舊版語言服務](../../extensibility/internals/registering-a-legacy-language-service2.md)