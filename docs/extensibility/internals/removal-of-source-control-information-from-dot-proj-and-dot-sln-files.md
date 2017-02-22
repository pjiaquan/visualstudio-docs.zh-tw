---
title: "從原始檔控制資訊被移除。Proj 和。Sln 檔案 | Microsoft Docs"
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
  - "原始檔控制外掛程式、.sln 和.proj 檔案"
ms.assetid: 7b06883f-35de-41e2-9a9e-d3edba236f17
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# 從原始檔控制資訊被移除。Proj 和。Sln 檔案
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

在 \[原始檔控制外掛程式 API SCC 1.2 版資訊會儲存在 MSSCCPRJ 中。SCC 檔。  MSSCCPRJ 的優點。SCC 檔是 SCC 資訊是來源的控制，就像在.proj 和.sln 檔案。  
  
## 1.2 版變更  
 在 \[原始檔控制外掛程式會根據原始檔控制外掛程式 API 1.1 版，原始檔控制的相關資訊會儲存 \(.proj\) 的專案和方案 \(.sln\) 檔中。  資料庫位置的原始檔控制資訊所指定的 AuxPath，和在資料庫中的特定位置由指定 ProjName。  這種情形會造成問題，分支、 分叉或複製作業之後，因為 ProjName 通常具有無效後任何一項作業。  
  
 在 \[原始檔控制外掛程式 API 使用的版本 1.1 版中，IDE ~ 偵測如果外掛程式支援 MSSCCPRJ 的 SAK 檔案。SCC 儲存原始檔控制資訊的方法。  原始檔控制外掛程式 API 1.2 版提供偵測支援 「 MSSCCPRJ 」 的新功能。SCC 檔，而不需使用 ~ SAK 檔案。  如需詳細資訊，請參閱 [消除 ~ SAK 檔案](../../extensibility/internals/elimination-of-tilde-sak-files.md)。  
  
## 請參閱  
 [原始檔控制外掛程式 API 版本 1.2 新功能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)