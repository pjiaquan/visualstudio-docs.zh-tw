---
title: "啟用 Visual C++ 的偵錯功能 (/D_DEBUG) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "/D_DEBUG 編譯器選項 [C++]"
  - "_DEBUG 巨集"
  - "判斷提示, 啟用偵錯功能"
  - "D_DEBUG 編譯器選項"
  - "偵錯組建, MFC"
  - "偵錯 [C++], 啟用偵錯功能"
  - "偵錯 [MFC], 啟用偵錯功能"
  - "MFC 程式庫, 偵錯版本"
ms.assetid: 276e2254-7274-435e-ba4d-67fcef4f33bc
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 啟用 Visual C++ 的偵錯功能 (/D_DEBUG)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在 [!INCLUDE[vcprvc](../debugger/includes/vcprvc_md.md)] 中，當您使用已定義的 **\_DEBUG** 符號編譯您的程式時，便會啟用判斷提示 \(Assertion\) 之類的偵錯功能。  您可以使用下列兩種方法之一定義 **\_DEBUG**：  
  
-   在原始程式碼中指定 **\#define \_DEBUG**，或  
  
-   指定 **\/D\_DEBUG** 編譯器選項 \(如果您在 Visual Studio 中使用精靈建立專案，會在偵錯組態中自動定義 **\/D\_DEBUG**\)  
  
 完成 **\_DEBUG** 定義之後，編譯器便會編譯 **\#ifdef \_DEBUG** 和 `#endif` 所包圍的程式碼區段。  
  
 MFC 程式的偵錯組態必須與 MFC 程式庫的偵錯版本連結。  MFC 標頭檔 \(Header File\) 會根據您已定義的符號，例如 **\_DEBUG** 和 **\_UNICODE**，來決定要連結到哪一個正確版本的 MFC 程式庫。  如需詳細資訊，請參閱 [MFC 程式庫版本](/visual-cpp/mfc/mfc-library-versions)。  
  
## 請參閱  
 [偵錯機器碼](../debugger/debugging-native-code.md)   
 [C\+\+ 偵錯組態的專案設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)