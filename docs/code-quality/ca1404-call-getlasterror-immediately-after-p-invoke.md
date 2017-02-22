---
title: "CA1404：必須在 P/Invoke 之後立即呼叫 GetLastError | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CallGetLastErrorImmediatelyAfterPInvoke"
  - "CA1404"
helpviewer_keywords: 
  - "CallGetLastErrorImmediatelyAfterPInvoke"
  - "CA1404"
ms.assetid: 52ae9eff-50f9-4b2f-8039-ca7e49fba88e
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1404：必須在 P/Invoke 之後立即呼叫 GetLastError
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|CallGetLastErrorImmediatelyAfterPInvoke|  
|CheckId|CA1404|  
|分類|Microsoft.Interoperability|  
|中斷變更|中斷|  
  
## 原因  
 會對 <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A?displayProperty=fullName> 方法或對等 Win32  `GetLastError` 函式進行呼叫，而且緊接在前的呼叫並不是平台叫用方法。  
  
## 規則描述  
 平台叫用方法會存取 Unmanaged 程式碼，而且是使用 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中之 `Declare` 關鍵字或 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> 屬性所定義的。  一般而言，失敗時，Unmanaged 函式會呼叫 Win32 `SetLastError` 函式，以設定與失敗相關聯的錯誤碼。  失敗函式的呼叫端會呼叫 Win32 `GetLastError` 函式，以擷取錯誤碼並判斷失敗的原因。  錯誤碼是根據每個執行緒進行維護，而且會在下次呼叫 `SetLastError` 時遭到覆寫。  在呼叫失敗的平台叫用方法之後，Managed 程式碼可以呼叫 <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> 方法擷取錯誤碼。  因為來自其他 Managed 類別庫 \(Class Library\) 方法的內部呼叫可以覆寫錯誤碼，所以在平台叫用方法呼叫之後，應該立即呼叫 `GetLastError` 或 <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> 方法。  
  
 當下列 Managed 成員發生在呼叫平台叫用方法及呼叫 <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> 之間時，規則會忽略呼叫這些成員。  這些成員並不會變更錯誤碼，而且有助於判斷部分平台叫用方法呼叫是否成功。  
  
-   <xref:System.IntPtr.Zero?displayProperty=fullName>  
  
-   <xref:System.IntPtr.op_Equality%2A?displayProperty=fullName>  
  
-   <xref:System.IntPtr.op_Inequality%2A?displayProperty=fullName>  
  
-   <xref:System.Runtime.InteropServices.SafeHandle.IsInvalid%2A?displayProperty=fullName>  
  
## 如何修正違規  
 若要修正此規則的違規情形，請將呼叫移到 <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>，讓這個錯誤能夠立即跟隨對平台叫用方法的呼叫。  
  
## 隱藏警告的時機  
 如果平台叫用方法呼叫與 <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> 方法呼叫之間的程式碼無法明確或隱含地導致錯誤碼變更，則您可以放心地隱藏這項規則的警告。  
  
## 範例  
 下列範例會顯示違反規則的方法和滿足規則的方法。  
  
 [!code-vb[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/VisualBasic/ca1404-call-getlasterror-immediately-after-p-invoke_1.vb)]
 [!code-cs[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/CSharp/ca1404-call-getlasterror-immediately-after-p-invoke_1.cs)]  
  
## 相關規則  
 [CA1060：將 P\/Invokes 移到 NativeMethods 類別](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)  
  
 [CA1400：P\/Invoke 進入點應該要存在](../Topic/CA1400:%20P-Invoke%20entry%20points%20should%20exist.md)  
  
 [CA1401：P\/Invokes 不應該為可見的](../Topic/CA1401:%20P-Invokes%20should%20not%20be%20visible.md)  
  
 [CA2101：必須指定 P\/Invoke 字串引數的封送處理](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)  
  
 [CA2205：必須使用 Win32 API 的 Managed 對應項](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)