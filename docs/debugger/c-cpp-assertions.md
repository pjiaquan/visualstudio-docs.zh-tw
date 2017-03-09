---
title: "C/C++ 判斷提示 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "_DEBUG 巨集"
  - "ASSERT 巨集"
  - "判斷提示已失敗對話方塊"
  - "判斷提示"
  - "判斷提示, 副作用"
  - "呼叫堆疊視窗, 判斷提示失敗"
  - "偵錯 [C++], 判斷提示"
  - "偵錯 [MFC], 判斷提示"
  - "錯誤 [C++], 依判斷提示來捕捉"
  - "失敗, 尋找位置"
  - "檢查結果"
  - "結果, 檢查"
  - "測試, 依據判斷提示陳述式的錯誤狀況"
  - "VERIFY 巨集"
ms.assetid: 2d7b0121-71aa-414b-bbb6-ede1093d0bfc
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# C/C++ 判斷提示
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

判斷提示陳述式指定想要在您的程式中的一個點，則為 true 的條件。  如果該條件不為真，表示判斷提示失敗，會中斷程式執行，以及[判斷提示已失敗對話方塊](../debugger/assertion-failed-dialog-box.md)就會出現。  
  
 Visual C\+\+ 的支援以下列建構函式為基礎的判斷提示陳述式：  
  
-   MFC 程式的 MFC 判斷提示。  
  
-   [ATLASSERT](../Topic/ATLASSERT.md) 使用 ATL 的程式  
  
-   使用 C 執行階段程式庫的程式的 CRT 判斷提示。  
  
-   ANSI [宣告函式](/visual-cpp/c-runtime-library/reference/assert-macro-assert-wassert)其他 C\/c \+ \+ 程式。  
  
 您可以使用判斷提示來捕捉邏輯錯誤，檢查作業的結果，測試應該已處理的錯誤情況。  
  
##  <a name="BKMK_In_this_topic"></a> 本主題中  
 [判斷提示的運作方式](#BKMK_How_assertions_work)  
  
 [在偵錯和發行組建的判斷提示](#BKMK_Assertions_in_Debug_and_Release_builds)  
  
 [使用判斷提示的副作用](#BKMK_Side_effects_of_using_assertions)  
  
 [CRT 判斷提示](#BKMK_CRT_assertions)  
  
 [MFC 判斷提示](#BKMK_MFC_assertions)  
  
-   [MFC ASSERT_VALID 和 CObject::AssertValid](#BKMK_MFC_ASSERT_VALID_and_CObject__AssertValid)  
  
-   [AssertValid 的限制](#BKMK_Limitations_of_AssertValid)  
  
 [使用判斷提示](#BKMK_Using_assertions)  
  
-   [攔截邏輯錯誤](#BKMK_Catching_logic_errors)  
  
-   [檢查結果](#BKMK_Checking_results_)  
  
-   [尋找未處理的錯誤](#BKMK_Testing_error_conditions_)  
  
##  <a name="BKMK_How_assertions_work"></a> 判斷提示的運作方式  
 當偵錯工具暫停因為 MFC 或 C 執行階段程式庫判斷提示時，然後如果來源是可供使用，偵錯工具會巡覽至發生判斷提示的原始程式檔中的點。  判斷提示訊息會出現在兩個[輸出&#93; 視窗](../ide/reference/output-window.md) 和 **判斷提示已失敗**對話方塊。  您可以將複製的判斷提示訊息**輸出**視窗至文字視窗，如果您想要儲存它供未來參考。  **輸出**視窗可能包含其他錯誤訊息。  這些訊息仔細地檢查，因為它們提供了造成判斷提示失敗的線索。  
  
 使用判斷提示來在開發期間偵測到錯誤。  一般而言，使用每個假設一個判斷提示。  例如，如果您假設引數不是 NULL，使用判斷提示來測試該假設。  
  
 [本主題中](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Assertions_in_Debug_and_Release_builds"></a> 在偵錯和發行組建的判斷提示  
 判斷提示陳述式編譯時，才`_DEBUG`所定義。  否則，編譯器會判斷提示視為 null 陳述式。  因此，判斷提示陳述式對造成沒有的額外負荷，或效能成本在最終發行程式中，並可讓您避免使用`#ifdef`指示詞。  
  
##  <a name="BKMK_Side_effects_of_using_assertions"></a> 使用判斷提示的副作用  
 當您的程式碼加入判斷提示時，請確定判斷提示不會有副作用。  例如，請考慮下列判斷提示的修改`nM`值：  
  
```  
ASSERT(nM++ > 0); // Don't do this!  
  
```  
  
 因為`ASSERT`在您的程式的發行版本中無法評估運算式  `nM`偵錯和發行版本中會有不同的值。  若要避免這個問題，在 MFC 中的，您可以使用[驗證](../Topic/VERIFY.md) 巨集，而不是  `ASSERT`.   `VERIFY`評估所有版本中的運算式，但不會檢查在發行版本的結果。  
  
 是尤其要特別注意使用判斷提示陳述式中的函式呼叫，因為評估函式可以有未預期的副作用。  
  
```  
ASSERT ( myFnctn(0)==1 ) // unsafe if myFnctn has side effects  
VERIFY ( myFnctn(0)==1 ) // safe  
```  
  
 `VERIFY`呼叫  `myFnctn`在偵錯和發行版本中，所以是可接受的使用。  不過，使用`VERIFY`加諸在發行版本中不必要的函式呼叫的負荷。  
  
 [本主題中](#BKMK_In_this_topic)  
  
##  <a name="BKMK_CRT_assertions"></a> CRT 判斷提示  
 CRTDBG。H 標頭檔定義 [\_assert 狀況和 \_asserte 的判斷提示巨集](/visual-cpp/c-runtime-library/reference/assert-asserte-assert-expr-macros)的判斷提示檢查。  
  
|巨集|結果|  
|--------|--------|  
|`_ASSERT`|如果指定的運算式評估為 FALSE，檔名和行號的 `_ASSERT`.|`_ASSERTE`|  
|`_ASSERTE`|與相同 `_ASSERT`，再加上運算式，判斷提示的字串表示。|  
  
 `_ASSERTE`因為它會報告已判斷提示是 FALSE 的運算式，則是功能更強大。  這可能是不足以識別問題，而不參照到的原始碼。  然而，您的應用程式的偵錯版本會包含每個運算式使用字串常數 `_ASSERTE`.  如果您使用許多`_ASSERTE`巨集，這些字串運算式會佔用大量的記憶體。  如果這證實會產生問題，使用`_ASSERT`以節省記憶體。  
  
 當`_DEBUG`定義，  `_ASSERTE`巨集定義，如下所示：  
  
```  
#define _ASSERTE(expr) \  
   do { \  
      if (!(expr) && (1 == _CrtDbgReport( \  
         _CRT_ASSERT, __FILE__, __LINE__, #expr))) \  
         _CrtDbgBreak(); \  
   } while (0)  
```  
  
 如果已判斷提示的運算式評估為 FALSE，  [\_CrtDbgReport](/visual-cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw) 呼叫以報告 \(根據預設，使用訊息對話方塊\) 的判斷提示失敗。  如果您選擇**再試一次** 在 \[訊息\] 對話方塊中，  `_CrtDbgReport`，則傳回 1 和  `_CrtDbgBreak`透過偵錯工具會呼叫  `DebugBreak`.  
  
### 檢查堆積損毀  
 下列範例會使用 [\_CrtCheckMemory](/visual-cpp/c-runtime-library/reference/crtcheckmemory) 檢查堆積損毀：  
  
```  
_ASSERTE(_CrtCheckMemory());  
```  
  
### 檢查指標有效性  
 下列範例會使用 [\_CrtIsValidPointer](/visual-cpp/c-runtime-library/reference/crtisvalidpointer) 來檢查指定的記憶體範圍是否有效來讀取或寫入。  
  
```  
_ASSERTE(_CrtIsValidPointer( address, size, TRUE );  
```  
  
 下列範例會使用 [\_CrtIsValidHeapPointer](/visual-cpp/c-runtime-library/reference/crtisvalidheappointer) 來驗證指標指向本機的堆積中的記憶體 \(堆積所建立和管理這個執行個體的 C 執行階段程式庫 — DLL 可以擁有自己的程式庫，因此它自己的堆積，外部應用程式的堆集的執行個體\)。  這個判斷提示就會攔截不只 null 或超出範圍的位址，但也靜態變數、 堆疊變數和任何其他非本機記憶體的指標。  
  
```  
_ASSERTE(_CrtIsValidPointer( myData );  
```  
  
### 檢查記憶體區塊  
 下列範例會使用 [\_CrtIsMemoryBlock](/visual-cpp/c-runtime-library/reference/crtismemoryblock) ，請確認記憶體區塊本機的堆積中，且具有有效的區塊型別。  
  
```  
_ASSERTE(_CrtIsMemoryBlock (myData, size, &requestNumber, &filename, &linenumber));  
```  
  
 [本主題中](#BKMK_In_this_topic)  
  
##  <a name="BKMK_MFC_assertions"></a> MFC 判斷提示  
 MFC 定義 [ASSERT](../Topic/ASSERT%20\(MFC\).md) 的巨集，判斷提示檢查。  它也會定義`MFC ASSERT_VALID`和  `CObject::AssertValid`進行檢查的內部狀態的方法  `CObject`\-衍生物件。  
  
 如果引數的 MFC  `ASSERT`巨集評估成零或 false，巨集中止程式執行，系統會通知使用者 ； 否則，會繼續執行。  
  
 判斷提示失敗時，訊息對話方塊顯示原始程式檔和行號的判斷提示的名稱。  如果您在對話方塊中選擇 \[重試\] 方塊中，呼叫 [AfxDebugBreak](../Topic/AfxDebugBreak%20\(MFC\).md) 會使偵錯工具中斷執行。  此時，您可以檢查呼叫堆疊，並使用其他的偵錯工具設施，來決定 \[判斷提示失敗的原因。  如果您已啟用[時間僅偵錯](../debugger/just-in-time-debugging-in-visual-studio.md)，且偵錯工具已經不在執行，\[\] 對話方塊可以啟動偵錯工具。  
  
 下列範例示範如何使用`ASSERT`來檢查函式的傳回值：  
  
```  
int x = SomeFunc(y);  
ASSERT(x >= 0);   //  Assertion fails if x is negative  
```  
  
 您可以使用判斷提示與 [IsKindOf](../Topic/CObject::IsKindOf.md) 提供型別檢查函數的引數的函式：  
  
```  
ASSERT( pObject1->IsKindOf( RUNTIME_CLASS( CPerson ) ) );  
```  
  
 `ASSERT`巨集，會產生發行版本中的沒有程式碼。  如果您要評估的版本中的運算式，請使用[驗證](../Topic/VERIFY.md)而不是判斷提示的巨集。  
  
###  <a name="BKMK_MFC_ASSERT_VALID_and_CObject__AssertValid"></a> MFC ASSERT\_VALID 和 CObject::AssertValid  
 [CObject::AssertValid](../Topic/CObject::AssertValid.md) 方法會提供執行階段會檢查物件的內部狀態。  雖然您不需要覆寫`AssertValid`時衍生您的類別，從  `CObject`，您可以讓您的類別更可靠這麼。  `AssertValid`應該在所有物件的成員變數，以確認它們包含有效的值上都執行判斷提示。  例如，它應該檢查指標成員變數不是 NULL。  
  
 下列範例示範如何宣告`AssertValid`函式：  
  
```  
class CPerson : public CObject  
{  
protected:  
    CString m_strName;  
    float   m_salary;  
public:  
#ifdef _DEBUG  
    // Override  
    virtual void AssertValid() const;  
#endif  
    // ...  
};  
  
```  
  
 當您覆寫 `AssertValid`、 呼叫的基底類別版本  `AssertValid`在執行您自己檢查之前。  然後如下所示，請檢查您的衍生類別的唯一成員使用 ASSERT 巨集：  
  
```  
#ifdef _DEBUG  
void CPerson::AssertValid() const  
{  
    // Call inherited AssertValid first.  
    CObject::AssertValid();  
  
    // Check CPerson members...  
    // Must have a name.  
    ASSERT( !m_strName.IsEmpty());  
    // Must have an income.  
    ASSERT( m_salary > 0 );  
}  
#endif  
  
```  
  
 如果任何成員變數儲存物件時，您可以使用`ASSERT_VALID`巨集，以測試其內部的有效性 \(如果它們的類別覆寫  `AssertValid`\)。  
  
 例如，假設類別 `CMyData`，哪些商店  [CObList](/visual-cpp/mfc/reference/coblist-class) 在它的成員變數的其中一個。   `CObList`變數，   `m_DataList`，存放一堆  `CPerson`物件。  縮寫的宣告`CMyData`看起來像這樣：  
  
```  
class CMyData : public CObject  
{  
    // Constructor and other members ...  
    protected:  
        CObList* m_pDataList;  
    // Other declarations ...  
    public:  
#ifdef _DEBUG  
        // Override:  
        virtual void AssertValid( ) const;  
#endif  
    // And so on ...  
};  
  
```  
  
 `AssertValid`中覆寫  `CMyData`看起來像這樣：  
  
```  
#ifdef _DEBUG  
void CMyData::AssertValid( ) const  
{  
    // Call inherited AssertValid.  
    CObject::AssertValid( );  
    // Check validity of CMyData members.  
    ASSERT_VALID( m_pDataList );  
    // ...  
}  
#endif  
  
```  
  
 `CMyData`使用  `AssertValid`機制來測試物件儲存在其資料成員的有效性。  覆寫`AssertValid`的  `CMyData`叫用  `ASSERT_VALID`自己 m\_pDataList 成員變數的巨集。  
  
 有效性測試不會停止在此層級因為類別`CObList`也會覆寫  `AssertValid`.  這個覆寫執行額外的有效性測試清單的內部狀態。  因此，有效測試上`CMyData`物件會導致預存的內部狀態的額外的有效性測試  `CObList`清單物件。  
  
 透過一些工作，您可以為加入有效性測試`CPerson`也儲存在\] 清單中的物件。  您無法衍生類別`CPersonList`的  `CObList`而覆寫  `AssertValid`.  在覆寫時，您會呼叫 `CObject::AssertValid`，然後逐一查看清單中，呼叫  `AssertValid`上每個  `CPerson`清單中儲存的物件。   `CPerson`已經本主題開頭所示的類別會覆寫  `AssertValid`.  
  
 當您建置偵錯時，這是強大的機制。  當您接下來建置發行時，此機制會自動關閉。  
  
###  <a name="BKMK_Limitations_of_AssertValid"></a> AssertValid 的限制  
 觸發判斷提示表示物件一定是壞，而且會停止執行。  然而，缺乏判斷提示表示只沒有發現問題，但不是保證物件是很好。  
  
 [本主題中](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Using_assertions"></a> 使用判斷提示  
  
###  <a name="BKMK_Catching_logic_errors"></a> 攔截邏輯錯誤  
 您可以設定必須根據您的程式邏輯，則為 true 的條件判斷提示。  除非發生邏輯錯誤，判斷提示就會有任何作用。  
  
 例如，假設您模擬瓦斯分子中一種容器和變數`numMols`代表分子總數。  這個數字不能小於零，因此您可以包含像這樣的 MFC 判斷提示陳述式：  
  
```  
ASSERT(numMols >= 0);  
  
```  
  
 或者，您可能會包含像這樣的 CRT 判斷提示：  
  
```  
_ASSERT(numMols >= 0);  
```  
  
 如果您的程式運作正常，這些陳述式會執行任何動作。  如果邏輯錯誤造成`numMols` 小於零，不過，判斷提示暫停程式執行，並顯示  [判斷提示已失敗對話方塊](../debugger/assertion-failed-dialog-box.md).  
  
 [本主題中](#BKMK_In_this_topic)  
  
###  <a name="BKMK_Checking_results_"></a> 檢查結果  
 判斷提示是有價值的測試的作業的結果可能不明顯的快速視覺檢視。  
  
 例如，請考慮下列的程式碼，更新變數`iMols`所指的連結清單的內容為基礎  `mols`：  
  
```  
/* This code assumes that type has overloaded the != operator  
 with const char *   
It also assumes that H2O is somewhere in that linked list.   
Otherwise we'll get an access violation... */  
while (mols->type != "H2O")  
{  
 iMols += mols->num;  
 mols = mols->next;  
}  
ASSERT(iMols<=numMols); // MFC version  
_ASSERT(iMols<=numMols); // CRT version  
```  
  
 分子數計算`iMols`都必須小於或等於總數分子，   `numMols`.  迴圈的視覺檢視不會顯示這一定會大小寫，所以判斷提示陳述式用於迴圈之後來測試該條件。  
  
 [本主題中](#BKMK_In_this_topic)  
  
###  <a name="BKMK_Testing_error_conditions_"></a> 尋找未處理的錯誤  
 您可以使用判斷提示在程式碼中測試錯誤條件，在某個點也就是其中的任何錯誤就應該處理。  在下列範例中，一個圖形常式會傳回錯誤代碼或成功的零。  
  
```  
myErr = myGraphRoutine(a, b);  
  
/* Code to handle errors and  
   reset myErr if successful */  
  
ASSERT(!myErr); -- MFC version  
_ASSERT(!myErr); -- CRT version  
```  
  
 如果錯誤處理程式碼正常運作，錯誤應該會處理和`myErr`重設為零之前，判斷提示就會到達。  如果`myErr`有另一個值，判斷提示失敗，則程式會中止，  [判斷提示已失敗對話方塊](../debugger/assertion-failed-dialog-box.md)就會出現。  
  
 判斷提示陳述式沒有替代的錯誤處理程式碼，不過。  下列範例會顯示在最後發行程式碼中將造成判斷提示陳述式：  
  
```  
myErr = myGraphRoutine(a, b);  
  
/* No Code to handle errors */  
  
ASSERT(!myErr); // Don't do this!  
_ASSERT(!myErr); // Don't do this, either!  
```  
  
 這段程式碼依賴判斷提示陳述式，來處理錯誤狀況。  錯誤的任何程式碼所傳回的結果是，  `myGraphRoutine`會在最後發行程式碼中未處理。  
  
 [本主題中](#BKMK_In_this_topic)  
  
## 請參閱  
 [偵錯工具安全性](../debugger/debugger-security.md)   
 [偵錯機器碼](../debugger/debugging-native-code.md)   
 [Managed 程式碼中的判斷提示](../debugger/assertions-in-managed-code.md)