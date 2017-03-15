---
title: "CA2000：必須在超出範圍前處置物件 | Microsoft Docs"
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
  - "CA2000"
  - "Dispose objects before losing scope"
  - "DisposeObjectsBeforeLosingScope"
helpviewer_keywords: 
  - "CA2000"
  - "DisposeObjectsBeforeLosingScope"
ms.assetid: 0c3d7d8d-b94d-46e8-aa4c-38df632c1463
caps.latest.revision: 32
caps.handback.revision: 32
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2000：必須在超出範圍前處置物件
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|DisposeObjectsBeforeLosingScope|  
|CheckId|CA2000|  
|類別|Microsoft.Reliability|  
|中斷變更|中斷|  
  
## 原因  
 已建立 <xref:System.IDisposable> 型別的區域物件 \(Local Object\)，但在此物件的所有參考都超出範圍之後才會處置此物件。  
  
## 規則描述  
 如果在可處置物件的所有參考都超出範圍前明確未處置掉該物件，在記憶體回收行程執行該物件的完成項時，於某個不定時間處置該物件。  由於可能會發生例外事件，導致物件的完成項無法執行，所以應改為明確處置物件。  
  
## 如何修改違規情況  
 若要修正此規則的違規情形，請在物件的所有參考都超出範圍之前，在此物件上呼叫 <xref:System.IDisposable.Dispose%2A>。  
  
 請注意，您可以使用 `using` 陳述式 \(在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中為 `Using`\) 來包裝實作 `IDisposable` 的物件。  在 `using` 區段結束時將會自動處置以這種方式包裝的物件。  
  
 在下列一些情況下，使用陳述式不足以保護 IDisposable 物件，而且可能會導致發生 CA2000。  
  
-   要傳回可處置的物件，需要在使用中區塊外部的 try\/finally 區塊中建構該物件。  
  
-   初始化可處置物件的成員不應該在使用陳述式的建構函式中進行。  
  
-   只被一個例外狀況處理常式保護的巢狀建構函式。  例如：  
  
    ```  
    using (StreamReader sr = new StreamReader(new FileStream("C:\myfile.txt", FileMode.Create)))  
    { ... }  
    ```  
  
     使 CA2000 發生的原因是因為 StreamReader 物件建構中的失敗可能會導致 FileStream 物件永遠不會關閉。  
  
-   動態物件應該使用陰影物件來實作 IDisposable 物件的 Dispose 模式。  
  
## 隱藏警告的時機  
 請勿隱藏這項規則的警告，除非您在呼叫 `Dispose`之物件的方法，例如 <xref:System.IO.Stream.Close%2A>，或假如這隻引發警告的方法傳回了IDisposable 物件來包裝您的物件。  
  
## 相關規則  
 [CA2213：可處置的欄位應該受到處置](../code-quality/ca2213-disposable-fields-should-be-disposed.md)  
  
 [CA2202：不要多次處置物件](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)  
  
## 範例  
 如果您要實作的方法會傳回可處置物件，請使用 try\/finally 區塊而不含 Catch 區塊，來確定處置該物件。  利用 try\/finally 區塊，您可允許在錯誤點引發例外狀況，並確保處置該物件。  
  
 在 OpenPort1 方法中，開啟 ISerializable 物件 SerialPort 的呼叫，或是 SomeMethod 的呼叫都可能失敗。  在此實作上會引發 CA2000 警告。  
  
 在 OpenPort2 方法中，會宣告兩個 SerialPort 物件並將其設定為 null：  
  
-   `tempPort`，用來測試方法作業是否成功。  
  
-   `port`，用於方法的傳回值。  
  
 `tempPort` 會在 `try` 區塊中建構和開啟，而且其他任何必要的工作都會在相同的 `try` 區塊中執行。  在 `try` 區塊的結尾，已開啟的連接埠會指派至會傳回的 `port` 物件，而且 `tempPort` 物件會設定為  `null`。  
  
 `finally` 區塊會檢查 `tempPort` 的值。  如果它不是 Null，方法中的作業便已失敗，而且已關閉 `tempPort` 以確保會釋放任何資源。  如果方法的作業成功，傳回的連接埠物件將包含開啟的 SerialPort 物件，如果作業失敗，則會是 null。  
  
 [!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../code-quality/codesnippet/VisualBasic/ca2000-dispose-objects-before-losing-scope_1.vb)]
 [!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../code-quality/codesnippet/VisualBasic/ca2000-dispose-objects-before-losing-scope_1.vb)]
 [!code-cs[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../code-quality/codesnippet/CSharp/ca2000-dispose-objects-before-losing-scope_1.cs)]  
  
## 範例  
 預設情況下，[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 編譯器會對所有算術運算子進行溢位檢查。  因此，任何 Visual Basic 算術運算都可能擲回 <xref:System.OverflowException>。  這可能會導致如 CA2000 規則中的意外違規。  例如，下列 CreateReader1 函式會產生 CA2000 違規，因為 Visual Basic 編譯器會針對可能擲回例外狀況，進而使 StreamReader 不處置的加入，發出溢位檢查指令。  
  
 若要修正此問題，您可以用您專案中的 Visual Basic 編譯器來停用的溢位檢查的發出，或者可以像下列 CreateReader2 函式一樣修改您的程式碼。  
  
 若要停用發出溢位檢查，請以滑鼠右鍵按一下 \[方案總管\] 中的專案名稱，然後按一下 \[**內容**\]。  請按一下 \[**編譯**\]，按一下 \[**進階編譯選項**\]，然後再核取 \[**移除整數的溢位檢查**\]。  
  
 [!CODE [FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope.VBOverflow#1](FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope.VBOverflow#1)]  
  
## 請參閱  
 <xref:System.IDisposable>   
 [處置模式](../Topic/Dispose%20Pattern.md)