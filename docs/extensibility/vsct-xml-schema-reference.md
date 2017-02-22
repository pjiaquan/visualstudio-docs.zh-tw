---
title: "VSCT XML 結構描述參考 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio 命令資料表設定檔 (VSCT)、 XML 結構描述"
  - "VSCT XML 結構描述項目"
ms.assetid: 49e7efae-e713-4762-a824-96fdaf92cdc9
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# VSCT XML 結構描述參考
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

提供的命令資料表編譯器結構描述項目，以允許子元素和屬性每個。  
  
 以 XML 為基礎的命令資料表 \(.vsct\) 組態檔定義 VSPackage 所提供的命令項目整合式的開發環境 \(IDE\)。 這些元素包括功能表項目、 功能表、 工具列和下拉式方塊。  
  
> [!NOTE]
>  VSCT 編譯器可以.vsct 檔上執行前置處理器。 這通常是因為 c \+ \+ 前置處理器，您可以定義包含和巨集具有相同的語法 c \+ \+ 檔案中使用。 .vsct 中提供的範例檔 **新的專案** VSPackage 專案建立精靈。  
  
## 選擇性的項目  
 某些 VSCT 項目是選擇性的。 如果 `Parent` 未指定引數，會隱含 Group\_Undefined:0。 如果 `Icon` 未指定引數，會隱含 guidOfficeIcon:msotcidNoIcon。 定義快速鍵時，模擬，也就是通常未使用，是選擇性的。  
  
 點陣圖的項目可能會在編譯時期內嵌，藉由指定點陣圖區域中的位置 `href` 引數。 點陣圖區是在合併期間複製而不是擷取自 DLL 的資源。 當 `href` 提供引數，則 `usedList` 引數成為選用項目，並使用視為點陣圖區中的所有位置。  
  
 使用符號名稱，必須定義所有 GUID 和 ID 值。 在標頭檔或 VSCT \< 符號 \> 區段中，可能會定義這些名稱。 透過 \< 加入 \> 項目，包含或參考的 \< Extern \> 項目符號的名稱必須是本機。 若是在簡單模式，\< Extern \> 項目中指定的標頭檔從匯入的符號名稱 \#define 符號值。 值可以是另一個符號，只要先前定義的符號。 GUID 定義必須遵循 \[OLE\] 或 \[c \+ \+ 的格式。 ID 值可能是十進位或十六進位數字會以 0x，前面加上下列程式碼行中所示:  
  
-   {} 6D484634\-E53D\-4a2c\-ADCB\-55145C9362C8  
  
-   {0x6d484634、 0xe53d、 0x4a2c，{0xad、 0xcb，0x55、 0x14，0x5c、 0x93，0x62，0xc8 建立}}  
  
 可能會使用 XML 註解，但是反覆存取的圖形化使用者介面 \(GUI\) 工具可能會捨棄它們。 不論格式為何維護保證 \< 註釋 \> 項目的內容。  
  
## 結構描述階層架構  
 .Vsct 檔具有下列主要項目。  
  
 [CommandTable 項目](../extensibility/commandtable-element.md)  
  
 [Extern 項目](../extensibility/extern-element.md)  
  
 [包含項目](../extensibility/include-element.md)  
  
 [定義項目](../extensibility/define-element.md)  
  
 [Commands 元素](../extensibility/commands-element.md)  
  
 [CommandPlacements 項目](../extensibility/commandplacements-element.md)  
  
 [VisibilityConstraints 項目](../extensibility/visibilityconstraints-element.md)  
  
 [按鍵組合的項目](../extensibility/keybindings-element.md)  
  
 [UsedCommands 項目](../extensibility/usedcommands-element.md)  
  
 [Parent 項目](../extensibility/parent-element.md)  
  
 [Icon 項目](../extensibility/icon-element.md)  
  
 [字串的項目](../extensibility/strings-element.md)  
  
 [命令旗標的項目](../extensibility/command-flag-element.md)  
  
 [符號的項目](../extensibility/symbols-element.md)  
  
 [條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)  
  
## 請參閱  
 [VSPackages 如何新增使用者介面項目](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Vspackage 中的命令路由](../extensibility/internals/command-routing-in-vspackages.md)