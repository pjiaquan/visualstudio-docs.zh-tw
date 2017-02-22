---
title: "舊版的語言服務擴充性 | Microsoft Docs"
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
  - "語言服務"
  - "Visual Studio 中，語言服務"
ms.assetid: 2700cd4d-5f68-43fc-b62f-dc80c3f3aa85
caps.latest.revision: 42
caps.handback.revision: 42
ms.author: "gregvanl"
manager: "ghogen"
---
# 舊版的語言服務擴充性
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

語言服務提供編輯原始程式碼在 IDE 中的特定語言的支援。  
  
 舊版的語言服務會實作成，VSPackage 的一部分，但實作語言服務功能的較新的方法是使用 MEF 延伸模組。 若要了解有關實作語言服務的新方法的詳細資訊，請參閱 [編輯器和語言服務擴充功能](../../extensibility/editor-and-language-service-extensions.md)。  
  
 本節討論的結構與舊版語言服務的實作。  
  
## 在本節中  
 [移轉舊版語言服務](../../extensibility/internals/migrating-a-legacy-language-service.md)  
 說明如何更新語言服務從 Visual Studio 2008 的最新版本。  
  
 [舊版的語言服務的基本資訊](../../extensibility/internals/legacy-language-service-essentials.md)  
 提供有關如何開發整合 Visual Studio 中的程式語言的語言服務的重要資訊。  
  
 [開發語言服務](../../extensibility/internals/developing-a-legacy-language-service.md)  
 提供可協助您建立語言服務的主題連結。  
  
 [語法著色在舊版語言服務](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 提供有關支援語法反白顯示的語言服務中的資訊。  
  
 [實作傳統語言服務](../../extensibility/internals/implementing-a-legacy-language-service1.md)  
 提供如何使用受管理的封裝架構 \(MPF\)，在 managed 程式碼中實作功能完整的語言服務的相關資訊。  
  
 [支援符號瀏覽工具](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 描述程式庫和工具，可讓您瀏覽樹狀檢視的 IDE 中的符號。  
  
## 相關章節  
 [編輯器和語言服務擴充功能](../../extensibility/editor-and-language-service-extensions.md)  
 提供 Visual Studio 編輯器的概觀。  
  
 [語言服務支援偵錯](../../extensibility/internals/language-service-support-for-debugging.md)  
 Visual Studio 偵錯 sdk 》，其中包含建立和自訂用來偵錯程式的偵錯工具元件需要的資訊來提供資訊和連結。