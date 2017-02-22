---
title: "開始使用 VSIX 專案範本 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio SDK，VSIX 專案範本"
ms.assetid: 89fac33e-9380-4723-9b45-048a6e16f0ed
caps.latest.revision: 25
caps.handback.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
---
# 開始使用 VSIX 專案範本
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以使用 VSIX 專案範本建立的擴充功能或封裝部署的現有擴充功能。 VSIX 專案範本會提供 Visual Basic 和 Visual C\# 版本和安裝 Visual Studio SDK 的一部分。  
  
 VSIX 專案範本只包含 source.extension.vsixmanifest 檔案中，其中包含有關擴充的資訊和附隨的資產。  
  
 若要尋找 VSIX 專案範本，您必須安裝 Visual Studio SDK。 如需詳細資訊，請參閱[Visual Studio SDK](../extensibility/visual-studio-sdk.md)。  
  
## 部署自訂專案範本使用 VSIX 專案範本  
 下列步驟顯示如何使用 VSIX 專案封裝專案範本，您可以與其他開發人員共用，或上傳至 Visual Studio 組件庫。  
  
1.  建立專案範本。  
  
    1.  開啟要從中建立範本的專案。 此專案可以是任何專案類型。  
  
    2.  按一下 \[**檔案**\] 功能表上的 \[**匯出範本**\]。 完成精靈的步驟。  
  
         .Zip 檔案會在 %USERPROFILE%\\My Documents\\Visual Studio *\< 版本 \>*\\My Exported Templates\\。  
  
2.  建立空的 VSIX 專案。  
  
     在 \[檔案\] 功能表上，按一下 \[新增\] 及 \[專案\]。 選取 \[ **Visual Basic** 或 **Visual C\#**。 在選取節點，選取 **擴充性**, ，然後選取 **VSIX 專案**。  
  
3.  將.zip 檔案加入至專案。 設定其 **複製到輸出目錄** 屬性 `Copy Always`。  
  
4.  在 **方案總管\] 中**, ，連按兩下 `source.extension.vsixmanifest` 中開啟該檔案 **VSIX 資訊清單設計工具**, ，然後進行下列變更 ︰  
  
    -   設定 **產品名稱** 欄位 **我的專案範本**。  
  
    -   設定 **產品識別碼** 欄位 **MyProjectTemplate\-1**。  
  
    -   設定 **作者** 欄位 **Fabrikam**。  
  
    -   設定 **描述** 欄位 **我的專案範本**。  
  
    -   在 **資產** 區段中，加入 **Microsoft.VisualStudio.ProjectTemplate** 輸入，並將其路徑設定為.zip 檔案的名稱。  
  
5.  儲存並關閉 source.extension.vsixmanifest 檔案。  
  
6.  建置專案。  
  
7.  在輸出目錄中，按兩下此.vsix 檔案。  
  
8.  A **VSIX 安裝程式** 訊息方塊隨即出現。 請依照下列指示來安裝擴充功能。  
  
9. 關閉 Visual Studio，然後再重新開啟它。  
  
10. 選取 **擴充功能和更新** \(在 **工具** 功能表\)，然後選取 **範本** 類別。 其中一個可用的擴充功能應該 **我的專案範本**。  
  
11. 新的專案範本會出現在 **新的專案** \] 對話方塊中的原始專案範本相同的位置。 例如，如果您已建立名為 **VB 主控台** Visual Basic 主控台應用程式中，從 **VB 主控台** 會出現在同一個窗格為 Visual Basic **主控台應用程式** 範本。  
  
#### 在 \[新增專案\] 對話方塊中指定範本的位置  
  
1.  範本資料夾位於 *Visual Studio 安裝路徑*\\Common7\\IDE\\ProjectTemplates 和 *Visual Studio 安裝路徑*\\Common7\\IDE\\ItemTemplates 目錄。 在 \[新增專案\] 對話方塊中的最上層區段的名稱與範本資料夾名稱不完全相符。 它們之間的差異，使用範本資料夾的名稱。  
  
     將.vsix 檔案副檔名變更為.zip，然後再開啟 \[檔案。  
  
2.  建立新的資料夾與範本應該會出現在 \[新增專案\] 對話方塊的區段名稱相同。  
  
3.  如果範本才會出現在子區段中，建立具有相同名稱的子資料夾。  
  
4.  將範本.zip 檔案移到新的資料夾。  
  
5.  將.zip 副檔名變更為.vsix。  
  
6.  開啟 VSIX 資訊清單。  
  
7.  在 VSIX 資訊清單中，更新 **資產** 範本，讓它指向包含範本檔案目錄樹狀結構根目錄的路徑。 例如，如果範本在 \\CSharp\\Windows，參考應該指向 \\CSharp。