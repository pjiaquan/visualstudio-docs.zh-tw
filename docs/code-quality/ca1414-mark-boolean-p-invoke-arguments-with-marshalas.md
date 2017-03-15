---
title: "CA1414：以 MarshalAs 標記布林值 P/Invoke 引數 | Microsoft Docs"
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
  - "CA1414"
  - "MarkBooleanPInvokeArgumentsWithMarshalAs"
helpviewer_keywords: 
  - "CA1414"
  - "MarkBooleanPInvokeArgumentsWithMarshalAs"
ms.assetid: c0c84cf5-7701-4897-9114-66fc4b895699
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1414：以 MarshalAs 標記布林值 P/Invoke 引數
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|MarkBooleanPInvokeArgumentsWithMarshalAs|  
|CheckId|CA1414|  
|分類|Microsoft.Interoperability|  
|中斷變更|中斷|  
  
## 原因  
 平台叫用方法宣告包含 <xref:System.Boolean?displayProperty=fullName> 參數或傳回值，但 <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName> 屬性 \(Attribute\) 不適用該參數或傳回值。  
  
## 規則描述  
 平台叫用方法會存取 Unmanaged 程式碼，而且是使用 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中之 `Declare` 關鍵字或 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> 所定義的。  <xref:System.Runtime.InteropServices.MarshalAsAttribute> 指定用來在 Managed 和 Unmanaged 程式碼之間，轉換資料型別的封送處理行為。  許多簡單的資料型別 \(例如 <xref:System.Byte?displayProperty=fullName> 和 <xref:System.Int32?displayProperty=fullName>\) 在 Unmanaged 程式碼中都有單一表示，且不需要指定它們的封送處理行為，Common Language Runtime 即會自動提供正確的行為。  
  
 <xref:System.Boolean> 資料型別在 Unmanaged 程式碼中有多種表示。  未指定 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 時，<xref:System.Boolean> 資料型別的預設封送處理行為是 <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>。  這是 32 位元的整數，但不適用所有情況。  Unmanaged 方法所需的布林表示應加以判斷，並符合適當的 <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>。  UnmanagedType.Bool 是 Win32 BOOL 型別，其一定為 4 位元組。  UnmanagedType.U1 應該用於 C\+\+ `bool` 或其他 1 位元組的型別。  如需詳細資訊，請參閱[Default Marshaling for Boolean Types](http://msdn.microsoft.com/zh-tw/d4c00537-70f7-4ca6-8197-bfc1ec037ff9)。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請將 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 套用至 <xref:System.Boolean> 參數或傳回值。  將屬性值設定成適當的 <xref:System.Runtime.InteropServices.UnmanagedType>。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  即使是適當的預設封送處理行為，只要明確指定該行為，即可輕易地維護程式碼。  
  
## 範例  
 下列範例會顯示兩個以適當 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性標記的平台叫用方法。  
  
 [!code-cs[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CSharp/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cs)]
 [!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/VisualBasic/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.vb)]
 [!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CPP/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cpp)]  
  
## 相關規則  
 [CA1901：P\/Invoke 宣告應該是可移植的](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)  
  
 [CA2101：必須指定 P\/Invoke 字串引數的封送處理](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)  
  
## 請參閱  
 <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>   
 [Default Marshaling for Boolean Types](http://msdn.microsoft.com/zh-tw/d4c00537-70f7-4ca6-8197-bfc1ec037ff9)   
 [與 Unmanaged 程式碼互通](../Topic/Interoperating%20with%20Unmanaged%20Code.md)