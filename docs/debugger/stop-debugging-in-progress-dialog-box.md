---
title: "停止進行中的偵錯對話方塊 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.stopnow"
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
  - "停止進行中的偵錯對話方塊"
ms.assetid: ed7ef49d-e25f-4a4d-9396-9bc7b4143117
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# 停止進行中的偵錯對話方塊
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

如果偵錯工具嘗試停止偵錯工作階段，但是工作階段需要一些時間才會停止，這個對話方塊就會出現。  停止偵錯工作階段通常很快就能完成，所以不會出現這個對話方塊。  不過，有時可能需要多花一些時間才能從所有正在偵錯的處理序中斷連結。  如果停止工作階段需花費數秒 \(或是發生中斷連結錯誤\)，這個對話方塊就會出現。  如果經常發生這種情況，可能是因為內部問題，建議您連絡產品支援服務。  
  
 您可以等候處理序中斷連結而且這個對話方塊消失，或者使用 \[**立即停止**\] 按鈕強制立即結束。  
  
 **立即停止**  
 按一下這個按鈕會立即結束偵錯工作階段。  使用 \[**立即停止**\] 會結束偵錯中的處理序，而不是中斷處理序連結。  如果您正在進行系統處理序偵錯，使用 \[**立即停止**\] 結束這些處理序可能會產生非預期且不想要的結果。  
  
## 請參閱  
 [偵錯工具安全性](../debugger/debugger-security.md)   
 [Detaching Programs](http://msdn.microsoft.com/zh-tw/f2c756c2-8079-474b-94c2-01c19a141a01)