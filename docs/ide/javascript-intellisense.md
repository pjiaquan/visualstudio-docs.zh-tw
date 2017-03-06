---
title: JavaScript IntelliSense | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IntelliSense [JavaScript]
- <reference> JavaScript XML tag
- JavaScript Code Editor
- XML code comments, JavaScript IntelliSense
- reference JavaScript XML tag
- JavaScript, IntelliSense
- code comments, JavaScript IntelliSense
- JavaScript, reference groups
- JavaScript Editor
- reference directives [JavaScript]
- JavaScript, XML documentation comments
- reference groups [JavaScript]
- JavaScript, reference directives
- IntelliSense [JavaScript], about
- IntelliSense extensibility [JavaScript]
- XML documentation comments [JavaScript]
ms.assetid: af1a3171-c9d8-45a3-9c96-a763e3b163ef
caps.latest.revision: 63
author: mikejo
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
ms.sourcegitcommit: d07820eda0d76163d99d7752789750eaf56182fd
ms.openlocfilehash: 1f8372fe201d6b23ee2c65e0f6d6a2fa28976654
ms.lasthandoff: 02/22/2017

---
# <a name="javascript-intellisense"></a>JavaScript IntelliSense
[!include[vs_dev15](../misc/includes/vs_dev15_md.md)] 提供現成可用的強大 JavaScript 編輯體驗。 由 TypeScript 型語言服務提供，Visual Studio 提供更豐富的 IntelliSense、支援最新的 JavaScript 功能，並改善如移至定義、重構及更多的生產力功能。

> [!NOTE]
>  [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] 中的 JavaScript 語言服務使用新的語言服務引擎 ("salsa")。 本主題包含詳細資料，您也可以閱讀本[部落格文章](https://blogs.msdn.microsoft.com/visualstudio/2016/04/08/previewing-salsa-javascript-language-service-visual-studio-15/)。 新的編輯體經驗大部分也適用於 VS 程式碼。 如需詳細資訊，請參閱 [JavaScript in VS Code](https://code.visualstudio.com/docs/languages/javascript) (VS 程式碼中的 JavaScript)。

如需一般之 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] IntelliSense 功能的詳細資訊，請參閱[使用 IntelliSense](../ide/using-intellisense.md)。 

## <a name="whats-new-in-the-javascript-language-service-in-includevsdev15miscincludesvsdev15mdmd"></a>[!include[vs_dev15](../misc/includes/vs_dev15_md.md)] 的 JavaScript 語言服務新功能

- 更豐富的 IntelliSense

    [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] 中的 JavaScript IntelliSense 現在會顯示更多有關參數及成員清單的資訊。
此項新資訊是由 TypeScript 語言服務提供，使用程式碼更容易了解的幕後靜態分析。
TypeScript 會使用數項來源來建置這項資訊。
    - [以型別推斷為基礎的 IntelliSense](#TypeInference)
    - [以 JSDoc 為基礎的 IntelliSense](#JsDoc)
    - [以 TypeScript 宣告檔案為基礎的 IntelliSense](#TSDeclFiles)

- [自動擷取型別定義](#Auto)
- [支援 ES6 和更新版本](#ES6)
- [JSX 語法支援](#JSX)

## <a name="a-nametypeinferenceaintellisense-based-on-type-inference"></a><a name="TypeInference"></a>以型別推斷為基礎的 IntelliSense
在 JavaScript 中，大部分的時間不提供任何明確的類型資訊。 幸運的是，只要指定周圍的程式碼內容，通常很容易就能推斷型別。
此程序稱為型別推斷。

變數或屬性的類型，通常是用來初始化值的類型或最新的值指派。 

```js
var nextItem = 10;
nextItem; // here we know nextItem is a number

nextItem = "box";
nextItem; // now we know nextItem is a string
```

函式的傳回型別則可從傳回的陳述式推斷。 

函式參數目前沒有任何推斷，但使用 JSDoc 或 TypeScript `.d.ts` 檔案有多種方法可處理 (請參閱稍後的章節)。

此外，還有下列項目的特殊推斷︰
 - "ES3-style" 類別，使用建構函式和原型屬性指派所指定。
 - CommonJS-style 模組模式，指定為 `exports` 物件的屬性指派或 `module.exports` 屬性的指派。

```js
function Foo(param1) {
    this.prop = param1;
}
Foo.prototype.getIt = function () { return this.prop; };
// Foo will appear as a class, and instances will have a 'prop' property and a 'getIt' method.

exports.Foo = Foo;
// This file will appear as an external module with a 'Foo' export.
// Note that assigning a value to "module.exports" is also supported.
```

## <a name="a-namejsdoca-intellisense-based-on-jsdoc"></a><a name="JsDoc"></a> 以 JSDoc 為基礎的 IntelliSense

遇到不提供所需類型資訊 (或支援文件) 的型別推斷，可能會透過 JSDoc 註解明確提供類型資訊。  例如，若要為部分宣告的物件提供特定的類型，您可以使用 `@type` 標記，如下所示︰

```js
/**
 * @type {{a: boolean, b: boolean, c: number}}
 */
var x = {a: true};
x.b = false;
x. // <- "x" is shown as having properties a, b, and c of the types specified
```

如前所述，永遠不會推斷函式參數。 不過，使用 JSDoc `@param` 標記也可以在函式參數中加入類型。 

```js
/**
 * @param {string} param1 - The first argument to this function
 */
function Foo(param1) {
    this.prop = param1; // "param1" (and thus "this.prop") are now of type "string".
}
```
 
如需目前支援的 JsDoc 註解，請參閱[本文](https://github.com/Microsoft/TypeScript/wiki/JsDoc-support-in-JavaScript)。

## <a name="a-nametsdeclfilesa-intellisense-based-on-typescript-declaration-files"></a><a name="TsDeclFiles"></a> 以 TypeScript 宣告檔案為基礎的 IntelliSense

因為 JavaScript 和 TypeScript 現在是以相同的語言服務為基礎，所以能夠以更豐富的方式互動。 例如，可為 `.d.ts` 檔案中宣告的值提供 JavaScript IntelliSense ([更多資訊](https://github.com/Microsoft/TypeScript-Handbook/blob/master/pages/Writing%20Definition%20Files.md))，而在 TypeScript 中宣告的介面和類別等類型，可提供 JsDoc 註解當作類型使用。 

以下簡單示範 TypeScript 定義檔案 (透過介面) 向同一專案中的 JavaScript 檔案 (使用 JsDoc 標記) 提供此類的類型資訊。

_**JavaScript 中使用的 TypeScript 宣告**_

<img src="https://raw.githubusercontent.com/wiki/Microsoft/TypeScript/images/decl1.png" height="400" width="640"/>

## <a name="a-nameautoa-automatic-acquisition-of-type-definitions"></a><a name="Auto"></a> 自動擷取型別定義
在 TypeScript 世界中，最熱門的 JavaScript 程式庫都使用 `.d.ts` 檔案描述其 API，而這類定義最常見的儲存機制位於 [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped)。

根據預設，Salsa 語言服務會嘗試偵測使用中的 JavaScript 程式庫為何，並自動下載及參考對應的 `.d.ts` 檔案，依序描述程式庫以便提供更豐富的 IntelliSense。 這些檔案會下載到位於 `%LOCALAPPDATA%\Microsoft\TypeScript` 的使用者資料夾下的快取。 

> [!NOTE]
> 如果使用 `tsconfig.json` 組態檔，這項功能預設 [停用]，但可設定為 [啟用]，詳細資訊如下所述)。

自動偵測目前處理從 npm (藉由讀取 `package.json` 檔案)、Bower (藉由讀取 `bower.json` 檔案)，以及比對前 400 多個熱門 JavaScript 程式庫清單的專案中的鬆散式檔案下載的相依性。 例如，如果您的專案中有 `jquery-1.10.min.js`，則會擷取並載入檔案 `jquery.d.ts` 以提供更好的編輯體驗。 此 `.d.ts` 檔案對您的專案沒有任何影響。 

如果您不想使用自動擷取，請如下所示新增組態檔來停用這項功能。 您仍然放置定義檔案，以手動方式直接在專案中使用它。

## <a name="a-namees6a-support-for-es6-and-beyond"></a><a name="ES6"></a> 支援 ES6 和更新版本

ES6 (或稱 ECMAScript 2015) 是 JavaScript 的下一個版本。 它帶來新的語言語法，例如類別、箭頭函式、`let`/`const` 等等。 Visual Studio 支援此新語法的全部。

TypeScript 提供的重要功能之一是能夠使用 ES6 功能，以及發出可在還不了解這些新功能的 JavaScript 執行階段中執行的程式碼。 這通常稱為「轉譯」。 因為 JavaScript 使用相同的語言服務，所以它也可以利用 ES6 + 到 ES5 的轉譯。

您需要對設定選項有一些了解，才能進行此設定。  TypeScript 是透過 `tsconfig.json` 檔案設定。 沒有此類檔案時，會使用某些預設值。 基於相容性的理由，這些預設值在只有 JavaScript 檔案 (或 `.d.ts` 檔案) 的內容中是不同的。 若要編譯 JavaScript 檔案，必須新增 `tsconfig.json` 檔案，然後必須明確設定某些預設值。

tsconfig 檔案的必要設定列示如下︰

 - `allowJs`︰此值必須設為 `true` 才能夠辨識 JavaScript 檔案。
當 TypeScript 編譯至 JavaScript，這預設為 `false`，這是為了避免編譯器包含它剛所編譯的檔案。
 - `outDir`︰這應該設定為不包含在專案中的位置，以不偵測到發出的 JavaScript 檔案，然後包含在專案中 (請參閱後文的 `exclude`)。
 - `module`︰如果使用模組，此設定會告知編譯器發出的程式碼應該使用哪種模組格式 (例如節點的 `commonjs` 或 Browserify 等搭配程式)。
 - `exclude`︰此設定會指出專案不包含哪些資料夾。 
 輸出位置以及 `node_modules` 或 `temp` 等非專案資料夾，應該加入此設定。
 - `enableAutoDiscovery`︰此設定會啟用自動偵測和下載定義檔案，如上文所述。
 - `compileOnSave`︰此設定會告知編譯器是否只要來源檔案儲存在 Visual Studio 中，就應該隨時重新編譯。

為將 JavaScript 檔案轉換為 `./out` 資料夾中的 CommonJS 模組，與下例類似的設定可能會包含在 `tsconfig.json` 檔案中。

```json
{
  "compilerOptions": {
    "module": "commonjs",
    "allowJs": true,
    "outDir": "out"
  },
  "exclude": [
    "node_modules",
    "wwwroot",
    "out"
  ],
  "compileOnSave": true,
  "typingOptions": {
    "enableAutoDiscovery": true
  }
}
```

如果現有的來源檔案 (`./app.js`) 包含以下數種 ECMAScript 2015 語言功能，即就地使用上述設定︰

```js
import {Subscription} from 'rxjs/Subscription';

class Foo {
    sayHi(name) {
        return `Hi ${name}, welcome to Salsa!`;
    }
}

export let sqr = x => x * x;
export default Subscription;
```

然後檔案會發出至 `./out/app.js`，以類似下例的 ECMAScript 5 為目標 (預設值)：

```js
"use strict";
var Subscription_1 = require('rxjs/Subscription');
var Foo = (function () {
    function Foo() {
    }
    Foo.prototype.sayHi = function (name) {
        return "Hi " + name + ", welcome to Salsa!";
    };
    return Foo;
}());
exports.sqr = function (x) { return x * x; };
Object.defineProperty(exports, "__esModule", { value: true });
exports.default = Subscription_1.Subscription;
//# sourceMappingURL=app.js.map
```

## <a name="a-namejsxa-jsx-syntax-support"></a><a name="JSX"></a>JSX 語法支援

Visual Studio 2017 中的 JavaScript 充分支援 JSX 語法。 JSX 是一種語法集，可讓 HTML 在 JavaScript 檔案中標記。 

下圖顯示 `comps.tsx` TypeScript 檔案中所定義的反應元件，然後從 `app.jsx` 檔案使用此元件，以 JSX 運算式內的完成及記錄來完成 IntelliSense。
這裡不需要 TypeScript，此特例只是也剛好包含一些 TypeScript 程式碼。
<img src="https://raw.githubusercontent.com/wiki/Microsoft/TypeScript/images/react.png" height="500" width="640"/>

> [!NOTE]
> 將 JSX 語法轉換成回應呼叫，`"jsx": "react"` 設定必須新增至上述 `tsconfig.json` 檔案的 `compilerOptions` 中。

於建置時建立在 `./out/app.js' 的 JavaScript 檔案會包含程式碼：

```js
"use strict";
var comps_1 = require('./comps');
var x = React.createElement(comps_1.RepoDisplay, {description: "test"});
```

