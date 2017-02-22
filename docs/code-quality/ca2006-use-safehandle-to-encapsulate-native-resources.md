---
title: "CA2006：使用 SafeHandle 封裝原生資源 | Microsoft Docs"
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
  - "CA2006"
  - "UseSafeHandleToEncapsulateNativeResources"
helpviewer_keywords: 
  - "UseSafeHandleToEncapsulateNativeResources"
  - "CA2006"
ms.assetid: a71950bd-bcc1-463d-b1f2-5233bc451456
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2006：使用 SafeHandle 封裝原生資源
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|UseSafeHandleToEncapsulateNativeResources|  
|CheckId|CA2006|  
|分類|Microsoft.Reliability|  
|中斷變更|中斷|  
  
## 原因  
 Managed 程式碼使用 <xref:System.IntPtr> 存取原生資源。  
  
## 規則描述  
 在 Managed 程式碼中使用 `IntPtr` 可能會有潛在的安全性和可靠性問題。  對於 `IntPtr` 的所有使用情況，都必須檢閱以判斷是否需要在該處使用 <xref:System.Runtime.InteropServices.SafeHandle> 或類似技術。  如果 `IntPtr` 代表某些應是 Managed 程式碼擁有的原生資源 \(例如記憶體、檔案控制代碼或通訊端\) 時，便會發生問題。  如果 Managed 程式碼擁有資源，它也必須釋放與其相關聯的原生資源，因為若無法執行這項作業就會造成資源流失。  
  
 在這類案例中，如果允許對 `IntPtr` 進行多執行緒存取，而又提供釋放 `IntPtr` 所表示之資源的方法，也會存在安全性和可靠性問題。  在另一個執行緒上正在使用資源的同時釋放該資源的情況下，這些問題牽涉到 `IntPtr` 值的回收。  這可能會造成競爭條件，使其中一個執行緒可以讀取或寫入與錯誤資源相關聯的資料。  例如，若您的型別將 OS 控制代碼儲存為 `IntPtr`，並且允許使用者使用該控制代碼同時呼叫 **Close** 和任何其他方法 \(未經同步處理\)，則您的程式碼會有控制代碼回收問題。  
  
 這個控制代碼回收問題可能導致資料損毀，並經常導致安全性弱點。  `SafeHandle` 和其同層級類別 <xref:System.Runtime.InteropServices.CriticalHandle> 提供機制，將原生控制代碼封裝到資源，以便能夠避免這類執行緒的問題。  此外，您還可以將 `SafeHandle` 及其同層級類別 `CriticalHandle` 用於處理其他執行緒問題，例如，對包含呼叫原生方法之原生控制代碼複本的 Managed 物件，小心控制它們的存留期 \(Lifetime\)。  在此情況下，您通常可以移除對 `GC.KeepAlive` 的呼叫。  當您使用 `SafeHandle` 時造成的效能負荷 \(使用 `CriticalHandle` 的情況會稍微好一些\)，通常可以透過小心設計來減輕。  
  
## 如何修正違規  
 將 `IntPtr` 用法轉換成 `SafeHandle`，以便安全地管理原生資源的存取。  如需範例，請參閱 <xref:System.Runtime.InteropServices.SafeHandle> 參考主題。  
  
## 隱藏警告的時機  
 您不應該隱藏這項警告。  
  
## 請參閱  
 <xref:System.IDisposable>