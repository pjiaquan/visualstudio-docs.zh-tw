---
title: "VSPackage 註冊 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: ecd20da8-b04b-4141-a8f4-a2ef91dd597a
caps.latest.revision: 18
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
ms.openlocfilehash: bebd023d8cbecf97f75570bf57ed2cd4462ffe92
ms.lasthandoff: 02/22/2017

---
# <a name="vspackage-registration"></a>VSPackage 註冊
必須告知 Vspackage[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]它們已安裝，且應該會載入。 此程序被透過將資訊寫入登錄中。 這是安裝程式的典型的作業。  
  
> [!NOTE]
>  已接受的做法是使用自我註冊 VSPackage 開發期間。 不過，[!INCLUDE[vsipprvsip](../../extensibility/includes/vsipprvsip_md.md)]夥伴就無法出貨產品安裝程式中使用自我登錄。  
  
 Windows Installer 封裝中的登錄項目通常會進行登錄資料表中。 您也可以登錄資料表中註冊的副檔名。 不過，Windows 安裝程式會提供內建支援，透過程式設計識別項 (ProgId)、 類別、 延伸模組和動詞資料表。 如需詳細資訊，請參閱[資料庫資料表](http://msdn.microsoft.com/library/aa368259\(VS.85\).aspx)。  
  
 請確定您的登錄項目相關聯的元件符合您所選擇的並排的策略。 例如，共用檔案的登錄項目應該是與該檔案的 Windows Installer 元件相關聯。 同樣地，版本特定檔案的登錄項目應與該檔案的元件相關聯。 否則，安裝或解除安裝一個版本 VSPackage[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]在其他版本中可能會破壞 VSPackage。 如需詳細資訊，請參閱[支援多個版本的 Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)  
  
> [!NOTE]
>  管理註冊最簡單的方式是使用相同的資料相同的檔案中，開發人員註冊和安裝階段註冊。 比方說，有些 installer 開發工具可以在建置階段取用.reg 格式檔案。 如果開發人員維護自己的日常開發的.reg 檔案，並進行偵錯，這些相同的檔案可以包含在安裝程式自動。 如果您不能自動共用登錄資料，您必須確定註冊資料的安裝程式的複本是最新。  
  
## <a name="registering-unmanaged-vspackages"></a>註冊 Unmanaged 的 Vspackage  
 Unmanaged 的 VSPackages （包括 Visual Studio 封裝範本所產生） 會使用 ATL 樣式.rgs 檔案來儲存註冊資訊。 .Rgs 檔案格式是 ATL 特有，而且通常不能做為取用-是撰寫工具的安裝。 VSPackage 安裝程式的註冊資訊必須分開維護。 比方說，開發人員可以保留檔案格式為.reg.rgs 同步檔案變更。 .Reg 檔案可以合併使用 RegEdit 的開發工作，或由安裝程式。  
  
## <a name="registering-managed-vspackages"></a>註冊 Managed 的 VSPackages  
 RegPkg 工具從受管理的 VSPackage 讀取註冊屬性，並可以是直接將資訊寫入登錄或寫入.reg 格式檔案，可供安裝程式。  
  
> [!NOTE]
>  RegPkg 工具可轉散發套件並不能再註冊使用者的系統上的 VSPackage。  
  
## <a name="why-vspackages-should-not-self-register-at-install-time"></a>為什麼 VSPackages 不應自我註冊在安裝階段  
 VSPackage 的安裝程式不應依賴自我登錄。 乍看之下，只有在本身的 VSPackage 中保留的 VSPackage 登錄值看起來像是個不錯的主意。 指定開發人員的例行工作需要可用的登錄值，而且測試合理避免維護個別的安裝程式中的登錄資料的複本。 安裝程式會依賴 VSPackage 本身寫入登錄值。  
  
 好的理論上，同時自我登錄會有幾個缺點，可讓您安裝 VSPackage 不適用︰  
  
-   正確支援安裝、 解除安裝，安裝復原和解除安裝回復需要撰寫自我呼叫 RegPkg 註冊每個 managed VSPackage 的四個自訂動作。  
  
-   並行所支援的方法可能會要求您撰寫自訂的 RegSvr32 或 RegPkg 叫用每個支援版本的四個動作[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
-   安裝含自我登錄模組無法安全地復原，因為沒有辦法告訴自我登錄機碼由其他功能或應用程式。  
  
-   自我登錄的 Dll 有時會連結至不存在或版本不正確的輔助 Dll。 相反地，Windows Installer 可以註冊 Dll 登錄表使用不會相依於目前的系統狀態。  
  
-   自我登錄程式碼可能會遭到拒絕存取網路資源，例如型別程式庫中，如果元件是同時指定為從來源執行，而且 SelfReg 表所列。 這可能會導致元件失敗的系統管理安裝期間安裝。  
  
## <a name="see-also"></a>另請參閱  
 [Windows 安裝程式](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)   
 [受管理的套件登錄](http://msdn.microsoft.com/en-us/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)
