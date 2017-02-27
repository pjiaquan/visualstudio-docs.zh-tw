---
title: "使用 ClickOnce 部署 COM 元件 | Microsoft Docs"
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
  - "ClickOnce 部署, COM 元件"
  - "COM 元件, 部署"
  - "元件, 部署"
  - "部署應用程式 [ClickOnce], COM 元件"
  - "免註冊的 COM 部署"
ms.assetid: 1a4c7f4c-7a41-45f2-9af4-8b1666469b89
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 12
---
# 使用 ClickOnce 部署 COM 元件
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

部署舊版 COM 元件一直是困難的工作。  元件必須是全域註冊，因此它們在重疊的應用程式之間可能造成副作用。  這個情況在 .NET Framework 應用程式中通常不會構成問題，因為元件已完全與應用程式隔離或是並存相容的。  Visual Studio 可讓您將隔離的 COM 元件部署在 Windows XP \(含\) 以上版本作業系統。  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 提供部署 .NET 應用程式的簡單安全機制。  不過，如果應用程式使用舊版 COM 元件，您將需要其他部署步驟。  此主題描述如何部署隔離的 COM 元件和參考原生元件 \(例如，取自 Visual Basic 6.0 或 Visual C\+\+ 的元件\)。  
  
 如需部署隔離的 COM 元件的詳細資訊，請參閱＜使用 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 和免註冊的 COM 簡化應用程式部署＞\(英文\) \(位於 [http:\/\/msdn.microsoft.com\/msdnmag\/issues\/05\/04\/RegFreeCOM\/default.aspx](http://msdn.microsoft.com/msdnmag/issues/05/04/RegFreeCOM/default.aspx) 上\)。  
  
## 免註冊的 COM  
 免註冊的 COM 是部署及啟動隔離之 COM 元件的一項新技術。  若要啟用該技術，只要將所有元件的型別程式庫和一般安裝在系統登錄中的註冊資訊，置入名為 manifest 的 XML 檔案 \(該檔案儲存在與應用程式相同的資料夾內\) 即可。  
  
 隔離 COM 元件的必要條件是，該元件必須已在開發人員的電腦上註冊，但在使用者的電腦上則不一定要進行註冊。  若要隔離 COM 元件，您只需要將它的參考的 \[**Isolated**\] 屬性設定為 \[**True**\] 即可。  此屬性預設會設定為 \[**False**\]，表示應該將它視為已註冊的 COM 參考。  如果這個屬性為 \[**True**\]，則在建置時間將會產生這個元件的資訊清單。  還會造成在安裝期間，將對應的檔案複製到應用程式資料夾中。  
  
 當資訊清單產生器遇到隔離的 COM 參考時，它會列舉元件型別程式庫中所有的 `CoClass` 項目，將每個項目與它對應的系統註冊資料進行比對，並為型別程式碼檔中的所有 COM 類別產生資訊清單定義。  
  
## 使用 ClickOnce 部署免註冊的 COM 元件  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署技術非常適合用來部署隔離的 COM 元件，因為 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 和免註冊的 COM 都需要具有資訊清單的元件才能進行部署。  
  
 元件作者通常應該提供資訊清單。  如果沒有提供，Visual Studio 也能夠為 COM 元件自動產生資訊清單。  資訊清單產生會在 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 的 \[發行\] 處理序期間執行；如需詳細資訊，請參閱[發行 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)。  這個功能也可讓您使用在先前開發環境 \(例如 Visual Basic 6.0\) 中所撰寫的舊版元件。  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 有兩個部署 COM 元件的方法：  
  
-   使用啟動載入器 \(Bootstrapper\) 部署 COM 元件，適用於所有支援的平台。  
  
-   使用原生元件隔離 \(又稱為免註冊的 COM\) 部署。  不過，只適用於 Windows XP \(含\) 以上版本作業系統。  
  
### 隔離及部署簡單 COM 元件的範例  
 為了示範免註冊的 COM 元件的部署，此範例會在 Visual Basic 中建立 Windows 架構應用程式 \(該應用程式會參考使用 Visual Basic 6.0 建立的隔離原生 COM 元件\)，再利用 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署它。  
  
 首先，您必須先建立原生 COM 元件：  
  
##### 若要建立原生 COM 元件  
  
1.  使用 Visual Basic 6.0，按一下 \[**檔案**\] 功能表中的 \[**新增**\]，再按一下 \[**專案**\]。  
  
2.  在 \[**新增專案**\] 對話方塊中，選取 \[**Visual Basic**\] 節點，再選取 \[**ActiveX DLL**\] 專案。  在 \[**名稱**\] 方塊中，輸入 `VB6Hello`。  
  
    > [!NOTE]
    >  免註冊的 COM 只支援使用 ActiveX DLL 和 ActiveX 控制項專案類型；ActiveX EXE 和 ActiveX 文件專案類型不受支援。  
  
3.  在 \[**方案總管**\] 中，按兩下 \[**Class1.vb**\] 開啟文字編輯器。  
  
4.  在 Class1.vb 中，在為 `New` 方法產生的程式碼之後，加入下列程式碼：  
  
    ```  
    Public Sub SayHello()  
       MsgBox "Message from the VB6Hello COM component"  
    End Sub  
    ```  
  
5.  建置元件。  在 \[**建置**\] 功能表中，按一下 \[**建置方案**\]。  
  
> [!NOTE]
>  免註冊的 COM 僅支援 DLL 和 COM 控制項專案類型。  您無法將 EXE 與免註冊的 COM 一起使用。  
  
 現在，您可以建立 Windows 架構的應用程式並將 COM 元件的參考加入其中。  
  
##### 若要使用 COM 元件建立 Windows 架構應用程式  
  
1.  使用 Visual Basic，按一下 \[**檔案**\] 功能表中的 \[**新增**\]，再按一下 \[**專案**\]。  
  
2.  在 \[**新增專案**\] 對話方塊中，選取 \[**Visual Basic**\] 節點，再選取 \[**Windows 應用程式**\]。  在 \[**名稱**\] 方塊中，輸入 `RegFreeComDemo`。  
  
3.  在 \[**方案總管**\] 中，按一下 \[**顯示所有檔案**\] 按鈕顯示專案參考。  
  
4.  以滑鼠右鍵按一下 \[**參考**\] 節點，再從內容功能表中選取 \[**加入參考**\]。  
  
5.  在 \[**加入參考**\] 對話方塊中，按一下 \[**瀏覽**\] 索引標籤，瀏覽到 VB6Hello.dll，然後選取它。  
  
     \[**VB6Hello**\] 參考會出現在參考清單中。  
  
6.  指向 \[**工具箱**\]，選取 \[**按鈕**\] 控制項，再將它拖曳到 \[**Form1**\] 表單。  
  
7.  在 \[**屬性**\] 視窗中，將按鈕的 \[**Text**\] 屬性設定為 Hello。  
  
8.  按兩下按鈕以便加入處理常式程式碼，然後在原始程式碼檔中加入程式碼，則處理常式看起來如下所示：  
  
    ```  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
        Dim VbObj As New VB6Hello.Class1  
        VbObj.SayHello()  
    End Sub  
    ```  
  
9. 執行應用程式。  在 \[**偵錯**\] 功能表中按一下 \[**啟動偵錯**\]。  
  
 接下來，您必須隔離控制項。  在專案中將應用程式使用的每個 COM 元件表示為 COM 參考。  在 \[**方案總管**\] 視窗中的 \[**參考**\] 節點底下，可以找到這些參考   \(請注意，您可以透過下列方式加入參考：直接利用 \[**專案**\] 功能表中的 \[**加入參考**\] 命令，或間接將 ActiveX 控制項拖曳到表單上\)。  
  
 下列步驟會示範如何隔離 COM 元件，以及發行內含隔離控制項的更新應用程式：  
  
##### 若要隔離 COM 元件  
  
1.  在 \[**方案總管**\] 的 \[**參考**\] 節點中，選取 \[**VB6Hello**\] 參考。  
  
2.  在 \[**屬性**\] 視窗中，將 \[**Isolated**\] 屬性的值從 \[**False**\] 變更為 \[**True**\]。  
  
3.  在 \[**建置**\] 功能表中，按一下 \[**建置方案**\]。  
  
 現在按下 F5 的話，應用程式會如預期般運作，但它目前是使用免註冊的 COM 來執行。  為了證實此點，請試著在 Visual Studio IDE 外移除註冊 VB6Hello.dll 元件並執行 RegFreeComDemo1.exe。  這麼做之後再按一下按鈕的話，它仍能運作。  如果您暫時將應用程式資訊清單重新命名，則它會再次失敗。  
  
> [!NOTE]
>  您可以藉由暫時移除註冊 COM 元件，模擬缺少它的情況。  請開啟命令提示字元，輸入 `cd /d %windir%\system32`，移至系統資料夾，再輸入 `regsvr32 /u VB6Hello.dll`，移除註冊元件。  您可以輸入 `regsvr32 VB6Hello.dll`，重新註冊此元件。  
  
 最後一個步驟是使用 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 發行應用程式：  
  
##### 若要使用隔離的 COM 元件發行應用程式更新  
  
1.  從 \[**建置**\] 功能表中，按一下 \[**發行 RegFreeComDemo**\]。  
  
     \[發行精靈\] 隨即出現。  
  
2.  在 \[發行精靈\] 中，指定本機電腦磁碟上的一個位置，您可以在此位置存取及檢視已發行的檔案。  
  
3.  按一下 \[**完成**\] 發行應用程式。  
  
 如果您檢查已發行的檔案，會注意到 sysmon.ocx 檔已包含在內。  該控制項已完全與此應用程式隔離，這表示如果使用者電腦上有另一個使用不同控制項版本的應用程式，該控制項也不會妨礙此應用程式。  
  
## 參考原生組件  
 Visual Studio 支援對原生 Visual Basic 6.0 或 C\+\+ 組件的參考；此類參考稱為原生參考。  您可以透過確認參考的 \[**File Type**\] 屬性已設定為 \[**Native**\] 或 \[**ActiveX**\]，藉此分辨參考是否為原生參考。  
  
 若要加入原生參考，請使用 \[**加入參考**\] 命令，然後瀏覽至資訊清單。  部分元件將資訊清單放在 DLL 中。  在這個情況下，您只需要選擇 DLL 本身，當 Visual Studio 偵測到元件包含內嵌資訊清單時，就會把它當做原生參考加入。  如果資訊清單中所列的任何相依檔或組件和參考的元件位在相同的資料夾中，Visual Studio 也會自動將它們納入。  
  
 COM 控制項隔離可讓還沒有資訊清單之 COM 元件的部署工作變得容易。  但是，如果元件已具備資訊清單，則可以直接參考此資訊清單。  事實上，只要可能的話，您應該都要使用由元件作者所提供的資訊清單，而不是使用 \[**Isolated**\] 屬性。  
  
## 免註冊 COM 元件的部署限制  
 免註冊的 COM 提供清楚超越傳統部署技巧的優勢。  不過，在這裡我們也必須指出一些限制和警告。  最大的限制是它只適用於 Windows XP \(含\) 以上版本。  免註冊的 COM 實作 \(Implementation\) 必須變更元件載入核心作業系統的方式。  不幸地，免註冊的 COM 沒有舊版支援層。  
  
 不是所有元件都適合使用免註冊的 COM。  如果元件符合下列其中一個條件，它就不適合：  
  
-   元件是跨處理序的伺服器。  EXE 伺服器不受支援；只支援 DLL。  
  
-   元件屬於作業系統的一部分，或者它本身就是一個系統元件，例如 XML、Internet Explorer 或 Microsoft Data Access Components \(MDAC\)。  您應該依循元件作者的轉散發原則；請洽詢您的廠商。  
  
-   元件屬於應用程式的一部分，如 Microsoft Office。  舉例來說，您不應該嘗試隔離 Microsoft Excel 物件模型。  因為它屬性 Office 的一部分，而且只能在已安裝完整 Office 產品的電腦上使用該元件。  
  
-   元件主要做為增益集或嵌入式管理單元使用，例如 Office 增益集或 Web 瀏覽器中的控制項。  這類元件一般都需要某種由裝載環境所定義的註冊機制，而該機制卻超出資訊清單本身的範圍。  
  
-   元件會管理系統的實體或虛擬裝置，例如，列印多工緩衝處理程式的裝置驅動程式。  
  
-   元件一個 Data Access 可轉散發套件。  資料應用程式通常必須在它們開始執行之前，先安裝個別的 Data Access 可轉散發套件。  您不應該嘗試隔離元件，例如 Microsoft ADO 資料控制項、Microsoft OLE DB 或 Microsoft Data Access Components \(MDAC\)。  如果您的應用程式改為使用 MDAC 或 SQL Server Express，您應該將它們設為必要條件；請參閱 [如何：使用 ClickOnce 應用程式安裝必要條件](../Topic/How%20to:%20Install%20Prerequisites%20with%20a%20ClickOnce%20Application.md)。  
  
 在某些情況下，元件開發人員可能可以為免註冊的 COM 重新設計元件。  如果不可能這麼做，您仍可以透過使用啟動載入器 \(Bootstrapper\) 的標準註冊機制，建置及發行相依於這些元件的應用程式。  如需詳細資訊，請參閱 [建立啟動載入器套件](../deployment/creating-bootstrapper-packages.md)。  
  
 每個應用程式只能隔離一次 COM 元件。  例如，您不能從兩個不同的 \[**類別庫**\] \(Class Library\) 專案，將屬於相同應用程式一部分的相同 COM 元件加以隔離。  這麼做會造成建置警告，而且應用程式將無法在執行階段載入。  為了避免這個問題，Microsoft 建議您在單一類別庫中封裝 COM 元件。  
  
 在部分案例中，即使應用程式的部署不需要註冊，開發人員的機器上還是需要 COM 註冊。  為了在建置期間自動產生資訊清單，`Isolated` 屬性必須在開發人員的機器上註冊 COM 元件。  在建置期間，並沒有叫用自我登錄的登錄捕捉功能。  而且，未在型別程式庫中明確定義的任何類別將不會反映在資訊清單中。  使用具有預先存在之資訊清單 \(例如原生參考\) 的 COM 元件時，可能不需要在開發階段註冊元件。  但是，如果元件是 ActiveX 控制項而且您想在 \[**工具箱**\] 和 Windows Form 設計工具中包含該元件，便需要註冊。  
  
## 請參閱  
 [ClickOnce 安全性和部署](../deployment/clickonce-security-and-deployment.md)