---
title: "CA1060：將 P/Invokes 移到 NativeMethods 類別 | Microsoft Docs"
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
  - "MovePInvokesToNativeMethodsClass"
  - "CA1060"
helpviewer_keywords: 
  - "CA1060"
  - "MovePInvokesToNativeMethodsClass"
ms.assetid: 06686c8c-6ad3-42f7-a355-cbaefa347cfc
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1060：將 P/Invokes 移到 NativeMethods 類別
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|MovePInvokesToNativeMethodsClass|  
|CheckId|CA1060|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## 原因  
 方法會使用平台引動服務 \(Platform Invocation Service\) 存取 Unmanaged 程式碼，而且不是其中一個 **NativeMethods** 類別的成員。  
  
## 規則描述  
 平台引動方法，例如使用 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> 屬性 \(Attribute\) 所標記的方法，或在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中使用 `Declare` 關鍵字定義的方法，都會存取 Unmanaged 程式碼。  這些方法應屬於下列其中一個類別：  
  
-   **NativeMethods** \- 這個類別不會隱藏 Unmanaged 程式碼權限的堆疊查核行程 \(Stack Walk\) \(<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> 不得套用至這個類別\)。這個類別適用於因為執行堆疊查核行程而可用於任何地方的方法。  
  
-   **SafeNativeMethods** \- 這個類別會隱藏 Unmanaged 程式碼權限的堆疊查核行程 \(<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> 會套用至此類別\)。這個類別適用於任何人呼叫都沒有安全顧慮的方法。  這些方法的呼叫端不需執行完整的安全性檢閱來確保使用安全，因為這些方法對於任何呼叫端而言都沒有危害。  
  
-   **UnsafeNativeMethods** \- 這個類別會隱藏 Unmanaged 程式碼權限的堆疊查核行程 \(<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> 會套用至此類別\)。這個類別適用於有潛在危險的方法。  因為不會執行堆疊查核行程，這些方法的所有呼叫端都必須執行完整的安全性檢閱，才能確保使用安全。  
  
 這些類別已宣告為 `internal` \(在 Visual Basic 中為 `Friend`\)，並且會宣告私用建構函式 \(Constructor\) 以防止建立新的執行個體。  這些類別中的方法必須是 `static` 和 `internal` \(在 Visual Basic 中為 `Shared` 和 `Friend`\)。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請將方法移到適當的 **NativeMethods** 類別。  對大多數應用程式來說，將 P\/Invokes 移至名為 **NativeMethods** 的新類別就已足夠。  
  
 不過，如果您正在開發可在其他應用程式中使用的程式庫，應該考慮定義其他兩個名為 **SafeNativeMethods** 和 **UnsafeNativeMethods** 的類別。  這些類別類似 **NativeMethods** 類別，但是它們會使用稱為 **SuppressUnmanagedCodeSecurityAttribute** 的特殊屬性 \(Attribute\) 加以標記。  套用這個屬性時，執行階段不會執行完整的堆疊查核行程，以確保所有的呼叫端都具有 **UnmanagedCode** 使用權限。  執行階段通常會在啟動時檢查這個使用權限。  由於未執行檢查，使其可以大幅改善呼叫這些 Unmanaged 方法時的效能，並且可以讓使用權限受限的程式碼呼叫這些方法。  
  
 但是，您應該非常小心使用這個屬性。  如果不正確地實作，它可能會有嚴重的安全性含意。  
  
 如需如何實作方法的詳細資訊，請參閱 **NativeMethods** 範例、**SafeNativeMethods** 範例和 **UnsafeNativeMethods** 範例。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## 範例  
 下列範例會宣告違反此規則的方法。  若要修正違規的情形，您應該將 **RemoveDirectory** P\/Invoke 移至專門為了保存 P\/Invokes 而設計的適當類別。  
  
 [!code-vb[FxCop.Design.DllImportNativeMethods#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_1.vb)]
 [!code-cs[FxCop.Design.DllImportNativeMethods#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_1.cs)]  
  
## NativeMethods 範例  
  
### 說明  
 由於 **NativeMethods** 類別不應以 **SuppressUnmanagedCodeSecurityAttribute** 標記，因此置於其中的 P\/Invokes 將會需要 **UnmanagedCode** 使用權限。  由於大多數的應用程式都會從本機電腦執行，並以完全信任授權執行該應用程式，因此這通常不是問題。  不過，如果您要開發可重複使用的程式庫，則應該考慮定義 **SafeNativeMethods** 或 **UnsafeNativeMethods** 類別。  
  
 下列範例會顯示包裝 **MessageBeep** 函式 \(來自 user32.dll\) 的 **Interaction.Beep** 方法。  **MessageBeep** P\/Invoke 是置於 **NativeMethods** 類別中。  
  
### 程式碼  
 [!code-cs[FxCop.Design.NativeMethods#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_2.cs)]
 [!code-vb[FxCop.Design.NativeMethods#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_2.vb)]  
  
## SafeNativeMethods 範例  
  
### 說明  
 可以安全地公開給任何應用程式，並且沒有任何副作用 \(Side Effect\) 的 P\/Invoke 方法都應該置於名為 **SafeNativeMethods** 的類別內。  您不需要求使用權限，也不需特別注意呼叫它們的位置。  
  
 下列範例會顯示包裝 **GetTickCount** 函式 \(來自 kernel32.dll\) 的 **Environment.TickCount** 屬性。  
  
### 程式碼  
 [!CODE [FxCop.Design.NativeMethodsSafe#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethodsSafe#1)]  
  
## UnsafeNativeMethods 範例  
  
### 說明  
 無法安全呼叫且可能導致副作用的 P\/Invoke 方法應該放在名為 **UnsafeNativeMethods** 的類別中。  這些方法應該經過精密的檢查，以確保不會在無意間公開給使用者。  [CA2118：必須檢視 SuppressUnmanagedCodeSecurityAttribute 使用方法](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md)的規則可以協助執行此動作。  或者，當使用者使用這些方法時，這些方法應該具有其他使用權限，而不是 **UnmanagedCode**。  
  
 下列範例會顯示包裝 **ShowCursor** 函式 \(來自 user32.dll\) 的 **Cursor.Hide** 方法。  
  
### 程式碼  
 [!code-vb[FxCop.Design.NativeMethodsUnsafe#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_3.vb)]
 [!code-cs[FxCop.Design.NativeMethodsUnsafe#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_3.cs)]  
  
## 請參閱  
 [設計警告](../code-quality/design-warnings.md)