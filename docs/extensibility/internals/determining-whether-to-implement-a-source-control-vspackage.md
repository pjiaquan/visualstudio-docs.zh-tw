---
title: "決定是否要實作的原始檔控制 VSPackage | Microsoft Docs"
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
  - "關於原始檔控制套件的原始檔控制套件"
ms.assetid: 60b3326e-e7e2-4729-95fc-b682e7ad5c99
caps.latest.revision: 24
caps.handback.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
---
# 決定是否要實作的原始檔控制 VSPackage
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

這一節 elaborates 來擴充解決方案，並提供廣泛的方針，選擇適合的整合路徑相關的原始檔控制的原始檔控制外掛程式和 VSPackages 的原始檔控制的選項。  
  
## 小型原始檔控制方案，並以有限的資源  
 如果資源有限，而且無法負擔寫入原始檔控制套件的額外負荷，您可以建立原始檔控制外掛程式 API 為基礎外掛? 式。  這可讓您能夠與原始檔控制套件，並排，您可以切換原始檔控制外掛程式，並隨選的封裝。  如需詳細資訊，請參閱 [註冊和選取範圍](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)。  
  
## 大型原始檔控制方案，並以豐富的功能設定  
 如果您想要實作提供豐富的原始檔控制模型不會適當地擷取使用原始檔控制外掛程式 API 的原始檔控制方案，您可以考慮為整合路徑的原始檔控制套件。  此動作會套用特別是如果您不會取代原始檔控制配接器套件 \(這樣會與原始檔控制外掛程式進行通訊，並提供基本的原始檔控制 UI\) 時，才使用您自己，讓您可以自訂的方式來處理來源的控制項事件。  如果您已經有令人滿意的原始檔控制 UI，並想要保留這樣的經驗，在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，\[原始檔控制套件\] 選項可讓您執行上述工作。  原始檔控制套件不是泛型，且只為了與使用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE。  
  
 如果您想要實作提供彈性和更多控制的原始檔控制的邏輯和 UI 的原始檔控制方案，您可能偏好的原始檔控制套件整合路由。  您可以：  
  
1.  註冊您自己的原始檔控制 VSPackage \(請參閱[註冊和選取範圍](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)\)。  
  
2.  使用自訂的使用者介面來取代預設的原始檔控制 UI \(請參閱[自訂使用者介面](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)\)。  
  
3.  指定用來處理方案總管\] 中的圖像 \(glyph\) 事件的圖像 \(glyph\) \(請參閱[圖像控制項](../../extensibility/internals/glyph-control-source-control-vspackage.md)\)。  
  
4.  處理查詢編輯和查詢儲存的事件 \(請參閱[儲存查詢編輯查詢](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)\)。  
  
## 請參閱  
 [建立原始檔控制外掛程式](../../extensibility/internals/creating-a-source-control-plug-in.md)