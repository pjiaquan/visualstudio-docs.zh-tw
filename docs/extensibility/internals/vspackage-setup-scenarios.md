---
title: "VSPackage 安裝案例 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSPackages，部署考量"
ms.assetid: d2928498-f27c-46b4-a9cd-cba41fd85a10
caps.latest.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 21
---
# VSPackage 安裝案例
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

請務必設計您的 VSPackage 安裝程式的彈性。 比方說，您可能需要在未來，發行安全性修補程式，或您可能會變更商務策略，需要完整的並存版本控制支援。  
  
 在 [支援多個版本的 Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md), ，您可以閱讀的優點與支援\-並存安裝問題 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage 的共用或並存安裝。 簡單地說，由並行 VSPackages 提供您最大的彈性來支援新功能的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 本主題中討論的案例不是唯一的選擇，但是會以建議的最佳作法。  
  
## 元件、 隱私權和共用  
  
##### 讓獨立的元件  
 一旦您找出並填入元件時，指派 `GUID`, ，部署元件，您無法變更其構造。 如果您變更元件的組合，將產生的元件必須是新元件與新 `GUID`。 根據這些事實為基礎，最大版本控制的彈性就會提供藉由在每個元件的獨立、 獨立地單位。 多個元件的規則的詳細資訊，請參閱 [變更元件的程式碼](http://msdn.microsoft.com/library/aa367849\(VS.85\).aspx) 和 [要是元件規則分別？](http://msdn.microsoft.com/library/aa372795\(VS.85\).aspx)。  
  
##### 請勿混用在元件中的共用和私用的資源  
 參考計數就會發生在元件層級上。 因此，混用一個元件中的共用和私用的資源，使得更新私用的資源，例如可執行檔，而不也覆寫共用的資源。 這種情況下建立回溯相容性問題，並會限制您建立的並行功能。  
  
 登錄值，例如用來註冊與 VSPackage [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 應該會分開的元件中用來註冊與 VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 共用的檔案或登錄值放在另一個元件。  
  
## 案例 1︰ 共用的 VSPackage  
 在此案例中，共用 VSPackage \(單一二進位檔，可支援多個版本的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]\) 隨附於 Windows Installer 套件。 向每個版本 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 控制使用者可選取的功能。 這也表示，指派給個別功能時，每個元件可以選取個別的安裝或解除安裝，讓使用者控制整合的不同版本的 VSPackage 的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 \(請參閱 [Windows Installer 功能](http://msdn.microsoft.com/library/aa372840\(VS.85\).aspx) 如需有關使用 Windows Installer 封裝中的功能。\)  
  
 ![VS 的共用 VSPackage 圖形](../../extensibility/internals/media/vs_sharedpackage.png "VS\_SharedPackage")  
共用的 VSPackage 安裝程式  
  
 下圖所示，共用的元件都會 Feat\_Common 功能，一定會安裝的一部分。 藉由 Feat\_VS2002 和 Feat\_VS2003 功能可見，使用者可以在安裝時選擇的哪一個版本 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 他們想要整合 VSPackage。 使用者也可以使用新增或移除功能，這在此情況下從新增或移除 VSPackage 註冊資訊的不同版本的 Windows Installer 維護模式 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
> [!NOTE]
>  將功能顯示資料行設定為 0，會隱藏它。 低層級的資料行值，例如 1，可確保一定會安裝。 如需詳細資訊，請參閱 [INSTALLLEVEL 屬性](http://msdn.microsoft.com/library/aa369536\(VS.85\).aspx) 和 [功能資料表](http://msdn.microsoft.com/library/aa368585.aspx)。  
  
## 案例 2︰ 共用 VSPackage 更新  
 在此案例中，出貨 VSPackage 安裝程式，在案例 1 的更新的版本。 討論中，更新會新增支援 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], ，但也可能是較簡單安全性修補程式或 bug 修正 service pack。 較新的元件安裝的 Windows 安裝程式的規則需要不變的元件已經在系統上不會重新複製。 在此情況下，已經存在的 1.0 版的系統會覆寫更新的元件 Comp\_MyVSPackage.dll，並且讓使用者選擇將新的功能 Feat\_VS2005 Comp\_VS2005\_Reg 其元件。  
  
> [!CAUTION]
>  每當多個版本之間的共用 VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], ，很重要的 VSPackage 後續版本維持與舊版的回溯相容性 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 您無法維護回溯相容性，其中，您必須使用由並行的私人 Vspackage。 如需詳細資訊，請參閱[支援多個版本的 Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)。  
  
 ![VS 共用的 VS 套件更新影像](../../extensibility/internals/media/vs_sharedpackageupdate.png "VS\_SharedPackageUpdate")  
共用 VSPackage 更新安裝程式  
  
 這種情況下提供新 VSPackage 的安裝程式，還能善用次要升級的 Windows 安裝程式的支援。 使用者只需在安裝版本 1.1 和 1.0 版升級。 不過，不需要有系統的 1.0 版。 相同的安裝程式將安裝在系統，而 1.0 版的 1.1 版。 提供重要的更新，以這種方式的優點是，不需要經過開發升級的安裝程式和完整產品安裝程式的工作。 一個安裝程式會執行這兩個作業。 安全性修正程式或服務組件可能會改為充分利用 Windows Installer 修補程式。 如需詳細資訊，請參閱 [修補和升級](http://msdn.microsoft.com/library/aa370579\(VS.85\).aspx)。  
  
## 案例 3:\-並存 VSPackage  
 本案例說明兩個 VSPackage 安裝程式 — 一個用於每個版本的 Visual Studio.NET 2003年和 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 每個安裝程式會安裝由側邊或私用，VSPackage \(特別是建置和安裝特定版本的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]\)。 每個 VSPackage 是在自己的元件。 因此，每個可個別服務修補程式或維護釋出。 VSPackage DLL 現在是版本專屬的則相同的元件與 DLL 中包含的註冊資訊。  
  
 ![VS 並存的 VS 套件圖形](../../extensibility/internals/media/vs_sbys_package.gif "VS\_SbyS\_Package")  
並存 VSPackage 安裝程式  
  
 每個安裝程式也包含兩個安裝程式之間共用的程式碼。 如果共用的程式碼安裝到一般的位置時，安裝這兩個.msi 檔案會安裝共用的程式碼一次。 第二個安裝程式只會遞增參考計數在元件上。 參考計數可確保如果 VSPackages 的其中一個解除安裝，共用程式碼仍針對其他 VSPackage。 如果第二個 VSPackage 也會解除安裝，將會移除共用的程式碼。  
  
## 案例 4:\-並存 VSPackage 更新  
 在此案例中，為 VSPackage [!INCLUDE[vsprvslong](../../code-quality/includes/vsprvslong_md.md)] 發生從安全性的弱點可能會與您要發行更新。 如案例 2 所示，您可以建立一個新的.msi 檔案，更新包括安全性修正程式，以及部署新的安裝已經安全性修正就地使用現有的安裝。  
  
 在此情況下，VSPackage 是安裝在全域組件快取 \(GAC\) 中的受管理的 VSPackage。 當您重建它包含安全性修正程式時，您必須變更組件版本號碼的修訂號碼部分。 註冊資訊的新組件版本號碼會覆寫先前的版本，造成 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 載入固定的組件。  
  
 ![VS 並存的 VS 套件更新圖形](../../extensibility/internals/media/vs_sbys_packageupdate.png "VS\_SbyS\_PackageUpdate")  
並行的 VSPackage 更新安裝程式  
  
 **注意** 如需有關部署為並存組件的詳細資訊，請參閱 [簡化部署和使用.NET Framework 解決 DLL Hell](http://msdn.microsoft.com/library/ms973843.aspx)。  
  
## 請參閱  
 [Windows Installer](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)   
 [支援多個版本的 Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)