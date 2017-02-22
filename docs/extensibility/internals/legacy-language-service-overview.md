---
title: "舊版的語言服務概觀 | Microsoft Docs"
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
  - "語言服務的相關語言服務 [受管理的封裝 framework]"
ms.assetid: bb44e27b-d228-463c-b2cf-cd5c24c7c1b5
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# 舊版的語言服務概觀
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

提供可讓您實作特定的編輯器支援的語言服務[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]功能。  管理套件架構 \(MPF\) 語言服務類別提供常用的功能和部分支援其他功能的完整支援。  
  
## 完全支援的功能，在 MPF  
 MPF 語言服務類別支援下列功能：  
  
-   語法反白顯示  
  
-   大綱  
  
-   註解的程式碼區塊  
  
-   括號對稱  
  
-   程式碼片段  
  
-   自訂文件屬性  
  
-   IntelliSense 參數資訊  
  
-   IntelliSense 快速資訊  
  
-   IntelliSense 成員完成  
  
-   IntelliSense 文字自動完成  
  
## 部分支援的功能，在 MPF  
 MPF 提供下列功能僅部分支援。  這表示您必須實作由 MPF 所呼叫的方法。  
  
-   重新格式化程式碼。  您提供實作重新格式化的程式碼。  
  
-   驗證藉由識別有效的程式碼的中斷點都會擴展。  您提供用來識別程式碼 span 的程式碼。  
  
-   支援偵錯工具**自動變數**來顯示變數視窗。  您提供的程式碼，判斷應顯示在視窗中。  
  
-   支援**導覽列**型別和成員之間快速巡覽。  實作，並傳回填入的清單中的協助程式類別**導覽列**下拉式方塊。  
  
## 實作  
 您必須先完成幾個步驟，以實作 「 語言 」 服務本身，以及您想要為您的語言支援的語言服務功能。  下列主題將討論這些步驟執行：  
  
-   [實作語言服務](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
  
-   [註冊語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md)  
  
-   [語法色彩標示在舊版語言服務](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)  
  
-   [舊版語言服務中的比對括號](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)  
  
-   [舊版語言服務中的大綱](../../extensibility/internals/outlining-in-a-legacy-language-service.md)  
  
-   [在舊版語言服務中的註解程式碼](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)  
  
-   [重新格式化舊版語言服務中的程式碼](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)  
  
-   [在舊版語言服務中的自訂文件屬性](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)  
  
-   [在舊版語言服務中的程式碼片段的支援](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)  
  
-   [在舊版語言服務中的導覽列的支援](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)  
  
-   [在舊版語言服務中的文字完成](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)  
  
-   [在舊版語言服務中的成員完成](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)  
  
-   [在舊版語言服務中的參數資訊](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)  
  
-   [在舊版語言服務中的 \[快速諮詢](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)  
  
-   [支援舊版語言服務中的自動變數視窗](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)  
  
-   [驗證舊版語言服務中的中斷點](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)  
  
## 請參閱  
 [實作傳統語言服務](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [舊版的語言服務擴充性](../../extensibility/internals/legacy-language-service-extensibility.md)