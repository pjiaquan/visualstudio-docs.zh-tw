---
title: "VSG_NODEFAULT_INSTANCE | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 19c95b0d-9a4d-441f-9ed7-3acb39e67521
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# VSG_NODEFAULT_INSTANCE
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

由它的存在來定義是否已提供 [VsgDbg 類別](../debugger/vsgdbg-class.md) 類別——其提供程式設計方式擷取介面——的預設執行個體。  
  
## 語法  
  
```cpp  
#define VSG_NODEFAULT_INSTANCE  
```  
  
## 值  
 前置處理器符號，由其存在與否判斷是否已經提供 `VsgDbg` 類別的預設執行個體。  如果此符號已定義，則不會提供 `VsgDbg` 類別的預設執行個體；否則在您的程式執行之前會提供預設的執行個體並初始化之。  
  
 程式設計方式擷取介面將由具有全域範圍的指標`g_pVsgDbg`所提供。  
  
```  
VsgDbg *g_pVsgDbg;  
```  
  
## 備註  
 預設執行個體通常已足夠，不過，當 D3D 裝置建立於DLL外部時，若要使用程式設計擷取DLL 內的介面，您必須建立及管理 `VsgDbg` 類別的執行個體。  如果您以這種方式管理介面對程式設計擷取應用程式開發介面，請定義 `VSG_NODEFAULT_INSTANCE` 避免額外負荷，來停用預設執行個體。  
  
 如果預設執行個體尚未停用，它會在您的程式執行前自動進行初始化，並在程式結束時自動終結。  您不需要對此執行個體作明確初始化或未初始化。  
  
 若要停用預設執行個體，您必須在程式引用 `vsgcapture.h`之前，先定義 `VSG_NODEFAULT_INSTANCE` 。  
  
## 範例  
 這個範例顯示如何停用預設執行個體：  
  
```  
// Define VSG_NODEFAULT_INSTANCE before including vsgcapture.h  
#define VSG_NODEFAULT_INSTANCE  
  
#include <vsgcapture.h>  
```