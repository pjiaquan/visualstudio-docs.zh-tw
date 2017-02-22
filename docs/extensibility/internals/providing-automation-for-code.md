---
title: "提供自動化的程式碼 | Microsoft Docs"
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
  - "CodeModel 物件"
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# 提供自動化的程式碼
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

建立自動化模型的程式碼不是必要的。  環境 SDK 並未提供這樣的範例。  開發程式碼模型，請參閱<xref:EnvDTE.CodeModel>物件。  
  
 若要實作程式碼模型，您必須實作由您的內部資料結構的任何介面。  物件必須衍生自`IDispatch` 類別。  
  
 物件，將其延伸， <xref:EnvDTE.CodeModel>和<xref:EnvDTE.FileCodeModel>，可以從<xref:EnvDTE.Project>物件，並看起來如下：  
  
 <xref:EnvDTE.Project.CodeModel%2A>  
  
 <xref:EnvDTE.ProjectItem.FileCodeModel%2A>  
  
 您可以選擇實作只是`CodeModel`或`FileCodeModel`介面，您即可從傳回的物件中您`Project`和<xref:EnvDTE.ProjectItem>物件。  提供從這個介面適用於您的專案系統的任何功能。  
  
 如果您想要新增功能，例如方法或屬性時無法使用標準`CodeModel`和`FileCodeModel`介面，建立自己的標準會繼承的介面。  請務必記錄與您的專案系統，讓一般使用者也將會尋找它。  傳回標準的介面，但使用者可以呼叫`QueryInterface`方法或轉型，您若已知存在的介面。  
  
## 請參閱  
 [自動化模型概觀](../../extensibility/internals/automation-model-overview.md)