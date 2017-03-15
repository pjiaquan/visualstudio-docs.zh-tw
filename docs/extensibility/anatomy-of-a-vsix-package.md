---
title: "VSIX 套件的剖析 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- visual studio extension
- vsix
- packages
ms.assetid: 8b86d62f-c274-4e91-82e0-38cdb9a423d5
caps.latest.revision: 15
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
ms.sourcegitcommit: 7278fb37984b92a6a07823c552db5c59a446d0d2
ms.openlocfilehash: 633db03670180ac83c5c936f66953fb38d4ebd67
ms.lasthandoff: 02/22/2017

---
# <a name="anatomy-of-a-vsix-package"></a>VSIX 套件的剖析
VSIX 套件是.vsix 檔案，其中包含一或多個 Visual Studio 擴充功能，以及 Visual Studio 會使用分類，並安裝擴充功能的中繼資料。 中繼資料包含在 VSIX 資訊清單和 [Content_Types].xml 檔案中。 VSIX 套件也包含一或多個 Extension.vsixlangpack 檔案來提供當地語系化的安裝程式文字，而且可能包含其他的 VSIX 套件安裝相依項目。  
  
 VSIX 套件格式遵循開放封裝慣例 (OPC) 標準。 封裝包含二進位檔和支援檔案，以及 [Content_Types].xml 檔案和.vsix 資訊清單檔案。 一個 VSIX 套件可能包含多個專案或有其本身的資訊清單的多個封裝的輸出。  
  
> [!NOTE]
>  包含在 VSIX 套件的檔案名稱不得包含空格，也不會保留在統一資源識別元 (URI)，做為字元定義下[ \[RFC2396\]](http://go.microsoft.com/fwlink/?LinkId=90339)。  
  
## <a name="the-vsix-manifest"></a>VSIX 資訊清單  
 VSIX 資訊清單包含要安裝擴充功能，如下所示 VSX 結構描述的相關資訊。 如需詳細資訊，請參閱[VSIX 擴充功能結構描述 1.0 參考](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)。 範例 VSIX 資訊清單，請參閱[PackageManifest 元素 （根項目、 VSX 結構描述）](http://msdn.microsoft.com/en-us/f8ae42ba-775a-4d2b-976a-f556e147f187)。  
  
 VSIX 資訊清單必須命名為`extension.vsixmanifest`包含.vsix 檔案中時。  
  
## <a name="the-content"></a>內容  
 VSIX 套件可能包含範本、 工具箱項目、 VSPackages 或任何其他種類的 Visual Studio 所支援的延伸模組。  
  
## <a name="language-packs"></a>語言套件  
 VSIX 套件可能包含一次或更多的 Extension.vsixlangpack 檔案，在安裝期間提供當地語系化的文字。 如需詳細資訊，請參閱[當地語系化 VSIX 套件](../extensibility/localizing-vsix-packages.md)。  
  
## <a name="dependencies-and-references"></a>相依性和參考  
 VSIX 套件可能包含其他 VSIX 套件做為參考。 每個這些其他封裝必須包含它自己的 VSIX 資訊清單。  
  
 如果使用者嘗試安裝具有相依性的擴充功能，安裝程式會確認使用者系統上已安裝的必要的組件。 如果找不到必要的組件，**擴充功能和更新**顯示遺漏的組件的清單。  
  
 如果延伸模組資訊清單包含一或多個[參考](http://msdn.microsoft.com/en-us/32c52934-e81e-4b53-8cb6-4df45ef7bfa8)項目，**擴充功能和更新**比較每個參考系統已安裝的擴充功能的資訊清單，並且會安裝受參考的延伸模組，如果尚未安裝。 如果已安裝較早版本的參考延伸模組，較新版本取代它。  
  
 多專案方案中的專案包含另一個專案的參考相同方案中，如果 VSIX 套件包含該專案的相依性。 您可以依序按一下 參考內部的專案，然後在 覆寫這個行為**屬性** 視窗中，設定**輸出群組包含在 VSIX**屬性`BuiltProjectOutputGroup`。  
  
 若要在 VSIX 套件中包含從參考組件的附屬 Dll，新增`SatelliteDllsProjectOutputGroup`至**輸出群組包含在 VSIX**屬性。  
  
## <a name="installation-location"></a>安裝位置  
 在安裝期間，**擴充功能和更新**求取在資料夾之下的 %localappdata%\microsoft\visualstudio\14.0\extensions VSIX 套件的內容。  
  
 根據預設，安裝只適用於目前的使用者，因為 %localappdata%是使用者特有的目錄。 不過，如果您設定[AllUsers](http://msdn.microsoft.com/en-us/ac817f50-3276-4ddb-b467-8bbb1432455b)資訊清單的項目`True`，將會在安裝延伸模組...\\ *VisualStudioInstallationFolder*\Common7\IDE\Extensions，便可以在電腦的所有使用者。  
  
## <a name="contenttypesxml"></a>[Content_Types].xml  
 [Content_Types].xml 檔案識別此展開的.vsix 檔案中的檔案類型。 Visual Studio 安裝套件時使用此檔案，但不會安裝檔案本身。 如需此檔案的詳細資訊，請參閱[結構 [Content_types].xml 檔案](the-structure-of-the-content-types-dot-xml-file.md)。  
  
 [Content_Types].xml 檔案需要由開放封裝慣例 (OPC) 標準。 如需有關 OPC 的詳細資訊，請參閱[OPC: 新標準的封裝您的資料](http://go.microsoft.com/fwlink/?LinkID=148207)MSDN 網站上。
