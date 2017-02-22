---
title: "可靠性警告 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.reliabilityrules"
helpviewer_keywords: 
  - "警告, 可靠性"
  - "可靠性警告"
  - "Managed 程式碼分析警告, 可靠性警告"
ms.assetid: 77886846-10a2-4585-968a-7eb60ebe07e8
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 可靠性警告
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

支援程式庫和應用程式可靠性的可靠性警告，如記憶體和執行緒的正確用法。  
  
## 在本節中  
  
|規則|描述|  
|--------|--------|  
|[CA2000：必須在超出範圍前處置物件](../code-quality/ca2000-dispose-objects-before-losing-scope.md)|因為可能會發生例外事件以防止執行物件的完成項，所以應在物件的所有參考都超出範圍之前，明確處置物件。|  
|[CA2001：避免呼叫有問題的方法](../Topic/CA2001:%20Avoid%20calling%20problematic%20methods.md)|成員呼叫了可能有危險或問題的方法。|  
|[CA2002：請勿鎖定具有弱式識別的物件](../Topic/CA2002:%20Do%20not%20lock%20on%20objects%20with%20weak%20identity.md)|可以跨應用程式定義域範圍直接存取的物件，即所謂具有弱式識別的物件。  嘗試取得具有弱式識別之物件鎖定的執行緒，可以被不同應用程式定義域中具有相同物件鎖定的第二個執行緒所封鎖。|  
|[CA2003：不要將 Fiber 視為執行緒](../code-quality/ca2003-do-not-treat-fibers-as-threads.md)|Managed 執行緒已視為 Win32 執行緒。|  
|[CA2004：必須移除對 GC.KeepAlive 的呼叫](../Topic/CA2004:%20Remove%20calls%20to%20GC.KeepAlive.md)|如果您要轉換成 SafeHandle 用法，則會移除對 GC.KeepAlive \(物件\) 的所有呼叫。  在此情況下，類別不一定要呼叫 GC.KeepAlive，假設它們沒有完成項，但會根據 SafeHandle 最終處理其 OS 控制代碼。|  
|[CA2006：使用 SafeHandle 封裝原生資源](../code-quality/ca2006-use-safehandle-to-encapsulate-native-resources.md)|在 Managed 程式碼中使用 IntPtr，可能會有潛在的安全性和可靠性問題。  必須檢閱所有使用 IntPtr 的情況，判斷是否需要在該處使用 SafeHandle \(或類似技術\)。|