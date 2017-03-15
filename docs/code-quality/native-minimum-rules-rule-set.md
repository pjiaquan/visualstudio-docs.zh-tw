---
title: "原生最小規則規則集 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2d898bc4-fba5-472e-8f09-b0c6b511c5a3
caps.latest.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 3
---
# 原生最小規則規則集
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Microsoft 原生最小規則的重點在於機器碼中最關鍵的問題，包括潛在的安全性漏洞和應用程式損毀。  您應該在您為原生專案建立的任何自訂規則集中都包含這個規則集。  
  
|規則|說明|  
|--------|--------|  
|[C6001](../code-quality/c6001.md)|使用尚未初始化的記憶體。|  
|[C6011](../code-quality/c6011.md)|取值 NULL 指標。|  
|[C6029](../code-quality/c6029.md)|使用未經確認的值 。|  
|[C6053](../code-quality/c6053.md)|從呼叫的無終止。|  
|[C6059](../code-quality/c6059.md)|終結串連|  
|[C6063](../code-quality/c6063.md)|遺漏格式化函式中的字串引數。|  
|[C6064](../code-quality/c6064.md)|遺漏整格式化函式中的整數引數。|  
|[C6066](../code-quality/c6066.md)|遺漏格式化函式中的指標引數。|  
|[C6067](../code-quality/c6067.md)|遺漏格式化函式中的字串指標引數。|  
|[C6101](../code-quality/c6101.md)|傳回未初始化的記憶體。|  
|[C6200](../code-quality/c6200.md)|索引超出緩衝區最大值|  
|[C6201](../code-quality/c6201.md)|索引超出堆疊緩衝區最大值|  
|[C6270](../code-quality/c6270.md)|遺漏格式化函式中的浮點引數。|  
|[C6271](../code-quality/c6271.md)|格式化函式中的額外引數。|  
|[C6272](../code-quality/c6272.md)|格式化函式中的非浮點引數。|  
|[C6273](../code-quality/c6273.md)|格式化函式中的非整數引數。|  
|[C6274](../code-quality/c6274.md)|格式化函式中的非字元引數。|  
|[C6276](../code-quality/c6276.md)|無效的字串轉換。|  
|[C6277](../code-quality/c6277.md)|無效的 CreateProcess 呼叫|  
|[C6284](../code-quality/c6284.md)|無效的格式化函式中的物件引數。|  
|[C6290](../code-quality/c6290.md)|Logical\-Not Bitwise\-And 優先順序|  
|[C6291](../code-quality/c6291.md)|Logical\-Not Bitwise\-Or 優先順序。|  
|[C6302](../code-quality/c6302.md)|無效的格式化函式中的字串引數。|  
|[C6303](../code-quality/c6303.md)|無效的格式化函式中的寬字元字串引數。|  
|[C6305](../code-quality/c6305.md)|不相符的大小和使用數目。|  
|[C6306](../code-quality/c6306.md)|不正確的變數引數函式呼叫。|  
|[C6328](../code-quality/c6328.md)|可能的引數型別不符。|  
|[C6385](../code-quality/c6385.md)|讀取滿溢|  
|[C6386](../code-quality/c6386.md)|撰寫滿溢|  
|[C6387](../code-quality/c6387.md)|無效的參數值。|  
|[C6500](../code-quality/c6500.md)|無效的屬性|  
|[C6501](../code-quality/c6501.md)|發生衝突的屬性值。|  
|[C6503](../code-quality/c6503.md)|參考不可以是空值。|  
|[C6504](../code-quality/c6504.md)|在非指標的空值。|  
|[C6505](../code-quality/c6505.md)|在 void的MustCheck|  
|[C6506](../code-quality/c6506.md)|在非指標或陣列的緩衝區大小。|  
|[C6507](http://msdn.microsoft.com/zh-tw/18f88cd1-d035-4403-a6a4-12dd0affcf21)|在取值零的空值不符|  
|[C6508](../code-quality/c6508.md)|常數的寫入權限。|  
|[C6509](../code-quality/c6509.md)|在之前狀況中回傳使用過|  
|[C6510](../code-quality/c6510.md)|在非指標的空值結束|  
|[C6511](../code-quality/c6511.md)|MustCheck 屬性必須為 Yes 或 No。|  
|[C6513](../code-quality/c6513.md)|沒有緩衝區大小的項目大小。|  
|[C6514](../code-quality/c6514.md)|緩衝區大小超過陣列大小|  
|[C6515](../code-quality/c6515.md)|在非指標的緩衝區大小。|  
|[C6516](../code-quality/c6516.md)|在屬性中沒有屬性。|  
|[C6517](../code-quality/c6517.md)|在不可讀取緩衝區的有效大小|  
|[C6518](../code-quality/c6518.md)|在非可寫入緩衝區的可寫入的大小|  
|[C6519](http://msdn.microsoft.com/zh-tw/2b6326b0-0539-4d26-8fb1-720114933232)|無效的註釋: 'NeedsRelease' 屬性的值必須為 Yes 或 No。|  
|[C6521](http://msdn.microsoft.com/zh-tw/e98d0ae3-6f13-47b2-9a15-15d4055af9ef)|無效的指標值的字串大小。|  
|[C6522](../code-quality/c6522.md)|無效的字串型別的大小|  
|[C6523](http://msdn.microsoft.com/zh-tw/11397a31-b224-46b0-afb7-d49ca576a3bb)|無效的字串參數大小|  
|[C6525](../code-quality/c6525.md)|無效的不可能執行到的位置的字串大小。|  
|[C6526](http://msdn.microsoft.com/zh-tw/59c590c7-0098-4166-a1ac-87f324596002)|無效的字串緩衝區型別的大小|  
|[C6527](../code-quality/c6527.md)|無效的註釋: NeedsRelease 屬性在 void 型別的值不能使用。|  
|[C6530](../code-quality/c6530.md)|無法辨認的格式字串樣式|  
|[C6540](../code-quality/c6540.md)|在這個函式上使用屬性附註會使其所有存在的 \_\_declspec 附註無效。|  
|[C6551](../code-quality/c6551.md)|無效的大小規格: 無法剖析運算式|  
|[C6552](../code-quality/c6552.md)|無效的 Deref\=或 Notref\=: 無法剖析運算式|  
|[C6701](../code-quality/c6701.md)|值不是有效的Yes\/No\/Maybe。|  
|[C6702](../code-quality/c6702.md)|值不是字串。|  
|[C6703](../code-quality/c6703.md)|值不是數值。|  
|[C6704](../code-quality/c6704.md)|未預期的註釋運算式錯誤|  
|[C6705](../code-quality/c6705.md)|附註的引數的預期數字不符合附註的引數的實際數目|  
|[C6706](../code-quality/c6706.md)|附註的未預期的附註錯誤。|  
|[C28021](../code-quality/c28021.md)|被附註的參數必須是指標。|  
|[C28182](../code-quality/c28182.md)|正在取值 NULL 指標。  指標含有與另一個指標的空值。|  
|[C28202](../code-quality/c28202.md)|非靜態成員之不合法的參考。|  
|[C28203](../code-quality/c28203.md)|類別成員的參考模稜兩可。|  
|[C28205](../code-quality/c28205.md)|Success\_ 或 \_On\_failure\_ 用於不合法的內容中:|  
|[C28206](../code-quality/c28206.md)|左運算元指向結構，請使用 '\-\>'。|  
|[C28207](../code-quality/c28207.md)|左運算元是結構，請使用 '.'。|  
|[C28210](../code-quality/c28210.md)|On\_failure\_ 內容的註釋不能明確在pre context 中|  
|[C28211](../code-quality/c28211.md)|SAL\_context 必須有靜態內容名稱。|  
|[C28212](../code-quality/c28212.md)|附註必須有預期的指標運算式。|  
|[C28213](../code-quality/c28213.md)|\_Use\_decl\_annotations\_ 附註必須不需修改就能用來參考預先宣告。|  
|[C28214](../code-quality/c28214.md)|屬性參數名稱必須是 p1...p9。|  
|[C28215](../code-quality/c28215.md)|typefix 不能套用到已經有 typefix 的參數|  
|[C28216](../code-quality/c28216.md)|checkReturn 附註只適用於為特定函式參數的後置條件。|  
|[C28217](../code-quality/c28217.md)|對於函式，附註的參數數目與其所找到的不符。|  
|[C28218](../code-quality/c28218.md)|對於函式參數，附註的參數與在檔案找到的不符。|  
|[C28219](../code-quality/c28219.md)|註釋中標註的參數需要列舉的成員|  
|[C28220](../code-quality/c28220.md)|整數運算式為附註預期標記法的參數|  
|[C28221](../code-quality/c28221.md)|用於附註的參數預期的字串運算式。|  
|[C28222](../code-quality/c28222.md)|\_\_yes、 \_\_no 或 \_\_maybe為預期的附註|  
|[C28223](../code-quality/c28223.md)|未找到預期的附註參數語彙基元\/識別項。|  
|[C28224](../code-quality/c28224.md)|附註需要參數。|  
|[C28225](../code-quality/c28225.md)|沒有找到附註中參數所需的正確數目|  
|[C28226](../code-quality/c28226.md)|附註不可以同時是 PrimOp \(在目前宣告中\)。|  
|[C28227](../code-quality/c28227.md)|附註不可以同時是 PrimOp \(請參閱預先宣告\)。|  
|[C28228](../code-quality/c28228.md)|附註參數:無法使用附註中的型別|  
|[C28229](../code-quality/c28229.md)|附註不支援參數。|  
|[C28230](../code-quality/c28230.md)|參數的型別沒有成員。|  
|[C28231](../code-quality/c28231.md)|附註只在陣列有效|  
|[C28232](../code-quality/c28232.md)|pre、post 或 deref 未套用至任何附註。|  
|[C28233](../code-quality/c28233.md)|pre、post 或 deref 已套用至區塊。|  
|[C28234](../code-quality/c28234.md)|\_\_at 運算式不套用於目前函式。|  
|[C28235](../code-quality/c28235.md)|函式無法單獨做為附註。|  
|[C28236](../code-quality/c28236.md)|附註不能用在運算式中。|  
|[C28237](../code-quality/c28237.md)|不再支援參數的註釋。|  
|[C28238](../code-quality/c28238.md)|在參數的註釋具有一個以上的值，stringValue 和 longValue。  使用 paramn\=xxx|  
|[C28239](../code-quality/c28239.md)|在參數的註釋具有兩個值，stringValue 或 longValue 以及 paramn\=xxx。  請只使用 paramn\=xxx|  
|[C28240](../code-quality/c28240.md)|參數的註釋有 param2 但沒有 param1。|  
|[C28241](../code-quality/c28241.md)|函式的附註參數無法辨認|  
|[C28243](../code-quality/c28243.md)|函式的註釋需要執行的取值比實際註釋之型別允許的還多。|  
|[C28245](../code-quality/c28245.md)|函式的附註會在非成員函式上附註 'this'。|  
|[C28246](../code-quality/c28246.md)|函式中的參數附註不符合參數的型別。|  
|[C28250](../code-quality/c28250.md)|函式不一致的附註:先前的執行個體有錯誤發生。|  
|[C28251](../code-quality/c28251.md)|函式不一致的附註:這個執行個體有錯誤發生。|  
|[C28252](../code-quality/c28252.md)|函式不一致的附註:參數在這個執行個體有另一個附註。|  
|[C28253](../code-quality/c28253.md)|函式不一致的附註:參數在這個執行個體有另一個附註。|  
|[C28254](../code-quality/c28254.md)|dynamic\_cast\<\>\(\)在附註中不支援。|  
|[C28262](../code-quality/c28262.md)|在函式中找到附註的語法錯誤:|  
|[C28263](../code-quality/c28263.md)|找到內建的條件式註釋語法錯誤:|  
|[C28264](http://msdn.microsoft.com/zh-tw/bf6ea983-a06e-4752-a042-747a7dbf338c)|結果清單值必須是常數。|  
|[C28267](../code-quality/c28267.md)|在函式中找到附註的語法錯誤:|  
|[C28272](../code-quality/c28272.md)|函式、參數的附註在檢查時，與函式宣告不一致。|  
|[C28273](../code-quality/c28273.md)|對於函式，線索與函式宣告不一致。|  
|[C28275](../code-quality/c28275.md)|\_Macro\_value\_ 的參數為空值。|  
|[C28279](../code-quality/c28279.md)|找到符號的 'begin'，但沒有相符的 'end'。|  
|[C28280](../code-quality/c28280.md)|找到符號的 'end'，但沒有相符的 'begin'。|  
|[C28282](../code-quality/c28282.md)|格式化字串必須在前置條件|  
|[C28285](../code-quality/c28285.md)|針對函式，在參數中的語法錯誤|  
|[C28286](../code-quality/c28286.md)|函式的結尾附近發生錯誤。|  
|[C28287](../code-quality/c28287.md)|函式的 \_At\_\(\) 附註中有語法錯誤 \(無法辨認的參數名稱\)。|  
|[C28288](../code-quality/c28288.md)|函式的 \_At\_\(\) 附註中有語法錯誤 \(無效的參數名稱\)。|  
|[C28289](../code-quality/c28289.md)|對函式來說: ReadableTo 或 WritableTo 沒有有限的規格做為參數。|  
|[C28290](../code-quality/c28290.md)|函式的附註包含比實際參數數目還多的外部。|  
|[C28291](../code-quality/c28291.md)|位於 deref 層級 0 的 post null\/notnull 對函式是無意義的。|  
|[C28300](../code-quality/c28300.md)|運算子不相容型別的運算式運算元。|  
|[C28301](../code-quality/c28301.md)|函式的第一個宣告中沒有附註。|  
|[C28302](../code-quality/c28302.md)|額外的 \_Deref\_ 運算子在註解中被找到。|  
|[C28303](../code-quality/c28303.md)|一個模稜兩可的 \_Deref\_ 運算子在註解中被找到。|  
|[C28304](../code-quality/c28304.md)|找到非正確定位 \_Notref\_ 運算子套用至語彙基元。|  
|[C28305](../code-quality/c28305.md)|在剖析時語彙基元找到的錯誤。|  
|[C28350](../code-quality/c28350.md)|附註描述條件上不適合的情況:|  
|[C28351](../code-quality/c28351.md)|附註描述條件中不可以使用動態值 \(變數\)。|