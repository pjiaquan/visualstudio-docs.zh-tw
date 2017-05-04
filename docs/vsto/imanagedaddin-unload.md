---
title: "IManagedAddin::Unload | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Unload 方法"
  - "IManagedAddin::Unload"
ms.assetid: 40a73f07-2605-4745-8ac5-0a0189167fd7
caps.latest.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# IManagedAddin::Unload
  卸載 Managed VSTO 增益集之前呼叫。  
  
## 語法  
  
```  
HRESULT Unload();  
```  
  
## 傳回值  
 HRESULT 值，表示此方法是否已順利完成。  
  
## 備註  
 Microsoft Office 的目前版本不會呼叫這個方法。 這個方法是保留供日後使用。  
  
## 請參閱  
 [IManagedAddin 介面](../vsto/imanagedaddin-interface.md)   
 [IManagedAddin::Load](../vsto/imanagedaddin-load.md)  
  
  