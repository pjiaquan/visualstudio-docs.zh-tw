---
title: "IDispError 介面 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDispError 介面"
ms.assetid: 3dc7b55e-94ba-4669-b20a-1e011f2d07cf
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispError 介面
提供相關錯誤訊息。  
  
> [!NOTE]
>  這個介面在實作。  
  
 除了繼承自 `IUnknown` 的方法之外，`IDispError` 介面還會公開下列方法。  
  
## 依照 Vtable 順序的方法  
  
|方法|描述|  
|--------|--------|  
|[IDispError::QueryErrorInfo](../../winscript/reference/idisperror-queryerrorinfo.md)|擷取錯誤訊息的特定型別。|  
|[IDispError::GetNext](../../winscript/reference/idisperror-getnext.md)|擷取下一 `IDispError` 物件。|  
|[IDispError::GetHresult](../../winscript/reference/idisperror-gethresult.md)|從 `IDispError` 物件擷取錯誤碼。|  
|[IDispError::GetSource](../../winscript/reference/idisperror-getsource.md)|傳回引發錯誤的類別或應用程式的語言相關的程式設計識別項。|  
|[IDispError::GetHelpInfo](../../winscript/reference/idisperror-gethelpinfo.md)|如果可能傳回說明檔和說明錯誤主題代碼的路徑。|  
|[IDispError::GetDescription](../../winscript/reference/idisperror-getdescription.md)|傳回錯誤的文字描述。|