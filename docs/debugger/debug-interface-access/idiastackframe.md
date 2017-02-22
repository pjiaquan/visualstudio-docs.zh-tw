---
title: "IDiaStackFrame | Microsoft Docs"
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
  - "IDiaStackFrame 介面"
ms.assetid: 486d25b8-a590-41c1-bdb5-faff3ae35632
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaStackFrame
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

堆疊框架的屬性公開 \(expose\)。  
  
## 語法  
  
```  
IDiaStackFrame : IUnknown  
```  
  
## 方法 Vtable 順序  
 這個介面支援的方法如下：  
  
|方法|描述|  
|--------|--------|  
|[IDiaStackFrame::get\_allocatesBasePointer](../../debugger/debug-interface-access/idiastackframe-get-allocatesbasepointer.md)|會擷取旗標，表示這個位址範圍中的程式碼為配置之後的基底指標。  這個方法已被取代。|  
|[IDiaStackFrame::get\_base](../../debugger/debug-interface-access/idiastackframe-get-base.md)|擷取的框架位址基底。|  
|[IDiaStackFrame::get\_cplusplusExceptionHandling](../Topic/IDiaStackFrame::get_cplusplusExceptionHandling.md)|會擷取旗標，表示 C\+\+ 例外處理作用中。|  
|[IDiaStackFrame::get\_functionStart](../../debugger/debug-interface-access/idiastackframe-get-functionstart.md)|會擷取旗標，表示該區塊包含進入點函式。|  
|[IDiaStackFrame::get\_lengthLocals](../../debugger/debug-interface-access/idiastackframe-get-lengthlocals.md)|會擷取區域變數推入堆疊的位元組數目。|  
|[IDiaStackFrame::get\_lengthParams](../../debugger/debug-interface-access/idiastackframe-get-lengthparams.md)|擷取的推入堆疊的參數的位元組數目。|  
|[IDiaStackFrame::get\_lengthProlog](../../debugger/debug-interface-access/idiastackframe-get-lengthprolog.md)|擷取初構中的程式碼區塊的位元組的數目|  
|[IDiaStackFrame::get\_lengthSavedRegisters](../Topic/IDiaStackFrame::get_lengthSavedRegisters.md)|擷取已儲存的暫存器推入堆疊的位元組數目。|  
|[IDiaStackFrame::get\_localsBase](../../debugger/debug-interface-access/idiastackframe-get-localsbase.md)|擷取區域變數位址基的底。|  
|[IDiaStackFrame::get\_maxStack](../../debugger/debug-interface-access/idiastackframe-get-maxstack.md)|擷取最大的推入堆疊框架中的位元組數。|  
|[IDiaStackFrame::get\_rawLVarInstanceValue](../../debugger/debug-interface-access/idiastackframe-get-rawlvarinstancevalue.md)|擷取指定的本機變數的值，以未經處理位元組。|  
|[IDiaStackFrame::get\_registerValue](../../debugger/debug-interface-access/idiastackframe-get-registervalue.md)|擷取指定的暫存器值。|  
|[IDiaStackFrame::get\_returnAddress](../../debugger/debug-interface-access/idiastackframe-get-returnaddress.md)|擷取框架的寄件人的地址。|  
|[IDiaStackFrame::get\_size](../Topic/IDiaStackFrame::get_size.md)|擷取的框架，以位元組為單位的大小。|  
|[IDiaStackFrame::get\_systemExceptionHandling](../../debugger/debug-interface-access/idiastackframe-get-systemexceptionhandling.md)|會擷取旗標，表示系統例外處理作用中。|  
|[IDiaStackFrame::get\_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)|擷取的框架類型。|  
  
## 備註  
 堆疊框架是抽象函式呼叫的執行期間。  
  
## 呼叫者的備忘稿  
 取得這個介面，藉由呼叫[IDiaEnumStackFrames::Next](../../debugger/debug-interface-access/idiaenumstackframes-next.md)方法。  請參閱[IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)介面，如需取得範例`IDiaStackFrame`介面。  
  
## 範例  
 本範例顯示各種不同的堆疊框架的屬性。  
  
```cpp#  
void PrintStackFrame(IDiaStackFrame* pFrame)  
{  
    if (pFrame != NULL)  
    {  
        ULONGLONG bottom = 0;  
        ULONGLONG top    = 0;  
  
        if (pFrame->get_base(&bottom) == S_OK &&  
            pFrame->get_registerValue( CV_REG_ESP, &top ) == S_OK )  
        {  
             printf("range = 0x%08I64x - 0x%08I64x\n", bottom, top);  
        }  
  
        ULONGLONG returnAddress = 0;  
        if (pFrame->get_returnAddress(&returnAddress) == S_OK)  
        {  
             printf("return address = 0x%08I64x\n", returnAddress);  
        }  
  
        DWORD lengthFrame     = 0;  
        DWORD lengthLocals    = 0;  
        DWORD lengthParams    = 0;  
        DWORD lengthProlog    = 0;  
        DWORD lengthSavedRegs = 0;  
        if (pFrame->get_size(&lengthFrame) == S_OK &&  
            pFrame->get_lengthLocals(&lengthLocals) == S_OK &&  
            pFrame->get_lengthParams(&lengthParams) == S_OK &&  
            pFrame->get_lengthProlog(&lengthProlog) == S_OK &&  
            pFrame->get_lengthSavedRegisters(&lengthSavedRegs) == S_OK)  
        {  
            printf("stack frame size          = 0x%08lx bytes\n", lengthFrame);  
            printf("length of locals          = 0x%08lx bytes\n", lengthLocals);  
            printf("length of parameters      = 0x%08lx bytes\n", lengthParams);  
            printf("length of prolog          = 0x%08lx bytes\n", lengthProlog);  
            printf("length of saved registers = 0x%08lx bytes\n", lengthSavedRegs);  
        }  
    }  
}  
```  
  
## 需求  
 標頭: Dia2.h  
  
 媒體櫃： diaguids.lib  
  
 DLL： msdia80.dll  
  
## 請參閱  
 [介面 \(偵錯介面存取 SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)   
 [IDiaEnumStackFrames::Next](../../debugger/debug-interface-access/idiaenumstackframes-next.md)   
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)