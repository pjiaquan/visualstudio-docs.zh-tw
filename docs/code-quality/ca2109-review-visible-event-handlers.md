---
title: "CA2109：必須檢視可見的事件處理常式 | Microsoft Docs"
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
  - "CA2109"
  - "ReviewVisibleEventHandlers"
helpviewer_keywords: 
  - "CA2109"
  - "ReviewVisibleEventHandlers"
ms.assetid: 8f8fa0ee-e94e-400e-b516-24d8727725d7
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2109：必須檢視可見的事件處理常式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|ReviewVisibleEventHandlers|  
|CheckId|CA2109|  
|分類|Microsoft.Security|  
|中斷變更|中斷|  
  
## 原因  
 偵測到公用或保護的事件處理方法。  
  
## 規則描述  
 外部可見的事件處理方法會呈現出需要檢視的安全性問題。  
  
 除非有絕對的必要性，否則不應該公開 \(Expose\) 事件處理方法。  只要處理常式和事件簽章相符，叫用 \(Invoke\) 公開之方法的事件處理常式 \(即委派型別\) 就可以加入至任何事件。  事件可能會由任何程式碼所引發，更經常由受到高度信任的系統程式碼所引發，以回應一些使用者動作 \(例如按一下按鈕\)。  將安全性檢查加入至事件處理方法不能防止程式碼登錄叫用方法的事件處理常式。  
  
 此要求無法確實保護事件處理常式叫用的方法。  安全性要求可透過檢查呼叫堆疊上的呼叫端，協助保護程式碼免於不信任呼叫端的攻擊。  執行事件處理常式的方法時，將事件處理常式加入至事件的程式碼不需要出現在呼叫堆疊上。  因此，當叫用事件處理常式方法時，呼叫堆疊只能有高度信任的呼叫端。  這會導致事件處理常式方法提出的要求成功。  叫用方法時，要求的使用權限也可能會判斷提示 \(Assert\)。  針對這些原因，只會在檢視事件處理方法之後，評估不修正此規則之違規情形的風險。  檢視程式碼時，請留意下列問題：  
  
-   您的事件處理常式會執行任何危險或會被利用的作業嗎 \(例如判斷提示使用權限或隱藏 Unmanaged 程式碼使用權限\)？  
  
-   對於隨時只能以堆疊上高度信任的呼叫端執行的程式碼來說，會有哪些安全性威脅?  
  
## 如何修正違規  
 若要修正此規則的違規情形，請檢視方法並評估下列事項：  
  
-   可以讓事件處理方法成為非公用嗎？  
  
-   可以將所有危險的功能移出事件處理常式嗎？  
  
-   如果已加上安全性要求，可以使用其他方式完成這項作業嗎？  
  
## 隱藏警告的時機  
 只有在仔細檢視安全性，確定程式碼不會造成安全性威脅之後，才能隱藏此規則的警告。  
  
## 範例  
 下列程式碼顯示惡意程式碼可以濫用的事件處理方法。  
  
 [!code-cs[FxCop.Security.EventSecLib#1](../code-quality/codesnippet/CSharp/ca2109-review-visible-event-handlers_1.cs)]  
  
## 請參閱  
 <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName>   
 <xref:System.EventArgs?displayProperty=fullName>   
 [Security Demands](http://msdn.microsoft.com/zh-tw/324c14f8-54ff-494d-9fd1-bfd20962c8ba)