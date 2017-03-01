---
title: "新產生的專案︰ 在幕後，第二部 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 73ce91d8-0ab1-4a1f-bf12-4d3c49c01e13
caps.latest.revision: 14
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: c5f214774a5cf0aeb3896004632f8a2076782b14
ms.lasthandoff: 02/22/2017

---
# <a name="new-project-generation-under-the-hood-part-two"></a>新產生的專案︰ 在幕後，第二部
中[產生新的專案︰ 所以然、 第一段](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)我們看到如何**新的專案**對話方塊方塊會填入。 假設您已選取**Visual C# Windows 應用程式**、 填寫**名稱**和**位置**文字方塊中，然後按下 [確定]。  
  
## <a name="generating-the-solution-files"></a>產生的方案檔  
 選擇應用程式範本會指示[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]解壓縮及開啟對應的.vstemplate 檔，以及啟動來解譯此檔案中的 XML 命令範本。 這些命令會建立新的或現有方案中專案和專案項目。  
  
 範本會解壓縮從相同的.vstemplate 檔案的.zip 資料夾稱為項目範本的來源檔案。 範本會將這些檔案複製到新的專案，並據此自訂它們。 如需專案和項目範本的概觀，請參閱[NIB: Visual Studio 範本](http://msdn.microsoft.com/en-us/141fccaa-d68f-4155-822b-27f35dd94041)。  
  
### <a name="template-parameter-replacement"></a>範本參數取代  
 當範本複製至新的專案項目範本時，它會取代任何範本參數來自訂檔案的字串。 樣板參數是特殊的語彙基元，是前後錢幣符號，例如、 $date$。  
  
 讓我們看看一般專案項目範本。 解壓縮並檢查 Program.cs Program Files\Microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip 資料夾中。  
  
```  
using System;  
using System.Collections.Generic;  
using System.Windows.Forms;  
  
namespace $safeprojectname$  
{  
    static class Program  
    {  
        // source code deleted here for brevity  
    }  
}  
```  
  
 如果您建立新的 Windows 應用程式專案，名為 Simple 時，範本會取代`$safeprojectname$`參數與專案的名稱。  
  
```  
using System;  
using System.Collections.Generic;  
using System.Windows.Forms;  
  
namespace Simple  
{  
    static class Program  
    {  
        // source code deleted here for brevity  
    }  
}  
```  
  
 如需範本參數的完整清單，請參閱[範本參數](../../ide/template-parameters.md)。  
  
## <a name="a-look-inside-a-vstemplate-file"></a>深入了解。VSTemplate 檔案  
 基本.vstemplate 檔案具有此格式  
  
```  
<VSTemplate Version="2.0.0"     xmlns="http://schemas.microsoft.com/developer/vstemplate/2005"     Type="Project">  
    <TemplateData>  
    </TemplateData>  
    <TemplateContent>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 我們探討了\<TemplateData > 一節中[產生新的專案︰ 所以然、 第一段](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)。 本章節中的標記用來控制的外觀**新的專案**對話方塊。  
  
 中的標記\<TemplateContent > 一節控制項產生新的專案和專案項目。 以下是\<TemplateContent > 區段 cswindowsapplication.vstemplate files\microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip 資料夾中的。  
  
```  
<TemplateContent>  
  <Project File="WindowsApplication.csproj" ReplaceParameters="true">  
    <ProjectItem ReplaceParameters="true"  
      TargetFileName="Properties\AssemblyInfo.cs">  
      AssemblyInfo.cs  
    </ProjectItem>  
    <ProjectItem TargetFileName="Properties\Resources.resx">  
      Resources.resx  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Resources.Designer.cs">  
      Resources.Designer.cs  
    </ProjectItem>  
    <ProjectItem TargetFileName="Properties\Settings.settings">  
      Settings.settings  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Settings.Designer.cs">  
      Settings.Designer.cs  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true" OpenInEditor="true">  
      Form1.cs  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true">  
      Form1.Designer.cs  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true">  
      Program.cs  
    </ProjectItem>  
  </Project>  
</TemplateContent>  
```  
  
 \<專案 > 標記控制的專案時，產生和\<專案項目 > 標記控制的專案項目產生。 如果參數 ReplaceParameters 為 true，範本會自訂專案檔或項目中的所有範本參數。 在此情況下，所有專案項目會都自訂，Settings.settings 除外。  
  
 TargetFileName 參數指定的名稱和產生的專案檔案或項目的相對路徑。 這可讓您建立專案的資料夾結構。 如果您沒有指定這個引數，專案項目會有同名的專案項目範本。  
  
 所產生的 Windows 應用程式資料夾結構看起來像這樣︰  
  
 ![SimpleSolution](../../extensibility/internals/media/simplesolution.png "SimpleSolution")  
  
 第一個且唯一\<專案 > 中的範本讀取的標記︰  
  
```  
<Project File="WindowsApplication.csproj" ReplaceParameters="true">  
```  
  
 這會指示新的專案範本來建立複製和自訂範本項目 windowsapplication.csproj Simple.csproj 專案檔。  
  
### <a name="designers-and-references"></a>設計工具和參考  
 您可以看到 [方案總管] 中 [屬性] 資料夾存在，且包含預期的檔案。 關於專案所參考但設計工具檔案相依性，例如 Resources.resx，到了 Resources.Designer.cs 和 Form1.cs 到 form1.designer.cs 嗎？  這些是設定 Simple.csproj 檔案時產生。  
  
 以下是\<ItemGroup > 從 Simple.csproj 所建立的專案參考︰  
  
```  
<ItemGroup>  
    <Reference Include="System" />  
    <Reference Include="System.Data" />  
    <Reference Include="System.Deployment" />  
    <Reference Include="System.Drawing" />  
    <Reference Include="System.Windows.Forms" />  
    <Reference Include="System.Xml" />  
</ItemGroup>  
```  
  
 您所見，這些是出現在 [方案總管] 中的六個專案參考。 以下是從另一個區段\<ItemGroup >。 為了清楚起見，已被刪除的程式碼行數。 這個區段會使相依於 Settings.settings Settings.Designer.cs:  
  
```  
<ItemGroup>  
    <Compile Include="Properties\Settings.Designer.cs">  
        <DependentUpon>Settings.settings</DependentUpon>  
    </Compile>  
</ItemGroup>  
```  
  
## <a name="see-also"></a>另請參閱  
 [新產生的專案︰ 在幕後，第一部](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)  
 [ MSBuild](../../msbuild/msbuild1.md)
