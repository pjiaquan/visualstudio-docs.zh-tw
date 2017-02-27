---
title: "符號的項目 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "符號項目 (VSCT XML 結構描述)"
  - "VSCT XML 結構描述項目符號"
ms.assetid: 1cda43d8-42a5-4b1b-a3c8-cf0401c3202f
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# 符號的項目
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

定義 Guid 和 Id，以供其他 VSCT 項目。 Unmanaged 程式碼，這項資訊通常是由所指定的標頭檔 [Extern 項目](../extensibility/extern-element.md)。 Managed 程式碼會使用項目的子項目符號來定義這項資訊。  
  
 如果您從現有的.cto 檔案建立.vsct 檔，將會以符號項目的子系產生符號。 如需詳細資訊，請參閱[如何：從現有的 .Cto 檔建立 .Vsct 檔](../Topic/How%20to:%20Create%20a%20.Vsct%20File%20from%20an%20Existing%20.Cto%20File.md)。  
  
 符號的項目不應與混淆 [定義項目](../extensibility/define-element.md), ，以定義以供前置處理器的名稱 \/ 值組。  
  
## 語法  
  
```  
<Symbols>  
  <GuidSymbol>... </GuidSymbol>  
  <GuidSymbol>... </GuidSymbol>  
</Symbols>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|無||  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|GuidSymbol|定義 GUID 符號。 GuidSymbol 具有兩個必要的屬性: 名稱和值。 名稱是符號的名稱和值是以字串 GUID 值。<br /><br /> 例如: \< GuidSymbol 名稱 \="guidVsPackage1Pkg"value \="{c5f54698\-101a\-4846\-84d3\-dc748f9cd848}"\/ \>|  
|IDSymbol|定義符號。 IDSymbol 具有兩個必要的屬性: 名稱和值。 名稱是符號的名稱和值是做為字串的符號值。<br /><br /> 例如: \< IDSymbol 名稱 \="MyMenuGroup"value \="0x1020"\/ \>|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[CommandTable 項目](../extensibility/commandtable-element.md)|.Vsct 檔的根項目。|  
  
## 範例  
  
```  
<Symbols> <GuidSymbol name="guidVsPackage1Pkg" value="{c5f54698-101a-4846-84d3-dc748f9cd848}" /> <GuidSymbol name="guidVsPackage1CmdSet" value="{cb9dfd7f-2fcc-4a3e-aae8-f7fe30b1cfac}"> <IDSymbol name="MyMenuGroup" value="0x1020" /> <IDSymbol name="cmdidMyCommand" value="0x0100" /> <IDSymbol name="cmdidMyTool" value="0x0101" /> </GuidSymbol> </Symbols>  
```  
  
## 請參閱  
 [Visual Studio 命令資料表 \(。Vsct\) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)