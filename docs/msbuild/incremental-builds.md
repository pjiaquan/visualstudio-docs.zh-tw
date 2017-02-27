---
title: "累加建置 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "msbuild, 累加建置"
ms.assetid: 325e28c7-4838-4e3f-b672-4586adc7500c
caps.latest.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 8
---
# 累加建置
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

累加建置是最佳化的建置，如此才不會執行擁有最新輸出檔 \(相對於其對應的輸入檔\) 的目標。  目標項目 \(Element\) 可以有 `Inputs` 屬性 \(Attribute\) 和 `Outputs` 屬性，前者表示目標預期做為輸入的項目 \(Item\)，後者則表示目標會產生為輸出的項目 \(Item\)。  MSBuild 會試著在這些屬性值之間尋找一對一的對應。  如果有一對一的對應存在，MSBuild 會比較每一個輸入項目的時間戳記與其對應輸出項目的時間戳記。  沒有一對一對應的輸出檔會與所有輸入檔進行比較。  如果項目的輸出檔與輸入檔同齡或是前者較舊，該項目則可視為最新狀態。  
  
 如果所有輸出項目都是最新的，MSBuild 便會略過該目標。  目標的這個「*累加建置*」\(Incremental Build\) 可以大幅改善建置速度。  如果只有部分檔案是最新的，MSBuild 則會執行該目標，但是略過最新的項目，由此讓所有項目成為最新狀態。  這個程序稱為「*部分累加建置*」\(Partial Incremental Build\)。  
  
 一對一對應通常是由項目轉換所產生。  如需詳細資訊，請參閱[轉換](../msbuild/msbuild-transforms.md)。  
  
 請參考下列目標：  
  
```  
<Target Name="Backup" Inputs="@(Compile)"   
    Outputs="@(Compile->'$(BackupFolder)%(Identity).bak')">  
    <Copy SourceFiles="@(Compile)" DestinationFiles=  
        "@(Compile->'$(BackupFolder)%(Identity).bak')" />  
</Target>  
```  
  
 `Compile` 項目類型所代表的檔案集會複製到備份目錄。  備份檔的副檔名為 .bak。  如果在執行備份目標之後，並未刪除或修改 `Compile` 項目類型所代表的檔案或是對應的備份檔，則會在後續的建置中略過此備份目標。  
  
## 輸出推斷  
 MSBuild 會比較目標的 `Inputs` 和 `Outputs` 屬性，以決定是否必須執行目標。  理想上，不論是否執行關聯的目標，在完成累加建置之後存在的檔案集都應該維持不變。  因為工作所建立或修改的屬性 \(Property\) 和項目可能會影響組建，所以即使略過了會造成影響的目標，MSBuild 仍必須推斷其值。  這稱為「*輸出推斷*」\(Output Inference\)。  
  
 具有下列三種情況：  
  
-   目標的 `Condition` 屬性 \(Attribute\) 評估為 `false`。  在此情況下，目標並未執行，而且對組建沒有任何影響。  
  
-   目標具有最新的輸出，並予以執行以產生最新輸出。  
  
-   目標沒有最新的輸出，並予以略過。  MSBuild 會評估目標並且變更項目和屬性 \(Property\)，彷彿已執行過目標一樣。  
  
 若要支援累加編譯，工作必須確保任何 `Output` 項目 \(Element\) 的 `TaskParameter` 屬性 \(Attribute\) 值等於工作輸入參數。  以下是一些範例：  
  
```  
<CreateProperty Value="123">  
    <Output PropertyName="Easy" TaskParameter="Value" />  
</CreateProperty>  
```  
  
 這會建立 Easy 屬性 \(Property\)，而不論是執行或略過目標，該屬性的值都是 "123"。  
  
```  
<CreateItem Include="a.cs;b.cs">  
    <Output ItemName="Simple" TaskParameter="Include" />  
</CreateItem>  
```  
  
 這會建立 Simple 項目類型，而不論是執行或略過目標，該類型都具有兩個項目："a.cs" 和 "b.cs"。  
  
 開始 MSBuild 3.5 時，系統會自動對目標中的項目和屬性群組執行輸出推斷。  目標不需要 `CreateItem` 工作，應予以避免。  此外，`CreateProperty` 工作只能用於目標，以判斷目標是否已經執行。  
  
## 判斷目標是否已經執行  
 由於執行輸出推斷，所以您必須將 `CreateProperty` 工作加入至目標以檢查其屬性和項目，以便判斷目標是否已經執行。  將 `CreateProperty` 工作加入至目標，並將 `TaskParameter` 為 "ValueSetByTask" 的 `Output` 項目提供給它。  
  
```  
<CreateProperty Value="true">  
    <Output TaskParameter="ValueSetByTask" PropertyName="CompileRan" />  
</CreateProperty>  
```  
  
 這會建立 CompileRan 屬性並提供 `true` 值，但僅限於已經執行目標時。  如果目標已經略過，則不會建立 CompileRan。  
  
## 請參閱  
 [目標](../msbuild/msbuild-targets.md)