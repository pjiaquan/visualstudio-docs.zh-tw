---
title: "舊版的語言服務 Features1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "語言服務 [受管理的封裝 framework]"
ms.assetid: a646e4f0-767d-4cd1-8e1a-9a2aa210a1b7
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# 舊版的語言服務功能
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

受管理的封裝架構 \(MPF\) 語言服務在一或多可支援[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]功能，例如語法反白顯示、 IntelliSense 和中斷點驗證。  每一項功能可獨立於其他實作，但所有需要剖析及掃描軟體除了語法反白顯示，而這會掃瞄器。  
  
## 在本節中  
 [舊版語言服務中的比對括號](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)  
 說明什麼是用來支援對應之後，也就括號對稱的語言配對。  
  
 [在舊版語言服務中的註解程式碼](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)  
 說明什麼是用來支援加註解，並選取的程式碼的 uncommenting。  
  
 [在舊版語言服務中的自訂文件屬性](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)  
 說明什麼是用來支援內嵌在原始程式檔中的文件內容。  
  
 [舊版語言服務中的大綱](../../extensibility/internals/outlining-in-a-legacy-language-service.md)  
 說明什麼是用來支援透過實作隱藏區域的大綱。  
  
 [重新格式化舊版語言服務中的程式碼](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)  
 說明什麼是用來支援 reformatting 的程式碼。  
  
 [在舊版語言服務中的程式碼片段的支援](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)  
 說明什麼是用來支援是程式碼的區段，就會插入，且可編輯的程式碼片段。  
  
 [在舊版語言服務中的參數資訊](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)  
 說明什麼是用來支援輸入方法時會顯示方法的簽章的 IntelliSense 參數資訊作業。  
  
 [在舊版語言服務中的 \[快速諮詢](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)  
 說明什麼是用來支援 IntelliSense 快速諮詢作業來顯示識別項的相關資訊。  
  
 [在舊版語言服務中的成員完成](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)  
 描述所需以支援從清單中選取的命名空間成員的 IntelliSense 成員完成作業。  
  
 [在舊版語言服務中的文字完成](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)  
 說明什麼是用來支援 IntelliSense 自動完成文字作業完成部分鍵入的文字。  
  
 [支援舊版語言服務中的自動變數視窗](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)  
 描述語言服務可執行以支援**自動變數**而您正在偵錯\] 視窗。  
  
 [在舊版語言服務中的導覽列的支援](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)  
 說明如何使用**導覽列**提供快速巡覽至任何型別或成員，該檢視中顯示檔案中的 \[編輯器\] 檢視的上方。.  
  
 [語法色彩標示在舊版語言服務](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)  
 說明什麼是用來支援語法反白顯示的原始程式碼。  
  
 [驗證舊版語言服務中的中斷點](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)  
 語言服務可以怎麼做才能支援驗證的中斷點，偵錯工具外部的描述。  
  
## 相關章節  
 [舊版的語言服務剖析器和掃描器](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)  
 描述的剖析器和實作的使用受管理的封裝架構的語言服務的所有功能所需的掃描程式。  
  
 [實作語言服務](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
 將告訴您為何需要使用 MPF 來實作語言服務。  
  
 [註冊語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md)  
 註冊以 MPF 為基礎的語言服務所需的步驟將告訴您[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 [使用 IntelliSense](../../ide/using-intellisense.md)  
 說明如何 IntelliSense 讓語言參考很容易存取。  
  
 [實作傳統語言服務](../../extensibility/internals/implementing-a-legacy-language-service1.md)  
 提供有關如何使用 managed 程式碼中實作全功能的語言服務的管理的套件架構 \(MPF\) 的資訊。