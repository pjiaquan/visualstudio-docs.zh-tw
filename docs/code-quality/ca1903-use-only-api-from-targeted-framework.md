---
title: "CA1903：只使用來自目標架構的 API | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UseOnlyAPIFromTargetedFramework"
  - "CA1903"
helpviewer_keywords: 
  - "CA1903"
  - "UseOnlyApiFromTargetedFramework"
ms.assetid: efdb5cc7-bbd8-4fa7-9fff-02b91e59350e
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 8
---
# CA1903：只使用來自目標架構的 API
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|UseOnlyApiFromTargetedFramework|  
|CheckId|CA1903|  
|分類|Microsoft.Portability|  
|中斷變更|中斷 \- 對外部可見成員或型別的簽章引發時。<br /><br /> 非中斷 \- 在方法主體中引發時。|  
  
## 原因  
 某一個成員或型別使用的是 Service Pack 中所含的成員或型別，但是專案的目標 Framework 中卻沒有包含該成員或型別。  
  
## 規則描述  
 新成員和型別已包含在 .NET Framework 2.0 Service Pack 1 與 2、.NET Framework 3.0 Service Pack 1 與 2，以及 .NET Framework 3.5 Service Pack 1。  以 .NET Framework 主要版本為目標的專案會無意間與這些新的 API 產生相依關係。  為了避免產生這樣的相依關係，所使用的任一新成員及型別，只要不是專案目標 Framework 預設包含的範圍，便會引發這項規則。  
  
 **目標 Framework 與 Service Pack 的相依性**  
  
|||  
|-|-|  
|當目標 Framework 為|使用下列版本中包含的成員時引發|  
|.NET Framework 2.0|.NET Framework 2.0 SP1、.NET Framework 2.0 SP2|  
|.NET Framework 3.0|.NET Framework 2.0 SP1、.NET Framework 2.0 SP2、.NET Framework 3.0 SP1、.NET Framework 3.0 SP2|  
|.NET Framework 3.5|.NET Framework 3.5 SP1|  
|.NET Framework 4|N\/A|  
  
 若要變更專案的目標 Framework，請參閱[以特定的 .NET Framework 版本為目標](../ide/targeting-a-specific-dotnet-framework-version.md)。  
  
## 如何修正違規  
 若要移除 Service Pack 上的相依性關係，請停止使用所有新成員或型別。  如果這個相依性關係是刻意建立的，可以隱藏不要顯示警告或是關閉這個規則。  
  
## 隱藏警告的時機  
 如果這並不是特定 Service Pack 上刻意建立的相依性，請不要隱藏這項規則的警告。  在這種情況下，您的應用程式可能會因為沒有安裝這個 Service Pack 而無法在系統上執行。  如果這個相依性關係是刻意建立的，可以隱藏不要顯示警告或是關閉這個規則。  
  
## 範例  
 下列範例顯示的類別所使用的型別 DateTimeOffset 只有在 .NET 2.0 Service Pack 1 才有。  這個範例中，\[專案\] 屬性其 \[目標 Framework\] 下拉式清單中的 .NET Framework 2.0 必須已選取。  
  
 [!code-cs[FxCop.Portability.UseOnlyApiFromTargetedFramework#1](../code-quality/codesnippet/CSharp/ca1903-use-only-api-from-targeted-framework_1.cs)]  
  
## 範例  
 以下範例修正了先前說明的違規，即使用 DateTime 型別來取代 DateTimeOffset 型別的問題。  
  
 [!code-cs[FxCop.Portability.UseOnlyApiFromTargetedFramework2#1](../code-quality/codesnippet/CSharp/ca1903-use-only-api-from-targeted-framework_2.cs)]  
  
## 請參閱  
 [可攜性警告](../code-quality/portability-warnings.md)   
 [以特定的 .NET Framework 版本為目標](../ide/targeting-a-specific-dotnet-framework-version.md)