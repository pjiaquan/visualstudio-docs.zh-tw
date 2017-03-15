---
title: "Visual Studio 範本資訊清單結構描述參考 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bc7d0a81-0df5-41a9-a912-1b30e5da1d13
caps.latest.revision: 3
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 512014c5070e4314ad2b7d0e8c5c404c43f32cd9
ms.openlocfilehash: 0f4abf286dc8b1cf00e47468ddaa4831747a059d
ms.lasthandoff: 02/22/2017

---
# <a name="visual-studio-template-manifest-schema-reference"></a>Visual Studio 範本資訊清單結構描述參考
此結構描述會描述針對 Visual Studio 專案或項目樣板所產生的 Visual Studio 範本資訊清單 (.vstman) 檔案格式，並描述的位置和其他範本的相關資訊。  
  
 ︰ 由於有個別的項目和專案範本目錄中，資訊清單應該永遠不會有項目和專案範本的混合。  
  
> [!IMPORTANT]
>  使用 Visual Studio 2017 從這份資訊清單。  
  
## <a name="vstemplatemanifest-element"></a>VSTemplateManifest 項目  
 資訊清單的根項目。  
  
### <a name="attributes"></a>屬性  
  
-   **版本**︰ 字串，表示範本資訊清單的版本。 必要項。  
  
-   **地區設定**︰ 字串，表示範本資訊清單的地區設定的地區設定。 地區設定值套用至所有範本，因此您必須使用不同的資訊清單，每個地區設定。 選擇項。  
  
### <a name="child-elements"></a>子項目  
  
-   **VSTemplateContainer**選擇性。  
  
-   **VSTemplateDir**選擇性。  
  
### <a name="parent-element"></a>Parent 項目  
 無。  
  
## <a name="vstemplatecontainer"></a>VSTemplateContainer  
 資訊清單的項目範本的容器。 資訊清單中有一個範本容器，它會定義每個範本。  
  
### <a name="attributes"></a>屬性  
 **VSTemplateType** ︰ 指定的範本類型的字串值 (`"Project"`， `"Item"`，或`"ProjectGroup"`)。 必要  
  
### <a name="child-elements"></a>子項目  
  
-   **RelativePathOnDisk**︰ 磁碟上的範本檔案的相對路徑。 此位置也會定義範本的位置在範本樹狀目錄中所示**新的專案**或**新項目** 對話方塊。 部署目錄和個別檔案為範本，此路徑是指包含範本檔案的目錄。 範本部署為.zip 檔案，此路徑應.zip 檔案的路徑。  
  
-   **VSTemplateHeader** : A [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)描述標頭的項目。  
  
### <a name="parent-element"></a>Parent 項目  
 **VSTemplateManifest**  
  
## <a name="vstemplatedir"></a>VSTemplateDir  
 描述範本所在的目錄。 資訊清單可以包含多個**VSTemplateDir**提供當地語系化的名稱和排序順序目錄控制其外觀範本類別目錄樹狀結構中的項目。  
  
 因為它們的設計， **VSTemplateDir**應該只在非地區設定的指定資訊清單中出現項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子項目  
  
-   **RelativePath**︰ 範本的路徑。 可以有只有一個項目，每個路徑，因此第一個會為所有的資訊清單中獲得優先權。  
  
-   **LocalizedName**: A **NameDescriptionIcon**項目，指定當地語系化的名稱。 選擇項。  
  
-   **SortOrder** ︰ 字串，指定排序次序。 選擇項。  
  
-   **ParentFolderOverrideName**︰ 覆寫的父資料夾的名稱。 選擇項。 這個項目有**名稱**屬性，也就是指定名稱的字串值。  
  
### <a name="parent-element"></a>Parent 項目  
 **VSTemplateManifest**  
  
## <a name="namedescriptionicon"></a>NameDescriptionIcon  
 指定的名稱和描述，可能是當地語系化的範本。 請參閱**LocalizedName**上方。  
  
### <a name="attributes"></a>屬性  
  
-   **封裝**︰ 指定的封裝的字串值。 選擇項。  
  
-   **識別碼**︰ 字串值，指定識別碼。 選擇項。  
  
### <a name="child-elements"></a>子項目  
 無。  
  
### <a name="parent-element"></a>Parent 項目  
 **LocalizedName**  
  
## <a name="examples"></a>範例  
 以下是專案範本.vstman 檔案的範例。  
  
```xml  
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">  
  <VSTemplateContainer TemplateType="Project">  
    <RelativePathOnDisk>CSharp\1033\TestProjectTemplate</RelativePathOnDisk>  
    <TemplateFileName>TestProjectTemplate.vstemplate</TemplateFileName>  
    <VSTemplateHeader>  
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
        <Name>TestProjectTemplate</Name>  
        <Description>TestProjectTemplate</Description>  
        <Icon>TestProjectTemplate.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>  
        <SortOrder>1000</SortOrder>  
        <TemplateID>aac0aeea-7883-4003-992f-937d53d70ab1</TemplateID>  
        <CreateNewFolder>true</CreateNewFolder>  
        <DefaultName>TestProjectTemplate</DefaultName>  
        <ProvideDefaultName>true</ProvideDefaultName>  
      </TemplateData>  
    </VSTemplateHeader>  
  </VSTemplateContainer>  
</VSTemplateManifest>  
  
```  
  
 項目範本.vstman 檔案的範例如下。  
  
```  
VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">  
  <VSTemplateContainer TemplateType="Item">  
    <RelativePathOnDisk>CSharp\1033\ItemTemplate1</RelativePathOnDisk>  
    <TemplateFileName>ItemTemplate1.vstemplate</TemplateFileName>  
    <VSTemplateHeader>  
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
        <Name>ItemTemplate1</Name>  
        <Description>ItemTemplate1</Description>  
        <Icon>ItemTemplate1.ico</Icon>  
        <TemplateID>bfeadf8e-a251-4109-b605-516b88e38c8d</TemplateID>  
        <ProjectType>CSharp</ProjectType>  
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>  
        <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
        <DefaultName>Class.cs</DefaultName>  
      </TemplateData>  
    </VSTemplateHeader>  
  </VSTemplateContainer>  
</VSTemplateManifest>  
  
```
