---
title: "部署自訂起始頁 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- package start page
- deploy start page
ms.assetid: 4a7eb360-de83-41d5-be53-3cfb160d19f9
caps.latest.revision: 21
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
ms.openlocfilehash: 9e99f022f1dec71b82c2261cae1d45705fe8dc7f
ms.lasthandoff: 02/22/2017

---
# <a name="deploying-custom-start-pages"></a>部署自訂起始頁
使用 VSIX 部署，或將檔案複製到目標電腦上的正確位置，您可以部署自訂頁面起始位置。  
  
## <a name="vsix-deployment-by-using-the-start-page-project-template"></a>使用啟動頁面專案範本的 VSIX 部署  
 當您使用入門 頁面上的專案範本，建立啟動 頁面，然後建置專案時，Visual Studio 會建立可散發.vsix 檔案。 封裝.vsix 檔案的 [入門] 頁面上，提供您下列選項來進行部署，根據您對象︰  
  
-   在網路共用或公用網站上，您可以將.vsix 檔案。 當使用者開啟檔案時，[啟動] 頁面會自動安裝。  
  
-   您可以上傳至.vsix 檔[Visual Studio 元件庫](http://go.microsoft.com/fwlink/?LinkID=123847)Web 網站，以便使用者可以使用來安裝它**擴充管理員**。  
  
 起始頁專案範本會建立一份 Visual Studio 起始頁的預設值，可讓您可以修改複本，並保留原始。  
  
 您可以使用，以取得入門 頁面上的專案範本**擴充管理員**或下載的網站。  
  
## <a name="vsix-deployment-without-using-the-start-page-project-template"></a>VSIX 部署，而不使用啟動頁面專案範本  
 成功的 VSIX 部署需要安裝資料夾中的可辨識 VSIX 註冊程序和擴充**擴充管理員**。 起始頁專案範本已指定正確的資料夾，因為我們建議您用它每當您想要封裝 VSIX 部署的擴充功能。 不過，如果您有的案例，您無法使用範本，您可以建立 VSIX 部署而不使用它。  
  
 若要建立 VSIX 部署，而不使用入門 頁面上的專案範本，首先建立.vsix 檔的開始頁面中這兩種方式之一︰  
  
-   自訂起始頁檔案加入空的 VSIX 專案。 如需詳細資訊，請參閱[VSIX 專案範本](../extensibility/vsix-project-template.md)。  
  
-   手動建立.vsix 檔案。 如需詳細資訊，請參閱[How to︰ 手動封裝擴充功能 （VSIX 部署）](../misc/how-to-manually-package-an-extension-vsix-deployment.md)。  
  
 Visual Studio 能夠辨識入門 頁面中，如`Content Element`VSIX 資訊清單必須包含`CustomExtension Element`具有`Type`屬性設為`"StartPage"`。 使用 VSIX 部署已安裝的起始頁延伸模組會出現在**自訂起始頁**清單**啟動**選項 頁面上，做為**[安裝延伸模組]** *副檔名*。  
  
 如果您啟動 頁面上的封裝包含的組件，您必須新增繫結路徑註冊 Visual Studio 啟動時才可用。 若要這樣做，請確定您的封裝包含.pkgdef 檔具有下列資訊。  
  
```  
[$RootKey$\BindingPaths\{Insert a new GUID here}]  
"$PackageFolder$"=""  
```  
  
### <a name="vsix-deployment-for-all-users"></a>所有使用者的 VSIX 部署  
 根據預設，在 VSIX 套件部署延伸模組安裝只會針對目前的使用者。 您可以讓目標電腦的所有使用者入門 頁面上安裝建立所有使用者部署。  
  
##### <a name="to-create-an-all-users-deployment"></a>若要建立所有使用者部署  
  
1.  在程式碼檢視中開啟 extension.vsixmanifest 檔案。  
  
2.  在`Identifier`vsix 資訊清單項目加入`AllUsers`具有值的項目`true`。  
  
    ```  
    <AllUsers>true</AllUsers>  
    ```  
  
     這會造成提示提供系統管理員權限，然後再將檔案安裝到 \Common7\IDE\Extensions vsix 安裝程式。  
  
3.  開啟.pkgdef 檔。  
  
4.  修改以加入下列命令，來設定預設起始頁 HKLM 底下.pkgdef 其中*MyStartPage.xaml*的.xaml 檔案，包含起始網頁的名稱。  
  
     [$RootKey$ \StartPage\Default]  
  
     "Uri"="$PackageFolder$\\*MyStartPage.xaml*」  
  
     這會告訴 Visual 名人，若要查看在新起始頁的位置。  
  
## <a name="file-copy-deployment"></a>檔案複製部署  
 您沒有建立.vsix 檔案，以部署自訂起始頁。 相反地，您可以直接在使用者的 \StartPages\ 資料夾複製標記和支援檔案。 **自訂起始頁**清單**啟動**選項 頁面會列出在該資料夾，以及路徑中的每個.xaml 檔案 — 例如，%USERPROFILE%\My Documents\Visual Studio*版本*\StartPages\\*檔案名稱*.xaml。 如果您的起始頁包含私用組件的參考，您必須複製並貼入 \PrivateAssemblies\ 資料夾。  
  
 若要將您建立封裝沒有起始頁它在.vsix 檔案中，我們建議基本檔案複製策略，例如，批次指令碼或任何其他部署技術，可讓您放置檔案所需的目錄中。  
  
#### <a name="to-manually-install-a-custom-start-page"></a>若要手動安裝自訂起始頁  
  
1.  .xaml 檔案，包含起始頁的標記，以及任何支援的檔案以外的組件，複製並貼上使用者的 \StartPages\ 資料夾中。  
  
2.  如果 [啟動] 頁面會要求組件，將它們複製並貼在...\\ *Visual Studio 安裝資料夾*\Common7\IDE\PrivateAssemblies\\。  
  
3.  在**自訂起始頁**清單**啟動**選項頁面上，選取新的 [開始] 頁面。 如需詳細資訊，請參閱[自訂起始頁](../ide/customizing-the-start-page-for-visual-studio.md)。  
  
## <a name="see-also"></a>另請參閱  
 [自訂起始頁](../ide/customizing-the-start-page-for-visual-studio.md)   
 [將使用者控制項加入至 [開始] 頁面](../extensibility/adding-user-control-to-the-start-page.md)
