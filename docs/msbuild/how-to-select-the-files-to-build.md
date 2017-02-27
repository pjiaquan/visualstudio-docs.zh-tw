---
title: "如何：選取要建置的檔案 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Include 屬性 [MSBuild]"
  - "MSBuild, 加入檔案"
  - "MSBuild, 萬用字元"
ms.assetid: f5ff182f-7b3a-46fb-9335-37df54cfb8eb
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# 如何：選取要建置的檔案
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

建置 \(Build\) 內含許多檔案的專案時，您可以在專案檔中分別列出這些檔案，或者使用萬用字元，併入某一目錄或巢狀目錄集內的所有檔案。  
  
## 指定輸入  
 項目表示建置的輸入。  如需項目的詳細資訊，請參閱 [項目](../msbuild/msbuild-items.md)。  
  
 若要加入建置的檔案，這些檔案必須置於 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 專案檔的項目清單中。  若要在項目清單中加入多重檔案，您可以個別併入檔案，或使用萬用字元一次併入許多檔案。  
  
#### 若要個別宣告項目  
  
-   請以下列方式使用 `Include` 屬性 \(Attribute\)：  
  
     `<CSFile Include="form1.cs"/>`  
  
     \-或\-  
  
     `<VBFile Include="form1.vb"/>`  
  
    > [!NOTE]
    >  如果項目集合中的項目不在專案檔所在的目錄中，您必須指定完整\] 或 \[相對路徑項目。   例如：`Include="..\..\form2.cs"`。  
  
#### 若要宣告多個項目  
  
-   請以下列方式使用 `Include` 屬性 \(Attribute\)：  
  
     `<CSFile Include="form1.cs;form2.cs"/>`  
  
     \-或\-  
  
     `<VBFile Include="form1.vb;form2.vb"/>`  
  
## 使用萬用字元指定輸入  
 您也可以使用萬用字元，以遞迴方式併入子目錄中的所有檔案或特定檔案，做為建置的輸入。  如需萬用字元的詳細資訊，請參閱 [項目](../msbuild/msbuild-items.md)  
  
 以下範例所依據的專案含有位於下列目錄和子目錄中的圖形檔，專案檔則位於 Project 目錄。  
  
 Project\\Images\\BestJpgs  
  
 Project\\Images\\ImgJpgs  
  
 Project\\Images\\ImgJpgs\\Img1  
  
#### 若要併入 Image 目錄和子目錄中的所有 .jpg 檔案  
  
-   請使用下列 `Include` 屬性：  
  
     `Include="Images\**\*.jpg"`  
  
#### 若要併入開頭為 "img" 的所有 .jpg 檔案  
  
-   請使用下列 `Include` 屬性：  
  
     `Include="Images\**\img*.jpg"`  
  
#### 若要併入目錄中檔名結尾為 "jpgs" 的所有檔案  
  
-   使用下列其中一個 `Include` 屬性：  
  
     `Include="Images\**\*jpgs\*.*"`  
  
     \-或\-  
  
     `Include="Images\**\*jpgs\*"`  
  
## 將項目傳遞至工作  
 在專案檔的工作中，您可以使用 @\(\) 標記法指定整個項目清單做為建置的輸入。  無論分別列出檔案或使用萬用字元，都可以使用這個標記法。  
  
#### 若要使用所有 Visual C\# 或 Visual Basic 檔案做為輸入  
  
-   請以下列方式使用 `Include` 屬性：  
  
     `<CSC Sources="@(CSFile)">...</CSC>`  
  
     \-或\-  
  
     `<VBC Sources="@(VBFile)">...</VBC>`  
  
> [!NOTE]
>  您必須在項目中使用萬用字元指定建置的輸入，不能在 [Csc](../msbuild/csc-task.md) 或 [Vbc](../msbuild/vbc-task.md) 等 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 工作中使用 `Sources` 屬性來指定輸入。  下列範例在專案檔中無效：  
>   
>  `<CSC Sources="*.cs">...</CSC>`  
  
## 範例  
 在下列程式碼中，示範了個別併入所有輸入檔的專案：  
  
```  
<Project DefaultTargets="Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
    <PropertyGroup>  
        <Builtdir>built</Builtdir>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <CSFile Include="Form1.cs"/>  
        <CSFile Include="AssemblyInfo.cs"/>  
  
        <Reference Include="System.dll"/>  
        <Reference Include="System.Data.dll"/>  
        <Reference Include="System.Drawing.dll"/>  
        <Reference Include="System.Windows.Forms.dll"/>  
        <Reference Include="System.XML.dll"/>  
    </ItemGroup>  
  
    <Target Name="PreBuild">  
        <Exec Command="if not exist $(builtdir) md $(builtdir)"/>  
    </Target>  
  
    <Target Name="Compile" DependsOnTargets="PreBuild">  
        <Csc Sources="@(CSFile)"  
            References="@(Reference)"  
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).exe"  
            TargetType="exe" />  
    </Target>  
</Project>  
```  
  
## 範例  
 下列程式碼範例使用萬用字元併入所有 .cs 檔案：  
  
```  
<Project DefaultTargets="Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <PropertyGroup>  
        <builtdir>built</builtdir>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <CSFile Include="*.cs"/>  
  
        <Reference Include="System.dll"/>  
        <Reference Include="System.Data.dll"/>  
        <Reference Include="System.Drawing.dll"/>  
        <Reference Include="System.Windows.Forms.dll"/>  
        <Reference Include="System.XML.dll"/>  
    </ItemGroup>  
  
    <Target Name="PreBuild">  
        <Exec Command="if not exist $(builtdir) md $(builtdir)"/>  
    </Target>  
  
    <Target Name="Compile" DependsOnTargets="PreBuild">  
        <Csc Sources="@(CSFile)"  
            References="@(Reference)"  
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).exe"  
            TargetType="exe" />  
    </Target>  
</Project>  
```  
  
## 請參閱  
 [如何：從組建中排除檔案](../msbuild/how-to-exclude-files-from-the-build.md)   
 [項目](../msbuild/msbuild-items.md)