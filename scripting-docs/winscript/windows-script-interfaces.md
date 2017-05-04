---
title: "Windows 指令碼的介面 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4c750627-6797-4857-9f5e-e5f54371f83c
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Windows 指令碼的介面
Microsoft Windows 指令碼介面為應用程式加入指令碼和 OLE Automation 提供。  仰賴 Windows 指令碼的指令碼的主應用程式可以使用多個來源和廠商的指令碼引擎處理指令碼在元件之間。  指令碼本身語言，語法，保存格式，執行模型的實作，並在如此保留給指令碼廠商。  
  
 Windows 指令碼文件分為下列部分:  
  
 [Windows Script Host](../winscript/windows-script-hosts.md)  
  
 [Windows 指令碼引擎](../winscript/windows-script-engines.md)  
  
 [動態指令碼偵錯概觀](../winscript/active-script-debugging-overview.md)  
  
 [動態指令碼分析概觀](../winscript/active-script-profiling-overview.md)  
  
 [Windows 指令碼介面參考](../winscript/reference/windows-script-interfaces-reference.md)  
  
## Windows 指令碼背景  
 Windows 指令碼介面可分為兩類:Windows Script Host 和 Windows 指令碼引擎。  主應用程式會建立一個指令碼引擎和呼叫在引擎執行指令碼。  Windows Script Host 範例包括:  
  
-   Microsoft Internet Explorer  
  
-   網際網路撰寫工具  
  
-   Shell  
  
 Windows 指令碼引擎可以為任何語言或執行階段環境中開發，包括:  
  
-   Microsoft Visual Basic Scripting Edition \(VBScript\) Visual Basic  
  
-   Perl  
  
-   匯入。  
  
 若要使實作主應用程式相同的彈性盡可能，提供 Windows 指令碼的 OLE Automation 包裝函式。  不過，使用這個包裝函式物件具現化指令碼引擎的主機沒有程度為執行階段名稱空間，持續性模型的控制項，依此類推，它會使用，則了視窗直接指令碼。  
  
 Windows 指令碼設計隔離在建立環境只需要的介面項目，讓 nonauthoring 的主應用程式 \(例如瀏覽器和檢視器\)，而且指令碼引擎 \(例如， VBScript\) 可以保持輕量型。  
  
## Windows 指令碼基本架構。  
 下圖顯示 Windows Script Host 之間的互動和 Windows 指令碼引擎。  
  
 在主應用程式和引擎之間的互動所需的步驟下列清單中所指定。  
  
1.  建立專案。  主應用程式載入一個專案或檔案。  \(這個步驟不是特殊到視窗為完整性指令碼，不過，包括這裡\)。  
  
2.  建立 Windows 指令碼引擎。  主應用程式會呼叫來建立 `CoCreateInstance` 的新視窗指令碼引擎，指定類別識別項 \(CLSID\) 特定指令碼引擎使用。  例如， Internet Explorer HTML 瀏覽器會在 HTML \<OBJECT\> 標記的 CLSID\= 屬性接收指令碼引擎的類別識別項。  
  
3.  載入指令碼。  如果指令碼內容保存，主應用程式呼叫指令碼引擎的 `IPersist*::Load` 方法送入其指令碼儲存區、資料流或屬性包。  否則，主應用程式使用 `IPersist*::InitNew` 或 [IActiveScriptParse::InitNew](../winscript/reference/iactivescriptparse-initnew.md) 方法會建立空白的指令碼。  維護一個指令碼的主機，當文字可以使用 [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md) 送入指令碼引擎的指令碼文字，在呼叫 `IActiveScriptParse::InitNew`之後。  
  
4.  將具名項目。  對於每個最上層具名項目 \(例如頁面和表單\) 匯入指令碼引擎的命名空間，主應用程式會呼叫 [IActiveScript::AddNamedItem](../winscript/reference/iactivescript-addnameditem.md) 方法會在引擎的命名空間中的項目。  這個步驟不是必要的最上層命名項目是否已經是指令碼的永續狀態的一部分所裝載的第 3. 步驟。  主應用程式不使用 `IActiveScript::AddNamedItem` 將分段具名項目 \(例如在 HTML 網頁上的控制項\);相反地，使用主機的 `ITypeInfo` 和 `IDispatch` 介面，引擎間接從最上層項目的分段項目。  
  
5.  執行指令碼。  主機造成引擎啟動指令碼的設定在 [IActiveScript::SetScriptState](../winscript/reference/iactivescript-setscriptstate.md) 方法的 SCRIPTSTATE\_CONNECTED 旗標負責。  這個方法會在可以將執行任何指令碼引擎架構工作，包括靜態繫結，插入事件 \(參看下方\) 和執行程式碼，類似指令化 `main()` 函式。  
  
6.  取得項目的資訊。  每次指令碼引擎必須具有相關符號以最上層項目，它會呼叫 [IActiveScriptSite::GetItemInfo](../winscript/reference/iactivescriptsite-getiteminfo.md) 方法，會傳回有關特定項目的資訊。  
  
7.  連結事件。  在啟動實際指令碼之前，所有相關物件事件傳遞 `IConnectionPoint` 連接的指令碼引擎連接。  
  
8.  叫用屬性和方法。  當指令碼，指令碼引擎在 `IDispatch::Invoke` 或其他標準 OLE 繫結機制實現對方法中具名物件的參考和屬性。  
  
## Windows 指令碼詞彙  
 這個清單包含用於文件的指令碼相關的詞彙的定義。  
  
|詞彙|定義|  
|--------|--------|  
|程式碼物件|與名為的項目，例如在表單後的模組在 Visual Basic 或 C \+\+. 類別與具名項目的指令碼引擎會建立的執行個體。  更好地，這是支援 OLE Automation，讓主應用程式或其他非指令碼實體可以管理程式碼物件的 OLE 元件物件模型 \(COM\) \(COM\) 物件。|  
|具名項目|OLE COM 物件 \(支援 OLE Automation\) 裝載視窗為有趣的指令碼的最好是具有的。  範例在 Web 瀏覽器中包含 HTML 網頁和瀏覽器和文件和對話方塊 \(Microsoft Word。|  
|指令碼|該資料表組成該程式的指令碼引擎。  指令碼可以是任何觸控可執行檔資料，包括文字、區塊 `pcode`，甚至有關電腦特定的可執行檔位元組程式碼片段。  主應用程式載入指令碼的指令碼引擎將其中一個 `IPersist*` 介面或透過 [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) 介面。|  
|指令碼引擎|處理指令碼的 OLE 物件。  一個指令碼引擎實作 [IActiveScript](../winscript/reference/iactivescript.md) ，而且，或者， [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) 介面。|  
|指令碼的主機|主控視窗指令碼引擎的應用程式或程式。  主機實作 [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) ，而且，或者， [IActiveScriptSiteWindow](../winscript/reference/iactivescriptsitewindow.md) 介面。|  
|Scriptlet|取得指令碼的部分附加至物件透過 [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) 介面。  Scriptlet 的彙總集合是指令碼。|  
|指令碼語言。|指令碼撰寫的語言 \(例如 VBScript\)，以及該語言語意。|  
  
## 請參閱  
 [Windows Script Interfaces](../winscript/windows-script-interfaces.md)