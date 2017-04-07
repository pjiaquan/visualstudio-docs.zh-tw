---
title: "Visual Studio 中的 JavaScript | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f3eee13e-30e4-4bc1-81f5-058d7e379b75
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 77e7ce26df70e41e2328442454fe78c7a663f1f3
ms.openlocfilehash: de00ef86413571739446b61427c3a8e6c4680c06
ms.lasthandoff: 03/08/2017

---
# <a name="javascript-in-visual-studio"></a>Visual Studio 中的 JavaScript
JavaScript 是在 Visual Studio 中的第一級語言。 當您在 Visual Studio IDE 中撰寫 JavaScript 程式碼時，可以使用大部分或所有標準編輯輔助，包括程式碼片段、IntelliSense 等等。 您可以為許多應用程式類型和服務撰寫 JavaScript 程式碼。  
  
 如需 JavaScript 語言參考文件，請參閱 [JavaScript](https://docs.microsoft.com/scripting/javascript/javascript-language-reference)。
  
 可能需要特定版本的 Visual Studio 或特定的 Visual Studio 擴充功能，才能開發特定應用程式類型和使用 HTML 和 JavaScript 的服務。 下列清單中有詳細資訊的連結。  
  
-   若要使用 Apache Cordova 來建立跨平台應用程式，請參閱[適用於 Apache Cordova 的 Visual Studio 工具 (英文)](https://docs.microsoft.com/visualstudio/cross-platform/tools-for-cordova/)。  
  
-   如需您可在 Visual Studio 中使用的 JavaScript 技術連結，請參閱 [JavaScript (英文)](https://docs.microsoft.com/scripting/javascript/) 和[指令碼技術 (英文)](https://docs.microsoft.com/scripting/) 頁面。
  
 Visual Studio 中的 JavaScript 編輯器會提供 IntelliSense 支援。 如需詳細資訊，請參閱 [JavaScript IntelliSense](../ide/javascript-intellisense.md)。  
  
## <a name="whats-new-in-javascript"></a>JavaScript 的新功能  
 下表中列出 JavaScript 的新功能。  
  
|功能|描述|  
|-------------|-----------------|  
|類別|新的語法支援[類別](http://msdn.microsoft.com/Library/bf45ebad-4678-4062-88df-55d32b603c69)宣告。|  
|Promise|[Promise](http://msdn.microsoft.com/Library/358ad98b-f7fa-448c-9ee0-ef1e2a45e9c6) 使非同步撰寫程式碼更方便、更俐落。 同時支援 Promise 建構函式及 `all` 和 `race` 公用程式方法。|  
|Iterator|現在您可以反覆查看遞迴的物件 (包括陣列、類似陣列的物件和迭代器) ，叫用自訂的反覆項目攔截程序，來執行每個相異的屬性值陳述式。 如需詳細資訊，請參閱[迭代器和產生器](http://msdn.microsoft.com/Library/68ef5b2f-0349-492b-b557-73ff2a2f90cf)。 **注意：**目前還不支援產生器。|  
|Arrow 函式|Arrow 函式 (=>) 提供簡寫語法，用於 `function` 關鍵字，以語彙 `this` 繫結為特色。|  
|內建物件的新方法|[Array 物件](http://msdn.microsoft.com/Library/08e5f552-0797-4b48-8164-609582fc18c9)、[Math 物件](http://msdn.microsoft.com/Library/607b94cb-921c-43cd-b514-fdbc13aeced6)、[Number 物件](http://msdn.microsoft.com/Library/76e87c37-cf6c-46cc-bafa-04be1fe3d78d)、[Object 物件](http://msdn.microsoft.com/Library/d24ef8fc-217b-4828-94e1-19f72780bae0)及 [String 物件](http://msdn.microsoft.com/Library/8063ecd5-5778-4e87-b985-b21420171914)等內建物件包含許多新的公用程式函式和屬性，可用來操作和檢查資料。|  
|物件常值的增強功能|物件現在支援計算的屬性、簡潔的方法定義，以及簡寫語法，用於其值已初始化為相同名稱變數的屬性。 如需詳細資訊，請參閱[建立物件](http://msdn.microsoft.com/Library/58d1baa5-4fe8-4a56-a926-5b11765df704)。|  
|Proxy|[Proxy](http://msdn.microsoft.com/Library/2b89abee-04fa-47e6-9676-980016cff5f8) 可為物件啟用自訂行為。|  
|剩餘參數|剩餘參數可讓您將函式呼叫中連續的引數轉為陣列。 如需詳細資訊，請參閱[函式](http://msdn.microsoft.com/Library/e2a72b5a-3edd-43d8-95e8-91721b38c1c1)。|  
|Spread 運算子|[spread 運算子](http://msdn.microsoft.com/Library/10263a4c-bd27-4d87-9917-fb4b6bf373db) (`…`) 會把可逐一查看的運算式擴充成個別的引數。 例如，`a.b(…array)` 和 `a.b.apply(a, array)` 大致上相同。|  
|Symbol|[Symbol](http://msdn.microsoft.com/Library/2ad059f1-4b7f-4758-882a-c74ce1283ab0) 物件可允許由其他程式碼將屬性新增到現有的物件，而不會干擾現有的物件屬性，也不會有非預期的可視性和其他未經協調的新增。|  
|範本字串|[範本字串](http://msdn.microsoft.com/Library/f2e525a5-b0fc-49c3-95a0-641788e5c12a)是一種字串常值，可讓運算式被評估並與字串常值串連。|  
|Unicode 增強功能|已改善 Unicode 支援。 例如，新的逸出序列格式支援 astral 字碼指標 (超過&4; 個十六進位數字的字碼指標)。 如需詳細資訊，請參閱[特殊字元](http://msdn.microsoft.com/Library/3b38b1bd-1f0f-4748-b13e-55cab36fd126)。|  
|WeakSet|[WeakSet](http://msdn.microsoft.com/Library/f97e6e7c-d678-4e32-978e-d949a7cafa3a) 是一種物件集合，如果沒有任何其他地方參考它，就會由記憶體回收。|
