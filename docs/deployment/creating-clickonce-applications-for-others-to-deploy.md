---
title: "建立 ClickOnce 應用程式供其他人部署 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<useManifestForTrust> 項目"
  - "應用程式資訊清單 [ClickOnce]"
  - "ClickOnce 應用程式, 由其他人部署"
  - "ClickOnce 應用程式, 舊版 .NET Framework"
  - "ClickOnce 應用程式, 舊版 .NET Framework"
  - "客戶部署 [ClickOnce]"
  - "資料清單 [ClickOnce]"
  - "多個 ClickOnce 部署和品牌"
  - "保留品牌資訊"
  - "信任應用程式, ClickOnce"
  - "useManifestForTrust 項目"
ms.assetid: d20766c7-4ef3-45ab-8aa0-3f15b61eccaa
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 10
---
# 建立 ClickOnce 應用程式供其他人部署
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

不是所有正在建立 ClickOnce 部署計劃的開發人員都打算自己部署應用程式；  其中有許多人只是要使用 ClickOnce 封裝他們的應用程式，然後再將檔案交給客戶 \(例如大型企業\)，  再由客戶負責將應用程式裝載到其網路上。  本主題討論在 .NET Framework 3.5 版之前的版本中，這種部署所本身所存在的某些問題。  接著並說明使用 .NET Framework 3.5 中新增之「使用信任資訊清單」功能所提供的新方案。  最後再總結說明建立 ClickOnce 部署的建議策略，以供還在使用舊版 .NET Framework 的客戶使用。  
  
## 為客戶建立部署時所涉及的問題  
 當您規劃要提供部署給客戶時，將會發生幾個問題。  第一個問題與程式碼簽署有關。  為了跨網路進行部署，ClickOnce 部署的部署資訊清單和應用程式資訊清單都必須使用數位憑證進行簽署。  這項需求引發了簽署資訊清單時應該使用開發人員的憑證還是客戶的憑證的問題。  
  
 使用哪一個憑證的問題非常重要，因為 ClickOnce 應用程式的識別 \(Identity\) 是以部署資訊清單的數位簽章做為基礎。  如果開發人員簽署了部署資訊清單，當客戶是大型公司，而且公司中有一個以上部門部署該應用程式的自訂版本時，可能就會造成衝突的情況。  
  
 例如，假設 Adventure Works 公司有財務部門和人力資源部門，  而這兩個部門都已授權使用 Microsoft Corporation 提供的 ClickOnce 應用程式，以便從儲存在 SQL 資料庫中的資料產生報告。  Microsoft 分別為這兩個部門提供適用於其資料的自訂應用程式版本。  如果這些應用程式都使用相同的 Authenticode 憑證進行簽署，則嘗試同時使用這兩種應用程式的使用者將會遇到錯誤，因為 ClickOnce 會將第二個應用程式和第一個應用程式視為完全相同。  在這種情況下，客戶可能會遇到無法預期且不必要的副作用，包括遺失應用程式儲存在本機的資料。  
  
 另外一個與程式碼簽署有關的問題是部署資訊清單中的 `deploymentProvider` 項目，它可用來告知 ClickOnce 尋找應用程式更新的適當位置。  這個項目必須先加入至部署資訊清單中，然後才能進行簽署。  如果在簽署之後才加入這個項目，則必須重新簽署部署資訊清單。  
  
### 要求客戶簽署部署資訊清單  
 如果要解決這種非唯一部署的問題，其中一種解決方法是讓開發人員簽署應用程式資訊清單，然後讓客戶簽署部署資訊清單。  雖然這個方法很有效，但是卻會引發其他問題。  由於 Authenticode 憑證必須維持受保護的資產之形態，因此客戶不能直接將此憑證提供給開發人員來簽署部署。  雖然客戶可以任意使用 .NET Framework SDK 所提供的工具以自行簽署部署資訊清單，這項程序所需要的技術知識可能超過客戶願意或能夠提供的範圍。  在這種情況下，開發人員通常都會建立應用程式、網站或其他機制，讓客戶可以透過這些機制送出他們的應用程式版本來進行簽署。  
  
### 客戶簽署對 ClickOnce 應用程式安全性的影響  
 即使開發人員和客戶都同意應該由客戶來簽署應用程式資訊清單，還是會引發與應用程式識別有關的其他問題，尤其是將應用程式識別套用至受信任的應用程式部署時   \(如需此功能的詳細資訊，請參閱[受信任的應用程式部署概觀](../deployment/trusted-application-deployment-overview.md)\)。 假設 Adventure Works 公司想要設定用戶端電腦，好讓 Microsoft Corporation 提供給他們的任何應用程式都能夠以完全信任的層級執行。  如果 Adventure Works 簽署了部署資訊清單，ClickOnce 就會使用 Adventure Works 的安全性簽章來判斷應用程式的信任層級。  
  
## 使用信任應用程式資訊清單建立客戶部署  
 .NET Framework 3.5 中的 ClickOnce 包含一項新功能，可以為開發人員和客戶提供新的方案，以解決如何簽署資訊清單的案例。  ClickOnce 應用程式資訊清單支援一個名為 `<useManifestForTrust>` 的新項目，這個項目可以讓開發人員清楚說明，在決定信任層級時應該使用應用程式資訊清單的數位簽章。  開發人員可以使用 ClickOnce 封裝工具 \(例如 Mage.exe、MageUI.exe 和 Visual Studio\) 將這個項目包含在應用程式資訊清單中，同時也將他們的發行者 \(Publisher\) 名稱和應用程式名稱都內嵌在資訊清單中。  
  
 使用 `<useManifestForTrust>` 時，部署資訊清單不需要以憑證授權單位所核發的 Authenticode 憑證進行簽署，  而且可以改用所謂的自我簽署憑證來簽署。  自我簽署憑證是由客戶或開發人員利用標準的 .NET Framework SDK 工具所產生的憑證，然後再使用標準的 ClickOnce 部署工具套用到部署資訊清單。  如需詳細資訊，請參閱[Makecert.exe \(Certificate Creation Tool\)](../Topic/Makecert.exe%20\(Certificate%20Creation%20Tool\).md)。  
  
 使用自我簽署憑證處理部署資訊清單有幾個優點。  由於客戶不需要取得或建立自己的 Authenticode 憑證，因此 `<useManifestForTrust>` 可以簡化客戶的部署工作，同時也讓開發人員可以在應用程式上保留自己專屬的品牌識別。  這種方式所產生的結果是一組已簽署的部署，而這組部署除了更為安全之外，也會有唯一的應用程式識別，  因此可以消除因為將同一個應用程式部署到多個客戶所可能產生的潛在衝突。  
  
 如需如何在啟用 `<useManifestForTrust>` 的情況下建立 ClickOnce 部署的逐步資訊，請參閱[逐步解說：手動部署不需要重新簽署而且會保留商標資訊的 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md)。  
  
### 信任應用程式資訊清單在執行階段的運作方式  
 若要更進一步了解使用信任應用程式資訊清單在執行階段運作的方式，請參考以下範例。  Microsoft 建立了以 .NET Framework 3.5 為目標的 ClickOnce 應用程式。  其應用程式資訊清單使用 `<useManifestForTrust>` 項目，並由 Microsoft 加以簽署。  Adventure Works 使用自我簽署憑證來簽署部署資訊清單。  Adventure Works 用戶端則已設定為信任由 Microsoft 簽署的任何應用程式。  
  
 當使用者按一下部署資訊清單的連結時，ClickOnce 便會將應用程式安裝在使用者的電腦上。  憑證和部署資訊可讓 ClickOnce 唯一識別用戶端電腦上的應用程式。  如果使用者再次嘗試從不同的位置安裝相同的應用程式，ClickOnce 就可以使用這項識別判斷應用程式是否已經存在用戶端上。  
  
 接著，ClickOnce 會檢查用來簽署應用程式資訊清單的 Authenticode 憑證，並決定 ClickOnce 將授與的信任層級。  由於 Adventure Works 已將其用戶端設定為信任由 Microsoft 簽署的任何應用程式，因此這個 ClickOnce 應用程式將會取得完全信任的授權。  如需詳細資訊，請參閱 [受信任的應用程式部署概觀](../deployment/trusted-application-deployment-overview.md)。  
  
## 建立舊版本的客戶部署  
 如果開發人員要為使用舊版 .NET Framework 的客戶部署 ClickOnce 應用程式，應該如何處理？  以下各節摘要說明幾個建議的方案，以及各個方案的優缺點。  
  
### 代表客戶簽署部署  
 其中一種可能的部署策略是由開發人員建立一種機制，利用客戶本身的私密金鑰來代表客戶簽署部署。  這種方法使得開發人員不需要管理私密金鑰或多個部署套件，  而只需要提供相同的部署給每一位客戶，  然後再由客戶依據其環境，自行利用簽署服務來自訂部署。  
  
 這種方法的其中一個缺點是實作的時間和成本。  雖然這類服務可以使用 .NET Framework SDK 所提供的工具來建置，但是卻會拉長產品生命週期中的開發時間。  
  
 如本主題前面所述，另一個缺點是每個客戶的應用程式版本都會有相同的應用程式識別，而可能產生衝突。  如果這點可能造成問題，開發人員可以變更產生部署資訊清單時所使用的 \[名稱\] 欄位，以針對每個應用程式指定一個唯一的名稱。  如此便可為每個應用程式版本建立個別的識別，也可以消除任何潛在的識別衝突。  這個欄位對應於 Mage.exe 的 `-Name` 引數，以及 MageUI.exe 中 \[**名稱**\] 索引標籤上的 \[**名稱**\] 欄位。  
  
 例如，假設開發人員已經建立一個名為 Application1 的應用程式。  除了建立將 \[名稱\] 欄位設定為 Application1 的單一部署以外，開發人員也可以建立幾個部署，並因客戶不同為這個名稱進行變化，例如 Application1\-CustomerA、Application1\-CustomerB，依此類推。  
  
### 使用安裝套件部署  
 第二個可能的部署策略是產生 Microsoft 安裝專案，以執行 ClickOnce 應用程式的初始部署。  這個安裝專案可以透過幾種不同的格式來提供，包括 MSI 部署、安裝程式可執行檔 \(.EXE\)，或是封包 \(.cab\) 檔搭配批次指令碼等格式。  
  
 使用這種技巧時，開發人員提供給客戶的部署中將包括應用程式檔案、應用程式資訊清單和做為範本的部署資訊清單。  客戶會執行安裝程式，而安裝程式則會提示客戶提供部署 URL \(使用者用來安裝 ClickOnce 應用程式的伺服器或檔案共用位置\) 以及數位憑證。  安裝應用程式可能也會選擇提示其他 ClickOnce 組態選項，例如更新檢查間隔。  在蒐集這些資訊之後，安裝程式便會產生實際的部署資訊清單、簽署該資訊清單，然後將 ClickOnce 應用程式發行到指定的伺服器位置。  
  
 在這種情況下，客戶可以透過下列三種方式來簽署部署資訊清單：  
  
1.  客戶可以使用憑證授權單位 \(CA\) 核發的有效憑證。  
  
2.  與前述方法類似，客戶也可以選擇使用自我簽署憑證來簽署其部署資訊清單。  這種方法的缺點是它會在詢問使用者是否要安裝應用程式時，導致應用程式顯示 \[未知的發行者\] 等文字。  不過，優點是規模較小的客戶不需要花費大量時間和金錢取得憑證授權單位所核發的憑證。  
  
3.  最後，開發人員還可以將他們自己的自我簽署憑證包含在安裝套件中。  這種方法可能會造成本主題前面所述的應用程式識別相關問題。  
  
 安裝部署專案方法的缺點是建置自訂部署應用程式所需的時間和成本。  
  
### 讓客戶產生部署資訊清單  
 第三種可能的部署策略是只將應用程式檔案和應用程式資訊清單交給客戶。  在這種情況下，必須由客戶負責使用 .NET Framework SDK 來產生及簽署部署資訊清單。  
  
 這種方法的缺點是客戶必須安裝 .NET Framework SDK 工具，而且其開發人員或系統管理員必須熟悉這些工具的用法。  有些客戶可能會要求您提供只需要少數技術性需求或根本沒有任何技術性需求的解決方案。  
  
## 請參閱  
 [針對測試和實際執行伺服器部署 ClickOnce 應用程式但不重新簽章](../deployment/deploying-clickonce-applications-for-testing-and-production-servers-without-resigning.md)   
 [逐步解說：手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [逐步解說：手動部署不需要重新簽署而且會保留商標資訊的 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md)