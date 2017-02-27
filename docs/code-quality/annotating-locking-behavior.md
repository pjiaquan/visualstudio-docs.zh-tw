---
title: "註釋鎖定行為 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_Releases_nonreentrant_lock_"
  - "_Lock_kind_mutex_"
  - "_Lock_kind_critical_section_"
  - "_Acquires_lock_"
  - "_Releases_lock_"
  - "_Has_lock_kind_"
  - "_Releases_exclusive_lock_"
  - "_Post_same_lock_"
  - "_Requires_exclusive_lock_held_"
  - "_Requires_shared_lock_held_"
  - "_Lock_kind_semaphore_"
  - "_Requires_lock_held_"
  - "_Acquires_exclusive_lock_"
  - "_Create_lock_level_"
  - "_Acquires_nonreentrant_lock_"
  - "_Releases_shared_lock_"
  - "_Has_lock_level_"
  - "_Lock_kind_spin_lock_"
  - "_Requires_lock_not_held_"
  - "_Acquires_shared_lock_"
  - "_Requires_no_locks_held_"
  - "_Lock_level_order_"
  - "_Lock_kind_event_"
ms.assetid: 07769c25-9b97-4ab7-b175-d1c450308d7a
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 註釋鎖定行為
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

若要避免在多執行緒程式的並行錯誤，請遵循適當的鎖定規則並使用 SAL 附註。  
  
 並行錯誤極難以重新產生、診斷和偵錯，因為他們是不決定性的。  當您設計的一些執行緒有更多的程式碼主體，討論執行緒交錯的問題會變得困難且不實際。  因此，最好在多執行緒應用程式中遵循鎖定規則。  例如，當擷取多個鎖定時遵循一個鎖定可以幫助避免死結，並在存取共用資源之前取得適當嚴密監控鎖定有助於避免競爭情形。  
  
 可惜的是，介面上簡單鎖定的規則在實際上是難以遵循的。  在今天的程式設計語言和編譯器的基本限制並不直接支援並行要求規格和分析。  程式設計人員必須依賴非正式的程式碼註解，以表示其使用鎖定的目的。  
  
 並行 SAL 附註可以幫助您指定鎖定副作用、鎖定責任、資料保護、鎖定命令階層架構和其他必要的鎖定行為。  藉由將隱含規則變為明確， SAL 並行附註提供一致的方式來記錄您的程式碼如何使用鎖定規則。  並行附註可以提高程式碼分析工具的能力，找出競爭情形、死結、不相符的同步處理作業和其他細小的並行存取錯誤。  
  
## 一般方針  
 藉由使用附註，您可以陳述陳述在實作 \(被呼叫端\) 和用戶端 \(呼叫端\) 之間的函式定義隱含的合約，以及表示不變項目和可進一步改善分析程式的其他屬性。  
  
 SAL 支援各種不同的鎖定基本型別 ，例如關鍵區段、Mutexe、微調鎖定和其他資源物件。  許多並行附註採用鎖定運算式做為參數。  依照慣例，鎖定已由基礎鎖定物件的路徑運算式表示。  
  
 請注意某些執行緒擁有權規則：  
  
-   微調鎖定是擁有清除執行緒擁有權的不可計數鎖定。  
  
-   Mutex 和關鍵區域是擁有清除執行緒擁有權的計數鎖定。  
  
-   號誌和事件是未擁有清楚執行緒擁有權的計數鎖定。  
  
## 鎖定附註  
 下表列出鎖定的附註。  
  
|註釋|說明|  
|--------|--------|  
|`_Acquires_exclusive_lock_(expr)`|附註一個函式並且指出，在後製狀態，函式以 1 間隔增加名為 `expr` 的鎖定物件的排除鎖定計數。|  
|`_Acquires_lock_(expr)`|附註一個函式並且指出，在後製狀態，函式以 1 間隔增加名為 `expr` 的鎖定物件的鎖定計數。|  
|`_Acquires_nonreentrant_lock_(expr)`|取得名為 `expr` 的鎖定。如果鎖定已經被保留，會報告錯誤。|  
|`_Acquires_shared_lock_(expr)`|附註一個函式並且指出，在後製狀態，函式以 1 間隔增加名為 `expr` 的鎖定物件的共享鎖定計數。|  
|`_Create_lock_level_(name)`|宣告符號 `name` 是鎖定層級的陳述式，所以它可以用於附註 `_Has_Lock_level_` 和 `_Lock_level_order_`。|  
|`_Has_lock_kind_(kind)`|附註任何物件去修改資源物件的型別資訊。  有時，一個常用的型別針對不同類型的資源和並不足以分辨各種資源中的語意要求的多載的型別而使用。  以下是預先定義的 `kind` 參數清單：<br /><br /> `_Lock_kind_mutex_`<br /> Mutex 的鎖定類型 ID。<br /><br /> `_Lock_kind_event_`<br /> 事件的鎖定類型 ID。<br /><br /> `_Lock_kind_semaphore_`<br /> 號誌的鎖定類型 ID。<br /><br /> `_Lock_kind_spin_lock_`<br /> 微調鎖定上的鎖定類型 ID。<br /><br /> `_Lock_kind_critical_section_`<br /> 關鍵區段的鎖定類型 ID。|  
|`_Has_lock_level_(name)`|附註一個鎖定物件並給予 `name` 的鎖定層級。|  
|`_Lock_level_order_(name1, name2)`|一個陳述式給定 `name1` `name2`和之間的鎖定的順序。|  
|`_Post_same_lock_(expr1, expr2)`|附註一個函式並在兩個鎖定的後置狀態中指出， `expr1` 和 `expr2` 都會被視為它們是相同的鎖定物件。|  
|`_Releases_exclusive_lock_(expr)`|附註一個函式並且指出，在後製狀態，函式以 1 間隔減少名為 `expr` 的鎖定物件的排除鎖定計數。|  
|`_Releases_lock_(expr)`|附註一個函式並且指出，在後製狀態，函式以 1 間隔減少名為 `expr` 的鎖定物件的鎖定計數。|  
|`_Releases_nonreentrant_lock_(expr)`|名為 `expr` 的鎖定已釋出。  若鎖定目前沒有被保留，會報告錯誤。|  
|`_Releases_shared_lock_(expr)`|附註一個函式並且指出，在後製狀態，函式以 1 間隔減少名為 `expr` 的鎖定物件的共享鎖定計數。|  
|`_Requires_lock_held_(expr)`|附註一個函式並且在前置狀態指出，名為 `expr` 的物件的鎖定計數至少為一。|  
|`_Requires_lock_not_held_(expr)`|附註一個函式並且在前置狀態指出，名為 `expr` 的物件的鎖定計數為零。|  
|`_Requires_no_locks_held_`|附註一個函式並且指出檢查者已知所有鎖定的鎖定計數為零。|  
|`_Requires_shared_lock_held_(expr)`|附註一個函式並且在前置狀態指出，名為 `expr` 的物件的共享鎖定計數至少為一。|  
|`_Requires_exclusive_lock_held_(expr)`|附註一個函式並且在前置狀態指出，名為 `expr` 的物件的排除鎖定計數至少為一。|  
  
## 未公開之鎖定物件的 SAL 內在變數  
 某些鎖定物件不是由關聯的鎖定之函式實作公開。下表列出可在作業於那些未公開的鎖定物件的函式註解的 SAL 內部變數。  
  
|註釋|說明|  
|--------|--------|  
|`_Global_cancel_spin_lock_`|說明移除微調鎖定。|  
|`_Global_critical_region_`|描述關鍵區域。|  
|`_Global_interlock_`|描述繫結的作業。|  
|`_Global_priority_region_`|描述優先權區域。|  
  
## 共用資料存取附註  
 下表列出使用共用資料存取的附註。  
  
|註釋|說明|  
|--------|--------|  
|`_Guarded_by_(expr)`|附註一個變數並指出，每次存取變數時，以 `expr` 命名的鎖定物件的鎖定計數至少為一。|  
|`_Interlocked_`|附註一個變數會相等於 `_Guarded_by_(_Global_interlock_)`。|  
|`_Interlocked_operand_`|附註函式參數為目標的其中一個運算元各種連鎖的函式。這些運算元必須有特定額外屬性。|  
|`_Write_guarded_by_(expr)`|附註一個變數並指出，每次修改變數時，以 `expr` 命名的鎖定物件的鎖定計數至少為一。|  
  
## 請參閱  
 [使用 SAL 註釋減少 C\/C\+\+ 程式碼的缺失](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [了解 SAL](../code-quality/understanding-sal.md)   
 [註釋函式參數和傳回值](../code-quality/annotating-function-parameters-and-return-values.md)   
 [註釋函式行為](../code-quality/annotating-function-behavior.md)   
 [註釋結構和類別](../code-quality/annotating-structs-and-classes.md)   
 [指定套用註釋的時機和位置](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [內建函式](../code-quality/intrinsic-functions.md)   
 [最佳作法和範例](../code-quality/best-practices-and-examples-sal.md)   
 [程式碼分析小組部落格](http://go.microsoft.com/fwlink/p/?LinkId=251197)