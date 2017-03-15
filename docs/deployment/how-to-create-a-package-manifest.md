---
title: "如何：建立封裝資訊清單 | Microsoft Docs"
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
  - "套件檔案 [ClickOnce]"
  - "套件檔案 [Windows Installer]"
  - "必要條件, 自訂啟動載入器套件"
ms.assetid: 5aecc507-2764-42f2-ae6f-c227971cf0af
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：建立封裝資訊清單
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

若要部署應用程式的必要條件，您可以使用啟動載入器套件。  啟動載入器套件只包含一個產品資訊清單檔案，但是包含每種地區設定的套件資訊清單。  不同當地語系化版本都會共用的功能應該放在產品資訊清單中。  
  
 如需套件資訊清單的詳細資訊，請參閱 [如何：建立產品資訊清單](../deployment/how-to-create-a-product-manifest.md)。  
  
## 建立套件資訊清單  
  
#### 若要建立套件資訊清單  
  
1.  建立啟動載入器套件的目錄。  這個範例會使用 C:\\package。  
  
2.  以地區設定的名稱建立子目錄，例如 en 代表英文。  
  
3.  在 Visual Studio 中，建立名為 `package.xml` 的 XML 檔，並將它儲存至 C:\\package\\en 資料夾。  
  
4.  加入 XML 程式碼以列出啟動載入器套件的名稱、這個當地語系化的套件資訊清單的文化特性，以及選擇性的授權合約。  下列 XML 程式碼會使用 `DisplayName` 和 `Culture` 變數，這些變數會在後面的項目中定義。  
  
    ```  
    <Package  
        xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
        Name="DisplayName"  
        Culture="Culture"  
        LicenseAgreement="eula.txt">  
    ```  
  
5.  加入 XML 程式碼以列出地區設定專用目錄中的所有檔案。  下列 XML 會使用 **en** 地區設定適用的 eula.txt 檔。  
  
    ```  
    <PackageFiles>  
      <PackageFile Name="eula.txt"/>  
    </PackageFiles>  
    ```  
  
6.  加入 XML 程式碼以定義啟動載入器套件的可當地語系化字串。  下列 XML 程式碼會加入 en 地區設定適用的錯誤字串。  
  
    ```  
      <Strings>  
        <String Name="DisplayName">Custom Bootstrapper Package</String>  
        <String Name="CultureName">en</String>  
        <String Name="NotAnAdmin">You must be an administrator to install   
    this package.</String>  
        <String Name="GeneralFailure">A general error has occurred while   
    installing this package.</String>  
    </Strings>  
    ```  
  
7.  將 C:\\package 資料夾複製至 Visual Studio 啟動載入器目錄中。  如果是 Visual Studio 2010，則這是 \\Program Files\\Microsoft SDKs\\Windows\\v7.0A\\Bootstrapper\\Packages 目錄。  
  
## 範例  
 套件資訊清單包含地區設定專用資訊，例如錯誤訊息、軟體授權條款和語言套件。  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<Package  
  xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
  Name="DisplayName"  
  Culture="Culture"  
  LicenseAgreement="eula.txt">  
  
  <PackageFiles>  
    <PackageFile Name="eula.txt"/>  
  </PackageFiles>  
  
  <Strings>  
    <String Name="DisplayName">Custom Bootstrapper Package</String>  
    <String Name="Culture">en</String>  
    <String Name="NotAnAdmin">You must be an administrator to install this package.</String>  
    <String Name="GeneralFailure">A general error has occurred while   
installing this package.</String>  
  </Strings>  
</Package>  
```  
  
## 請參閱  
 [產品和封裝結構描述參考](../deployment/product-and-package-schema-reference.md)