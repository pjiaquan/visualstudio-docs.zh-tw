---
title: "互通性警告 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.Interoperabilityrules"
helpviewer_keywords: 
  - "Managed 程式碼分析警告，互通性警告"
  - "互通性警告"
  - "警告，互通性"
ms.assetid: 95de6eb3-40c4-4063-9f59-25cb70e3b2b3
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# 互通性警告
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

互通性警告支援與 COM 用戶端進行互動。  
  
## 在本節中  
  
|規則|描述|  
|--------|--------|  
|[CA1400：P\/Invoke 進入點應該要存在](../Topic/CA1400:%20P-Invoke%20entry%20points%20should%20exist.md)|公用或受保護的方法是使用 System.Runtime.InteropServices.DllImportAttribute 屬性來標記。  有可能是找不到 Unmanaged 程式庫，或是方法不符合程式庫中的函式。|  
|[CA1401：P\/Invokes 不應該為可見的](../Topic/CA1401:%20P-Invokes%20should%20not%20be%20visible.md)|公用型別中公用或保護的方法具有 System.Runtime.InteropServices.DllImportAttribute 屬性 \(也會由 Visual Basic 中的 Declare 關鍵字實作\)。  但不得公開 \(Expose\) 此類方法。|  
|[CA1402：避免在 COM 可見介面中多載](../code-quality/ca1402-avoid-overloads-in-com-visible-interfaces.md)|當多載方法會對 COM 用戶端公開 \(Expose\) 時，只有第一個方法多載會保留它的名稱。  後續的多載則會透過將名稱附加至底線字元 \(\_\) 和對應於多載宣告之順序的整數，重新命名為唯一的名稱。|  
|[CA1403：自動配置類型不應該是 COM 可見](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)|COM 可見實值型別是使用設為 LayoutKind.Auto 的 System.Runtime.InteropServices.StructLayoutAttribute 屬性來標記。  這些型別的配置可能會在 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 的版本之間變更，進而中斷必須有特定配置的 COM 用戶端。|  
|[CA1404：必須在 P\/Invoke 之後立即呼叫 GetLastError](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)|系統會對 Marshal.GetLastWin32Error 方法或對等 [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] GetLastError 函式進行呼叫，而且緊接在前的呼叫並不是平台叫用方法。|  
|[CA1405：COM 可見類型的基底類型應該是 COM 可見](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md)|COM 可見型別會衍生自不是 COM 可見的型別。|  
|[CA1406：避免對 Visual Basic 6 用戶端使用 Int64 引數](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)|Visual Basic 6 COM 用戶端無法存取 64 位元整數。|  
|[CA1407：避免在 COM 可見類型中使用靜態成員](../Topic/CA1407:%20Avoid%20static%20members%20in%20COM%20visible%20types.md)|COM 不支援靜態方法。|  
|[CA1408：不要使用 AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)|使用雙重介面 \(Dual Interface\) 的型別可讓用戶端繫結至特定的介面配置。  在未來版本中，若型別或任何基底型別 \(Base Type\) 的配置有所變更，將會中斷繫結至此介面的 COM 用戶端。  根據預設，如果未指定 ClassInterfaceAttribute 屬性，則會使用分派介面。|  
|[CA1409：COM 可見類型應該是可建立的](../code-quality/ca1409-com-visible-types-should-be-creatable.md)|特別標示為 COM 可見的參考型別 \(Reference Type\) 包含公用參數化建構函式，但不包含公用預設 \(無參數\) 建構函式。  COM 用戶端無法建立沒有公用預設建構函式的型別。|  
|[CA1410：應該符合 COM 註冊方法](../code-quality/ca1410-com-registration-methods-should-be-matched.md)|型別會宣告使用 <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> 屬性 \(Attribute\) 所標記的方法，但不會宣告使用 <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> 屬性所標記的方法 \(反之亦然\)。|  
|[CA1411：COM 註冊方法不應該為可見的](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)|使用 System.Runtime.InteropServices.ComRegisterFunctionAttribute 屬性或 System.Runtime.InteropServices.ComUnregisterFunctionAttribute 屬性來標記的方法為外部可見。|  
|[CA1412：將 ComSource 介面標記為 IDispatch](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)|型別是使用 System.Runtime.InteropServices.ComSourceInterfacesAttribute 屬性來標記，而且至少其中一個指定的介面不是使用設為 ComInterfaceType.InterfaceIsIDispatch 的 System.Runtime.InteropServices.InterfaceTypeAttribute 屬性來標記。|  
|[CA1413：避免在 COM 可見的實值類型中使用非公用欄位](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)|COM 可見實值型別的非公用執行個體欄位對 COM 用戶端而言是可見的。  請檢閱不應該公開之資訊的欄位內容，或是會造成未預期的設計或安全性結果的欄位內容。|  
|[CA1414：以 MarshalAs 標記布林值 P\/Invoke 引數](../code-quality/ca1414-mark-boolean-p-invoke-arguments-with-marshalas.md)|布林資料型別在 Unmanaged 程式碼中有多種表示。|  
|[CA1415：P\/Invokes 必須正確宣告](../code-quality/ca1415-declare-p-invokes-correctly.md)|此規則會尋找以 [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] 函式為目標 \(具有指向 OVERLAPPED 結構參數的指標\) 的平台叫用方法宣告，而且相對應的 Managed 參數不是指向 <xref:System.Threading.NativeOverlapped?displayProperty=fullName> 結構的指標。|