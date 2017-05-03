---
title: "IDebugDocumentText 介面 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugDocumentText 介面"
ms.assetid: 242bad79-9c0a-4a30-879a-9f43db4e022b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentText 介面
提供對偵錯資料的純文字版本。  這個介面會使用下列慣例:  
  
-   符號位置和行號 \(行號以零為起始。  
  
-   字元位置中的字元位移 \(Offset\)，它們不表示位元組或文字位移。  對於 Win32，字元位置是位移的 Unicode。  
  
 除了繼承自 `IDebugDocument` 的方法之外，`IDebugDocumentText` 介面還會公開下列方法。  
  
## 依照 Vtable 順序的方法  
  
|方法|描述|  
|--------|--------|  
|[IDebugDocumentText::GetDocumentAttributes](../../winscript/reference/idebugdocumenttext-getdocumentattributes.md)|傳回文件的屬性。|  
|[IDebugDocumentText::GetSize](../../winscript/reference/idebugdocumenttext-getsize.md)|傳回字元的行數和數字在文件中。|  
|[IDebugDocumentText::GetPositionOfLine](../../winscript/reference/idebugdocumenttext-getpositionofline.md)|與該行的第一個字元的對應傳回字元位置。|  
|[IDebugDocumentText::GetLineOfPosition](../../winscript/reference/idebugdocumenttext-getlineofposition.md)|傳回行號，且，或者，字元位移 \(Offset\) 對應於指定之字元位置的程式碼行中。|  
|[IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)|擷取字元和字元與屬性關聯的字元位置範圍。|  
|[IDebugDocumentText::GetPositionOfContext](../../winscript/reference/idebugdocumenttext-getpositionofcontext.md)|傳回字元位置的範圍與文件內容的。|  
|[IDebugDocumentText::GetContextOfPosition](../../winscript/reference/idebugdocumenttext-getcontextofposition.md)|建立資料內容物件所提供的字元位置範圍對應。|