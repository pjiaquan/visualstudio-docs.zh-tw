---
title: "開發語言服務 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.vsip.LangServWiz.langtoks"
  - "vs.vsip.LangServWiz.welcome"
  - "vs.vsip.LangServWiz.langSpec"
  - "vs.vsip.LangServWiz.langInfo"
  - "vs.vsip.LangServWiz.langServOpts"
helpviewer_keywords: 
  - "語言服務開發"
ms.assetid: 6151ba88-c1c3-41de-a1cc-668f494d48d1
caps.latest.revision: 28
caps.handback.revision: 28
ms.author: "gregvanl"
manager: "ghogen"
---
# 開發語言服務
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

本小節會連結至主題可協助您建立舊版語言服務。  
  
 舊版的語言服務會實作成，VSPackage 的一部分，但實作語言服務功能的較新的方法是使用 MEF 延伸模組。 若要了解有關實作語言服務的新方法的詳細資訊，請參閱 [編輯器和語言服務擴充功能](../../extensibility/editor-and-language-service-extensions.md)。  
  
> [!NOTE]
>  我們建議您開始使用新的編輯器 API 儘速。 這會改善語言服務的效能，並可讓您充分利用新編輯器功能。  
  
## 在本節中  
 [舊版語言服務模型](../../extensibility/internals/model-of-a-legacy-language-service.md)  
 提供的最小語言服務模型 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 核心編輯器。 您可以使用這個模型做為指南，來建立您自己的語言服務。  
  
 [舊版的語言服務介面](../../extensibility/internals/legacy-language-service-interfaces.md)  
 討論實作語言服務所需的物件，並提供可用來提供語法反白顯示、 方法的資料，以及其他功能的其他物件的清單。  
  
 [攔截舊版語言服務命令](../../extensibility/internals/intercepting-legacy-language-service-commands.md)  
 說明如何插入至您的語言服務，以攔截命令文字檢視會處理的命令篩選器。  
  
 [註冊舊版語言服務](../../extensibility/internals/registering-a-legacy-language-service2.md)  
 提供如何使用註冊語言服務的相關資訊 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 [語言服務支援偵錯](../../extensibility/internals/language-service-support-for-debugging.md)  
 描述如何語言服務可以提供功能，可支援偵錯工具。  
  
 [檢查清單︰ 建立傳統語言服務](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)  
 提供逐步指示，建立以及整合核心編輯器的語言服務。  
  
## 相關章節  
 [語法著色在舊版語言服務](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 討論如何實作語言服務中的語法反白顯示。  
  
 [在舊版語言服務中的陳述式完成](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)  
 討論陳述式完成時，處理程序語言服務用來協助使用者完成語言關鍵字或啟動後輸入的項目。  
  
 [在舊版語言服務中的參數資訊](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)  
 描述如何為多載函式和方法提供方法提示。  
  
 [如何︰ 隱藏的文字中提供支援舊版語言服務](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)  
 說明隱藏的文字區域的用途，並提供指示，說明如何實作一個隱藏的文字區域。  
  
 [如何︰ 展開大綱中提供支援舊版語言服務](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)  
 說明擴充大綱您只能支援的語言支援的兩個選項 *摺疊至定義* 命令。