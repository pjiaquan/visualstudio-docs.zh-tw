---
title: "選項對話方塊、專案、Visual Basic 預設值 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Projects.VBDefaults"
helpviewer_keywords: 
  - "Option Explicit 陳述式, 在 IDE 中設定"
  - "Option Compare 陳述式, 在 IDE 中設定"
  - "Option Strict 陳述式, 在 IDE 中設定"
ms.assetid: 2465cd9d-18b6-4c4a-b1ea-86dbab23fc79
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# 選項對話方塊、專案、Visual Basic 預設值
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

指定 Visual Basic 專案選項的預設設定。  建立新專案時，指定的選項陳述式將會加入至程式碼編輯器中的專案標頭。  選項會套用至所有 Visual Basic 專案。  
  
 如果要存取這個對話方塊，請在 \[**工具**\] 功能表上按一下 \[**選項**\]，展開 \[**專案和方案**\] 資料夾後按一下 \[**VB 預設值**\]。  
  
 **Option Explicit**  
 設定編譯器預設值以至於需要明確宣告變數。  依據預設，**Option Explicit** 設定為 **On**。  如需詳細資訊，請參閱 [\/optionexplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit)。  
  
 **Option Strict**  
 設定編譯器預設值，所以需要明確縮小轉換且不允許晚期繫結。  依據預設，**Option Strict** 設定為 **Off**。  如需詳細資訊，請參閱 [\/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict)。  
  
 **Option Compare**  
 設定編譯器 \(Compiler\) 預設值以進行字串比較：二進位 \(區分大小寫\) 或文字 \(不區分大小寫\)。 依據預設，**Option Compare** 設定為**二進位**。  如需詳細資訊，請參閱 [\/optioncompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare)。  
  
 **Option Infer**  
 為區域型別推斷設定編譯器預設值。  根據預設，新建專案的 \[**Option Infer**\] 設定為 \[**On**\]，而在舊版 Visual Basic 中所建立的移轉專案則設定為 \[**Off**\]。  如需詳細資訊，請參閱 [\/optioninfer](/dotnet/visual-basic/reference/command-line-compiler/optioninfer)。  
  
## 請參閱  
 [專案和方案](../../ide/solutions-and-projects-in-visual-studio.md)