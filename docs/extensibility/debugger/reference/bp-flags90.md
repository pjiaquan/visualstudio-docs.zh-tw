---
title: "BP_FLAGS90 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BP_FLAGS90 enumeration
ms.assetid: 3e5a06c5-fb30-4b8a-b2d5-4a0570fc80bd
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
ms.openlocfilehash: 4dfb7dc681519b37fe5cb9cd20e4bca22d800b96
ms.lasthandoff: 02/22/2017

---
# <a name="bpflags90"></a>BP_FLAGS90
列舉有效的選擇性旗標值。 選擇性旗標可能會用來指定當您設定中斷點的其他資訊。 這個列舉型別擴充[BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)列舉型別。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
enum enum_BP_FLAGS90  
{  
   // VS 8.0 values  
   BP90_FLAG_NONE               = 0x0000,  
   BP90_FLAG_MAP_DOCPOSITION    = 0x0001,  
   BP90_FLAG_DONT_STOP          = 0x0002,  
  
   // Values added in VS 9.0  
   BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,  
};  
typedef DWORD BP_FLAGS90;  
```  
  
```c#  
public enum enum_BP_FLAGS90  
{  
   // VS 8.0 values  
   BP90_FLAG_NONE                = 0x0000,  
   BP90_FLAG_MAP_DOCPOSITION     = 0x0001,  
   BP90_FLAG_DONT_STOP           = 0x0002,  
  
   // Values added in VS 9.0  
   BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,  
};  
```  
  
#### <a name="parameters"></a>參數  
 BP90_FLAG_NONE  
 不指定任何中斷點旗標。  
  
 BP90_FLAG_MAP_DOCPOSITION  
 指定偵錯引擎 (DE) 應該將中斷點對應使用的文件位置。 這是僅適用於指令碼為導向的原始程式檔例如 Active Server Pages (ASP) 中設定中斷點。  
  
 BP90_FLAG_DONT_STOP  
 指定中斷點應由偵錯引擎中，但是，偵錯引擎最後應該停止那里;也就是[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)應該不會傳送事件物件。 這個旗標被設計主要是用於追蹤點。  
  
 BP90_FLAG_TRACEPOINT_CONTINUE  
 使用原生偵錯引擎來判斷是否應該清除逐步執行的狀態。 不同於 BP90_FLAG_DONT_STOP 因為 BP90_FLAG_DONT_STOP 不設定追蹤點執行巨集。  
  
## <a name="requirements"></a>需求  
 標頭︰ Msdbg90.h  
  
 命名空間︰ Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰ Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
