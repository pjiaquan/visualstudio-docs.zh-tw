---
title: "原始檔控制外掛程式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "原始檔控制外掛程式參考"
ms.assetid: 964980ca-21c5-4706-8535-6ea23e1c9cc9
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# 原始檔控制外掛程式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

原始檔控制外掛程式 SDK 參考章節包含可讓與整合的原始檔控制系統的完整介面規格 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 它會指定的語法和語意 \(semantics\) 的原始檔控制外掛程式必須實作介面的各種函式和資料類型 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 整合式的開發環境 \(IDE\)。  
  
## 在本節中  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)  
 列出原始檔控制外掛程式必須遵守原始檔控制外掛程式 API 實作的函式。  
  
 [IDE 所實作的回呼函式](../extensibility/callback-functions-implemented-by-the-ide.md)  
 描述函式的原始檔控制外掛程式用來執行特定命令時，將資訊傳遞至 IDE。  
  
 [列舉值](../extensibility/enumerators.md)  
 列出原始檔控制外掛程式必須了解的原始檔控制外掛程式 API 中的列舉值資料類型。  
  
 [功能旗標](../extensibility/capability-flags.md)  
 描述 `SCC_CAP_xxx` 旗標，會指示提供者的能力。  
  
 [特定命令所使用的位元旗標](../extensibility/bitflags-used-by-specific-commands.md)  
 列出可在特定命令的內容中的旗標。  
  
 [錯誤代碼](../extensibility/error-codes.md)  
 列出做為函式所傳回的常見錯誤值 `SCCTRN`。  
  
 [使用做為索引鍵來尋找原始檔控制外掛程式的字串](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)  
 描述用於存取登錄，以尋找原始檔控制外掛程式。  
  
 [MSSCCPRJ。SCC 檔案](../extensibility/mssccprj-scc-file.md)  
 描述用戶端檔案，其中包含資訊的不透明的 ide，但由原始檔控制外掛程式用來在版本控制中，找出方案或專案。  
  
 [實作原始檔控制外掛程式的最佳作法](../extensibility/best-practices-for-implementing-a-source-control-plug-in.md)  
 提供要記住，雖然您正在實作原始檔控制外掛程式 API 的重要技術提醒的集合。  
  
 [字串長度限制](../extensibility/restrictions-on-string-lengths.md)  
 描述限制在原始檔控制外掛程式 API 中的各種函式中使用的字串長度。  
  
 [字彙表](../extensibility/source-control-plug-in-glossary.md)  
 提供有用的條款與它們的定義來讀取原始檔控制外掛程式 SDK 文件。  
  
 [如何: 關閉原始檔控制外掛程式的相容性警告](../extensibility/how-to-turn-off-compatibility-warnings-for-source-control-plug-ins.md)  
 描述如何停用警告。  
  
## 相關章節  
 [Source Control Plug\-in Sample](http://msdn.microsoft.com/zh-tw/61de7d2b-71db-451e-8e3e-d41b11c7a4ca)  
 提供的原始檔控制外掛程式功能的範例。  
  
 [原始檔控制外掛程式的測試指南](../extensibility/internals/test-guide-for-source-control-plug-ins.md)  
 描述原始檔控制外掛程式的相關測試程序。  
  
 [建立原始檔控制外掛程式](../extensibility/internals/creating-a-source-control-plug-in.md)  
 討論如何建立原始檔控制外掛程式提供原始檔控制功能，當您使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 原始檔控制使用者介面 \(UI\)。  
  
 [Visual Studio SDK 參考](../extensibility/visual-studio-sdk-reference.md)  
 列出的參考主題。