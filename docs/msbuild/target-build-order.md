---
title: "目標建置順序 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "msbuild，建置順序"
ms.assetid: f4a26339-9f9a-497a-9aa6-0797183d450d
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# 目標建置順序
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

如果某個目標的輸入相依於其他目標的輸出，則必須將目標排序。  您可以使用這些屬性來指定目標的執行順序:  
  
-   `InitialTargets`.  這個 `Project` 屬性指定最先執行的目標，，即使目標指定在命令列上或 `DefaultTargets` 屬性。  
  
-   `DefaultTargets`.  這個 `Project` atttribute 指定哪些目標執行目標，則在命令列上未明確指定。  
  
-   `DependsOnTargets`.  這個 `Target` 屬性必須執行的目標，在此目標可執行之前。  
  
-   `BeforeTargets` 和 `AfterTargets`。  這些 `Target` 屬性指定這個目標應該在指定的目標 \(MSBuild 4.0\) 之前或之後執行。  
  
 在建置期間一個目標只能執行一次，即使組建中的後續目標對此目標具有相依性亦是如此。  一旦執行目標後，其對於組建的貢獻便已完成。  
  
 目標可以具有 `Condition` 屬性。  如果對 `false`的指定條件評估為，此目標則不會執行而且對組建沒有任何影響。  如需條件的詳細資訊，請參閱 [Conditions](../msbuild/msbuild-conditions.md)。  
  
## 初始目標  
 [專案](../msbuild/project-element-msbuild.md) 項目的 `InitialTargets` 屬性指定最先執行的目標，，即使目標指定在命令列上或 `DefaultTargets` 屬性。  初始目標通常用於檢查錯誤。  
  
 `InitialTargets` 屬性的值可以是以分號分隔，目標排序清單。  下列範例指定 `Warm` 目標執行， `Eject` 物件會執行。  
  
```  
<Project InitialTargets="Warm;Eject" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
```  
  
 匯入的專案可能有自己的 `InitialTargets` 屬性。  所有初始目標會彙總在一起並依序執行。  
  
 如需詳細資訊，請參閱[如何：指定要優先建置的目標](../msbuild/how-to-specify-which-target-to-build-first.md)。  
  
## 預設目標  
 [專案](../msbuild/project-element-msbuild.md) 項目的 `DefaultTargets` 屬性指定一個或多個目標建置目標，則在命令列上未明確指定。  
  
 `DefaultTargets` 屬性的值可以是以分號分隔\)，預設目標排序清單。  下列範例指定 `Clean` 目標執行， `Build` 物件會執行。  
  
```  
<Project DefaultTargets="Clean;Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
```  
  
 您可以在命令列中， **\/target** 參數可以覆寫預設目標。  下列範例指定 `Build` 目標執行， `Report` 物件會執行。  當您以此方式指定目標，所有預設目標被忽略。  
  
 `msbuild /target:Build;Report`  
  
 如果初始目標和預設目標，，和，如果命令未指定目標，則 MSBuild 會先執行初始目標，然後執行預設目標。  
  
 匯入的專案可能有自己的 `DefaultTargets` 屬性。  第一個遇到的 `DefaultTargets` 屬性會決定將執行哪些預設目標。  
  
 如需詳細資訊，請參閱[如何：指定要優先建置的目標](../msbuild/how-to-specify-which-target-to-build-first.md)。  
  
## 第一個目標  
 如果沒有初始目標、預設目標或命令列目標，則 MSBuild 會執行它在專案檔或任何匯入的專案檔中遇到的第一個目標。  
  
## 目標相依性  
 目標可以描述彼此的相依性關係。  `DependsOnTargets` 屬性表示某個目標相依於其他目標。  例如：  
  
```  
<Target Name="Serve" DependsOnTargets="Chop;Cook" />  
```  
  
 告知 MSBuild `Serve` 目標相依於 `Chop` 物件和 `Cook` 物件。  在執行 `Serve` 目標之前， MSBuild 會執行 `Chop` 目標，然後執行 `Cook` 目標。  
  
## 在目標之前並在目標之後  
 在 MSBuild 4.0 中，您可以使用 `BeforeTargets` 和 `AfterTargets` 屬性指定目標順序。  
  
 請考慮下列指令碼。  
  
```  
<Project DefaultTargets="Compile;Link" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="Compile">  
        <Message Text="Compiling" />  
    </Target>  
    <Target Name="Link">  
        <Message Text="Linking" />  
    </Target>  
</Project>  
```  
  
 建立執行時，在 `Compile` 目標之後，不過，中的目標 `Optimize` ，在 `Link` 物件中，將下列目標任何 `Project` 項目之前。  
  
```  
<Target Name="Optimize"   
    AfterTargets="Compile" BeforeTargets="Link">  
    <Message Text="Optimizing" />  
</Target>  
```  
  
## 決定目標建置順序  
 MSBuild 決定的目標建置順序如下所示：  
  
1.  `InitialTargets` 執行目標。  
  
2.  會執行由 **\/target** 參數在命令列上指定的目標。  如果您在命令列上未指定目標，則 `DefaultTargets` 執行目標。  如果都不存在，則為遇到的第一個目標執行。  
  
3.  會評估目標的 `Condition` 屬性。  如果 `Condition` 屬性是 `false`的存在和評估，此目標則不會執行並沒有對組建的進一步作用。  
  
4.  在執行目標之前，會先執行其 `DependsOnTargets` 目標。  
  
5.  在執行目標之前，會先執行列於 `BeforeTargets` 屬性中的任何目標。  
  
6.  在執行目標之前，會先比較其 `Inputs` 屬性和 `Outputs` 屬性。  如果 MSBuild 判斷所有輸出檔已過期的參考對應的輸入檔案，則 MSBuild 會執行目標。  否則，MSBuild 會略過此目標。  
  
7.  在執行或略過目標之後，會執行列於 `AfterTargets` 屬性中的任何目標。  
  
## 請參閱  
 [目標](../msbuild/msbuild-targets.md)