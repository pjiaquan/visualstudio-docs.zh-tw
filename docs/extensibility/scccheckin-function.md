---
title: "SccCheckin 函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccCheckin
helpviewer_keywords:
- SccCheckin function
ms.assetid: e3f26ac2-6163-42e1-a764-22cfea5a3bc6
caps.latest.revision: 16
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
ms.openlocfilehash: e8bfa87246bc866a251951e4700b796d833dd63f
ms.lasthandoff: 02/22/2017

---
# <a name="scccheckin-function"></a>SccCheckin 函式
此函式先前已簽出將檔案簽入原始檔控制系統，儲存所做的變更和建立新的版本。 以計數和簽入的檔案名稱的陣列，會呼叫此函數。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
SCCRTN SccCheckin (  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPSTR*    lpFileNames,  
   LPCSTR    lpComment,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>參數  
 pvContext  
 [in]原始檔控制外掛程式內容結構。  
  
 hWnd  
 [in]SCC 外掛程式使用一層，它會提供任何對話方塊 IDE 視窗控制代碼。  
  
 nFiles  
 [in]選取要簽入檔案的數目。  
  
 lpFileNames  
 [in]簽入檔案的完整格式的本機路徑名稱的陣列。  
  
 lpComment  
 [in]若要套用至每個選取的檔案在存回註解。 這是`NULL`如果原始檔控制外掛程式應該提示使用者輸入註解。  
  
 Stored  
 [in]命令旗標、 0 或`SCC_KEEP_CHECKEDOUT`。  
  
 pvOptions  
 [in]SCC 外掛程式專屬選項。  
  
## <a name="return-value"></a>傳回值  
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一︰  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|檔案已成功簽入。|  
|SCC_E_FILENOTCONTROLLED|選取的檔案不是原始程式碼控制之下。|  
|SCC_E_ACCESSFAILURE|無法存取原始檔控制系統，可能是因為網路或競爭問題。 建議使用重試。|  
|SCC_E_NONSPECIFICERROR|非特定的失敗。 檔案尚未登入。|  
|SCC_E_NOTCHECKEDOUT|使用者不具有簽出檔案，因此無法簽入。|  
|SCC_E_CHECKINCONFLICT|無法執行簽入，因為︰<br /><br /> -繼續另一位使用者簽入和`bAutoReconcile`時發生錯誤。<br /><br /> -或-<br /><br /> （例如，當檔案是二進位），則無法執行-自動合併。|  
|SCC_E_VERIFYMERGE|檔案已經自動合併，但是有尚未簽入暫止的使用者驗證。|  
|SCC_E_FIXMERGE|檔案已經自動合併，但尚未簽因為必須以手動方式解決合併衝突。|  
|SCC_E_NOTAUTHORIZED|不允許使用者執行這項作業。|  
|SCC_I_OPERATIONCANCELED|在完成之前取消作業。|  
|SCC_I_RELOADFILE|需要重新載入檔案或專案。|  
|SCC_E_FILENOTEXIST|找不到本機檔案。|  
  
## <a name="remarks"></a>備註  
 註解適用於所簽入的所有檔案。 註解引數可以是`null`字串，在此情況下的原始檔控制外掛程式可以提示使用者輸入的每個檔案的註解字串。  
  
 `fOptions`引數可以指定的值為`SCC_KEEP_CHECKEDOUT`旗標，表示要檢查的檔案，並再次查看使用者的意圖。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
