---
title: "安全性警告：附加至未受信任的使用者帳戶所擁有的處理序可能會造成危險。如果下面的資訊看起來有問題，或者您並不確定，請不要附加至此處理序 | Microsoft Docs"
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
  - "vs.debug.attachsecuritywarning"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 52246c1e-a371-40a0-b756-a435cc51876f
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 安全性警告：附加至未受信任的使用者帳戶所擁有的處理序可能會造成危險。如果下面的資訊看起來有問題，或者您並不確定，請不要附加至此處理序
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

當您附加至包含部分受信任程式碼的處理序，或是附加至在附加之前即由未受信任之使用者所擁有的處理序時，這個警告對話方塊就會出現。  包含惡意程式碼的未受信任處理序可能會損害進行偵錯的電腦。  如果您有不信任處理序的理由，則應該按一下 \[**取消**\] 避免進行偵錯。  
  
 若要在偵錯合法情節時隱藏這個警告，請關閉 Visual Studio，並將這個登錄機碼的值設為 1：`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\<version>\Debugger\DisableAttachSecurityWarning`，然後重新啟動 Visual Studio。  在您完成情節的偵錯之後，將值重設為 0，並重新啟動 Visual Studio。  
  
 「受信任的使用者」包括您自己以及一組標準使用者，這些使用者通常是在已安裝 .NET Framework 的電腦上定義，例如 `aspnet`、`localsystem`、`networkservice` 和 `localservice`。  
  
## UIElement 清單  
 名稱  
 要求進行偵錯的組件名稱  
  
 使用者  
 目前使用者  
  
 附加  
 按下以藉由附加繼續偵錯  
  
 不附加  
 不附加至處理序  
  
## 請參閱  
 [附加至執行中處理序](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [偵錯工具安全性](../debugger/debugger-security.md)