---
title: "IDebugContainerField::EnumFields |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugContainerField::EnumFields
helpviewer_keywords:
- IDebugContainerField::EnumFields method
ms.assetid: 9e5e681b-ad49-4c62-bd95-4afa11d61a57
caps.latest.revision: 10
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
ms.openlocfilehash: d0b126d5bc2de796cb9d9afc2e5ff9a832c79bab
ms.lasthandoff: 02/22/2017

---
# <a name="idebugcontainerfieldenumfields"></a>IDebugContainerField::EnumFields
建立容器的欄位的列舉值。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT EnumFields(   
   FIELD_KIND         dwKindFilter,  
   FIELD_MODIFIERS    dwModifiersFilter,  
   LPCOLESTR          pszNameFilter,  
   NAME_MATCH         nameMatch,  
   IEnumDebugFields** ppEnum  
);  
```  
  
```c#  
int EnumFields(  
   enum_ FIELD_KIND      dwKindFilter,   
   enum_ FIELD_MODIFIERS dwModifiersFilter,   
   string                pszNameFilter,   
   NAME_MATCH            nameMatch,   
   out IEnumDebugFields  ppEnum  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwKindFilter`  
 [in]結合[FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)選取的欄位来列舉的常數。 欄位類型可以描述存放裝置類型，例如類別或基本類型，或特定的資訊，例如本機、 參數或 「 this 」 指標。  
  
 `dwModifiersFilter`  
 [in]結合[FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)選取的欄位来列舉的常數。 欄位修飾詞可存取的權限，例如公用或私用或儲存體資訊，例如虛擬、 靜態的或最後一個。  
  
 `pszNameFilter`  
 [in]要列舉之欄位的名稱。 如果要傳回的所有欄位都是，這可以是 null 值。  
  
 `nameMatch`  
 [in]介於[NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)列舉型別會控制搜尋是否區分大小寫。  
  
 `ppEnum`  
 [out]傳回[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)物件，代表欄位的清單。 如果沒有任何欄位，則傳回 null 值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回 S_OK 或 S_FALSE，如果沒有任何欄位。 反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 `dwKindFilter`， `dwModifiersFilter`，和`pszNameFilter`參數可以結合，例如，若要選取名為 「 MyMethod 」 的所有公用的虛擬方法。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)   
 [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)   
 [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)
