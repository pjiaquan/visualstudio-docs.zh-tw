---
title: "最佳作法和範例 (SAL) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 666276fb-99c2-4dc9-8bac-d74861c203ea
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 最佳作法和範例 (SAL)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

以下是一些方式充分利用原始程式碼附註語言 \(SAL\) 並避免一些常見問題。  
  
## \_In\_  
 如果函式應該寫入項目，請使用`_Inout_` ，而不是 `_In_`。  這特別有關的會從舊的巨集自動化轉換成 SAL。  在 SAL 之前，許多程式設計人員使用巨集當做註解，巨集名為 `IN`、 `OUT` `IN_OUT`或這些名稱的變數。  雖然我們建議您將這些巨集將 SAL，我們也敦促您謹慎，當您將它們轉換時，因為程式碼已經變更，原始的原型被撰寫，而舊巨集可能不會反映程式碼。  特別小心 `OPTIONAL` 註解巨集，因為它常常被不正確地放置 \(例如，反向的逗號\)。  
  
```cpp  
  
// Incorrect  
void Func1(_In_ int *p1)  
{  
    if (p1 == NULL)   
        return;  
  
    *p1 = 1;  
}  
  
// Correct  
void Func2(_Inout_ PCHAR p1)  
{  
    if (p1 == NULL)   
        return;  
  
    *p1 = 1;  
}  
  
```  
  
## \_opt\_  
 如果呼叫端在 null 指標、使用 `_In_` 或 `_Out_`而不是 `_In_opt_` 或 `_Out_opt_`。  這會使用事件來檢查其參數並傳回錯誤的函式，如果是空的，則不應該。  雖然有功能會檢查它的非 null 參數和傳回適當是很好的方式編碼慣例，並不表示參數附註可以是任意型別 \(\_*Xxx*\_opt\_\)。  
  
```cpp  
  
// Incorrect  
void Func1(_Out_opt_ int *p1)  
{  
    *p = 1;  
}  
  
// Correct  
void Func2(_Out_ int *p1)  
{  
    *p = 1;  
}  
  
```  
  
## \_Pre\_defensive\_ 和 \_Post\_defensive\_  
 如果函式出現在信任界限，建議您使用 `_Pre_defensive_` 附註。這個「抵禦」修飾詞修改特定附註表示，在呼叫時，應確實地檢查介面，不過，在實作主體應該假設，無效參數可傳遞。  在這種情況下， `_In_ _Pre_defensive_` 優於信任界限表示，不過，呼叫端將會發生錯誤，則在嘗試將 null，會分析函式主體，就如同參數可能 null，嘗試取值指標，而不需先檢查 null 會加上旗標。`_Post_defensive_` 附註也用於回呼，這個信任的一方假設是呼叫端，不受信任的程式碼是呼叫程式碼。  
  
## \_Out\_writes\_  
 以下範例將說明 `_Out_writes_` 普遍的濫用。  
  
```cpp  
  
// Incorrect  
void Func1(_Out_writes_(size) CHAR *pb,   
    DWORD size  
);  
  
```  
  
 附註 `_Out_writes_` 表示您擁有緩衝區。  它會在匯出排列 `cb` 配置位元組，其中第一個位元組初始化。  這個標記法的內容不完全是 false，而且表示配置的大小會很有用。  但是，它不會說出呼叫多少個由函式進行初始化的項目。  
  
 下一個範例示範三個正確方式完整指定緩衝區的初始化區段的實際大小。  
  
```cpp  
  
// Correct  
void Func1(_Out_writes_to_(size, *pCount) CHAR *pb,   
    DWORD size,  
    PDWORD pCount  
);  
  
void Func2(_Out_writes_all_(size) CHAR *pb,   
    DWORD size  
);  
  
void Func3(_Out_writes_(size) PSTR pb,   
    DWORD size  
);  
  
```  
  
## \_Out\_ PSTR  
 使用 `_Out_ PSTR` 幾乎一定是錯誤的。  這會解譯對字元的頂點緩衝區的輸出參數和它是以 null 結束的。  
  
```cpp  
  
// Incorrect  
void Func1(_Out_ PSTR pFileName, size_t n);  
  
// Correct  
void Func2(_Out_writes_(n) PSTR wszFileName, size_t n);  
  
```  
  
 `_In_ PCSTR` 的附註是普遍和有用的。  它所指向的項目都將以 null 結尾的字串，因為 `_In_` 前置條件允許 null 結尾字串的辨識。  
  
## \_In\_ WCHAR\* p  
 `_In_ WCHAR* p` 會擁有指向一個字元的輸入指標 `p` 。  不過，在許多情況下，這可能就不是預期的規格。  相反地，原因可能是一個 Null 終端陣列的規格，若要這樣做，請使用 `_In_ PWSTR`。  
  
```cpp  
  
// Incorrect  
void Func1(_In_ WCHAR* wszFileName);  
  
// Correct  
void Func2(_In_ PWSTR wszFileName);  
  
```  
  
 遺漏 NULL 結尾適當的規格是很常見的。  如下列範例所示，使用適當的 `STR` 版本取代型別。  
  
```cpp  
  
// Incorrect  
BOOL StrEquals1(_In_ PCHAR p1, _In_ PCHAR p2)  
{  
    return strcmp(p1, p2) == 0;  
}  
  
// Correct  
BOOL StrEquals2(_In_ PSTR p1, _In_ PSTR p2)  
{  
    return strcmp(p1, p2) == 0;  
}  
  
```  
  
## \_Out\_range\_  
 如果參數為指標，而您想要表示元素值的範圍所指向的指標，請使用 `_Deref_out_range_` 而不是 `_Out_range_`。  在下列範例中，範圍的\*pcbFilled 被表示，而不是 pcbFilled。  
  
```cpp  
  
// Incorrect  
void Func1(  
    _Out_writes_bytes_to_(cbSize, *pcbFilled) BYTE *pb,   
    DWORD cbSize,   
    _Out_range_(0, cbSize) DWORD *pcbFilled  
);  
  
// Correct  
void Func2(  
    _Out_writes_bytes_to_(cbSize, *pcbFilled) BYTE *pb,   
    DWORD cbSize,   
    _Deref_out_range_(0, cbSize) _Out_ DWORD *pcbFilled   
);  
  
```  
  
 `_Deref_out_range_(0, cbSize)` 沒有針對某些工具完全是必要的，因為可以從 `_Out_writes_to_(cbSize,*pcbFilled)`推斷，不過，以求完整性所示。  
  
## \_When\_ 的錯誤內容。  
 另一個常見錯誤是前置條件的使用後狀態評估。  在下列範列中，`_Requires_lock_held_` 是前置條件。  
  
```cpp  
  
// Incorrect  
_When_(return == 0, _Requires_lock_held_(p->cs))  
int Func1(_In_ MyData *p, int flag);  
  
// Correct  
_When_(flag == 0, _Requires_lock_held_(p->cs))  
int Func2(_In_ MyData *p, int flag);  
  
```  
  
 在目前狀態的運算式 `result` 參考無法適用後狀態值。  
  
## \_Success\_設定為 true。  
 如果函式成功，則傳回為非零的值，請使用 `return != 0` 做為成功情況而不是 `return == TRUE`。  非零不一定表示等於編譯器為 `TRUE`提供的實際值。  對 `_Success_` 的參數是運算式，因此，下列運算式會評估為相等: `return != 0`、 `return != false`、 `return != FALSE`和 `return` 沒有參數或比較。  
  
```cpp  
  
// Incorrect  
_Success_(return == TRUE, _Acquires_lock_(*lpCriticalSection))  
BOOL WINAPI TryEnterCriticalSection(  
  _Inout_ LPCRITICAL_SECTION lpCriticalSection  
);  
  
// Correct  
_Success_(return != 0, _Acquires_lock_(*lpCriticalSection))  
BOOL WINAPI TryEnterCriticalSection(  
  _Inout_ LPCRITICAL_SECTION lpCriticalSection  
);  
  
```  
  
## 變數參考。  
 對參考變數， SAL 舊版使用隱含的指標為附註的目標且需要 `__deref` 加入附加至參考變數的附註。  這個版本使用物件並不需要其他附加的 `_Deref_`。  
  
```cpp  
  
// Incorrect  
void Func1(  
    _Out_writes_bytes_all_(cbSize) BYTE *pb,   
    _Deref_ _Out_range_(0, 2) _Out_ DWORD &cbSize  
);  
  
// Correct  
void Func2(  
    _Out_writes_bytes_all_(cbSize) BYTE *pb,   
    _Out_range_(0, 2) _Out_ DWORD &cbSize  
);  
  
```  
  
## 在傳回值的附註  
 下列範例會示範一個常見問題而導致值附註。  
  
```cpp  
  
// Incorrect  
_Out_opt_ void *MightReturnNullPtr1();  
  
// Correct  
_Ret_maybenull_ void *MightReturnNullPtr2();  
  
```  
  
 在此範例中， `_Out_opt_` 指標可能是 null 做為此前置條件的一部分。  不過，前提是不可套用至傳回值。  在這個案例中，正確的附註是 `_Ret_maybenull_`。  
  
## 請參閱  
 [使用 SAL 註釋減少 C\/C\+\+ 程式碼的缺失](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [了解 SAL](../code-quality/understanding-sal.md)   
 [註釋函式參數和傳回值](../code-quality/annotating-function-parameters-and-return-values.md)   
 [註釋函式行為](../code-quality/annotating-function-behavior.md)   
 [註釋結構和類別](../code-quality/annotating-structs-and-classes.md)   
 [註釋鎖定行為](../code-quality/annotating-locking-behavior.md)   
 [指定套用註釋的時機和位置](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [內建函式](../code-quality/intrinsic-functions.md)