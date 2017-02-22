---
title: "精靈介面 (IDTWizard) | Microsoft Docs"
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
  - "IDTWizard 介面"
  - "精靈、 介面"
ms.assetid: 09618d9d-d115-45b6-bccc-de328994b39c
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# 精靈介面 (IDTWizard)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

整合式的開發環境 \(IDE\) 會使用<xref:EnvDTE.IDTWizard>與精靈通訊的介面。  若要安裝在 IDE 中，精靈必須實作這個介面。  
  
 <xref:EnvDTE.IDTWizard.Execute%2A>方法是與相關聯的唯一方法<xref:EnvDTE.IDTWizard>介面。  精靈會實作這個方法，IDE 會在介面上呼叫方法。  下列範例會示範方法的簽章。  
  
```  
/* IDTWizard Method */  
STDMETHOD(Execute)(THIS_  
   /* [in] */ IDispatch *Application,  
   /* [in] */ long hwndOwner,  
   /* [in] */ SAFEARRAY * *ContextParams,  
   /* [in] */ SAFEARRAY * *CustomParams,  
   /* [out] [in] */ wizardResult *RetVal  
   );  
```  
  
 開始機制都很相似**新的專案** 和 **加入新項目**精靈。  若要啟動其中一個時，您呼叫<xref:EnvDTE.IDTWizard> Dteinternal.h 中所定義的介面。  唯一的差別在於顯示的內容及呼叫該介面時，會傳遞至介面的自訂參數。  
  
 下列資訊說明<xref:EnvDTE.IDTWizard>精靈必須在實作的介面[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE。  IDE 呼叫<xref:EnvDTE.IDTWizard.Execute%2A>在精靈中，將它傳遞下列方法：  
  
-   DTE 物件  
  
     DTE 物件是自動化模型的根。  
  
-   \[視窗\] 對話方塊中的程式碼片段中所示的控制代碼`hwndOwner ([in] long)`。  
  
     精靈會使用這`hwndOwner`為精靈\] 對話方塊的父代。  
  
-   內容參數傳遞給介面，作為 variant 的安全陣列時發生如所示在程式碼片段中， `[in] SAFEARRAY (VARIANT)* ContextParams`。  
  
     內容參數包含專用於啟動的精靈類型的值的陣列和專案的目前狀態。  IDE 會將內容參數傳遞給精靈。  如需詳細資訊，請參閱 [內容參數](../../extensibility/internals/context-parameters.md)。  
  
-   自訂參數傳遞給介面，作為 variant 的安全陣列時發生如所示在程式碼片段中， `[in] SAFEARRAY (VARIANT)* CustomParams`。  
  
     自訂參數會包含使用者定義的參數陣列。  .Vsz 檔案將自訂的參數傳遞至 IDE。  這些值由`Param=`陳述式。  如需詳細資訊，請參閱 [自訂參數](../../extensibility/internals/custom-parameters.md)。  
  
-   介面的傳回值  
  
    ```  
    wizardResultSuccess = -1,  
    wizardResultFailure = 0  
    wizardResultCancel = 1  
    wizardResultBackout = 2  
    ```  
  
## 請參閱  
 [內容參數](../../extensibility/internals/context-parameters.md)   
 [自訂參數](../../extensibility/internals/custom-parameters.md)   
 [精靈](../../extensibility/internals/wizards.md)   
 [精靈 \(。Vsz\) 檔案](../../extensibility/internals/wizard-dot-vsz-file.md)