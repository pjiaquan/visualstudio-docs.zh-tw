---
title: "CA2101：必須指定 P/Invoke 字串引數的封送處理 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SpecifyMarshalingForPInvokeStringArguments"
  - "CA2101"
helpviewer_keywords: 
  - "CA2101"
  - "SpecifyMarshalingForPInvokeStringArguments"
ms.assetid: 9d1abfc3-d320-41e0-9f6e-60cefe6ffe1b
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# CA2101：必須指定 P/Invoke 字串引數的封送處理
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|SpecifyMarshalingForPInvokeStringArguments|  
|CheckId|CA2101|  
|分類|Microsoft.Globalization|  
|中斷變更|中斷|  
  
## 原因  
 平台叫用成員允許部分信任的呼叫端、具有字串參數，並且未明確封送處理字串。  
  
## 規則描述  
 從 Unicode 轉換為 ANSI 時，並非所有 Unicode 字元都可以用特定的 ANSI 字碼頁 \(Code Page\) 表示。  「*自動調整對應*」\(Best\-fit mapping\) 會嘗試替換無法表示的字元以解決此問題。  使用此功能會導致潛在的安全性弱點，因為您無法控制所選擇的字元。  例如，惡意的程式碼會刻意建立包含特定字碼頁中找不到的字元之 Unicode 字串，這些字元會轉換為檔案系統的特殊字元，例如 '..' 或 '\/'。  另請注意，在字串轉換為 ANSI 之前，會經常發生特殊字元的安全性檢查。  
  
 自動調整對應是 Unmanaged 轉換 \(WChar 至 MByte\) 的預設值。  除非您明確停用自動調整對應，否則您的程式碼會因為此問題而包含可被利用的安全性弱點。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請明確封送處理字串資料型別。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## 範例  
 下列範例會顯示違反此規則的方法，然後顯示如何修正違規。  
  
 [!code-cs[FxCop.Security.PinvokeAnsiUnicode#1](../code-quality/codesnippet/CSharp/ca2101-specify-marshaling-for-p-invoke-string-arguments_1.cs)]