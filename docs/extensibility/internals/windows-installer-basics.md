---
title: "Windows 安裝程式的基本概念 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Windows Installer Vspackage"
  - "VSPackages，Windows 安裝程式的基本概念"
ms.assetid: 497e479b-add8-4644-870a-917f15306b97
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Windows 安裝程式的基本概念
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Windows Installer 安裝和解除安裝應用程式或使用者的電腦上的軟體產品執行這些工作單位稱為 Windows 安裝程式元件 （有時稱為 WICs 或只是元件）。 GUID 會識別每個 WIC，是安裝和參考計數，若是使用 Windows Installer 設定的基本單位。  
  
 完整的 Windows Installer 的文件，請參閱 Platform SDK 主題 [Windows Installer](http://msdn.microsoft.com/library/aa372866.aspx)。  
  
## 撰寫 VSPackage  
 Windows 安裝程式會使用安裝套件，其中包含 Windows 安裝程式需要安裝、 解除安裝或修復產品，並執行安裝程式使用者介面 \(UI\) 的資訊。 每個安裝套件包含.msi 檔案，其中包含安裝資料庫、 摘要資訊資料流和安裝的各部分的資料流。 若要使用安裝程式，您必須撰寫的安裝。 因為安裝程式會安裝元件的概念為中心的組織，並將安裝的相關資訊儲存在關聯式資料庫中，針對撰寫安裝套件的程序牽涉到下列步驟︰  
  
1.  規劃您的安裝程式編寫，以支援您的版本控制和並排的策略。  
  
2.  識別要呈現給使用者的功能。  
  
3.  元件組織的 VSPackage 和相依性。  
  
4.  填入安裝資料庫的資訊。  
  
5.  驗證安裝套件。  
  
 這份文件主要涉及程序的第一個和第三個步驟。 在這些步驟將組織 VSPackage 功能到 WICs 讓您可以將您的版本控制和服務的後續版本的策略框 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 其餘的三個步驟是平台 SDK 中的 Windows 安裝程式文件中的詳細說明。  
  
## 主要詞彙  
 以下是 Windows Installer 技術的相關的重要詞彙的定義。  
  
 資源  
 檔案、 登錄機碼、 捷徑或等等，可能會安裝到電腦。 這些資源會以邏輯方式分組為 Windows 安裝程式元件。  
  
 Windows 安裝程式元件 \(WIC\)  
 表示已安裝及解除安裝當做一個單位的相關資源的邏輯群組的安裝的基本單位。 Windows 安裝程式元件的唯一元件識別碼或 GUID 來識別。 此外，Windows Installer 會維護其參考計數 WIC 層級。 最大版本控制的彈性，在給定的 WIC 中包含有一個以上的主要資源，例如 DLL、。 請注意，識別並填入 WIC，不妨 GUID，並將其部署之後，您無法變更其構造。 如需詳細資訊，請參閱 [組織的應用程式元件](http://msdn.microsoft.com/library/aa370561.aspx)。  
  
 套件 （可轉散發套件）  
 .msi 檔案和外部的原始程式檔可能會指向這個檔案所組成的部署單位。 封裝包含所有 Windows 安裝程式必須執行 UI 和安裝或解除安裝應用程式的資訊。  
  
 .msi 檔案  
 COM 結構化儲存體檔案，其中包含的指示和安裝應用程式所需的資料。 每個套件都包含至少一個.msi 檔案。 將.msi 檔案包含安裝程式資料庫、 摘要資訊的資料流，並可能是一或多個轉換和內部的原始程式檔。 要安裝檔案可以壓縮成封包和儲存在.msi 檔案中的資料流或儲存、 壓縮，或外部來源媒體上的.msi 檔案未壓縮。 如需詳細資訊，請參閱 [Windows 安裝程式檔案的副檔名](http://msdn.microsoft.com/library/aa372842\(VS.85\).aspx)。  
  
## Windows 安裝程式規則強制  
 這兩組規則決定部署到您的安裝程式元件的資源。 您應該強制執行第二組安裝在撰寫時由 Windows 安裝程式本身，維護一個規則集。  
  
> [!NOTE]
>  只有當您執行的.msi 檔案的驗證，就會發生強制執行 Windows 安裝程式規則。 不過，您會 cautioned 這些規則視為最佳作法。 如需詳細資訊，請參閱 [驗證安裝資料庫](http://msdn.microsoft.com/library/aa372477\(VS.85\).aspx) 和 [封裝驗證](http://msdn.microsoft.com/library/aa370569\(VS.85\).aspx)。  
  
#### 安裝程式強制執行規則  
  
-   指定的元件中的所有檔案必須都安裝到相同的目錄。 相反地，安裝到個別的資料夾的檔案必須屬於元件分開。  
  
-   可以有只有一個機碼路徑中的每個元件。 機碼的路徑是只要檔案或登錄機碼，表示整個元件。  
  
#### 元件提供者的責任  
  
-   可能會分別在後續版本中隨附的任何兩個資源必須存在於不同的元件。 資源只當您確定這些資源將不會個別的上市時，才應該分組在同一個元件。 事實上，我們建議您所有的主要資源 \(例如 Dll\) 一律存在於個別 WICs。 如需詳細資訊，請參閱 [定義的安裝程式元件](http://msdn.microsoft.com/library/aa368269\(VS.85\).aspx)。  
  
-   沒有建立版本的資源不應該在一個以上的 WIC 交運。  
  
## 請參閱  
 [如果元件規則中斷發生什麼事？](http://msdn.microsoft.com/library/aa372795\(VS.85\).aspx)