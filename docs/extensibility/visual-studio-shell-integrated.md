---
title: "Visual Studio Shell （整合模式） |Microsoft 文件"
ms.custom: 
ms.date: 02/17/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, integrated mode features
- Shell [Visual Studio], integrated mode features
ms.assetid: 0b40d495-f17f-4bb9-ace8-b365a7172784
caps.latest.revision: 26
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
ms.sourcegitcommit: 4f2ddbc47f9a014acde2850dba5c72ef3a784847
ms.openlocfilehash: 8edd3a6fcca0c2ddd4d580f0874b737cfbbc40c9
ms.lasthandoff: 03/01/2017

---
# <a name="visual-studio-shell-integrated"></a>Visual Studio Shell （整合模式）
Visual Studio 整合式 shell 包括整合式的開發環境 (IDE)、 偵錯工具和原始檔控制整合。 不就會包含任何程式設計語言。 不過，整合式的 shell 並提供一種架構，可讓您新增的程式語言。  
  
 Visual Studio 整合式介面是實際的 Visual Studio 隔離 shell 加上其他的安裝，包括整合式的 shell 特定元件的組合。  整合式的 shell 應用程式應包含這兩個獨立的 shell 可轉散發套件從[Microsoft Visual Studio Shell （獨立模式） 可轉散發套件](http://go.microsoft.com/fwlink/?LinkId=616022)以及從整合式的 shell 可轉散發套件[Microsoft Visual Studio Shell （整合模式） 可轉散發套件](http://go.microsoft.com/fwlink/?LinkId=616021)。  
  
> [!NOTE]
>  您可以存取隔離和整合式 shell 可轉散發套件之前，系統會要求您填寫簡短的客戶問卷調查。  之後填寫問卷調查，您將被導向至 Visual Studio Connect 含可轉散發套件的下載連結。  您可以在後續造訪 Visual Studio 連線站台底下找到下載連結**程式 |VISUAL STUDIO 2015 整合和隔離 SHELL**  索引標籤。  
  
 如果完整版本的 Visual Studio 的同一部電腦上安裝整合式的 shell 應用程式，將會直接在 Visual Studio 整合應用程式的元件。  
  
## <a name="features-in-the-integrated-shell"></a>整合式 shell 的功能  
  
|||  
|-|-|  
|功能區|功能|  
|語言支援|-無|  
|IDE|<ul><li>設定<br /><br /> <ul><li>建立設定</li><li>匯入和匯出設定</li><li>重設設定</li></ul></li><li>**工具箱**整合</li><li>**工作清單**整合</li><li>說明整合</li><li>**選項**對話方塊</li><li>字型和色彩管理</li><li>**輸出**視窗</li><li>**命令**視窗</li><li>視窗管理</li><li>命令、 功能表和索引鍵繫結</li><li>定義域專屬語言 (DSL) 執行階段</li></ul>|  
|專案系統和專案類型|-方案和方案資料夾<br />方案組態管理員<br />項目管理<br />為單一專案和多專案方案<br />應用程式的設計工具 （簡化的專案屬性）<br />加入 Web 參考<br />加入服務參考<br />間單一專案的<br />為網站專案類型<br />Web 應用程式專案|  
|組建|的在 IDE 中自訂建置步驟<br />預先編譯保護智慧財產 (IP)<br />程式碼簽署<br />     MSBuild|  
|編輯器|程式瀏覽工具統一的尋找、 來源定義 （繼承） 的碼<br />程式碼巡覽<br />-IntelliSense<br />-智慧標籤<br />-重構<br />-美化<br />-IntelliSense 篩選<br />-   **程式碼定義**視窗|  
|Designer|Windows Presentation Foundation 設計工具<br />Windows Form 設計工具<br />-Web 設計工具和 HTML 編輯器|  
|資料|-   **伺服器總管**(簡化︰ 僅限資料)。 請參閱「注意 1」。<br />-   **資料來源**視窗<br />-完整的資料控制項<br />XML 編輯器<br />資料繫結至本機資料來源 (。MDF 或。MDB)<br />資料繫結至物件<br />資料繫結至 Web 服務<br />資料繫結到本機資料庫伺服器<br />資料繫結到遠端資料庫伺服器<br />遠端資料的 DDL 工具<br />-   **伺服器總管**擴充性 ([!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]範例)|  
|偵錯工具|本機偵錯。 請參閱附註 2。<br />-Managed 偵錯<br />本機偵錯<br />附加至本機處理序<br />附加至遠端處理序<br />匿名委派<br />-應用程式定義域<br />-ASPX 偵錯<br />屬性<br />-在函式評估期間中斷<br />-中斷點<br />中斷點條件約束<br />的呼叫堆疊<br />-   **命令**視窗<br />-跨執行緒偵錯<br />資料提示<br />資料視覺化檢視<br />-Managed 偵錯助理 (Mda) 偵錯工具支援<br />-類型轉送子偵錯工具支援<br />-DTEEvents OTB 支援<br />-JMC Stepper<br />偵錯程式 AppID 測試 (DBGCLR)<br />偵錯程式設定檔<br />-偵錯工具的工具和選項<br />-偵錯迭代器<br />為設計階段運算式評估<br />-C# 運算式評估工具<br />-反組譯碼<br />-編輯後繼續<br />運算式評估工具視窗 （監看式 區域變數 自動變數）<br />發生例外狀況時的協助程式<br />-例外狀況<br />執行<br />泛型<br />-取得正確的來源<br />-HPC/叢集偵錯<br />整合多國語言偵錯<br />-InterOp 偵錯<br />--Just-in-time 偵錯<br />本機偵錯<br />-Managed 偵錯<br />-手動控制 （處理序視窗）<br />不足記憶體<br />的支援小型傾印<br />-模組<br />-多處理序偵錯<br />原生偵錯<br />新的偵錯引擎支援<br />-最佳化程式碼偵錯<br />篩選輸出視窗<br />-處理裝載 managed 偵錯<br />-處理程序<br />-快速監看式<br />註冊<br />堆疊中註冊<br />為遠端偵錯<br />傳回值<br />指令碼偵錯<br />原始碼服務支援<br />安全性<br />---並排<br />SQL<br />符號伺服器<br />追蹤點<br />執行緒<br />-視覺效果<br />-可延伸樣式表語言轉換 (XSLT) 偵錯工具|  
|64 位元支援|-64 位元偵錯 managed 和原生程式碼，所有語言<br />-x64 原生支援|  
|原始程式碼控制 (SCC)|-基本 SCC 整合。 請參閱「注意 3」。<br />-工具和選項驗證|  
|擴充性|-使用 VSPackages 與 MEF 元件|  
  
## <a name="notes"></a>附註  
  
#### <a name="1-data-tools"></a>1.資料工具  
 整合式的 shell 包括資料庫開發工具，例如資料擴充性支援和簡化**方案總管 中**。 不過，SQL Server Express、 SQL 報告和詳細報告將不會納入整合式 shell。  
  
#### <a name="2-debugging-support"></a>2.偵錯支援  
 整合式的 shell 包含相同的偵錯引擎都包含在 Visual Studio 社群版本。 在偵錯引擎包含 managed 程式碼，以及相關的功能，一般的偵錯工具，例如連接、 設定中斷點、 編輯後繼續，以及其他人執行。 不過，在偵錯引擎不支援 SQL Server 資料庫偵錯。  
  
 雖然支援原生偵錯，就會包括基本的偵錯工具套件，您無法擴充以支援其他語言。  
  
#### <a name="3-source-code-control-integration"></a>3.原始程式碼控制整合  
 整合式的 shell 提供 Api 實作原始程式碼控制 (SCC) 以及提供 MSSCCI 基礎通用的原始檔控制整合元件。  
  
 雖然 SCC 整合不是一般的 Visual Studio Pro 版本功能，SCC 整合提供整合式 shell。  
  
#### <a name="4-build-support"></a>4.建置支援  
 整合式的 shell 建置支援。 您可以找到資訊中的組建[MSBuild 參考](../msbuild/msbuild-reference.md)。  
  
## <a name="features-not-included-in-the-integrated-shell"></a>不包含在整合式 Shell 的功能  
 以下是不包含在整合式 shell 的功能清單︰  
  
-   類別設計工具  
  
-   [先佔式保護-Dotfuscator](../ide/dotfuscator/index.md)  
  
-   語言功能  
  
-   VSHost  
  
-   沒有 Visual Studio 語言或其相關聯的專案範本或專案項目範本，會包含在整合式 shell。 沒有特定語言的實作其他功能還包括，範例的 Visual Basic 程式碼片段。  
  
## <a name="see-also"></a>另請參閱  
 [擴充 Visual Studio 概觀](../Topic/Extending%20Visual%20Studio%20Overview.md)
