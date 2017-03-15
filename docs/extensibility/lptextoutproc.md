---
title: "LPTEXTOUTPROC |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- LPTEXTOUTPROC
helpviewer_keywords:
- SccMsgDataOnMessage structure
- SccMsgDataOnBeforeGetFile structure
- SccMsgDataIsCancelled structure
- LPTEXTOUTPROC callback function
- SccMsgDataOnAfterGetFile structure
ms.assetid: 2025c969-e3c7-4cf4-a5c5-099d342895ea
caps.latest.revision: 21
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
ms.openlocfilehash: 7229d2681912663ad2cddcf95e140197495c0934
ms.lasthandoff: 02/22/2017

---
# <a name="lptextoutproc"></a>LPTEXTOUTPROC
當使用者執行從原始檔控制作業，在整合式的開發環境 (IDE) 內時，原始檔控制外掛程式可能會想要傳遞與作業相關的錯誤或狀態訊息。 外掛程式可以針對此目的顯示自己的訊息方塊。 不過，更多的緊密整合，外掛程式可以將字串傳遞至 IDE 中，然後顯示其原生方法來顯示狀態資訊。 這個機制是`LPTEXTOUTPROC`函式指標。 IDE 會實作此函式 （在下面詳細說明） 來顯示錯誤和狀態。  
  
 IDE 會傳遞至原始檔控制外掛程式函式指標，此函式，當成`lpTextOutProc`參數呼叫時[SccOpenProject](../extensibility/sccopenproject-function.md)。 SCC 作業期間，例如，呼叫中間[SccGet](../extensibility/sccget-function.md)涉及多個檔案，此外掛程式可以呼叫`LPTEXTOUTPROC`函式，定期將傳遞要顯示的字串。 IDE 可能會在狀態列上，在輸出視窗中，或在個別的訊息方塊中，適當地顯示這些字串。 （選擇性） 在 IDE 可能可以顯示與特定訊息**取消** 按鈕。 這可讓使用者取消作業，並提供 IDE 將此資訊傳回給外掛程式的能力。  
  
## <a name="signature"></a>簽章  
 IDE 的輸出函式具有下列簽章︰  
  
```cpp#  
typedef LONG (*LPTEXTOUTPROC) (  
   LPSTR display_string,  
   LONG mesg_type  
);  
```  
  
## <a name="parameters"></a>參數  
 display_string  
 若要顯示的文字字串。 這個字串不應以歸位字元傳回或換行字元結尾。  
  
 mesg_type  
 訊息的類型。 下表列出支援的值，這個參數。  
  
|值|描述|  
|-----------|-----------------|  
|`SCC_MSG_INFO, SCC_MSG_WARNING, SCC_MSG_ERROR`|訊息會視為資訊、 警告或錯誤。|  
|`SCC_MSG_STATUS`|訊息會顯示狀態，且可以在狀態列中顯示。|  
|`SCC_MSG_DOCANCEL`|不傳送任何訊息字串。|  
|`SCC_MSG_STARTCANCEL`|開始顯示**取消** 按鈕。|  
|`SCC_MSG_STOPCANCEL`|停止顯示**取消** 按鈕。|  
|`SCC_MSG_BACKGROUND_IS_CANCELLED`|詢問 IDE 背景作業是否會取消︰ IDE 傳回`SCC_MSG_RTN_CANCEL`如果作業已取消; 否則會傳回`SCC_MSG_RTN_OK`。 `display_string`參數轉換成[SccMsgDataIsCancelled](#LinkSccMsgDataIsCancelled)結構，其中提供的原始檔控制外掛程式。|  
|`SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE`|擷取從版本控制之前告訴 IDE 檔案。 `display_string`參數轉換成[SccMsgDataOnBeforeGetFile](#LinkSccMsgDataOnBeforeGetFile)結構，其中提供的原始檔控制外掛程式。|  
|`SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE`|告訴 IDE 檔案之後擷取從版本控制。 `display_string`參數轉換成[SccMsgDataOnAfterGetFile](#LinkSccMsgDataOnAfterGetFile)結構，其中提供的原始檔控制外掛程式。|  
|`SCC_MSG_BACKGROUND_ON_MESSAGE`|告訴 IDE 的背景作業的目前狀態。 `display_string`參數轉換成[SccMsgDataOnMessage](#LinkSccMsgDataOnMessage)結構，其中提供的原始檔控制外掛程式。|  
  
## <a name="return-value"></a>傳回值  
  
|值|描述|  
|-----------|-----------------|  
|SCC_MSG_RTN_OK|顯示字串，或作業已順利完成。|  
|SCC_MSG_RTN_CANCEL|使用者想要取消作業。|  
  
## <a name="example"></a>範例  
 假設 IDE 呼叫[SccGet](../extensibility/sccget-function.md)與&20; 個檔案名稱。 原始檔控制外掛程式想要防止取消中間檔案 get 作業。 取得之後的每個檔案，它會呼叫`lpTextOutProc`、 每個檔案，在傳遞狀態資訊並傳送`SCC_MSG_DOCANCEL`訊息如果還沒有狀態可以報告。 如果在任何時候外掛程式接收傳回值為`SCC_MSG_RTN_CANCEL`從 IDE，就會取消取得作業，以便不擷取任何檔案。  
  
## <a name="structures"></a>結構  
  
###  <a name="a-namelinksccmsgdataiscancelleda-sccmsgdataiscancelled"></a><a name="LinkSccMsgDataIsCancelled"></a>SccMsgDataIsCancelled  
  
```cpp#  
typedef struct {  
   DWORD dwBackgroundOperationID;  
} SccMsgDataIsCancelled;  
```  
  
 此結構會一起傳送`SCC_MSG_BACKGROUND_IS_CANCELLED`訊息。 它用來取消背景作業的識別碼。  
  
###  <a name="a-namelinksccmsgdataonbeforegetfilea-sccmsgdataonbeforegetfile"></a><a name="LinkSccMsgDataOnBeforeGetFile"></a>SccMsgDataOnBeforeGetFile  
  
```cpp#  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szFile;  
} SccMsgDataOnBeforeGetFile;  
```  
  
 此結構會一起傳送`SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE`訊息。 它用來傳達即將擷取檔案的名稱，以及擷取正在進行背景作業的識別碼。  
  
###  <a name="a-namelinksccmsgdataonaftergetfilea-sccmsgdataonaftergetfile"></a><a name="LinkSccMsgDataOnAfterGetFile"></a>SccMsgDataOnAfterGetFile  
  
```cpp#  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szFile;  
   SCCRTN sResult;  
} SccMsgDataOnAfterGetFile;  
```  
  
 此結構會一起傳送`SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE`訊息。 它用來擷取指定的檔案，以及未擷取背景作業的識別碼的結果進行通訊。 請參閱的傳回值[SccGet](../extensibility/sccget-function.md)的功能都可以獲得結果。  
  
###  <a name="a-namelinksccmsgdataonmessagea-sccmsgdataonmessage"></a><a name="LinkSccMsgDataOnMessage"></a>SccMsgDataOnMessage  
 [C++]  
  
```  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szMessage;  
   BOOL bIsError;  
} SccMsgDataOnMessage;  
```  
  
 此結構會一起傳送`SCC_MSG_BACKGROUND_ON_MESSAGE`訊息。 它用來傳達背景作業的目前狀態。 狀態會表示為字串的 IDE，來顯示和`bIsError`指出訊息的嚴重性 (`TRUE`的錯誤訊息。`FALSE`警告或資訊訊息)。 也會提供將訂單狀態傳送背景作業的識別碼。  
  
## <a name="code-example"></a>程式碼範例  
 以下是電話的簡短範例`LPTEXTOUTPROC`傳送`SCC_MSG_BACKGROUND_ON_MESSAGE`訊息，說明如何呼叫轉換的結構。  
  
```cpp#  
LONG SendStatusMessage(  
    LPTEXTOUTPROC pTextOutProc,  
    DWORD         dwBackgroundID,  
    LPCTSTR       pStatusMsg,  
    BOOL          bIsError)  
{  
    SccMsgDataOnMessage msgData = { 0 };  
    LONG                result  = 0;  
  
    msgData.dwBackgroundOperationID = dwBackgroundID;  
    msgData.szMessage               = pStatusMsg;  
    msgData.bIsError                = bIsError;  
  
    result = pTextOutProc(reinterpret_cast<LPCTSTR>(&msgData), SCC_MSG_BACKGROUND_ON_MESSAGE);  
    return result;  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [IDE 所實作的回呼函式](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)
