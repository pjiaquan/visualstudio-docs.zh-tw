---
title: "METADATA_TYPE |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- METADATA_TYPE
helpviewer_keywords:
- METADATA_TYPE structure
ms.assetid: 2d8b78f6-0aef-4d79-809a-cff9b2c24659
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 478cf0efe2bcb9079731ffd3154ce55352e35805
ms.lasthandoff: 02/22/2017

---
# <a name="metadatatype"></a>METADATA_TYPE
此結構會指定從中繼資料的欄位類型的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
typedef struct _tagTYPE_METADATA {  
   ULONG32  ulAppDomainID;  
   GUID     guidModule;  
   _mdToken tokClass;  
} METADATA_TYPE;  
```  
  
```c#  
public struct METADATA_TYPE {  
   public uint ulAppDomainID;  
   public Guid guidModule;  
   public int  tokClass;  
};  
```  
  
#### <a name="parameters"></a>參數  
 ulAppDomainID  
 應用程式的來源符號的識別碼。 這用來唯一識別應用程式的執行個體。  
  
 guidModule  
 模組包含此欄位的 GUID。  
  
 tokClass  
 此類型的中繼資料語彙基元的識別碼。  
  
 [C++]`_mdToken` is a `typedef` for a 32-bit `int`.  
  
## <a name="remarks"></a>備註  
 此結構會顯示在聯集的一部分[TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)結構時`dwKind`欄位`TYPE_INFO`結構設`TYPE_KIND_METADATA`(介於[dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)列舉型別)。  
  
 `tokClass`值是唯一識別型別的中繼資料語彙基元。 如需有關如何解譯較高的位元的中繼資料語彙基元 ID 的詳細資訊，請參閱`CorTokenType`corhdr.h 檔案中列舉[!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)]SDK。  
  
## <a name="requirements"></a>需求  
 標頭︰ sh.h  
  
 命名空間︰ Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰ Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
