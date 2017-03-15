---
title: "CV_CFL_LANG | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CV_CFL_LANG 列舉"
ms.assetid: 4e8e0613-ad02-4de9-9f46-e4753c5b0251
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# CV_CFL_LANG
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

指定原始程式碼語言的應用程式或連結的模組。  
  
## 語法  
  
```cpp#  
typedef enum CV_CFL_LANG {   
   CV_CFL_C       = 0x00,  
   CV_CFL_CXX     = 0x01,  
   CV_CFL_FORTRAN = 0x02,  
   CV_CFL_MASM    = 0x03,  
   CV_CFL_PASCAL  = 0x04,  
   CV_CFL_BASIC   = 0x05,  
   CV_CFL_COBOL   = 0x06,  
   CV_CFL_LINK    = 0x07,  
   CV_CFL_CVTRES  = 0x08,  
   CV_CFL_CVTPGD  = 0x09,  
   CV_CFL_CSHARP  = 0x0A,  
   CV_CFL_VB      = 0x0B,  
   CV_CFL_ILASM   = 0x0C,  
   CV_CFL_JAVA    = 0x0D,  
   CV_CFL_JSCRIPT = 0x0E,  
   CV_CFL_MSIL    = 0x0F,  
   CV_CFL_HLSL    = 0x10  
} CV_CFL_LANG;  
```  
  
## 項目  
 CV\_CFL\_C  
 應用程式的語言是 c。  
  
 CV\_CFL\_CXX  
 應用程式的語言是 C\+\+。  
  
 CV\_CFL\_FORTRAN  
 應用程式的語言是 FORTRAN。  
  
 CV\_CFL\_MASM  
 應用程式的語言是 Microsoft 巨集組合語言。  
  
 CV\_CFL\_PASCAL  
 應用程式的語言是依照 pascal 命名法。  
  
 CV\_CFL\_BASIC  
 應用程式的語言為基本。  
  
 CV\_CFL\_COBOL  
 應用程式的語言是 COBOL。  
  
 CV\_CFL\_LINK  
 應用程式是連結器產生的模組。  
  
 CV\_CFL\_CVTRES  
 應用程式是轉換 CVTRES 工具與資源模組。  
  
 CV\_CFL\_CVTPGD  
 應用程式是以 CVTPGD 工具產生最佳化的 POGO 模組。  
  
 CV\_CFL\_CSHARP  
 應用程式的語言是 C\#。  
  
 CV\_CFL\_VB  
 應用程式的語言是 Visual Basic。  
  
 CV\_CFL\_ILASM  
 應用程式的語言是中繼語言組件 \(也就是通用語言執行階段 \(CLR\) 組件\)。  
  
 CV\_CFL\_JAVA  
 應用程式的語言是 JAVA。  
  
 CV\_CFL\_JSCRIPT  
 應用程式的語言是 Jscript。  
  
 CV\_CFL\_MSIL  
 應用程式的語言是未知 Microsoft 中繼語言 \(MSIL\)，可能是使用所造成的[\/LTCG \(連結時間產生程式碼\)](/visual-cpp/build/reference/ltcg-link-time-code-generation)切換。  
  
 CV\_CFL\_HLSL  
 應用程式的語言是高級別著色器的語言。  
  
## 備註  
 這個列舉型別中的值會傳回由呼叫[IDiaSymbol::get\_language](../Topic/IDiaSymbol::get_language.md)方法。  
  
## 需求  
 標頭: cvconst.h  
  
## 請參閱  
 [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get\_language](../Topic/IDiaSymbol::get_language.md)