---
title: "註釋函式行為 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_On_failure_"
  - "_Return_type_success_"
  - "_Always_"
  - "_Maybe_raises_SEH_exception_"
  - "_Raises_SEH_exception_"
  - "_Called_from_function_class_"
  - "_Function_class_"
  - "_Must_inspect_result_"
  - "_Success_"
  - "_Check_return_"
  - "_Use_decl_annotations_"
ms.assetid: c0aa268d-6fa3-4ced-a8c6-f7652b152e61
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# 註釋函式行為
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

除了附註 [函式參數和傳回值](../code-quality/annotating-function-parameters-and-return-values.md)之外，您還可以標註整體函式的屬性。  
  
## 函式附註  
 下列附註適用於整個函式，說明它的行為或什麼是預期為 true。  
  
|註釋|說明|  
|--------|--------|  
|`_Called_from_function_class_(name)`|不適合單獨代表;相反地，它是所使用的述詞與 `_When_` 標記法。  如需詳細資訊，請參閱[指定套用註釋的時機和位置](../code-quality/specifying-when-and-where-an-annotation-applies.md)。<br /><br /> `name` 參數是也出現在某些函式的宣告的 `_Function_class_` 標記法的任意字串。  `_Called_from_function_class_` 會傳回零，如果目前的分析函式加註使用 `name`有相同的值則為 `_Function_class_` ;否則，會傳回零。|  
|`_Check_return_`|附註的傳回值，並指出呼叫端應檢查它。  如果此函式位在 null 內容被呼叫，這個檢查器會報告錯誤。|  
|`_Function_class_(name)`|`name` 參數是使用者所設定的選擇性字串。它會存在於不同於其他命名空間的命名空間。  函式、函式指標或 \(最有用的方式\) 函式指標型別可能會被指定為屬於一或多個函式類別。|  
|`_Raises_SEH_exception_`|附註一定會引發一個結構化例外狀況處理常式 \(SEH\) 例外狀況的函式 \(由 `_When_` 和 `_On_failure_` 條件所限制\)。  如需詳細資訊，請參閱[指定套用註釋的時機和位置](../code-quality/specifying-when-and-where-an-annotation-applies.md)。|  
|`_Maybe_raises_SEH_exception_`|附註一個可以選擇性地引發 SEH 例外狀況的函式 \(由 `_When_` 和 `_On_failure_` 條件所限制\)。|  
|`_Must_inspect_result_`|附註任何輸出值，包括傳回值、參數和全域變數。如果在標註物件的值之後尚未簽出，此分析器會報告錯誤。「檢查包括是否用於條件運算式，指定給輸出參數或全域，或傳遞做為參數。對於傳回值， `_Must_inspect_result_`表示 `_Check_return_`。|  
|`_Use_decl_annotations_`|在函式定義 \(也稱為函式主體\) 使用在附註的清單表單的標題。 當使用 `_Use_decl_annotations_` 時，會出現在相同函式的範圍標題使用的附註，如同它們也存在具有 `_Use_decl_annotations_` 標記法的定義。|  
  
## 成功或失敗附註  
 函式會失敗，，和，當它時，它的結果可能不完整或與結果不同，因為函式成功時。下列清單中的附註提供方式表示失敗行為。若要使用這些標記法中的任何一個，您必須啟用他們以能夠決定成功，因此需要 `_Success_` 附註。請注意 `NTSTATUS` 和 `HRESULT` 已指定 `_Success_` 附註會建置到它們;不過，因此，如果您在 `NTSTATUS` 或 `HRESULT`中指定 `_Success_` 標記法，它就會覆寫內建註釋。  
  
|註釋|說明|  
|--------|--------|  
|`_Always_(anno_list)`|與 `anno_list _On_failure_(anno_list)` 一樣；也就是無論函式是否成功，在 `anno_list` 的附註都會套用。|  
|`_On_failure_(anno_list)`|藉由在 typedef 的 `_Return_type_success_` 將使用，只有在 `_Success_` 也用來明確加註函式任一或隱含。  當 `_On_failure_` 標記法是存在於函式參數或傳回值時，在 anno \(\) 的每個附註的 `anno_list` 行為，就如同在實作 `_When_(!expr, anno)`， `expr` 是參數所需 `_Success_` 附註。  這表示所有後續狀況 `_Success_` 的隱含應用程式不適用 `_On_failure_`。|  
|`_Return_type_success_(expr)`|套用到 typedef。  傳回指示該型別，並沒有明確 `_Success_` 的所有函式加註，視為具有 `_Success_(expr)`。  `_Return_type_success_` 在函式或函式指標 typedef 無法使用。|  
|`_Success_(expr)`|`expr` 是產生右值的運算式。  當 `_Success_` 標記法是存在於函式宣告或定義，在函式每個標記法 \(`anno`\) 時，並加上狀況，就如同在實作 `_When_(expr, anno)`的行為。  在函式 \(而非其參數或傳回型別\)的`_Success_` 附註可能只能透過取得。  最多在函式只有一個 `_Success_` 附註，因此，它不可以是任何 `_When_`、 `_At_`或 `_Group_`內。  如需詳細資訊，請參閱[指定套用註釋的時機和位置](../code-quality/specifying-when-and-where-an-annotation-applies.md)。|  
  
## 請參閱  
 [使用 SAL 註釋減少 C\/C\+\+ 程式碼的缺失](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [了解 SAL](../code-quality/understanding-sal.md)   
 [註釋函式參數和傳回值](../code-quality/annotating-function-parameters-and-return-values.md)   
 [註釋結構和類別](../code-quality/annotating-structs-and-classes.md)   
 [註釋鎖定行為](../code-quality/annotating-locking-behavior.md)   
 [指定套用註釋的時機和位置](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [內建函式](../code-quality/intrinsic-functions.md)   
 [最佳作法和範例](../code-quality/best-practices-and-examples-sal.md)