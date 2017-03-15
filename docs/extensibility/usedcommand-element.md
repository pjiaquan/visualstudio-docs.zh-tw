---
title: "UsedCommand 項目 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "UsedCommands 項目 (VSCT XML 結構描述)"
  - "UsedCommands，VSCT XML 結構描述項目"
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# UsedCommand 項目
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

啟用存取另一個.vsct 檔案中定義的命令的 VSPackage。 例如，如果 VSPackage 使用標準 **複製** 命令，由定義 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 殼層\] 中，您可以將命令加入功能表或工具列沒有重新實作它。  
  
## 語法  
  
```  
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|guid|必要項。 識別命令的 GUID 識別碼組的 GUID。|  
|id|必要項。 識別命令的 GUID 識別碼組識別碼。|  
|條件|選擇項。 請參閱 [條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|無||  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[UsedCommands 項目](../extensibility/usedcommands-element.md)|群組 UsedCommand 項目和其他 UsedCommands 群組。|  
  
## 備註  
 將命令新增至 `<UsedCommands>` 項目，會通知 VSPackage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 環境 VSPackage 需要的命令。 您應該加入 `<UsedCommand>` 封裝需要的任何命令的項目可能不會包含在所有版本和 Visual studio 的設定。 例如，如果您的封裝呼叫 Visual c \+ \+ 特有的命令，命令將無法使用 Visual Web Developer 中的使用者除非您包含 `<UsedCommand>` 命令的項目。  
  
## 範例  
  
```  
<UsedCommands> <UsedCommand guid="guidVSStd97" id="cmdidCut"/> <UsedCommand guid="guidVSStd97" id="cmdidCopy"/> <UsedCommand guid="guidVSStd97" id="cmdidPaste"/> </UsedCommands>  
```  
  
## 請參閱  
 [UsedCommands 項目](../extensibility/usedcommands-element.md)   
 [Visual Studio 命令資料表 \(。Vsct\) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)