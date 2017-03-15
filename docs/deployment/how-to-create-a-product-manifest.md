---
title: "如何：建立產品資訊清單 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "相依性, 自訂啟動載入器套件"
  - "必要條件, 自訂啟動載入器套件"
  - "產品檔案 [ClickOnce]"
  - "產品檔案 [Windows Installer]"
ms.assetid: 2d316aaa-8bc0-4ce5-90ab-23b3eac0b5dd
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：建立產品資訊清單
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

若要部署應用程式的必要條件，您可以建立啟動載入器套件。  啟動載入器套件只包含一個產品資訊清單檔案，但是包含每種地區設定的套件資訊清單。  套件資訊清單包含套件中與當地語系化有關的部分。  這包括字串、使用者授權合約和語言套件。  
  
 如需產品資訊清單的詳細資訊，請參閱 [如何：建立封裝資訊清單](../deployment/how-to-create-a-package-manifest.md)。  
  
## 建立產品資訊清單  
  
#### 若要建立產品資訊清單  
  
1.  建立啟動載入器套件的目錄。  這個範例會使用 C:\\package。  
  
2.  在 Visual Studio 中，建立名為 `product.xml` 的新 XML 檔，並將它儲存至 C:\\package 資料夾中。  
  
3.  加入下列 XML 程式碼，以描述套件的 XML 命名空間和產品代碼。  請將產品代碼取代為套件的唯一識別項。  
  
    ```  
    <Product  
    xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"   
    ProductCode="Custom.Bootstrapper.Package">  
    ```  
  
4.  加入 XML 程式碼以指定套件具有相依性。  這個範例會使用對 Microsoft Windows Installer 3.1 的相依性。  
  
    ```  
    <RelatedProducts>  
        <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />  
      </RelatedProducts>  
    ```  
  
5.  加入 XML 程式碼以列出啟動載入器套件中的所有檔案。  這個範例會使用套件檔案名稱 CorePackage.msi。  
  
    ```  
    <PackageFiles>  
        <PackageFile Name="CorePackage.msi"/>  
    </PackageFiles>  
    ```  
  
6.  將 CorePackage.msi 檔案複製或移動至 C:\\package 資料夾。  
  
7.  加入 XML 程式碼，以使用啟動載入器命令來安裝套件。  啟動載入器會自動將 **\/qn** 旗標加入至將以無訊息模式自動安裝的 .msi 檔案中。  如果檔案是 .exe 檔，則啟動載入器會使用殼層執行 .exe 檔。  下列 XML 程式碼未顯示 CorePackage.msi 的引數，但您可以將命令列引數放到 Arguments 屬性中。  
  
    ```  
    <Commands>  
        <Command PackageFile="CorePackage.msi" Arguments="">  
    ```  
  
8.  加入下列 XML 程式碼，以檢查是否已安裝這個啟動載入器套件。  請將產品代碼取代為可轉散發元件的 GUID。  
  
    ```  
    <InstallChecks>  
        <MsiProductCheck   
            Property="IsMsiInstalled"   
            Product="{XXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>  
    </InstallChecks>  
    ```  
  
9. 加入 XML 程式碼，以視是否已安裝啟動載入器元件來變更啟動載入器行為。  如果已安裝該元件，則啟動載入器套件不會執行。  因為這個元件需要系統管理權限，所以下列 XML 程式碼會檢查目前使用者是否為系統管理員。  
  
    ```  
    <InstallConditions>  
        <BypassIf   
           Property="IsMsiInstalled"   
           Compare="ValueGreaterThan" Value="0"/>  
        <FailIf Property="AdminUser"   
            Compare="ValueNotEqualTo" Value="True"  
            String="NotAnAdmin"/>  
    </InstallConditions>  
    ```  
  
10. 加入 XML 程式碼，以設定安裝成功和需要重新開機時的結束代碼。  下列 XML 程式碼示範 Fail 和 FailReboot 結束代碼，這些結束代碼表示啟動載入器不會繼續安裝套件。  
  
    ```  
    <ExitCodes>  
        <ExitCode Value="0" Result="Success"/>  
        <ExitCode Value="1641" Result="SuccessReboot"/>  
        <ExitCode Value="3010" Result="SuccessReboot"/>  
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>  
    </ExitCodes>  
    ```  
  
11. 加入下列 XML 程式碼，以結束啟動載入器命令的區段。  
  
    ```  
        </Command>  
    </Commands>  
    ```  
  
12. 將 C:\\package 資料夾移至 Visual Studio 啟動載入器目錄中。  如果是 Visual Studio 2010，則這是 \\Program Files\\Microsoft SDKs\\Windows\\v7.0A\\Bootstrapper\\Packages 目錄。  
  
## 範例  
 產品資訊清單會包含安裝自訂必要條件的指示。  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<Product  
  xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
  ProductCode="Custom.Bootstrapper.Package">  
  
  <RelatedProducts>  
    <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />  
  </RelatedProducts>  
  
  <PackageFiles>  
    <PackageFile Name="CorePackage.msi"/>  
  </PackageFiles>  
  
  <InstallChecks>  
    <MsiProductCheck Product="IsMsiInstalled"   
      Property="{XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>  
  </InstallChecks>  
  
  <Commands>  
    <Command PackageFile="CorePackage.msi" Arguments="">  
  
      <InstallConditions>  
        <BypassIf Property="IsMsiInstalled"  
          Compare="ValueGreaterThan" Value="0"/>  
        <FailIf Property="AdminUser"   
          Compare="ValueNotEqualTo" Value="True"  
         String="NotAnAdmin"/>  
      </InstallConditions>  
  
      <ExitCodes>  
        <ExitCode Value="0" Result="Success"/>  
        <ExitCode Value="1641" Result="SuccessReboot"/>  
        <ExitCode Value="3010" Result="SuccessReboot"/>  
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>  
      </ExitCodes>  
    </Command>  
  </Commands>  
</Product>  
```  
  
## 請參閱  
 [產品和封裝結構描述參考](../deployment/product-and-package-schema-reference.md)