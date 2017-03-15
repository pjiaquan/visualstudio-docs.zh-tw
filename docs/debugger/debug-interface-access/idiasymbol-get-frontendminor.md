---
title: "IDiaSymbol::get_frontEndMinor | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaSymbol::get_frontEndMinor 方法"
ms.assetid: 40792153-827c-4859-be7c-6aa16d5abab6
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_frontEndMinor
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取前端次要版本號碼。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT get_frontEndMinor (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]傳回 front.end 次要版本號碼。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回 `S_OK`，否則會傳回 `S_FALSE` 或錯誤碼。  
  
> [!NOTE]
>  傳回值為 `S_FALSE` 表示屬性不是可用的符號。  
  
## <a name="remarks"></a>備註  
 編譯器通常組成兩個主要項目︰ 前端 （剖析器） 會處理剖析中繼形式的原始碼，以及後端 （程式碼產生器），它會將中繼格式轉換成組件。 並不罕見的前端有後端的版本不同。  
  
 前端或後端版本號碼是三個部分組成︰ \< 主要>。 \< 次要>。 \< 建置>, ，其中 \< 主要> 是主要版本號碼，\< 次要> 是次要版本號碼，以及 \< 建置> 是組建編號。 例如，13.10.3077。  
  
## <a name="requirements"></a>需求  
  
|需求|描述|  
|-----------------|-----------------|  
|Header:|dia2.h|  
|版本:|DIA SDK v7.0|  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)