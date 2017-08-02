---
title: "原始檔控制外掛程式架構 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "原始檔控制外掛程式架構"
ms.assetid: 35351d4c-9414-409b-98fc-f2023e2426b7
caps.latest.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 24
---
# 原始檔控制外掛程式架構
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

您可以加入至來源控制項支援[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]藉由實作和附加的原始檔控制外掛程式的整合式的開發環境 \(IDE\)。  IDE 會連接到原始檔控制外掛程式，透過定義完善的原始檔控制外掛程式 API 中。  IDE 公開 \(expose\) 所提供的工具列和功能表命令所組成的使用者介面 \(UI\) 的原始檔控制系統的版本控制等功能。  原始檔控制外掛程式實作的原始檔控制功能。  
  
## 原始檔控制外掛程式的資源  
 原始檔控制外掛程式提供資源，以協助建立並連接至應用程式版本控制[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE。  原始檔控制外掛程式會包含 API 規格，用來使它可以整合到原始檔控制外掛程式必須實作[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE。  它也包含實作的基本架構的原始檔控制外掛程式 demonstrating 實作必要的功能與原始檔控制外掛程式 API 相容的程式碼範例 \(以 c \+ \+\)。  
  
 原始檔控制外掛程式的 API 規格可讓您充分運用您所選擇的任何原始檔控制系統，如果您建立了必要的集合，以配合原始檔控制外掛程式的 API 實作的函式的 DLL 的原始檔控制。  
  
## 元件  
 在圖表中的原始檔控制配接器套件是 IDE 將轉譯成函式呼叫受原始檔控制外掛程式的原始檔控制作業的使用者要求的元件。  此選項時，IDE 和原始檔控制外掛程式都必須有有效的 IDE 和外掛程式之間來回傳送資訊\] 對話方塊。  此對話方塊中才會生效，對它們都必須說出相同的語言。  本文件所列的原始檔控制外掛程式 API 是這項交換的通用詞彙。  
  
 ![原始程式碼控制架構圖表](~/docs/extensibility/internals/media/vs_sccsdk_plug_in_arch.gif "vs\_sccsdk\_plug\_in\_arch")  
顯示互動 VS 和原始檔控制外掛程式的架構圖  
  
 如所示的架構圖中， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]殼層，標示為在圖表中，VS shell 裝載使用者的工作專案和相關聯的元件，例如 \[編輯器\] 和 \[方案總管。  原始檔控制配接器套件處理 IDE 和原始檔控制外掛程式之間的互動。  原始檔控制配接器套件提供它自己的原始檔控制 UI。  這是最上層來啟始及定義的原始檔控制作業範圍與使用者互動的 UI。  
  
 原始檔控制外掛程式可以有它自己的 UI，可能會包含兩個部分，如圖所示。  標記為 「 供應商 UI 」 的方塊表示，作為建立原始檔控制外掛程式者，提供的自訂使用者介面項目。  當使用者叫用的進階的原始檔控制作業，這些會顯示直接由原始檔控制外掛程式。  標示為 「 協助程式 UI 」 方塊是一組的原始檔控制外掛程式 UI 功能間接透過 IDE 叫用。  原始檔控制外掛程式會將 UI 相關的訊息傳遞到 IDE 所提供的特殊的回呼函式透過 IDE 中。  協助程式 UI 幫助您更緊密的整合與 IDE \(經常使用的**進階**按鈕\)，並因而提供更一致的使用者經驗。  
  
 原始檔控制外掛程式無法進行任何變更到[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]殼層，因此，原始檔控制配接器套件或原始檔控制提供 ide 的 UI。  它必須先透過一般使用者提供整合式的體驗不同的原始檔控制外掛程式的 API 函式實作所提供的彈性最大的使用。  原始檔控制外掛程式 API 的說明文件的參考 ＞ 一節包括一些進階的原始檔控制外掛程式的功能的資訊。  若要利用這些功能，原始檔控制外掛程式必須進行初始化期間，宣告它對 IDE 的進階的功能，它必須實作特定的進階的功能，每個功能。  
  
## 請參閱  
 [原始檔控制外掛程式](../../extensibility/source-control-plug-ins.md)   
 [字彙表](../../extensibility/source-control-plug-in-glossary.md)   
 [建立原始檔控制外掛程式](../../extensibility/internals/creating-a-source-control-plug-in.md)