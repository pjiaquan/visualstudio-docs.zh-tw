---
title: "CA2202：不要多次處置物件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2202"
  - "Do not dispose objects multiple times"
  - "DoNotDisposeObjectsMultipleTimes"
helpviewer_keywords: 
  - "CA2202"
ms.assetid: fa85349a-cf1e-42c8-a86b-eacae1f8bd96
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2202：不要多次處置物件
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|DoNotDisposeObjectsMultipleTimes|  
|CheckId|CA2202|  
|分類|Microsoft.Usage|  
|中斷變更|不中斷|  
  
## 原因  
 方法實作 \(Implementation\) 包含程式碼路徑，可在相同物件上造成多個 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> 呼叫或 Dispose 對等用法 \(例如，一些型別上的 Close\(\) 方法\)。  
  
## 規則描述  
 正確實作的 <xref:System.IDisposable.Dispose%2A> 方法可呼叫多次，而不會擲回例外狀況。  然而，這不保證且不會產生 <xref:System.ObjectDisposedException?displayProperty=fullName>，而您不應在物件上呼叫 <xref:System.IDisposable.Dispose%2A> 一次以上。  
  
## 相關規則  
 [CA2000：必須在超出範圍前處置物件](../code-quality/ca2000-dispose-objects-before-losing-scope.md)  
  
## 如何修正違規  
 若要修正此規則的違規情形，請變更實作，這樣不論程式碼路徑為何，都只會呼叫物件的 <xref:System.IDisposable.Dispose%2A> 一次。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  即使知道可安全地呼叫物件的 <xref:System.IDisposable.Dispose%2A> 多次，實作在未來也可能會變更。  
  
## 範例  
 巢狀的 `using` 陳述式 \(Visual Basic 中的 `Using`\) 可能會造成 CA2202 警告的違規。  如果巢狀內部 `using` 陳述式的 IDisposable 資源中包含外部 `using` 陳述式，巢狀資源的 `Dispose` 方法就會釋放所包含的資源。  當這種情況發生時，外部 `using` 陳述式的 `Dispose` 方法會第二次嘗試處置其資源。  
  
 在下列範例中，以外部使用之陳述式所建立的 <xref:System.IO.Stream> 物件，會在包含 `stream` 物件之 <xref:System.IO.StreamWriter> 物件的 Dispose 方法中的內部使用陳述式的結尾釋放。  在外部 `using` 陳述式的結尾，`stream` 物件會被第二次釋放。  第二次釋放是 CA2202 的違規。  
  
```  
using (Stream stream = new FileStream("file.txt", FileMode.OpenOrCreate))  
{  
    using (StreamWriter writer = new StreamWriter(stream))  
    {  
        // Use the writer object...  
    }  
}  
  
```  
  
## 範例  
 若要解決這個問題，請使用 `try` `finally` 區塊，而非外部 `using` 陳述式。  在 `finally` 區塊中，確定 `stream` 資源不是 null。  
  
```  
Stream stream = null;  
try  
{  
    stream = new FileStream("file.txt", FileMode.OpenOrCreate);  
    using (StreamWriter writer = new StreamWriter(stream))  
    {  
        stream = null;  
        // Use the writer object...  
    }  
}  
finally  
{  
    if(stream != null)  
        stream.Dispose();  
}  
  
```  
  
## 請參閱  
 <xref:System.IDisposable?displayProperty=fullName>   
 [處置模式](../Topic/Dispose%20Pattern.md)