---
title: "CA2003：不要將 Fiber 視為執行緒 | Microsoft Docs"
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
  - "CA2003"
  - "DoNotTreatFibersAsThreads"
helpviewer_keywords: 
  - "CA2003"
  - "DoNotTreatFibersAsThreads"
ms.assetid: 15398fb1-f384-4bcc-ad93-00e1c0fa9ddf
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2003：不要將 Fiber 視為執行緒
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|DoNotTreatFibersAsThreads|  
|CheckId|CA2003|  
|分類|Microsoft.Reliability|  
|中斷變更|中斷|  
  
## 原因  
 Managed 執行緒已視為 Win32 執行緒。  
  
## 規則描述  
 不要假設 Managed 執行緒是 Win32 執行緒。  它是一個 Fiber。  Common Language Runtime \(CLR\) 會在 SQL 擁有的即時執行緒內容中，以 Fiber 的方式執行 Managed 執行緒。  這些執行緒可以在 AppDomains 間，或甚至 SQL Server 處理序中的資料庫間共用。  可以使用 Managed 執行緒區域儲存區 \(Thread Local Storage\)，但是可能無法使用 Unmanaged 執行緒區域儲存區，而您的程式碼可能會在目前的 OS 執行緒上再次執行。  不要變更設定，例如執行緒的地區設定。  也不要透過 P\/Invoke 呼叫 CreateCriticalSection 或 CreateMutex，因為它們會要求進入鎖定的執行緒也必須結束鎖定。  由於使用 Fiber 時不會是這種情況，所以 Win32 關鍵區段 \(Critical Section\) 和 Mutex 在 SQL 中不會有任何作用。  您可以安全地使用 Managed System.Thread 物件上的大部分狀態。  這包括 Managed 執行緒區域儲存區和執行緒目前的使用者介面 \(UI\) 文化特性。  但是，由於使用程式撰寫模型 \(Programming Model\) 的緣故，您在使用 SQL 時，將無法變更執行緒目前的文化特性 \(這個部分將透過新的權限來強制執行\)。  
  
## 如何修正違規  
 檢查執行緒的使用方式，並據以變更您的程式碼。  
  
## 隱藏警告的時機  
 您不應該隱藏此規則。