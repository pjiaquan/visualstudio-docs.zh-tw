---
title: "原始檔控制整合的基本資訊 | Microsoft Docs"
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
  - "原始檔控制整合 essentials"
  - "原始檔控制整合概觀"
  - "essentials，原始檔控制整合"
ms.assetid: 442057cb-fd54-4283-96f8-2f6dc8bf2de7
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# 原始檔控制整合的基本資訊
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]支援兩種類型的原始檔控制整合： 原始檔控制外掛程式，會提供基本功能，而且會建置使用原始檔控制外掛程式 API \(之前稱為 MSSCCI API\)，並以 VSPackage 為基礎的原始檔控制整合解決方案，提供更強固的功能。  
  
## 原始檔控制外掛程式  
 實作原始檔控制外掛程式 API 以寫入原始檔控制外掛程式。  透過 API 提供註冊和原始檔控制整合功能。  這種方法都可以輕易地實作於原始檔控制 VSPackage，並且使用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]大部分原始檔控制作業的使用者介面 \(UI\)。  
  
 若要實作的原始檔控制外掛程式使用原始檔控制外掛程式的 API，請依照下列步驟執行：  
  
1.  建立實作中所指定的函式的 DLL [原始檔控制外掛程式](../../extensibility/source-control-plug-ins.md)。  
  
2.  藉由適當的登錄項目中，登錄 DLL，如所述[如何: 安裝原始檔控制外掛程式](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)。  
  
3.  建立協助程式 UI，並顯示它的原始檔控制配接器套件出現提示時 \( [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]處理透過原始檔控制外掛程式的原始檔控制功能的元件\)。  
  
 如需詳細資訊，請參閱 [建立原始檔控制外掛程式](../../extensibility/internals/creating-a-source-control-plug-in.md)。  
  
## 原始檔控制 VSPackage  
 原始檔控制 VSPackage 實作可讓您開發自訂的取代[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]原始檔控制 UI。  這種方法提供原始檔控制整合，完整的控制權，但它會要求您提供的 UI 項目，並實作，否則會提供適合插件在原始檔控制介面。  
  
 若要實作 VSPackage 的原始檔控制，您必須：  
  
1.  建立並登錄中所述的您自己的原始檔控制 VSPackage， [註冊和選取範圍](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)。  
  
2.  取代預設的原始檔控制 UI 自訂 UI。  請參閱 [自訂使用者介面](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)。  
  
3.  指定圖像 \(glyph\)，以及處理**方案總管\] 中**圖像 \(glyph\) 的事件。  請參閱 [圖像控制項](../../extensibility/internals/glyph-control-source-control-vspackage.md)。  
  
4.  處理中所示的查詢編輯和查詢儲存的事件， [儲存查詢編輯查詢](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)。  
  
 如需詳細資訊，請參閱 [建立原始檔控制 VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)。  
  
## 請參閱  
 [概觀](../../extensibility/internals/source-control-integration-overview.md)   
 [建立原始檔控制外掛程式](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [建立原始檔控制 VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)