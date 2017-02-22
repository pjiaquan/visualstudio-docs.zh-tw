---
title: "字串長度限制 | Microsoft Docs"
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
  - "原始檔控制外掛程式，字串長度限制"
ms.assetid: 877173d2-ca27-43b3-b1f4-8379f7c5e268
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# 字串長度限制
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

原始檔控制外掛程式 API 限制各種函式中使用的字串的長度。  
  
## 字串長度值  
  
|常數|值|  
|--------|-------|  
|`SCC_NAME_LEN`|31|  
|`SCC_AUXLABEL_LEN`|31|  
|`SCC_USER_LEN`|31|  
|`SCC_PRJPATH_LEN`|300|  
  
> [!NOTE]
>  長度不包括結尾的 `null`。 其他常數"\_SIZE"後置詞，而不是 「 \_LEN 」 就是包含空間終止 `null`。  
  
|常數|值|  
|--------|-------|  
|SCC\_NAME\_SIZE|32|  
|SCC\_AUXLABEL\_SIZE|32|  
|SCC\_USER\_SIZE|32|  
|SCC\_PRJPATH\_SIZE|301|  
  
## 請參閱  
 [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)