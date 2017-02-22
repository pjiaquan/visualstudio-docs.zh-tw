---
title: "FIELD_KIND | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "FIELD_KIND"
helpviewer_keywords: 
  - "FIELD_KIND 列舉型別"
ms.assetid: fd522b9c-52e2-42fa-939d-343347d5c3b1
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# FIELD_KIND
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定欄位中所含的[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)物件。  
  
## 語法  
  
```cpp#  
enum enum_FIELD_KIND {   
   FIELD_KIND_NONE       = 0x00000000,  
  
   // Type of field  
   FIELD_KIND_TYPE       = 0x00000001,  
   FIELD_KIND_SYMBOL     = 0x00000002,  
  
   // Storage type of the field  
   FIELD_TYPE_PRIMITIVE  = 0x00000010,  
   FIELD_TYPE_STRUCT     = 0x00000020,  
   FIELD_TYPE_CLASS      = 0x00000040,  
   FIELD_TYPE_INTERFACE  = 0x00000080,  
   FIELD_TYPE_UNION      = 0x00000100,  
   FIELD_TYPE_ARRAY      = 0x00000200,  
   FIELD_TYPE_METHOD     = 0x00000400,  
   FIELD_TYPE_BLOCK      = 0x00000800,  
   FIELD_TYPE_POINTER    = 0x00001000,  
   FIELD_TYPE_ENUM       = 0x00002000,  
   FIELD_TYPE_LABEL      = 0x00004000,  
   FIELD_TYPE_TYPEDEF    = 0x00008000,  
   FIELD_TYPE_BITFIELD   = 0x00010000,  
   FIELD_TYPE_NAMESPACE  = 0x00020000,  
   FIELD_TYPE_MODULE     = 0x00040000,  
   FIELD_TYPE_DYNAMIC    = 0x00080000,  
   FIELD_TYPE_PROP       = 0x00100000,  
   FIELD_TYPE_INNERCLASS = 0x00200000,  
   FIELD_TYPE_REFERENCE  = 0x00400000,  
   FIELD_TYPE_EXTENDED   = 0x00800000,  
  
   // Specific information about symbols  
   FIELD_SYM_MEMBER      = 0x01000000,  
   FIELD_SYM_LOCAL       = 0x02000000,  
   FIELD_SYM_PARAM       = 0x04000000,  
   FIELD_SYM_THIS        = 0x08000000,  
   FIELD_SYM_GLOBAL      = 0x10000000,  
   FIELD_SYM_PROP_GETTER = 0x20000000,  
   FIELD_SYM_PROP_SETTER = 0x40000000,  
   FIELD_SYM_EXTENDED    = 0x80000000,  
  
   FIELD_KIND_MASK       = 0x0000000f,  
   FIELD_TYPE_MASK       = 0x00fffff0,  
   FIELD_SYM_MASK        = 0xff000000,  
  
   FIELD_KIND_ALL        = 0xffffffff  
};  
typedef DWORD FIELD_KIND;  
```  
  
```c#  
public enum enum_FIELD_KIND {  
   FIELD_KIND_NONE       = 0x00000000,  
  
   // Type of field  
   FIELD_KIND_TYPE       = 0x00000001,  
   FIELD_KIND_SYMBOL     = 0x00000002,  
  
   // Storage type of the field  
   FIELD_TYPE_PRIMITIVE  = 0x00000010,  
   FIELD_TYPE_STRUCT     = 0x00000020,  
   FIELD_TYPE_CLASS      = 0x00000040,  
   FIELD_TYPE_INTERFACE  = 0x00000080,  
   FIELD_TYPE_UNION      = 0x00000100,  
   FIELD_TYPE_ARRAY      = 0x00000200,  
   FIELD_TYPE_METHOD     = 0x00000400,  
   FIELD_TYPE_BLOCK      = 0x00000800,  
   FIELD_TYPE_POINTER    = 0x00001000,  
   FIELD_TYPE_ENUM       = 0x00002000,  
   FIELD_TYPE_LABEL      = 0x00004000,  
   FIELD_TYPE_TYPEDEF    = 0x00008000,  
   FIELD_TYPE_BITFIELD   = 0x00010000,  
   FIELD_TYPE_NAMESPACE  = 0x00020000,  
   FIELD_TYPE_MODULE     = 0x00040000,  
   FIELD_TYPE_DYNAMIC    = 0x00080000,  
   FIELD_TYPE_PROP       = 0x00100000,  
   FIELD_TYPE_INNERCLASS = 0x00200000,  
   FIELD_TYPE_REFERENCE  = 0x00400000,  
   FIELD_TYPE_EXTENDED   = 0x00800000,  
  
   // Specific information about symbols  
   FIELD_SYM_MEMBER      = 0x01000000,  
   FIELD_SYM_LOCAL       = 0x02000000,  
   FIELD_SYM_PARAM       = 0x04000000,  
   FIELD_SYM_THIS        = 0x08000000,  
   FIELD_SYM_GLOBAL      = 0x10000000,  
   FIELD_SYM_PROP_GETTER = 0x20000000,  
   FIELD_SYM_PROP_SETTER = 0x40000000,  
   FIELD_SYM_EXTENDED    = 0x80000000,  
  
   FIELD_KIND_MASK       = 0x0000000f,  
   FIELD_TYPE_MASK       = 0x00fffff0,  
   FIELD_SYM_MASK        = 0xff000000,  
  
   FIELD_KIND_ALL        = 0xffffffff  
};  
```  
  
## Members  
 FIELD\_KIND\_TYPE  
 表示此欄位是僅限的型別。  
  
 FIELD\_KIND\_SYMBOL  
 表示此欄位是一個符號，與型別、 名稱和其他資訊。  
  
 FIELD\_TYPE\_PRIMITIVE  
 表示欄位為基本資料型別。  
  
 FIELD\_TYPE\_STRUCT  
 表示欄位是一種結構。  
  
 FIELD\_TYPE\_CLASS  
 表示欄位是一種類別。  
  
 FIELD\_TYPE\_INTERFACE  
 指示欄位為介面。  
  
 FIELD\_TYPE\_UNION  
 表示欄位為等位。  
  
 FIELD\_TYPE\_ARRAY  
 表示此欄位是陣列。  
  
 FIELD\_TYPE\_METHOD  
 表示欄位是一種方法。  
  
 FIELD\_TYPE\_BLOCK  
 表示此欄位是一個區塊。  
  
 FIELD\_TYPE\_POINTER  
 表示此欄位是變數的指標。  
  
 FIELD\_TYPE\_ENUM  
 表示此欄位是不列舉的資料型別。  
  
 FIELD\_TYPE\_LABEL  
 表示欄位為標籤。  
  
 FIELD\_TYPE\_TYPEDEF  
 表示此欄位是 typedef。  
  
 FIELD\_TYPE\_BITFIELD  
 表示此欄位是位元欄位內。  
  
 FIELD\_TYPE\_NAMESPACE  
 表示此欄位是命名空間。  
  
 FIELD\_TYPE\_MODULE  
 表示欄位是一個模組。  
  
 FIELD\_TYPE\_DYNAMIC  
 表示欄位是動態的。  
  
 FIELD\_TYPE\_PROP  
 表示該欄位的屬性。  
  
 FIELD\_TYPE\_INNERCLASS  
 表示此欄位是內部類別。  
  
 FIELD\_TYPE\_REFERENCE  
 表示欄位為參考。  
  
 FIELD\_TYPE\_EXTENDED  
 保留供將來使用。  
  
 FIELD\_SYM\_MEMBER  
 表示欄位為成員。  
  
 FIELD\_SYM\_LOCAL  
 表示欄位是在本機。  
  
 FIELD\_SYM\_PARAMETER  
 指示欄位為參數。  
  
 FIELD\_SYM\_THIS  
 表示此欄位是"this"指標。  
  
 FIELD\_SYM\_GLOBAL  
 表示全域欄位。  
  
 FIELD\_SYM\_PROP\_GETTER  
 指示欄位擷取屬性。  
  
 FIELD\_SYM\_PROP\_SETTER  
 表示該欄位會設定屬性。  
  
 FIELD\_SYM\_EXTENDED  
 保留供將來使用。  
  
 FIELD\_KIND\_MASK  
 表示遮罩的欄位類型。  
  
 FIELD\_TYPE\_MASK  
 表示遮罩的欄位型別。  
  
 FIELD\_SYM\_MASK  
 表示遮罩的符號資訊。  
  
## 備註  
 從呼叫傳回[GetKind](../Topic/IDebugField::GetKind.md)方法。  
  
 根據所使用的欄位中， [QueryInterface](/visual-cpp/atl/queryinterface)可以在呼叫[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)更特定的表單，介面的介面。  比方說，如果[GetKind](../Topic/IDebugField::GetKind.md)會傳回`FIELD_TYPE_METHOD`，您就可以呼叫`QueryInterface` i`DebugField`以取得[IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)介面。  
  
## 需求  
 標頭: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FIELD\_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)   
 [GetKind](../Topic/IDebugField::GetKind.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)