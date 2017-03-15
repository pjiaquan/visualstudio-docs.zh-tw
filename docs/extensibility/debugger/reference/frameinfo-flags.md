---
title: "FRAMEINFO_FLAGS |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- FRAMEINFO_FLAGS
helpviewer_keywords:
- FRAMEINFO_FLAGS enumeration
ms.assetid: 41578062-8455-412a-9d8b-1e1e9dc8d52e
caps.latest.revision: 12
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
ms.openlocfilehash: 9b06b64244d34552c986c26b5df8131f30ef9d06
ms.lasthandoff: 02/22/2017

---
# <a name="frameinfoflags"></a>FRAMEINFO_FLAGS
指定要擷取堆疊框架物件的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
enum enum_FRAMEINFO_FLAGS {  
   FIF_FUNCNAME              = 0x00000001,  
   FIF_RETURNTYPE            = 0x00000002,  
   FIF_ARGS                  = 0x00000004,  
   FIF_LANGUAGE              = 0x00000008,  
   FIF_MODULE                = 0x00000010,  
   FIF_STACKRANGE            = 0x00000020,  
   FIF_FRAME                 = 0x00000040,  
   FIF_DEBUGINFO             = 0x00000080,  
   FIF_STALECODE             = 0x00000100,  
   FIF_ANNOTATEDFRAME        = 0x00000200,  
   FIF_DEBUG_MODULEP         = 0x00000400,  
   FIF_FUNCNAME_FORMAT       = 0x00001000,  
   FIF_FUNCNAME_RETURNTYPE   = 0x00002000,  
   FIF_FUNCNAME_ARGS         = 0x00004000,  
   FIF_FUNCNAME_LANGUAGE     = 0x00008000,  
   FIF_FUNCNAME_MODULE       = 0x00010000,  
   FIF_FUNCNAME_LINES        = 0x00020000,  
   FIF_FUNCNAME_OFFSET       = 0x00040000,  
   FIF_FUNCNAME_ARGS_TYPES   = 0x00100000,  
   FIF_FUNCNAME_ARGS_NAMES   = 0x00200000,  
   FIF_FUNCNAME_ARGS_VALUES  = 0x00400000,  
   FIF_FUNCNAME_ARGS_ALL     = 0x00700000,  
   FIF_ARGS_TYPES            = 0x01000000,  
   FIF_ARGS_NAMES            = 0x02000000,  
   FIF_ARGS_VALUES           = 0x04000000,  
   FIF_ARGS_ALL              = 0x07000000,  
   FIF_ARGS_NOFORMAT         = 0x08000000,  
   FIF_ARGS_NO_FUNC_EVAL     = 0x10000000,  
   FIF_FILTER_NON_USER_CODE  = 0x20000000,  
   FIF_ARGS_NO_TOSTRING      = 0x40000000,  
   FIF_DESIGN_TIME_EXPR_EVAL = 0x80000000  
};  
typedef DWORD FRAMEINFO_FLAGS;  
```  
  
```c#  
public enum enum_FRAMEINFO_FLAGS {  
   FIF_FUNCNAME              = 0x00000001,  
   FIF_RETURNTYPE            = 0x00000002,  
   FIF_ARGS                  = 0x00000004,  
   FIF_LANGUAGE              = 0x00000008,  
   FIF_MODULE                = 0x00000010,  
   FIF_STACKRANGE            = 0x00000020,  
   FIF_FRAME                 = 0x00000040,  
   FIF_DEBUGINFO             = 0x00000080,  
   FIF_STALECODE             = 0x00000100,  
   FIF_ANNOTATEDFRAME        = 0x00000200,  
   FIF_DEBUG_MODULEP         = 0x00000400,  
   FIF_FUNCNAME_FORMAT       = 0x00001000,  
   FIF_FUNCNAME_RETURNTYPE   = 0x00002000,  
   FIF_FUNCNAME_ARGS         = 0x00004000,  
   FIF_FUNCNAME_LANGUAGE     = 0x00008000,  
   FIF_FUNCNAME_MODULE       = 0x00010000,  
   FIF_FUNCNAME_LINES        = 0x00020000,  
   FIF_FUNCNAME_OFFSET       = 0x00040000,  
   FIF_FUNCNAME_ARGS_TYPES   = 0x00100000,  
   FIF_FUNCNAME_ARGS_NAMES   = 0x00200000,  
   FIF_FUNCNAME_ARGS_VALUES  = 0x00400000,  
   FIF_FUNCNAME_ARGS_ALL     = 0x00700000,  
   FIF_ARGS_TYPES            = 0x01000000,  
   FIF_ARGS_NAMES            = 0x02000000,  
   FIF_ARGS_VALUES           = 0x04000000,  
   FIF_ARGS_ALL              = 0x07000000,  
   FIF_ARGS_NOFORMAT         = 0x08000000,  
   FIF_ARGS_NO_FUNC_EVAL     = 0x10000000,  
   FIF_FILTER_NON_USER_CODE  = 0x20000000,  
   FIF_ARGS_NO_TOSTRING      = 0x40000000,  
   FIF_DESIGN_TIME_EXPR_EVAL = 0x80000000  
};  
```  
  
## <a name="members"></a>Members  
 FIF_FUNCNAME  
 初始化/使用`m_bstrFuncName`欄位。  
  
 FIF_RETURNTYPE  
 初始化/使用`m_bstrReturnType`欄位。  
  
 FIF_ARGS  
 初始化/使用`m_bstrArgs`欄位。  
  
 FIF_LANGUAGE  
 初始化/使用`m_bstrLanguage`欄位。  
  
 FIF_MODULE  
 初始化/使用`m_bstrModule`欄位。  
  
 FIF_STACKRANGE  
 初始化/使用`m_addrMin`和`m_addrMax`（堆疊範圍） 的欄位。  
  
 FIF_FRAME  
 初始化/使用`m_pFrame`欄位。  
  
 FIF_DEBUGINFO  
 初始化/使用`m_fHasDebugInfo`欄位。  
  
 FIF_STALECODE  
 初始化/使用`m_fStaleCode`欄位。  
  
 FIF_ANNOTATEDFRAME  
 初始化/使用`m_fAnnotatedFrame`欄位。  
  
 FIF_DEBUG_MODULEP  
 初始化/使用`m_pModule`欄位。  
  
 FIF_FUNCNAME_FORMAT  
 格式函式名稱。 結果會傳回到`m_bstrFunName`以及任何其他欄位都已填寫。  
  
 FIF_FUNCNAME_RETURNTYPE  
 新增的傳回類型以`m_bstrFuncName`欄位。  
  
 FIF_FUNCNAME_ARGS  
 加入的引數`m_bstrFuncName`欄位。  
  
 FIF_FUNCNAME_LANGUAGE  
 新增的語言`m_bstrFuncName`欄位。  
  
 FIF_FUNCNAME_MODULE  
 將模組名稱來`m_bstrFuncName`欄位。  
  
 FIF_FUNCNAME_LINES  
 加入的行數`m_bstrFuncName`欄位。  
  
 FIF_FUNCNAME_OFFSET  
 將`m_bstrFuncName`欄位的位移，以位元組為單位，從一行的開頭，如果`FIF_FUNCNAME_LINES`指定。 如果`FIF_FUNCNAME_LINES`未指定，或如果無法使用行號，以位元組為單位加入位移從函式的開頭。  
  
 FIF_FUNCNAME_ARGS_TYPES  
 將每個函式引數的型別加入`m_bstrFuncName`欄位。  
  
 FIF_FUNCNAME_ARGS_NAMES  
 將每個函式引數的名稱加入`m_bstrFuncName`欄位。  
  
 FIF_FUNCNAME_ARGS_VALUES  
 將每個函式引數的值加入`m_bstrFuncName`欄位。  
  
 FIF_FUNCNAME_ARGS_ALL  
 新增類型、 名稱和值的所有引數的`m_bstrFuncName`欄位。  
  
 FIF_ARGS_TYPES  
 引數型別都會擷取並格式化。  
  
 FIF_ARGS_NAMES  
 引數名稱都會擷取並格式化。  
  
 FIF_ARGS_VALUES  
 引數的值都會擷取並格式化。  
  
 FIF_ARGS_ALL  
 擷取並格式化類型、 名稱和所有引數的值。  
  
 FIF_ARGS_NOFORMAT  
 指定引數不格式化 （例如，進行不加入括號和右括住的引數清單也加入引數之間的分隔符號）。  
  
 FIF_ARGS_NO_FUNC_EVAL  
 指定擷取引數的值時，不應該使用函式 （屬性） 評估。  
  
 FIF_FILTER_NON_USER_CODE  
 篩選非使用者程式碼框架，因此不會包含為偵錯引擎。  
  
 FIF_ARGS_NO_TOSTRING  
 不允許`ToString()`函式評估或格式時傳回函式引數。  
  
 FIF_DESIGN_TIME_EXPR_EVAL  
 框架資訊應該是從裝載的應用程式定義域，而不是使用裝載處理序。  
  
## <a name="remarks"></a>備註  
 這些旗標會傳遞至[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)和[GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)方法以指出哪些欄位是在初始化[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)結構。  
  
 這些旗標也可用來表示欄位[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)結構會使用和有效時，會傳回這個結構。 這些值可結合的位元`OR`。  
  
## <a name="requirements"></a>需求  
 標頭︰ msdbg.h  
  
 命名空間︰ Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰ Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)
