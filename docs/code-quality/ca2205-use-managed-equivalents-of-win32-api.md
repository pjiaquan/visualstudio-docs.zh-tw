---
title: "CA2205：必須使用 Win32 API 的 Managed 對應項 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UseManagedEquivalentsOfWin32Api"
  - "CA2205"
helpviewer_keywords: 
  - "CA2205"
  - "UseManagedEquivalentsOfWin32Api"
ms.assetid: 1c65ab59-3e50-4488-a727-3969c7f6cbe4
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 13
---
# CA2205：必須使用 Win32 API 的 Managed 對應項
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|UseManagedEquivalentsOfWin32Api|  
|CheckId|CA2205|  
|分類|Microsoft.Usage|  
|中斷變更|不中斷|  
  
## 原因  
 已定義平台叫用方法，而且 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 類別庫 \(Class Library\) 中有具同等功能的方法存在。  
  
## 規則描述  
 平台叫用方法會用於呼叫 Unmanaged DLL 函式，而且此方法是使用 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> 屬性 \(Attribute\) 或 Visual Basic 中的 `Declare` 關鍵字所定義。  未正確定義的平台叫用方法會造成執行階段例外狀況 \(Exception\)，原因在於諸如命名錯誤的函式、參數與傳回值資料型別的錯誤對應，以及不正確的欄位規格 \(如呼叫慣例 \(Calling Convention\) 和字元集 \(Character Set\)\) 等問題。  如果可以的話，呼叫對等的 Managed 方法比起直接定義並呼叫 Unmanaged 方法，通常較為簡單且較不易發生錯誤。  呼叫平台叫用方法也會造成其他需要加以處理的安全性問題。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請將 Unmanaged 函式的呼叫替換為 Managed 對等用法的呼叫。  
  
## 隱藏警告的時機  
 如果建議的取代方法未提供需要的功能，請隱藏這項規則的警告。  
  
## 範例  
 下列範例會顯示違反規則的平台叫用方法定義。  此外，還會顯示平台叫用方法的呼叫和對等的 Managed 方法。  
  
 [!code-cs[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/CSharp/ca2205-use-managed-equivalents-of-win32-api_1.cs)]
 [!code-vb[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/VisualBasic/ca2205-use-managed-equivalents-of-win32-api_1.vb)]  
  
## 相關規則  
 [CA1404：必須在 P\/Invoke 之後立即呼叫 GetLastError](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)  
  
 [CA1060：將 P\/Invokes 移到 NativeMethods 類別](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)  
  
 [CA1400：P\/Invoke 進入點應該要存在](../Topic/CA1400:%20P-Invoke%20entry%20points%20should%20exist.md)  
  
 [CA1401：P\/Invokes 不應該為可見的](../Topic/CA1401:%20P-Invokes%20should%20not%20be%20visible.md)  
  
 [CA2101：必須指定 P\/Invoke 字串引數的封送處理](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)