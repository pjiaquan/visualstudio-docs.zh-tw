---
title: "巢狀專案 | Microsoft Docs"
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
  - "專案的巢狀結構"
  - "巢狀的專案"
  - "專案 [Visual Studio SDK]，子專案"
  - "專案 [Visual Studio SDK]，巢狀結構"
ms.assetid: 12cce037-9840-4761-845e-5abd5fb317b0
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# 巢狀專案
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

企業應用程式開發人員使用您的 VS 套件可以方便地群組相似類型的專案一起放在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 使用 *專案巢狀*。 例如，企業樣板專案會使用巢狀的群組專案的專案分類。 商務外貌專案、 Web UI 專案等會群組在一個類別。  
  
 在此案例中，開發人員可以在每個父專案中，巢狀的專案的數目沒有限制雖然開發人員可以透過程式設計方式提供限制。 此群組的類型，您也可以進行遞迴，在此情況下為子專案的相同類型的專案可以巢狀在要成為子系，也就是父系的子專案的子專案的子系。  
  
 專案的巢狀結構不是內建函式的一部分 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 您必須撰寫程式碼來啟用巢狀結構和子專案子專案的巢狀結構。 父專案是特殊的 VSPackage 或專案類型，建立並註冊以包含程式碼，才能實作專案巢狀結構，其專屬 GUID。  
  
 您可以在 C\# Example.Nested 專案範例中找到巢狀專案的範例。  
  
## 巢狀的專案範例  
 ![巢狀專案方案](../../extensibility/internals/media/vsnestedprojects.gif "vsNestedProjects")  
巢狀的專案範例  
  
## 請參閱  
 [How to: 實作巢狀的專案](../../extensibility/internals/how-to-implement-nested-projects.md)   
 [卸載並重新載入巢狀專案的考量](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)   
 [巢狀專案的精靈支援](../../extensibility/internals/wizard-support-for-nested-projects.md)   
 [註冊專案和項目範本](../../extensibility/internals/registering-project-and-item-templates.md)   
 [實作命令處理巢狀專案](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)   
 [篩選巢狀專案 AddItem 對話方塊](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)   
 [檢查清單︰ 建立新的專案類型](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [內容參數](../../extensibility/internals/context-parameters.md)   
 [精靈 \(。Vsz\) 檔案](../../extensibility/internals/wizard-dot-vsz-file.md)