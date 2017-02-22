---
title: "消除 ~ SAK 檔案 | Microsoft Docs"
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
  - "暫存檔案"
  - "~ sak 檔案"
  - "原始檔控制外掛程式，~ SAK 檔案"
ms.assetid: 5277b5fa-073b-4bd1-8ba1-9dc913aa3c50
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# 消除 ~ SAK 檔案
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

在 \[原始檔控制外掛程式 API 1.2 ~ SAK 檔案已被取代功能旗標，並偵測到的原始檔控制外掛程式是否支援共用簽出與 MSSCCPRJ 檔案的新函式。  
  
## ~ SAK 的檔案  
 Visual Studio。NET 2003 中建立暫存檔，前面加上 ~ SAK。  這些檔案用來決定是否要支援的原始檔控制外掛程式：  
  
-   MSSCCPRJ。SCC 檔。  
  
-   多重 \(共用\) 的簽出。  
  
 外掛? 式在原始檔控制外掛程式 API 1.2 支援所提供的進階的功能，如 IDE 可以偵測到這些功能，而不需要建立暫存檔案使用的新功能、 旗標和函式，下列章節將詳細說明。  
  
## 新功能的旗標  
 `SCC_CAP_SCCFILE`  
  
 `SCC_CAP_MULTICHECKOUT`  
  
## 新函式  
 [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)  
  
 [SccIsMultiCheckoutEnabled](../../extensibility/sccismulticheckoutenabled-function.md)  
  
 如果原始檔控制外掛程式支援多重 \(共用\) 的簽出，那麼它會宣告`SCC_CAP_MULTICHECKOUT`功能和實作`SccIsMultiCheckOutEnabled`函式。  在任何原始檔控制專案的簽出作業發生時，會呼叫這個函式。  
  
 如果原始檔控制外掛程式可支援建立和使用的 MSSCCPRJ。SCC 檔，則它會宣告`SCC_CAP_SCCFILE`功能和實作[SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)。  這個函式呼叫時的檔案清單。  函式會傳回`TRUE/FALSE`的每個檔案來指示是否使用 Visual Studio 的 MSSCCPRJ。SCC 檔，讓它。  如果原始檔控制外掛程式選擇不支援這些新功能和函式，它可以使用下列的登錄機碼來停用建立這些檔案：  
  
 \[\] HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\8.0\\SourceControl"DoNotCreateTemporaryFilesInSourceControl"\= dword:00000001  
  
> [!NOTE]
>  如果這個登錄機碼設為 dword:00000000，它與機碼已不存在，而且 Visual Studio 仍會嘗試建立暫存檔案。  不過，如果登錄機碼設為 dword:00000001，Visual Studio 不會建立暫存檔案。  而是它假設原始檔控制外掛程式不支援的 MSSCCPRJ。SCC 檔並不支援共用簽出。  
  
## 請參閱  
 [原始檔控制外掛程式 API 版本 1.2 新功能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)