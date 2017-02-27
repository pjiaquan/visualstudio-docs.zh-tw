---
title: "如何：顯示以逗號分隔的項目清單 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, 格式化項目集合"
  - "MSBuild, 以分號分隔項目"
ms.assetid: 3cae844c-7c6d-4144-82dc-efad10ba458f
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# 如何：顯示以逗號分隔的項目清單
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

當您處理 [!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] \([!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\) 中的項目清單時，以簡易方式顯示這些項目清單的內容，有時候會很有用。  或者，您的工作所使用的項目清單可能需要以特殊的分隔符號字串來加以分隔。  無論是前述的任何一種情形，您都可以指定項目清單的分隔符號字串。  
  
## 以逗號分隔清單中的項目  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 預設使用分號來分隔清單中的項目。  舉例來說，假設有一個 `Message` 項目具有以下的值：  
  
 `<Message Text="This is my list of TXT files: @(TXTFile)"/>`  
  
 當 `@(TXTFile)` 項目清單含有 App1.txt、App2.txt 和 App3.txt 等項目時，訊息就會顯示為：  
  
 `This is my list of TXT files: App1.txt;App2.txt;App3.txt`  
  
 如果想變更預設行為，可以自行指定分隔符號。  指定項目清單分隔符號的語法如下：  
  
 `@(ItemListName, '<separator>')`  
  
 分隔符號可以是單一字元，也可以是以單引號括起來的字串。  
  
#### 若要在項目之間插入逗號和空格  
  
-   使用以下的項目標記法：  
  
     `@(TXTFile, ', ')`  
  
## 範例  
 在這個範例中，[Exec](../msbuild/exec-task.md) 工作會執行 findstr 工具，在 Phrases.txt 檔案中找出指定的文字字串。  在 findstr 命令中，常值搜尋字串是以 **\/c:** 參數表示，因此在 `@(Phrase)` 項目清單中，項目之間會插入分隔符號 `/c:`。  
  
 這個範例的對等命令列命令為：  
  
 `findstr /i /c:hello /c:world /c:msbuild phrases.txt`  
  
```  
<Project DefaultTargets = "Find"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <ItemGroup>  
        <Phrase Include="hello"/>  
        <Phrase Include="world"/>  
        <Phrase Include="msbuild"/>  
    </ItemGroup>  
  
    <Target Name = "Find">  
        <!-- Find some strings in a file -->  
        <Exec Command="findstr /i /c:@(Phrase, ' /c:') phrases.txt"/>  
    </Target>  
</Project>  
```  
  
## 請參閱  
 [MSBuild Reference](../msbuild/msbuild-reference.md)   
 [項目](../msbuild/msbuild-items.md)