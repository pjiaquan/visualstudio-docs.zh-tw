---
title: "實作傳統語言服務 | Microsoft Docs"
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
  - "管理語言服務"
ms.assetid: df638f24-166d-4b80-be82-c9c39ca7a556
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# 實作傳統語言服務
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

您可以使用受管理的封裝架構 \(MPF\) 中的類別來實作可支援各種不同的功能，舊版的語言服務，例如語法反白顯示、 括號對稱和 IntelliSense 完成。  
  
 舊版的語言服務會實作成，VSPackage 的一部分，但實作語言服務功能的較新的方法是使用 MEF 延伸模組。 若要了解有關實作語言服務的新方法的詳細資訊，請參閱 [編輯器和語言服務擴充功能](../../extensibility/editor-and-language-service-extensions.md)。  
  
> [!NOTE]
>  我們建議您開始使用新的編輯器 API 儘速。 這會改善語言服務的效能，並可讓您充分利用新編輯器功能。  
  
## 在本節中  
 [舊版的語言服務概觀](../../extensibility/internals/legacy-language-service-overview.md)  
 MPF 中支援的語言服務功能的概觀。  
  
 [實作語言服務](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
 說明為何需要使用 MPF 實作語言服務。  
  
 [註冊語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md)  
 說明註冊與 MPF 為基礎的語言服務所需的步驟 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 [舊版的語言服務剖析器和掃描器](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)  
 描述使用 MPF 實作語言服務的所有功能所需的兩個分析。  
  
 [逐步解說︰ 建立傳統語言服務](../../extensibility/internals/walkthrough-creating-a-legacy-language-service.md)  
 提供在 VSPackage 中實作的 MPF 語言服務所需的基本步驟。  
  
 [逐步解說︰ 開始安裝的程式碼片段 （舊版實作） 的清單](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)  
 示範的技術，擷取安裝的程式碼片段的清單。  
  
 [舊版的語言服務功能](../../extensibility/internals/legacy-language-service-features1.md)  
 提供主題連結，該做什麼才能使用 MPF 實作語言服務的所有功能的詳細資料。