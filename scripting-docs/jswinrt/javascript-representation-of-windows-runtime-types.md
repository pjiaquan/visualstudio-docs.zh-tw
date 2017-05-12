---
title: "以 JavaScript 表示 Windows 執行階段類型 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Windows 執行階段類型 [JavaScript]"
  - "JavaScript，Windows 執行階段類型"
ms.assetid: f4851802-8b40-4afa-ba6c-8a162a9a43cc
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# 以 JavaScript 表示 Windows 執行階段類型
下表描述 JavaScript 表示 Windows 執行階段型別的方式。  
  
> [!IMPORTANT]
>  Windows 執行階段功能不適用於 Internet Explorer 中執行的應用程式。  
  
## JavaScript 中的 Windows 執行階段型別  
  
|Windows 執行階段型別|JavaScript 表示|描述|  
|--------------------|-------------------|--------|  
|`UInt8`|`Number`|Windows 執行階段 `Uint8` 是不帶正負號的 8 位元整數，表示為 JavaScript 數字。  JavaScript 值會先轉換為 JavaScript 數字，接著會進行 `ToUint32` 處理序。  如果 JavaScript 數值是在 Uint8 範圍之外，結果將會對 2^8 套用模數。|  
|`Int32`|`Number`|Windows 執行階段 `Int32` 是帶正負號的 32 位元整數，表示為 JavaScript 數字。  JavaScript 值會先轉換為 JavaScript 數字，接著會進行 `ToInt32` 處理序。  如果 JavaScript 數值是在 `Int32` 範圍之外，結果將會對 2^16 套用模數。|  
|`Int64`|`Number`|Windows 執行階段 `Int64` 是帶正負號的 64 位元整數，如果它落在 \[\-2^53, 2^53\] 範圍內，則表示為標準數字。  如果在這個範圍之外，則表示為具有維持完整 64 位元整數資料之自訂備份存放區的數值。  在這些自訂 Int64 數值上的所有數學運算都會造成數值轉換成 \[\-2^53, 2^53\] 範圍內的標準數字。  如果值在此範圍之外，會發生型別錯誤。  這個轉換處理序的例外狀況是 `==`、 `===`、 `SameValue` 和 `RelationalComparison` 作業，這些作業會在傳遞兩個表示的 64 位元值時，根據完整 64 位元來比較引數。  如果其中一個引數是標準 JavaScript 數目，這些作業也會在比較之前將引數轉換成 JavaScript 數字。  如果 JavaScript 值是 Int64 值本身，就會直接指派這個值，否則會將該值套用 `ToInteger` 轉換的結果傳遞至 Windows 執行階段。  如果強制型轉失敗，則會傳回例外狀況。|  
|`Uint64`|`Number`|Windows 執行階段 `Uint64` 是不帶正負號的 64 位元整數，如果它落在 \[0, 2^53\] 範圍內，則表示為標準數字。  如果在這個範圍之外，則表示為具有維持完整 64 位元不帶正負號整數資料之自訂備份存放區的數字。  在這些自訂 Uint64 數值上的所有數學運算都會造成數值轉換成 \[0, 2^53\] 範圍內的標準數字。  如果值在此範圍之外，會發生型別錯誤。  這個轉換處理序的例外狀況是 `==`、 `===`、 `SameValue` 和 `RelationalComparison` 作業，這些作業會在傳遞兩個 64 位元值時，根據完整 64 位元來比較引數。  如果其中一個引數是標準 JavaScript 數目，這些作業也會在比較之前將引數轉換成 JavaScript 數字。  如果 JavaScript 值是 Uint64 值本身，就會直接指派這個值，否則會將該值先套用 `ToInteger` 轉換接著對 2^52 取模數的結果傳遞至 Windows 執行階段。  如果型別轉換失敗，則會傳回例外狀況。|  
|`Single`|`Number`|Windows 執行階段 `Single` 是 32 位元浮點數，透過挑選最接近單精確度值的雙精確度值，表示為 JavaScript 數字。  JavaScript 值先轉換成 JavaScript 數字，然後範圍檢查，以確保該值是以單精確度 32 位元 IEEE 754 浮點數表示。  如果轉換或範圍檢查失敗，則會傳回封送處理錯誤。|  
|`Double`|`Number`|Windows 執行階段 `Double` 是 64 位元浮點數。  `ToNumber` 用來將 Windows 執行階段 `Double` 轉換為 JavaScript 數字。  如果轉換失敗，則會傳回封送處理錯誤。|  
|`Boolean`|`Boolean`|Windows 執行階段 `Boolean` 是 8 位元值，其中零為 `false`，零以外的任何值為 `true`，表示為 JavaScript `Boolean`。  JavaScript 值會先由 `ToBoolean` 轉換為 JavaScript `Boolean`。  這表示宣告為 `void func(BOOL);` 的 Windows 執行階段函式，在 JavaScript 中可寫成 `obj.func("test");`。  Windows 執行階段函式是以做為 `TRUE` 傳遞的 `BOOL` 參數呼叫的。  如果轉換失敗，則會傳回封送處理錯誤。|  
|`Char16`|`String`|Windows 執行階段 `Char16` 是 16 位元 Unicode 字元，表示為包含單一字元的 JavaScript 字串。  JavaScript 值先由 `ToString` 轉換為 JavaScript 字串，接著會檢查以確定字串的長度是單一字元。  單一字元接著做為 `Char16` 值傳遞。  如果轉換或長度檢查失敗，則會傳回封送處理錯誤。|  
|`String`|`String`|Windows 執行階段 `String` 是不可變的 `Char16` 物件序列。  字串表示為 JavaScript `String` 物件。  Windows 執行階段字串對於 `null` 和空字串 \(""\) 沒有不同的值。  `null` 和空字串值轉換成 JavaScript 空字串。  注意：當 JavaScript `null` 傳遞給預期字串的 Windows 執行階段參數時，它會產生字串值 "null"，而不是 `null` 或空字串 \(""\)。  傳遞至 Windows 執行階段的字串一定要執行個體化為空字串。|  
|`Enumeration`|`Object`|Windows 執行階段 `Enumeration` 是有相關具名常數集合的 32 位元整數 \(帶正負號或不帶正負號\)。  在 JavaScript 中，列舉表示為包含每個具名值的唯讀欄位之物件。  列舉值轉換成 JavaScript 數字，如 `Int32` 和 `UInt32` 之前所定義。  當 JavaScript 值轉換為 Windows 執行階段列舉時，它會轉換、截斷且範圍檢查，如前面所述。  不過，產生的值不會根據在列舉中指定的已定義之具名值進行檢查。|  
|`Structure`|`Object`|Windows 執行階段 `Structure` 是具名資料欄位的異質性集合。  在 JavaScript，結構表示為包含結構中每個欄位的具名屬性的 JavaScript 物件。  如果任何結構值轉換失敗，則會傳回封送處理錯誤。  JavaScript 物件中沒有 Windows 執行階段結構對應項的欄位會被忽略。  注意：Windows 執行階段結構無法在 JavaScript 中以 `new` 關鍵字執行個體化。|  
|`Array`|`Array`|Windows 執行階段 `Array` 轉換為 JavaScript 陣列。  不過，Windows 執行階段陣列無法調整大小，因此，某些 JavaScript 陣列作業是不可能的。  已轉換之陣列的內部 \[\[Class\]\] 屬性不是設定為 "Array"，因為 ECMAScript 5 規格不允許此設定。  這表示 `Array.isArray(v)` 會傳回 `false`。  JavaScript 值轉換為 Windows 執行階段陣列，如下所示：如果這個值是 `null` 或 `undefined`，會轉換為原生 `null`。  如果其內部 \[\[Class\]\] 屬性設定為 “Array”，則它會複製到原生陣列，並傳遞此陣列的參考。  如果是轉換的陣列 \(如前所述\)，則會傳遞基礎原生陣列。  注意：將 JavaScript 陣列值傳遞至 Windows 執行階段方法會產生陣列的完整複本。|  
|委派 \(函式回呼\)|`Function`|Windows 執行階段委派是單一方法的參考。  Windows 執行階段委派在 JavaScript 中表示為 JavaScript `Function`，保證會在適合的執行緒上呼叫。  當 `Function` 叫用時，引數轉換為對等 Windows 執行階段參數型別。  如果 JavaScript 引數少於委派 `in` 參數，委派呼叫失敗。  如果 JavaScript 引數多於委派中的 `in` 參數，額外的 JavaScript 引數會被忽略。  在叫用委派之後，`out` 參數會轉換為 JavaScript 型別並傳回。  如果原生 JavaScript 函式物件轉換為 Windows 執行階段委派，它會包裝在對應型別的 Windows 執行階段委派中。  在叫用委派時，`in` 參數會轉換為 JavaScript 型別。  在叫用委派之後，傳回值會轉換為委派的 `out` 參數。|  
|介面|`Object`|介面和介面群組在 JavaScript 中不會直接表示為物件。  不過，介面表示為 Windows 執行階段方法的參數和傳回型別。  Windows 執行階段介面執行個體會被轉換成如下：<br /><br /> 1.  如果有有效的執行階段類別，將物件表示為該類別的執行個體。<br />2.  如果沒有有效的執行階段類別，則將物件表示為未命名的執行階段類別執行個體，這個執行個體確切實作它已知實作的介面，加上它的必要介面。<br /><br /> JavaScript 值會測試以判斷它是否為執行階段類別或介面的執行個體。  如果是，而且原始 Windows 執行階段值實作此介面，物件會傳遞至 Windows 執行階段。|  
|執行階段類別|`Object`|Windows 執行階段的物件可以是實作一個或多個介面的執行階段類別執行個體。  Windows 執行階段物件在 JavaScript 表示為物件。  在類別的所有實作介面上定義的方法、屬性和事件的聯集，表示 JavaScript 物件的原型的具名屬性。  JavaScript 消費者可以直接存取類別的所有成員。  Windows 執行階段物件有原型，包含執行階段類別中所有實作介面的所有成員。|  
  
## 請參閱  
 [在 JavaScript 中使用 Windows 執行階段](../jswinrt/using-the-windows-runtime-in-javascript.md)