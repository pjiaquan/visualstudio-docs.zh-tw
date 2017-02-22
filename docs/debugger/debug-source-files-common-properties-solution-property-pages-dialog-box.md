---
title: "方案屬性頁對話方塊、通用屬性、偵錯原始程式檔 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.options.FindSource"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "SQL"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "偵錯原始程式檔屬性頁"
  - "偵錯 [Visual Studio], 指定原始程式檔和符號檔"
  - "原始程式檔, 在偵錯工具中指定"
  - "偵錯工具, 原始程式檔"
ms.assetid: 0af11464-eeb1-4d0b-87a6-0cc96779afb1
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 方案屬性頁對話方塊、通用屬性、偵錯原始程式檔
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此屬性頁可指定對方案進行偵錯時，偵錯工具將於何處尋找原始程式檔。  
  
 若要存取 \[**偵錯原始程式檔**\] 屬性頁，請以滑鼠右鍵按一下 \[**方案總管**\] 中您的方案，然後從捷徑功能表選取 \[**屬性**\]。  展開 \[**通用屬性**\] 資料夾，然後按一下 \[**偵錯原始程式檔**\] 頁面。  
  
 **包含原始程式碼的目錄**  
 包含目錄清單，偵錯工具對方案進行偵錯時，會在這個清單中搜尋原始程式檔。  另外也會搜尋所指定目錄的子目錄。  
  
 **不要尋找這些原始程式檔**  
 輸入要讓偵錯工具讀取時排除的任何檔案名稱。  如果偵錯工具在上面其中一個指定的目錄中找到這些檔案中的某一個，就會忽略該檔案。  如果在進行偵錯時出現 \[**尋找原始碼**\] 對話方塊，而您按一下 \[**取消**\]，您之前搜尋的檔案就會加入至這個清單，如此偵錯工具就不會繼續搜尋該檔案。  
  
## 請參閱  
 [偵錯工具安全性](../debugger/debugger-security.md)   
 [偵錯設定和準備](../debugger/debugger-settings-and-preparation.md)