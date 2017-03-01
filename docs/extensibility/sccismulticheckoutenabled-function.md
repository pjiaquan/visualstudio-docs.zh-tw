---
title: "SccIsMultiCheckoutEnabled 函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccIsMultiCheckoutEnabled
helpviewer_keywords:
- SccIsMultiCheckoutEnabled function
ms.assetid: 6721639d-e475-4766-81b5-ee40a280fc70
caps.latest.revision: 13
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
ms.openlocfilehash: 3d767767f3e2d8d3b67971dceda49c8309c549bb
ms.lasthandoff: 02/22/2017

---
# <a name="sccismulticheckoutenabled-function"></a>SccIsMultiCheckoutEnabled 函式
此函式會檢查原始檔控制外掛程式是否允許多重簽出檔案。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
SCCRTN SccIsMultiCheckoutEnabled(  
   LPVOID pContext,  
   LPBOOL pbMultiCheckout  
);  
```  
  
#### <a name="parameters"></a>參數  
 pContext  
 [in]原始檔控制外掛程式內容結構。  
  
 pbMultiCheckout  
 [out]指定是否啟用多重簽出，以供此專案 （非零值表示，並支援多重簽出）。  
  
## <a name="return-value"></a>傳回值  
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一︰  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|檢查已成功。|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|非特定的失敗。|  
  
## <a name="remarks"></a>備註  
 IDE 可讓兩個檢查，以便決定是否檔案可以簽出同時由多個使用者。 首先，原始檔控制系統必須支援多重簽出。 原始檔控制外掛程式可以藉由指定初始化過程中指定這項功能`SCC_CAP_MULTICHECKOUT`。 此後，第二個檢查，IDE 會呼叫此函式可判斷目前的專案支援多重簽出。 如果選取的專案支援多重簽出，此外掛程式將傳回成功的程式碼，並設定`pbMultiCheckout`為非零 (`TRUE`) 或`FALSE`。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
