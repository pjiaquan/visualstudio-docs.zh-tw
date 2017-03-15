---
title: "建立自訂專案和項目範本 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 586da5dc-f678-402b-afd0-0332959fd7a6
caps.latest.revision: 10
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
ms.openlocfilehash: be53e0aa5179a38f9c2079513661607b45767a11
ms.lasthandoff: 02/22/2017

---
# <a name="creating-custom-project-and-item-templates"></a>建立自訂專案和項目範本
Visual Studio SDK 包含專案範本建立自訂專案範本和自訂的項目範本。 這些範本包含一些常見的參數替代項目，並建置為 zip 檔案。 自動部署，並且不可以在實驗執行個體。 您必須將複製的 zip 檔案的位置  
  
 建立範本可讓您範本包含在較大的擴充功能。 這可讓您實作上的原始程式檔的版本控制和建置成單一 VSIX 套件的一組範本專案。  
  
 基本的範本建立的情況下，您應該使用**匯出範本**精靈，它會輸出至壓縮檔。 如需建立基本範本的詳細資訊，請參閱[建立專案和項目範本](../ide/creating-project-and-item-templates.md)。  
  
 從 Visual Studio 2017，自訂專案和項目範本掃瞄將不再執行。 相反地，延伸模組必須提供範本描述這些範本的安裝位置的資訊清單檔案。 您可以使用 Visual Studio 2017 來更新您的 VSIX 擴充功能。 如果您部署使用 MSI 擴充功能，您必須以手動方式產生範本資訊清單檔案。 如需詳細資訊，請參閱[升級自訂專案和項目範本以供 Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md)。 範本的資訊清單結構描述會記載在[Visual Studio 範本資訊清單結構描述參考](../extensibility/visual-studio-template-manifest-schema-reference.md)。  
  
## <a name="creating-a-project-template"></a>建立專案範本  
  
1.  建立專案範本的專案。 您可以找到中的專案範本**新的專案** 對話方塊中的，在 Visual Basic 或 Visual C#**擴充性**資料夾。  
  
     範本會產生的類別檔案、 圖示、.vstemplate 檔、 名為 ProjectTemplate.vbproj 或 ProjectTemplate.csproj，可以讓您編輯專案檔和其他專案類型通常會產生一些檔案、 resources.resx 檔案、 AssemblyInfo 檔案中和.settings 檔案。 每個程式碼檔案包含通用參數替換適當的位置。  
  
2.  加入和移除專案對專案所需的項目。 請勿移除.vstemplate 檔案、 AssemblyInfo 檔案或可編輯的專案檔案。  
  
3.  更新以反映任何新增和刪除的.vstemplate 檔。 [專案](../extensibility/project-element-visual-studio-templates.md)元素必須包含[專案項目](../extensibility/projectitem-element-visual-studio-item-templates.md)每個檔案要包含在範本中的項目。  
  
4.  修改程式碼檔案和其他使用者端的內容，並新增適當的參數替代項目。  
  
5.  修改視需要產生的內容。  
  
6.  建置專案。  
  
     Visual Studio 建立.zip 檔案，其中包含您的範本。 未部署，並不是無法在實驗性執行個體。  
  
## <a name="creating-an-item-template"></a>建立項目範本  
  
1.  建立項目範本的專案。  
  
     範本會產生的類別檔案、 圖示、.vstemplate 檔案和 AssemblyInfo 檔案。 將類別檔案包含一些常見的參數替代項目。  
  
2.  加入和移除專案對專案所需的項目。  
  
3.  更新以反映任何新增和刪除的.vstemplate 檔。 [專案](../extensibility/project-element-visual-studio-templates.md)元素必須包含[專案項目](../extensibility/projectitem-element-visual-studio-item-templates.md)每個檔案要包含在範本中的項目。  
  
4.  修改程式碼檔案和其他使用者端的內容，並新增適當的參數替代項目。  
  
5.  修改產生所需的內容。  
  
6.  建置專案。  
  
     Visual Studio 會建立壓縮的檔案，包含您的範本。 未部署，並不是無法在實驗性執行個體。  
  
## <a name="deployment"></a>部署  
  
#### <a name="to-deploy-the-project-or-item-template"></a>若要部署專案或項目範本  
  
1.  建立 VSIX 專案。 如需詳細資訊，請參閱[VSIX 專案範本](../extensibility/vsix-project-template.md)。  
  
2.  將 VSIX 專案設定為啟始專案。 在**方案總管 中**，選取 VSIX 專案節點、 按一下滑鼠右鍵，然後選取**設定為啟始專案**。  
  
3.  設定專案範本為 VSIX 專案的資產。 開啟.vsixmanifest 檔案。 移至**資產**] 索引標籤上，按一下 [**新增**。  
  
    1.  設定**類型**欄位**Microsoft.VisualStudio.ProjectTemplate**或**Microsoft.VisualStudio.ItemTemplate**。  
  
    2.  針對來源選取**目前方案中的專案**選項，然後再選取包含您的範本的專案。  
  
4.  建置方案，然後按 F5。 實驗執行個體隨即出現。  
  
5.  專案範本專案中，您應該會看到您的專案範本中所列**新的專案**對話方塊 (**檔案 / 新增 / 專案**) 中的 Visual C# 或 Visual Basic 節點。 專案項目範本，您應該會看到您加入新項目 對話方塊中列出的項目範本 (在**方案總管 中**，選取專案節點，然後按一下 **新增 / 新的項目**)。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 範本參考](../ide/visual-studio-template-reference.md)
