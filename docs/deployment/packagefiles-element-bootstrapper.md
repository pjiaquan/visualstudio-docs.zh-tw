---
title: "&lt;PackageFiles&gt; 項目 (啟動載入器) | Microsoft Docs"
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
  - "<PackageFiles> 項目 [啟動載入器]"
ms.assetid: 3ea252d7-18a3-47d8-af83-47feebcfe82b
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# &lt;PackageFiles&gt; 項目 (啟動載入器)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`PackageFiles` 項目包含 `PackageFile` 項目，定義 `Command` 項目所產生的安裝套件 \(Package\)。  
  
## 語法  
  
```  
<PackageFiles  
    CopyAllPackageFiles  
>  
    <PackageFile   
        Name  
        HomeSite  
        CopyOnBuild  
        PublicKey  
        Hash  
    />  
</PackageFiles>  
```  
  
## 項目和屬性  
 `PackageFiles` 項目具有下列屬性。  
  
|屬性|描述|  
|--------|--------|  
|`CopyAllPackageFiles`|選擇項。  如果設定為 `false`，安裝程式只會從 `Command` 項目下載所參考的檔案。  如果設定為 `true`，將會下載所有檔案。<br /><br /> 如果設定為 `IfNotHomesite`，安裝程式的行為會與設定為 `False` 時相同 \(如果 `ComponentsLocation` 設定為 `HomeSite`\)，否則安裝程式的行為將會與設定為 `True` 時相同。  這項設定可用來讓本身即為啟動載入器 \(Bootstrapper\) 的套件在 HomeSite 案例下執行自己的行為。<br /><br /> 預設值為 `true`。|  
  
## PackageFile  
 `PackageFile` 項目是 `PackageFiles` 項目的子系。  `PackageFiles` 項目必須至少有一個 `PackageFile` 項目。  
  
 `PackageFile` 具有下列屬性。  
  
|屬性|描述|  
|--------|--------|  
|`Name`|必要項。  封裝檔案的名稱。  這是 `Command` 在定義套件的安裝條件時，將會參考的名稱。  這個值也可用來做為 `Strings` 資料表的索引鍵，藉以擷取當地語系化的名稱，讓 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 工具在描述套件時可以使用。|  
|`HomeSite`|選擇項。  套件在遠端伺服器上的位置 \(如果安裝程式未隨附套件的話\)。|  
|`CopyOnBuild`|選擇項。  指定啟動載入器是否應在建置階段將封裝檔案複製到磁碟上。  預設值是 true。|  
|`PublicKey`|套件之憑證簽署者的加密公開金鑰 \(Public Key\)。  如果使用 `HomeSite` 則為必要項，否則為選擇項。|  
|`Hash`|選擇項。  封裝檔案的 SHA1 雜湊資料。  這個雜湊資料用於在安裝階段驗證檔案的完整性。  如果無法從封裝檔案計算出相符的雜湊資料，則不會安裝該封裝。|  
  
## 範例  
 下列程式碼範例為 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 可轉散發套件及其相依性 \(例如 Windows Installer\) 定義套件。  
  
```  
<PackageFiles>  
    <PackageFile Name="instmsia.exe" HomeSite="InstMsiAExe" PublicKey="3082010A0282010100AA99BD39A81827F42B3D0B4C3F7C772EA7CBB5D18C0DC23A74D793B5E0A04B3F595ECE454F9A7929F149CC1A47EE55C2083E1220F855F2EE5FD3E0CA96BC30DEFE58C82732D08554E8F09110BBF32BBE19E5039B0B861DF3B0398CB8FD0B1D3C7326AC572BCA29A215908215E277A34052038B9DC270BA1FE934F6F335924E5583F8DA30B620DE5706B55A4206DE59CBF2DFA6BD154771192523D2CB6F9B1979DF6A5BF176057929FCC356CA8F440885558ACBC80F464B55CB8C96774A87E8A94106C7FF0DE968576372C36957B443CF323A30DC1BE9D543262A79FE95DB226724C92FD034E3E6FB514986B83CD0255FD6EC9E036187A96840C7F8E203E6CF050203010001"/>  
    <PackageFile Name="WindowsInstaller-KB884016-v2-x86.exe" HomeSite="Msi30Exe" PublicKey="3082010A0282010100B22D8709B55CDF5599EB5262E7D3F4E34571A932BF94F20EE90DADFE9DC7046A584E9CA4D1D84441FB647E0F65EEC817DA4DDBD9D650B40C565B6C16884BBF03EE504883EC4F88939A51E394197FFAB397A5CE606D9FDD4C9338BDCD345971E686CEE98399A096B8EAE0445B1342B93A484E5472F70896E400C482017643AF61C2DBFAE5C5F00213DDF835B40F0D5236467443B1A2CA9CDD7E99F1351177FB1526018ECFE0B804782A15FD72C66076910CE74FB218181B6989B4F12F211B66EACA91C7460DB91758715856866523D10232AE64A06FDA5295FDFBDD8D34F5C10C35A347D7E91B6AFA0F45B4E8321D7019BDD1F9E5641FEB8737EA6FD40D838FFD0203010001"/>  
    <PackageFile Name="dotnetfx.exe" HomeSite="DotNetFXExe" PublicKey="3082010A0282010100B22D8709B55CDF5599EB5262E7D3F4E34571A932BF94F20EE90DADFE9DC7046A584E9CA4D1D84441FB647E0F65EEC817DA4DDBD9D650B40C565B6C16884BBF03EE504883EC4F88939A51E394197FFAB397A5CE606D9FDD4C9338BDCD345971E686CEE98399A096B8EAE0445B1342B93A484E5472F70896E400C482017643AF61C2DBFAE5C5F00213DDF835B40F0D5236467443B1A2CA9CDD7E99F1351177FB1526018ECFE0B804782A15FD72C66076910CE74FB218181B6989B4F12F211B66EACA91C7460DB91758715856866523D10232AE64A06FDA5295FDFBDD8D34F5C10C35A347D7E91B6AFA0F45B4E8321D7019BDD1F9E5641FEB8737EA6FD40D838FFD0203010001"/>  
    <PackageFile Name="dotnetchk.exe"/>  
</PackageFiles>  
```  
  
## 請參閱  
 [\<Product\> 項目](../deployment/product-element-bootstrapper.md)   
 [\<Package\> 項目](../deployment/package-element-bootstrapper.md)   
 [產品和封裝結構描述參考](../deployment/product-and-package-schema-reference.md)