---
title: "自訂參數 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "精靈中，自訂參數"
  - "自訂參數"
ms.assetid: ba5c364b-66e6-47ea-9760-a0b70de8f0a0
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# 自訂參數
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

精靈啟動之後，自訂參數會控制精靈\] 的操作。  相關的.vsz 檔案提供使用者定義的參數，經由整合式的開發環境 \(IDE\) 時啟動精靈\] 做為陣列的字串傳遞給精靈的陣列。  然後，精靈會剖析字串的陣列，並控制實際操作的 「 精靈 」 會使用的資訊。  如此一來，精靈可以使用自訂功能.vsz 檔案的內容而定。  
  
 啟動精靈時，內容參數，相反地，定義專案的狀態。  如需詳細資訊，請參閱 [內容參數](../../extensibility/internals/context-parameters.md)。  
  
 下列是.vsz 檔案具有自訂參數的範例：  
  
```  
VSWIZARD 8.0  
Wizard=VsWizard.VsWizard_Engine  
Param="WIZARD_NAME = Sample Wizard"  
Param="WIZARD_UI = FALSE"  
Param="RELATIVE_PATH = VSWizards\Classwiz\ATL"  
Param="PREPROCESS_FUNCTION = CanAddATLSupport"  
Param="PROJECT_TYPE = CSPROJ"  
```  
  
 .Vsz 檔案的作者加入參數的值。  當使用者選取**新的專案** 或 **加入新項目** 在 \[檔案\] 功能表上，或以滑鼠右鍵按一下專案，以在 **方案總管\] 中**，IDE 會收集這些值轉換為字串的陣列。  IDE 接著會呼叫專案的<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A>方法以<xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION>旗標集和專案呼叫<xref:EnvDTE.IVsExtensibility.RunWizardFile%2A>負責執行精靈，並傳回結果的方法。  
  
 精靈已剖析的字串陣列，並適當地做對的字串。  如此一來，藉由實作自訂參數您可以建立一個精靈，以便在執行多種功能。  也就是說，一個精靈可以有三個不同的.vsz 檔案。  每個檔案會傳遞不同組的自訂參數，以控制在不同狀況下精靈的行為。  
  
 如需詳細資訊，請參閱 [精靈 \(。Vsz\) 檔案](../../extensibility/internals/wizard-dot-vsz-file.md)。  
  
## 請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 [內容參數](../../extensibility/internals/context-parameters.md)   
 [精靈](../../extensibility/internals/wizards.md)   
 [精靈 \(。Vsz\) 檔案](../../extensibility/internals/wizard-dot-vsz-file.md)