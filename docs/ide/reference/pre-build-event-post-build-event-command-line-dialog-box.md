---
title: "建置前事件/建置後事件命令列對話方塊 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cs.ProjectPropertiesBuildEventsBuilder"
  - "vb.ProjectPropertiesBuildEventsBuilder"
helpviewer_keywords: 
  - "$(SolutionExt)"
  - "$(ProjectDir)"
  - "$(TargetPath)"
  - "$(ProjectExt)"
  - "$(TargetFileName)"
  - "$(PlatformName)"
  - "$(SolutionName)"
  - "巨集，建置事件"
  - "$(SolutionPath)"
  - "$(ProjectPath)"
  - "$(ProjectFileName)"
  - "$(DevEnvDir)"
  - "$(TargetName)"
  - "$(TargetDir)"
  - "$(SolutionDir)"
  - "$(TargetExt)"
  - "$(OutDir)"
  - "$(ConfigurationName)"
  - "$(SolutionFileName)"
  - "$(ProjectName)"
  - "建置事件，巨集"
ms.assetid: d49b2c57-24bf-4fb2-8351-5c4b6cca938f
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# 建置前事件/建置後事件命令列對話方塊
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

您可以直接在編輯方塊中輸入[專案設計工具、建置事件 \(C\#\)](../../ide/reference/build-events-page-project-designer-csharp.md) 的建置前或建置後事件，或者從可用的巨集清單中選取建置前巨集和建置後巨集。  
  
> [!NOTE]
>  如果專案是最新的且未觸發任何建置，則不會執行建置前事件。  
  
## UI 項目清單  
 **命令列編輯方塊**  
 包含要對建置前或建置後執行的事件。  
  
> [!NOTE]
>  在執行 .bat 檔的所有建置後命令之前加入 `call` 陳述式。  例如，`call C:\MyFile.bat` 或 `call C:\MyFile.bat call C:\MyFile2.bat`。  
  
 **巨集**  
 展開編輯方塊，以顯示要在命令列編輯方塊中插入的巨集清單。  
  
 **巨集表**  
 列出可用的巨集和其值。  如需每個巨集的說明，請參閱底下的巨集。  您一次只能選取一個巨集，將其插入命令列編輯方塊。  
  
 **Insert**  
 將巨集表中選取的巨集插入命令列編輯方塊。  
  
### 巨集  
 在多重選取的情況下，您可以使用這些巨集指定檔案位置，或取得輸入檔的真正名稱。  這些巨集是不區分大小寫的。  
  
|巨集|描述|  
|--------|--------|  
|`$(ConfigurationName)`|目前專案組態的名稱 \(例如 "Debug"\)。|  
|`$(OutDir)`|相對於專案目錄的輸出檔目錄路徑。  這將解析為 \[輸出目錄\] 屬性 \(Property\) 的值。  尾端會加上反斜線「\\」。|  
|`$(DevEnvDir)`|Visual Studio 安裝目錄 \(定義為磁碟機 \+ 路徑\);包括後面的反斜線「\\」。|  
|`$(PlatformName)`|目前的目標平台名稱。  例如 "AnyCPU"。|  
|`$(ProjectDir)`|專案的目錄 \(定義為磁碟機 \+ 路徑\)，尾端會加上反斜線「\\」。|  
|`$(ProjectPath)`|專案的絕對路徑名稱 \(定義為磁碟機 \+ 路徑 \+ 主檔名 \+ 副檔名\)。|  
|`$(ProjectName)`|專案的主檔名。|  
|`$(ProjectFileName)`|專案的檔名 \(定義為主檔名 \+ 副檔名\)。|  
|`$(ProjectExt)`|專案檔的副檔名。  在副檔名之前包括一個 '.'。|  
|`$(SolutionDir)`|方案的目錄 \(定義為磁碟機 \+ 路徑\)，尾端會加上反斜線「\\」。|  
|`$(SolutionPath)`|方案的絕對路徑名稱 \(定義為磁碟機 \+ 路徑 \+ 主檔名 \+ 副檔名\)。|  
|`$(SolutionName)`|方案的主檔名。|  
|`$(SolutionFileName)`|方案的檔名 \(定義為主檔名 \+ 副檔名\)。|  
|`$(SolutionExt)`|方案的副檔名。  在副檔名之前包括一個 '.'。|  
|`$(TargetDir)`|建置主要輸出檔的目錄 \(定義為磁碟機 \+ 路徑\)。  尾端會加上反斜線「\\」。|  
|`$(TargetPath)`|建置主要輸出檔的絕對路徑名稱 \(定義為磁碟機 \+ 路徑 \+ 主檔名 \+ 副檔名\)。|  
|`$(TargetName)`|建置主要輸出檔的主檔名。|  
|`$(TargetFileName)`|建置主要輸出檔的檔名 \(定義為主檔名 \+ 副檔名\)。|  
|`$(TargetExt)`|建置主要輸出檔的副檔名。  在副檔名之前包括一個 '.'。|  
  
## 請參閱  
 [在 Visual Studio 中指定自訂建置事件](../../ide/specifying-custom-build-events-in-visual-studio.md)   
 [專案設計工具、建置事件 \(C\#\)](../../ide/reference/build-events-page-project-designer-csharp.md)   
 [如何：指定建置事件 \(Visual Basic\)](../Topic/How%20to:%20Specify%20Build%20Events%20\(Visual%20Basic\).md)   
 [如何：指定建置事件 \(C\#\)](../../ide/how-to-specify-build-events-csharp.md)