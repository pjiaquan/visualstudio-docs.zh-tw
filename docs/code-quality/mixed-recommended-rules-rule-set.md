---
title: "混合建議規則規則集 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c3186b5b-0149-4a75-826e-e3539e4e703f
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 混合建議規則規則集
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Microsoft 混合式建議規則的重點在於支援 Common Language Runtime 之 C\+\+ 專案中最常見且關鍵的問題，包括潛在的安全性漏洞和應用程式損毀，以及其他重要邏輯和設計錯誤。  您應該在您為支援 Common Language Runtime 之 C\+\+ 專案建立的任何自訂規則集中都包含這個規則集。  這個規則集是設計用來與 Visual Studio Professional \(含\) 以上版本一起設定。  
  
|規則|說明|  
|--------|--------|  
|[C6001](../code-quality/c6001.md)|使用尚未初始化的記憶體。|  
|[C6011](../code-quality/c6011.md)|取值 NULL 指標。|  
|[C6029](../code-quality/c6029.md)|使用未經確認的值 。|  
|[C6031](../code-quality/c6031.md)|忽略傳回值|  
|[C6053](../code-quality/c6053.md)|從呼叫的無終止。|  
|[C6054](../code-quality/c6054.md)|零終止遺失。|  
|[C6059](../code-quality/c6059.md)|終結串連|  
|[C6063](../code-quality/c6063.md)|遺漏格式化函式中的字串引數。|  
|[C6064](../code-quality/c6064.md)|遺漏整格式化函式中的整數引數。|  
|[C6066](../code-quality/c6066.md)|遺漏格式化函式中的指標引數。|  
|[C6067](../code-quality/c6067.md)|遺漏格式化函式中的字串指標引數。|  
|[C6101](../code-quality/c6101.md)|傳回未初始化的記憶體。|  
|[C6200](../code-quality/c6200.md)|索引超出緩衝區最大值|  
|[C6201](../code-quality/c6201.md)|索引超出堆疊緩衝區最大值|  
|[C6214](../code-quality/c6214.md)|BOOL 到HRESULT的轉換無效|  
|[C6215](../code-quality/c6215.md)|從BOOL 到HRESULT的轉換無效|  
|[C6216](../code-quality/c6216.md)|無效的HRESULT 編譯器插入轉型 BOOL|  
|[C6217](../code-quality/c6217.md)|無效的 HRESULT 測試與 NOT|  
|[C6220](../code-quality/c6220.md)|無效的 HRESULT 比較為\-1。|  
|[C6226](../code-quality/c6226.md)|無效的 HRESULT 指派為\-1。|  
|[C6230](../code-quality/c6230.md)|為布林值的無效用法 HRESULT|  
|[C6235](../code-quality/c6235.md)|含邏輯 OR的非零常數|  
|[C6236](../code-quality/c6236.md)|含非零常數的邏輯 OR|  
|[C6237](../code-quality/c6237.md)|零與邏輯And遺失副作用|  
|[C6242](../code-quality/c6242.md)|強制區域回溯|  
|[C6248](../code-quality/c6248.md)|建立空的 DACL|  
|[C6250](../code-quality/c6250.md)|未發行的位址描述項|  
|[C6255](../code-quality/c6255.md)|未受保護使用的Alloca|  
|[C6258](../code-quality/c6258.md)|請使用來結束執行緒|  
|[C6259](../code-quality/c6259.md)|在Bitwise\-Or限制的切換的無作用程式碼|  
|[C6260](../code-quality/c6260.md)|為位元組算術的使用。|  
|[C6262](../code-quality/c6262.md)|過多的堆疊的使用方式|  
|[C6263](../code-quality/c6263.md)|在迴圈中使用 Alloca|  
|[C6268](../code-quality/c6268.md)|轉換而遺失的括號|  
|[C6269](../code-quality/c6269.md)|忽略的指標取值|  
|[C6270](../code-quality/c6270.md)|遺漏格式化函式中的浮點引數。|  
|[C6271](../code-quality/c6271.md)|格式化函式中的額外引數。|  
|[C6272](../code-quality/c6272.md)|格式化函式中的非浮點引數。|  
|[C6273](../code-quality/c6273.md)|格式化函式中的非整數引數。|  
|[C6274](../code-quality/c6274.md)|格式化函式中的非字元引數。|  
|[C6276](../code-quality/c6276.md)|無效的字串轉換。|  
|[C6277](../code-quality/c6277.md)|無效的 CreateProcess 呼叫|  
|[C6278](../code-quality/c6278.md)|新陣列的純量 delete 刪除不相符|  
|[C6279](../code-quality/c6279.md)|純量新的刪除陣列不相符|  
|[C6280](../code-quality/c6280.md)|記憶體的配置解除配置不相符|  
|[C6281](../code-quality/c6281.md)|位元關聯的優先順序|  
|[C6282](../code-quality/c6282.md)|指派取代測試|  
|[C6283](../code-quality/c6283.md)|原始Array\-New Scalar\-Delete不相符|  
|[C6284](../code-quality/c6284.md)|無效的格式化函式中的物件引數。|  
|[C6285](../code-quality/c6285.md)|常數的邏輯 OR|  
|[C6286](../code-quality/c6286.md)|非零邏輯或遺失的副作用 \(Side Effect\)。|  
|[C6287](../code-quality/c6287.md)|重複測試|  
|[C6288](../code-quality/c6288.md)|相互包含邏輯和為 False|  
|[C6289](../code-quality/c6289.md)|互斥邏輯或是 true。|  
|[C6290](../code-quality/c6290.md)|Logical\-Not Bitwise\-And 優先順序|  
|[C6291](../code-quality/c6291.md)|Logical\-Not Bitwise\-Or 優先順序。|  
|[C6292](../code-quality/c6292.md)|從最大值向上來做計數。|  
|[C6293](../code-quality/c6293.md)|從最小值來向下計數。|  
|[C6294](../code-quality/c6294.md)|從未執行迴圈主體|  
|[C6295](../code-quality/c6295.md)|無限迴圈。|  
|[C6296](../code-quality/c6296.md)|只執行一次的迴圈|  
|[C6297](../code-quality/c6297.md)|轉換為較大的大小的移位結果|  
|[C6299](../code-quality/c6299.md)|為布林值比較的 Bitfield|  
|[C6302](../code-quality/c6302.md)|無效的格式化函式中的字串引數。|  
|[C6303](../code-quality/c6303.md)|無效的格式化函式中的寬字元字串引數。|  
|[C6305](../code-quality/c6305.md)|不相符的大小和使用數目。|  
|[C6306](../code-quality/c6306.md)|不正確的變數引數函式呼叫。|  
|[C6308](../code-quality/c6308.md)|Realloc 遺漏。|  
|[C6310](../code-quality/c6310.md)|不合法的例外狀況篩選條件常數|  
|[C6312](../code-quality/c6312.md)|例外狀況繼續執行迴圈|  
|[C6314](../code-quality/c6314.md)|Bitwise\-Or的優先順序。|  
|[C6317](../code-quality/c6317.md)|不是否定補數。|  
|[C6318](../code-quality/c6318.md)|例外狀況繼續搜尋|  
|[C6319](../code-quality/c6319.md)|以逗號忽略|  
|[C6324](../code-quality/c6324.md)|非字串複本的字串比較|  
|[C6328](../code-quality/c6328.md)|可能的引數型別不符。|  
|[C6331](../code-quality/c6331.md)|VirtualFree 無效旗標|  
|[C6332](../code-quality/c6332.md)|VirtualFree 無效的參數。|  
|[C6333](../code-quality/c6333.md)|VirtualFree 無效的大小|  
|[C6335](../code-quality/c6335.md)|遺漏處理序控制代碼|  
|[C6381](../code-quality/c6381.md)|關閉資訊遺失。|  
|[C6383](../code-quality/c6383.md)|項目計數位元組計數緩衝區滿溢 \(Buffer Overrun\)|  
|[C6384](../code-quality/c6384.md)|指標大小小節。|  
|[C6385](../code-quality/c6385.md)|讀取滿溢|  
|[C6386](../code-quality/c6386.md)|撰寫滿溢|  
|[C6387](../code-quality/c6387.md)|無效的參數值。|  
|[C6388](../code-quality/c6388.md)|無效的參數值。|  
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
|[C6995](../code-quality/c6995.md)|無法儲存 XML的記錄檔。|  
|[C26100](../code-quality/c26100.md)|競爭情形|  
|[C26101](../code-quality/c26101.md)|不正確地使用連鎖作業|  
|[C26110](../code-quality/c26110.md)|持有鎖定的呼叫端失敗|  
|[C26111](../code-quality/c26111.md)|釋放鎖定的呼叫端失敗|  
|[C26112](../code-quality/c26112.md)|呼叫端不可以有任何鎖定。|  
|[C26115](../code-quality/c26115.md)|不會釋放鎖定。|  
|[C26116](../code-quality/c26116.md)|無法取得或維持鎖定|  
|[C26117](../code-quality/c26117.md)|釋放未保留的鎖定|  
|[C26140](../code-quality/c26140.md)|並行 SAL 附註錯誤|  
|[C28020](../code-quality/c28020.md)|這個呼叫的運算式不是 true。|  
|[C28021](../code-quality/c28021.md)|被附註的參數必須是指標。|  
|[C28022](../code-quality/c28022.md)|這個函式上的函式類別與定義所用之 typedef 上的函式類別不符:|  
|[C28023](../code-quality/c28023.md)|指派或傳遞的函式應該至少有一個的 \_Function\_class\_ 附註類別|  
|[C28024](../code-quality/c28024.md)|要指派的函式指標會以函式類別標記附註，該類別並未包含在函式類別中。|  
|[C28039](../code-quality/c28039.md)|實際參數的型別應要完全符合型別:|  
|[C28112](../code-quality/c28112.md)|透過連鎖的函式存取的變數必須透過連鎖的函式永遠存取。|  
|[C28113](../code-quality/c28113.md)|存取區域變數透過連鎖的函式|  
|[C28125](../code-quality/c28125.md)|必須在 try\/except 區塊內呼叫函式|  
|[C28137](../code-quality/c28137.md)|變數引數應改成 \(常值\) 常數。|  
|[C28138](../code-quality/c28138.md)|常數引數應改成變數。|  
|[C28159](../code-quality/c28159.md)|考慮使用另一個函式。|  
|[C28160](../code-quality/c28160.md)|錯誤附註|  
|[C28163](../code-quality/c28163.md)|絕對不能從 try\/except 區塊內呼叫函式|  
|[C28164](../code-quality/c28164.md)|正在將引數傳遞給需要物件指標 \(而非指標的指標\) 的函式:|  
|[C28182](../code-quality/c28182.md)|正在取值 NULL 指標。  指標含有與另一個指標的空值。|  
|[C28183](../code-quality/c28183.md)|引數可以是一個值，而且是在指標中找到之值的複本|  
|[C28193](../code-quality/c28193.md)|變數必須檢查的值。|  
|[C28196](../code-quality/c28196.md)|這個需求不是未滿足。\(運算式未評估為 true\)。|  
|[C28202](../code-quality/c28202.md)|非靜態成員之不合法的參考。|  
|[C28203](../code-quality/c28203.md)|類別成員的參考模稜兩可。|  
|[C28205](../code-quality/c28205.md)|Success\_ 或 \_On\_failure\_ 用於不合法的內容中:|  
|[C28206](../code-quality/c28206.md)|左運算元指向結構，請使用 '\-\>'。|  
|[C28207](../code-quality/c28207.md)|左運算元是結構，請使用 '.'。|  
|[C28209](../code-quality/c28209.md)|符號的宣告有衝突的宣告。|  
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
|[C28244](../code-quality/c28244.md)|函式的附註具有無法剖析的參數\/外部附註。|  
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
|[C28306](../code-quality/c28306.md)|在參數中的標記法是逐漸會捨棄的狀態。|  
|[C28307](../code-quality/c28307.md)|在參數中的標記法是逐漸會捨棄的狀態。|  
|[C28350](../code-quality/c28350.md)|附註描述條件上不適合的情況:|  
|[C28351](../code-quality/c28351.md)|附註描述條件中不可以使用動態值 \(變數\)。|  
|[CA1001](../Topic/CA1001:%20Types%20that%20own%20disposable%20fields%20should%20be%20disposable.md)|具有可處置欄位的型別應該是可處置的|  
|[CA1009](../code-quality/ca1009-declare-event-handlers-correctly.md)|正確宣告事件處理常式|  
|[CA1016](../code-quality/ca1016-mark-assemblies-with-assemblyversionattribute.md)|以 AssemblyVersionAttribute 標記組件|  
|[CA1033](../Topic/CA1033:%20Interface%20methods%20should%20be%20callable%20by%20child%20types.md)|介面方法應該要可以由子型別呼叫|  
|[CA1049](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)|擁有原生資源的型別應為可處置|  
|[CA1060](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)|將 P\/Invokes 移到 NativeMethods 類別|  
|[CA1061](../code-quality/ca1061-do-not-hide-base-class-methods.md)|不要隱藏基底類別方法|  
|[CA1063](../code-quality/ca1063-implement-idisposable-correctly.md)|必須正確實作 IDisposable|  
|[CA1065](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)|不要在非預期的位置中引發例外狀況|  
|[CA1301](../Topic/CA1301:%20Avoid%20duplicate%20accelerators.md)|避免使用重複的快速鍵|  
|[CA1400](../Topic/CA1400:%20P-Invoke%20entry%20points%20should%20exist.md)|P\/Invoke 進入點應該要存在|  
|[CA1401](../Topic/CA1401:%20P-Invokes%20should%20not%20be%20visible.md)|P\/Invokes 不應該為可見的|  
|[CA1403](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)|自動配置型別不應該是 COM 可見的|  
|[CA1404](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)|必須在 P\/Invoke 之後立即呼叫 GetLastError|  
|[CA1405](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md)|COM 可見型別的基底型別應該是 COM 可見|  
|[CA1410](../code-quality/ca1410-com-registration-methods-should-be-matched.md)|應該符合 COM 註冊方法|  
|[CA1415](../code-quality/ca1415-declare-p-invokes-correctly.md)|P\/Invokes 必須正確宣告|  
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|必須移除空的完成項|  
|[CA1900](../code-quality/ca1900-value-type-fields-should-be-portable.md)|實值型別欄位應該為可移植的|  
|[CA1901](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|P\/Invoke 宣告應該是可移植的|  
|[CA2002](../Topic/CA2002:%20Do%20not%20lock%20on%20objects%20with%20weak%20identity.md)|請勿鎖定具有弱式識別的物件|  
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|必須檢視 SQL 查詢中是否有安全性弱點|  
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|必須指定 P\/Invoke 字串引數的封送處理|  
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|必須檢查實值型別上的宣告式安全性|  
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|指標不應該為可見的|  
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|受保護型別不應公開欄位|  
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|方法安全性應該是型別的超集|  
|[CA2116](../Topic/CA2116:%20APTCA%20methods%20should%20only%20call%20APTCA%20methods.md)|APTCA 方法應該只呼叫 APTCA 方法|  
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|APTCA 型別應該只擴充 APTCA 基底型別|  
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|不要間接公開具有連結要求的方法|  
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|覆寫連結要求應該與基底相同|  
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|必須將有弱點的 finally 子句包裝在外層 try 中|  
|[CA2126](../Topic/CA2126:%20Type%20link%20demands%20require%20inheritance%20demands.md)|必須同時具有型別連結要求和繼承要求|  
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|安全性關鍵型別可能未參與型別等價|  
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|預設建構函式至少必須和基底型別的預設建構函式一樣關鍵|  
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|委派必須繫結至透明度一致的方法|  
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|覆寫基底方法時，方法必須保持一致的透明度|  
|[CA2137](../Topic/CA2137:%20Transparent%20methods%20must%20contain%20only%20verifiable%20IL.md)|透明方法必須只包含可驗證的 IL|  
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|透明方法不可以使用 SuppressUnmanagedCodeSecurity 屬性呼叫方法|  
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|透明程式碼不可以參考安全性關鍵項目|  
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|透明方法不可以滿足 LinkDemand|  
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|型別至少必須和基底型別與介面一樣關鍵|  
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|透明的方法不可以使用安全性判斷提示|  
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|透明方法不可以呼叫機器碼|  
|[CA2200](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)|請重新擲回以保存堆疊詳細資料|  
|[CA2202](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)|不要多次處置物件|  
|[CA2207](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)|必須初始化實值型別的靜態欄位內嵌|  
|[CA2212](../code-quality/ca2212-do-not-mark-serviced-components-with-webmethod.md)|不要以 WebMethod 標記 Serviced 元件|  
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|可處置的欄位應該受到處置|  
|[CA2214](../Topic/CA2214:%20Do%20not%20call%20overridable%20methods%20in%20constructors.md)|不要呼叫建構函式中的可覆寫方法|  
|[CA2216](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)|可處置型別應該宣告完成項|  
|[CA2220](../code-quality/ca2220-finalizers-should-call-base-class-finalizer.md)|完成項應該呼叫基底類別完成項|  
|[CA2229](../code-quality/ca2229-implement-serialization-constructors.md)|請實作序列化建構函式|  
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|覆寫 ValueType.Equals 時必須一併多載等號比較運算子|  
|[CA2232](../code-quality/ca2232-mark-windows-forms-entry-points-with-stathread.md)|以 STAThread 標記 Windows Form 進入點|  
|[CA2235](../code-quality/ca2235-mark-all-non-serializable-fields.md)|必須標記所有不可序列化的欄位|  
|[CA2236](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)|必須呼叫 ISerializable 型別上的基底類別方法|  
|[CA2237](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)|必須以 SerializableAttribute 標記 ISerializable 型別|  
|[CA2238](../code-quality/ca2238-implement-serialization-methods-correctly.md)|請正確實作序列化方法|  
|[CA2240](../Topic/CA2240:%20Implement%20ISerializable%20correctly.md)|必須正確實作 ISerializable|  
|[CA2241](../code-quality/ca2241-provide-correct-arguments-to-formatting-methods.md)|必須提供格式化方法的正確引數|  
|[CA2242](../code-quality/ca2242-test-for-nan-correctly.md)|必須正確測試 NaN|