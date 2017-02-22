---
title: "使用做為索引鍵來尋找原始檔控制外掛程式的字串 | Microsoft Docs"
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
  - "原始檔控制外掛程式，用於尋找字串"
ms.assetid: c1e31f76-42a1-4c3d-afb2-664044ef12fd
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# 使用做為索引鍵來尋找原始檔控制外掛程式的字串
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

下列字串是用於存取登錄，以尋找資訊的原始檔控制外掛程式。  
  
 `STR_SCC_PROVIDER_REG_LOCATION`, `STR_PROVIDERREGKEY`, ，`STR_SCCPROVIDERPATH`, ，和 `STR_SCCPROVIDERNAME` 登錄機碼或用來註冊為原始檔控制外掛程式的 DLL，Visual Studio 的值。  
  
 `SCC_PROJECTNAME_KEY`, `SCC_PROJECTAUX_KEY`, ，`SCC_KEY, SCC_FILE_SIGNATURE`, ，和 `SCC_STATUS_FILE` 用來描述 MSSCCPRJ 的格式。SCC 檔案。  
  
## 字串索引鍵和值  
  
|索引鍵|值|  
|---------|-------|  
|`STR_SCC_PROVIDER_REG_LOCATION`|Software\\SourceCodeControlProvider|  
|`STR_PROVIDERREGKEY`|ProviderRegKey|  
|`STR_SCCPROVIDERPATH`|SCCServerPath|  
|`STR_SCCPROVIDERNAME`|SCCServerName|  
|`STR_SCC_INI_SECTION`|原始程式碼控制|  
|`STR_SCC_INI_KEY`|SourceCodeControlProvider|  
|`SCC_PROJECTNAME_KEY`|SCC\_Project\_Name|  
|`SCC_PROJECTAUX_KEY`|SCC\_Aux\_Path|  
|`SCC_STATUS_FILE`|MSSCCPRJ。SCC|  
|`SCC_KEY`|SCC|  
|`SCC_FILE_SIGNATURE`|原始程式碼控制檔案|  
|`SCC_NSE`|命名空間擴充|  
|`SCC_NSE_PREFIX`|Protocal 前置詞|  
|`SCC_NSE_DisableOpenSCC`|DisableOpenFromSourceControl|  
|`STR_SCCHELPCOLLECTION`|HelpCollection|  
|`STR_UI_LANGUAGE`|UILanguage|  
|`STR_SRCSAFE_ROOT_KEY`|Software\\Microsoft\\SourceSafe|  
  
## 請參閱  
 [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)   
 [如何: 安裝原始檔控制外掛程式](../extensibility/internals/how-to-install-a-source-control-plug-in.md)   
 [MSSCCPRJ。SCC 檔案](../extensibility/mssccprj-scc-file.md)