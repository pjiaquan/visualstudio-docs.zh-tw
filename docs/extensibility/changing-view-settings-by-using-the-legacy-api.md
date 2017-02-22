---
title: "使用舊版 API 來變更檢視設定 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "編輯器 [Visual Studio SDK]，舊版的變更檢視設定"
ms.assetid: 12c9b300-0894-4124-96a1-764326176d77
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# 使用舊版 API 來變更檢視設定
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

藉由使用者可以變更核心編輯器功能，例如自動換行、 選取範圍邊界和虛擬空間中，設定**選項**對話方塊。  不過，它也可變更這些設定以程式設計的方式。  
  
## 變更設定，以使用舊版 API  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer>介面公開 \(expose\) 的文字編輯器的屬性集。  文字檢視會包含某類屬性 \(GUID\_EditPropCategory\_View\_MasterSettings\)，表示文字檢視以程式設計方式變更設定的群組。  一旦檢視設定已經變更，如此一來，就無法變更在**選項**直到重設\] 對話方塊。  
  
 以下是典型的程序來變更執行個體的核心編輯器的檢視設定。  
  
1.  呼叫`QueryInterface`上 \(<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>\) 的<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer>介面。  
  
2.  呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A>方法，指定值為 GUID\_EditPropCategory\_View\_MasterSettings 的`rguidCategory`參數。  
  
     如此一來傳回變數的指標， <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer>介面，其中包含一組強制屬性的檢視。  永遠強制這個群組中的任何設定。  如果設定值不是這個群組中，則它會遵循中所指定的選項**選項**對話方塊或使用者的命令。  
  
3.  呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A>方法，指定適當的設定值，在`idprop`參數。  
  
     例如，若要強制換行，呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> ，並指定其值為 VSEDITPROPID\_ViewLangOpt\_WordWrap， `vt`的`idprop`參數。  在此呼叫時， `vt`是一的型別 VT\_BOOL 和`vt.boolVal`是 VARIANT\_TRUE。  
  
## 重設已變更的檢視設定  
 若要重設任何已變更的檢視設定核心編輯器執行個體，呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A>方法，並指定適當的設定值，在`idprop`參數。  
  
 比方說，若要允許自由浮動文字換行功能，您必須移除它從 \[屬性\] 類別藉由呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> ，並指定值為 VSEDITPROPID\_ViewLangOpt\_WordWrap 的`idprop`參數。  
  
 若要一次移除核心編輯器的所有變更過的值，指定值為 VSEDITPROPID\_ViewComposite\_AllCodeWindowDefaults，為 vt `idprop`參數。  在這個呼叫，vt 是類型 VT\_BOOL 的 VARIANT，vt.boolVal 是 VARIANT\_TRUE。  
  
## 請參閱  
 [核心編輯器內](../extensibility/inside-the-core-editor.md)   
 [使用舊版 API 存取 Text 檢視](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)   
 [選項對話方塊](../ide/reference/options-dialog-box-visual-studio.md)