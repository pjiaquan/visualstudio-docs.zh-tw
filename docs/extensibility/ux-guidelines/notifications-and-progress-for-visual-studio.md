---
title: "通知和 Visual Studio 進行 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f0ef65e9-0f1f-45f4-9f25-6e2398691168
caps.latest.revision: 6
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
ms.openlocfilehash: 1f7823754601161200edafdce998ebe9aeab2723
ms.lasthandoff: 02/22/2017

---
# <a name="notifications-and-progress-for-visual-studio"></a>通知和 Visual Studio 的進度
##  <a name="a-namebkmknotificationsystemsa-notification-systems"></a><a name="BKMK_NotificationSystems"></a>通知系統  
  
### <a name="overview"></a>概觀  
 有幾種方式來通知使用者發生什麼事 Visual Studio 中有關軟體開發工作。  
  
 當實作任何一種通知︰  
  
-   **保留的最小值的通知數目**有效數字。 通知訊息應該套用到大多數的 Visual Studio 使用者或特定功能/功能區域的使用者。 過度使用的通知可能 sidetrack 使用者，或降低可察覺的容易使用的系統。  
  
-   **請確定您要呈現清楚、 可採取動作的訊息**使用者可用來叫用適當的內容進行更複雜的選擇和採取進一步動作。  
  
-   **適當地呈現同步和非同步的訊息。** 同步通知表示需要立即處理，例如當 web 服務當機或程式碼擲回例外狀況。 這兩種情況中需要他們的意見，例如，在強制回應對話方塊的方式立即應該通知使用者。 非同步通知是使用者應該了解，但不是需要處理，例如網站上部署或建置作業完成時完成。 這些訊息應該更環境並不會中斷使用者的工作流程。  
  
-   **使用強制回應對話方塊，以防止使用者採取進一步動作的必要時才**之前認可訊息，或在對話方塊中的決定。  
  
-   **已不再有效時，請移除環境的通知。** 不需要以關閉通知，如果它們已採取的動作來解決這個問題已通知使用者。  
  
-   **請注意通知，可能會導致錯誤的關聯。** 使用者可能會認為，一或多個動作，其已觸發通知時事實上是沒有因果關係。 清除是相關的內容、 觸發程序和通知的來源通知訊息。  
  
### <a name="choosing-the-right-method"></a>選擇正確的方法  
 您可以使用此表格來協助您選擇正確的方法，以通知訊息的使用者。  
  
|方法|用法|請勿使用|  
|------------|---------|----------------|  
|[強制回應錯誤訊息對話方塊](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ModalErrorMessageDialogs)|當繼續進行之前，需要使用者回應時使用。|請勿使用時需要封鎖使用者，並中斷其流程。 請避免使用強制回應對話方塊，如果可能的話，以顯示訊息另一個、 較不干擾的方式。|  
|[IDE 狀態列](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_IDEStatusBar)|環境文字資訊與狀態相關的處理程序時使用。|請勿使用單獨。 適用於搭配其他的意見反應機制。|  
|[內嵌資訊列](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedInfobar)|在工具視窗或文件視窗中，使用通知進度、 錯誤狀態/結果或可採取動作的資訊。|請勿使用如果沒有與放置資料列的位置相關資訊。<br /><br /> 請勿使用外部文件/工具視窗。|  
|[滑鼠游標會變更](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_MouseCursorChanges)|可能用於通知的處理序正在進行的作業。 也用來通知的狀態變更滑鼠，例如滑鼠游標在進度或拖放時處於特定模式，例如繪圖模式。|不使用簡短進行變更，或如果 fluttering 的資料指標有可能 （例如，當繫結至組件的時間執行的處理序而不是整個程序）。|  
|[進度指標](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotSysProgressIndicators)|當您需要報告進度 （確定或不明確） 時使用。 有各種不同的進度指標類型和每個特定的使用方式。 請參閱[進度指標](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators)。||  
|[Visual Studio 的 [通知] 視窗](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_VSNotificationsToolWindow)|[通知] 視窗並未開放擴充。 不過，它用來進行通訊的各種 Visual Studio 中，包括重大的問題與您的授權資訊性通知更新至 Visual Studio 或套件的相關訊息。|請勿使用其他類型的通知。|  
|[錯誤清單](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ErrorList)|當此問題是與使用者的目前開啟的方案，有問題 （錯誤/警告/資訊） 時，他們可能需要採取動作的程式碼。<br /><br /> 這包括，例如︰<br /><br /> 編譯器訊息 （錯誤/警告/資訊）<br /><br /> 程式關於程式碼的碼分析/診斷訊息<br /><br /> 建置訊息<br /><br /> 可能很適合專案或方案檔中，相關的問題，但是先考慮的方案總管 中的指示。|請勿使用沒有任何關聯的使用者開啟方案的程式碼的項目。|  
|編輯器通知︰ 燈泡|當您有可供解決中開啟的檔案有問題的修正時使用。<br /><br /> 請注意燈泡也應使用裝載的快速動作進行隨選、 重整作業，例如使用者的程式碼，但在此情況下不會出現 「 通知樣式 」。|請勿使用開啟的檔案沒有任何關聯的項目。|  
|編輯器通知︰ 波浪線|使用提醒使用者他們開啟的程式碼 （例如，紅色曲線的錯誤） 的特定範圍的問題。|請勿使用不相關的開啟程式碼的特定範圍的項目。|  
|[內嵌的狀態列](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedStatusBars)|使用提供的內容或特定的工具視窗、 文件視窗或對話方塊視窗的內容中的程序相關的狀態。|請勿使用一般產品通知、 處理程序，或在特定時段內沒有任何關聯性內容的項目。|  
|[Windows 系統匣通知](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_WindowsTray)|用來呈現跨處理序的處理程序的通知或附屬應用程式。|請勿使用 IDE 與相關的通知。|  
|[通知泡泡](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotificationBubbles)|使用遠端程序的通知，或變更**外**的 IDE。|請勿使用做為通知使用者的處理序**內**IDE。|  
  
### <a name="notification-methods"></a>通知方法  
  
####  <a name="a-namebkmkmodalerrormessagedialogsa-modal-error-message-dialogs"></a><a name="BKMK_ModalErrorMessageDialogs"></a>強制回應錯誤訊息對話方塊  
 強制回應錯誤訊息對話方塊用來顯示錯誤訊息，要求使用者確認或動作。  
  
 ![強制回應錯誤訊息](../../extensibility/ux-guidelines/media/0901-01_modalerrormessage.png "0901年&01;_ModalErrorMessage")  
  
 **警示無效的連接字串至資料庫的使用者強制回應錯誤訊息對話方塊**  
  
####  <a name="a-namebkmkidestatusbara-ide-status-bar"></a><a name="BKMK_IDEStatusBar"></a>IDE 狀態列  
 使用者注意到狀態列文字的可能性相互關聯的全能電腦體驗和 Windows 平台特定的經驗。 Visual Studio 客戶通常會在這兩個區域中，有經驗，不過即使是經驗豐富的 Windows 使用者可能會錯過在狀態列中的變更。 因此，[狀態] 列最適合僅供參考之用，或做為備援提示的資訊顯示在其他位置。 在對話方塊中，或通知工具視窗中應提供任何類型的使用者必須立即解決的重要資訊。  
  
 Visual Studio 的 [狀態] 列被設計來提供數種類型的資訊顯示。 它被分割成的意見反應、 設計工具、 進度列、 動畫和用戶端區域。  
  
 意見反應區域和設計工具區域會永遠顯示。 進度列和動畫區域永遠是動態的而且根據使用者內容。 設計工具區域的靜態寬度取決於提取來自隨附的資源的文字訊息字串的長度。 這可讓當地語系化為調整寬度，而不需要變更程式碼。 英文，這個字串的寬度約為 220 的像素。 設計工具區域將會正常運作和意見反應區域可以吸收剩餘的空間。  
  
 [狀態] 列也以色彩標示傳達各種 IDE 狀態變更，例如當 IDE 偵錯模式中加入視覺效果和功能的值。  
  
 ![IDE 狀態列色彩變更](../../extensibility/ux-guidelines/media/0901-02_idestatusbar.png "0901年&02;_IDEStatusBar")  
  
 **IDE 狀態列色彩**  
  
####  <a name="a-namebkmkembeddedinfobara-embedded-infobar"></a><a name="BKMK_EmbeddedInfobar"></a>內嵌資訊列  
 資訊列可在文件視窗或工具視窗頂端的通知狀態或條件的使用者。 它也提供命令，以便使用者能夠輕鬆地採取動作。 資料列是標準的介面控制項。 請避免建立您自己，以採取行動，會出現不一致，有其他人在 IDE 中。 請參閱[資訊列](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars)實作詳細資料和使用方式的指引。  
  
 ![內嵌資訊列](../../extensibility/ux-guidelines/media/0901-03_embeddedinfobar.png "0901年&03;_EmbeddedInfobar")  
  
 **資訊列會內嵌在文件視窗中，警示使用者，IDE 歷程偵錯模式中編輯器 中將不會回應相同的方式與標準偵錯模式中。**  
  
####  <a name="a-namebkmkmousecursorchangesa-mouse-cursor-changes"></a><a name="BKMK_MouseCursorChanges"></a>滑鼠游標會變更  
 將滑鼠游標變更，當使用繫結至 VSColor 服務，而且已經與資料指標相關聯的色彩。 游標會變更用於表示進行中作業，以及叫用使用者停留所在可以拖曳、 置放，或使用選取的物件為目標的區域。  
  
 只有當所有可用的 CPU 時間必須保留為作業，防止使用者來表示任何進一步的輸入時，請使用等候忙碌滑鼠游標。 撰寫完善的應用程式使用多執行緒處理大部分的情況下，當使用者將無法執行其他作業的時間應該很少見。  
  
 請記住，游標會變更是相當有用的資訊重複提示呈現在其他位置。 請勿依賴游標變更做為唯一的方式與使用者進行通訊，尤其是當嘗試傳遞項目這一點十分重要的使用者必須解決。  
  
####  <a name="a-namebkmknotsysprogressindicatorsa-progress-indicators"></a><a name="BKMK_NotSysProgressIndicators"></a>進度指標  
 進度指標是重要花幾秒才能完成的處理程序期間提供的使用者意見反應。 您可以顯示進度指示器就地 （靠近的啟動點的動作進行中），內嵌的狀態列、 強制回應對話方塊，或在 Visual Studio 狀態列中。 請依照下列中的指導方針[進度指示器](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators)有關其使用和實作。  
  
####  <a name="a-namebkmkvsnotificationstoolwindowa-visual-studio-notifications-window"></a><a name="BKMK_VSNotificationsToolWindow"></a>Visual Studio 的 [通知] 視窗  
 Visual Studio 的 [通知] 視窗會通知開發人員授權、 環境 (Visual Studio)、 延伸及更新。 使用者可以關閉個別通知，或者可以選擇忽略特定類型的通知。 在管理的忽略通知清單的**工具 > 選項**頁面。  
  
 [通知] 視窗不是目前可延伸的。  
  
 ![Visual Studio 的 [通知] 視窗](../../extensibility/ux-guidelines/media/0901-06_vsnotificationswindow.png "0901年&06;_VSNotificationsWindow")  
  
 **Visual Studio 通知工具視窗**  
  
####  <a name="a-namebkmkerrorlista-error-list"></a><a name="BKMK_ErrorList"></a>錯誤清單  
 錯誤清單中的通知指出錯誤與警告的編譯期間發生，或建置程序，並可讓使用者瀏覽至該特定程式碼錯誤的程式碼中。  
  
 ![錯誤清單](../../extensibility/ux-guidelines/media/0901-08_errorlist.png "0901年&08;_ErrorList")  
  
 **在 Visual Studio 中的錯誤清單**  
  
####  <a name="a-namebkmkembeddedstatusbarsa-embedded-status-bars"></a><a name="BKMK_EmbeddedStatusBars"></a>內嵌的狀態列  
 IDE 狀態列是動態的與設定為使用中的文件視窗和資訊更新使用者的內容和 （或） 系統回應其用戶端區域內容，因為很難維護連續顯示資訊或提供長期的非同步處理序的狀態。 比方說，IDE 狀態列不適當的多個執行及/或立即採取行動的項目選取項目執行的測試結果的通知。 請務必保留文件或工具視窗使用者進行選取，或啟動的處理序的內容中的這類狀態資訊。  
  
 ![內嵌的狀態列](../../extensibility/ux-guidelines/media/0901-09_embeddedstatusbar.png "0901年&09;_EmbeddedStatusBar")  
  
 **在 Visual Studio 中的內嵌的狀態列**  
  
####  <a name="a-namebkmkwindowstraya-windows-tray-notifications"></a><a name="BKMK_WindowsTray"></a>Windows 系統匣通知  
 Windows 通知區域旁邊系統時鐘在 Windows 工作列上。 許多公用程式和軟體元件提供此區域中的圖示，讓使用者可取得整個系統的工作，例如變更螢幕解析度，或取得軟體更新的內容功能表。  
  
 環境層級通知應該顯示在 Visual Studio 通知中樞，而不 Windows 通知區域中。  
  
####  <a name="a-namebkmknotificationbubblesa-notification-bubbles"></a><a name="BKMK_NotificationBubbles"></a>通知泡泡  
 通知泡泡會顯示成參考用訊息在編輯器/設計工具或 Windows 通知區域的一部分。 使用者視為這些泡泡它們之後，就可以解決的問題也就是關鍵的通知的一項優點。 （泡泡） 是適當的使用者就必須立即解決的重要資訊。 如果您在 Visual Studio 中使用通知 （泡泡），請遵循[Windows 桌面通知泡泡指導](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742472\(v=vs.85\).aspx)。  
  
 ![通知泡泡](../../extensibility/ux-guidelines/media/0901-07_notificationbubbles.png "0901年&07;_NotificationBubbles")  
  
 **使用 Visual studio 的 Windows 通知區域中的通知泡泡**  
  
##  <a name="a-namebkmkprogressindicatorsa-progress-indicators"></a><a name="BKMK_ProgressIndicators"></a>進度指標  
  
### <a name="overview"></a>概觀  
 進度指示器都是提供使用者意見反應的通知系統的重要部分。 程序和操作將會完成時，它們會告訴使用者。 熟悉的指標類型包括進度列、 旋轉資料指標和動畫的圖示。 型別和進度列指示器的位置取決於內容，包括報告的內容和多久程序或作業才會完成。  
  
#### <a name="factors"></a>因素  
 若要判斷適當指標類型，您必須判斷下列因素。  
  
1.  **執行時間︰**作業所花的時間長度  
  
2.  **樣式︰**作業是強制性的環境 （鎖定 UI 程序完成之前）  
  
3.  **持續/暫時性︰**進度的最終結果是否需要在稍後會報告和/或檢視  
  
4.  **確定/未決︰**是否可以計算作業的結束時間和進度  
  
5.  **圖形/Textual 位置︰**進度或處理序是否擷取的內嵌，本文的訊息或特定的控制項，例如樹狀目錄控制項  
  
6.  **鄰近︰**是否進度應該非常接近關聯的 UI。 （比方說，它可以在狀態列上，這可能是遠，或沒有要附近的按鈕，啟動處理序）？  
  
#### <a name="determinate-progress"></a>確定的進度  
  
|進行型別|何時及如何使用|備註|  
|-------------------|-------------------------|-----------|  
|（確定） 的進度列|預期的持續時間 >&5; 秒。<br /><br /> 可能包含文字描述的程序詳細資料。|**不要**嵌入動畫的文字。|  
|資訊列|訊息內容的 UI 相關聯。 請參閱[資訊列](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars)。<br /><br /> 可能包含文字描述的程序詳細資料。|**不**使用多個資訊列，當您想要表示多個處理序。 請改用堆疊的進度列。|  
|輸出視窗|暫時性通知︰ 應用程式層級程序，使用者想要**檢閱**完成後的詳細資料。|**不要**如果使用者將需要稍後參考資料使用。|  
|記錄檔|搭配 intransient 通知，萬一時請務必**儲存**完成後的詳細資料。||  
|狀態列|暫時性通知︰ 應用程式層級程序，使用者將**不需要**的詳細資料之後完成。<br /><br /> 包含內嵌的進度列。<br /><br /> 可能包含文字描述的程序詳細資料。||  
  
#### <a name="indeterminate-progress"></a>不確定的進度  
  
|進行型別|何時及如何使用|備註|  
|-------------------|-------------------------|-----------|  
|（確定） 的進度列|預期的持續時間 >&5; 秒。<br /><br /> 可能包含文字描述的程序詳細資料。|**不要**嵌入動畫的文字。|  
|螞蟻 （水平點動畫）|伺服器的來回行程。<br /><br /> 放置 near 點內容的父容器的頂端。|**不要**如果沒有成為父代的整個容器使用。|  
|微調按鈕 （進度環）|相關內容的 ui，或其中空間是考量的處理程序。<br /><br /> 可能包含文字描述的程序詳細資料。||  
|資訊列|訊息內容的 UI 相關聯。 請參閱[資訊列](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars)。|**不**使用多個資訊列，當您想要表示多個處理序。 請改用堆疊的進度列。|  
|輸出視窗|暫時性通知︰ 應用程式層級程序，使用者會想要**檢閱**完成後的詳細資料。|**不要**用於需要在工作階段之間保存的資訊。|  
|記錄檔|搭配 intransient 通知，萬一時請務必**儲存**完成後的詳細資料。||  
|狀態列|暫時性通知︰ 應用程式層級程序，使用者將**不需要**的詳細資料之後完成。<br /><br /> 包含內嵌的進度列。<br /><br /> 可能包含文字描述的程序詳細資料。||  
  
### <a name="progress-indicator-types"></a>進度指標類型  
  
#### <a name="progress-bars"></a>進度列  
  
##### <a name="indeterminate"></a>不定  
 ![不確定的進度列](../../extensibility/ux-guidelines/media/0901-04_indeterminate.png "0901年&04;_Indeterminate")  
  
 **不確定的進度列**  
  
 「 不確定 」 表示作業的整體進度，或無法判斷處理程序。 使用不確定的進度列的作業需要無限的量的時間，或可存取的物件數目不明。 使用的文字描述伴隨著發生什麼事。 使用逾時，為範圍以時間為基礎的作業。 不確定的進度列會使用動畫來顯示進度正在進行，但未提供其他資訊。 請勿選擇只根據可能缺乏精確度單獨的不確定的進度列。  
  
##### <a name="determinate"></a>確定  
 ![確定的進度列](../../extensibility/ux-guidelines/media/0901-05_determinate.png "0901年&05;_Determinate")  
  
 **確定的進度列**  
  
 「 確定 」 表示 程序的作業需要繫結的一段時間，即使無法精確地預測的時間量。 清楚地表示完成。 不要讓進度列，除非在作業完成，請移至 100%。 確定的進度列動畫會移動左到右從 0 到 100%。  
  
 永遠不會移動回溯作業期間的進度指示器。 列應該向前移動穩定作業開始時，並結束時達到 100%。 進度列的重點是要讓使用者了解整個作業的時間，不論牽涉到幾個步驟。  
  
##### <a name="concurrent-reporting-stacked-progress-bars"></a>並行 reporting （堆疊的進度列）  
 如果作業需要很長的時間-可能是可能使用數個分鐘 – 則兩個進度列，其中一個，會顯示作業的整體進度，另一個用於目前步驟的進度。 例如，如果安裝程式正在複製許多檔案，然後一個進度列可用來表示整個程序的時間而第二個代表目前檔案的百分比，或是要複製目錄。 不會報告超過五個並行作業或使用堆疊的進度列的處理程序。 如果您有五個並行作業或報表的處理程序，使用強制回應對話方塊與 [取消] 按鈕和報表 [輸出] 視窗的進度詳細資料。  
  
##### <a name="textual-descriptions"></a>文字描述  
 使用的文字描述伴隨著發生什麼事，預估的完成時間。 如果無法判斷作業將會花多少時間，則可能是較佳的選擇，提供意見反應，動畫的圖示，而不是一個進度列。  
  
 Visual Studio 提供可供任何產品整合在 Visual Studio 的 [狀態] 列中的標準進度列。 進度列的動畫時所發生的文字描述，可以更新狀態列文字。  
  
#### <a name="other-progress-indicators"></a>其他的進度指示器  
  
##### <a name="ants-animated-horizontal-dots"></a>螞蟻 （水平點動畫）  
 ![進度流動外框](../../extensibility/ux-guidelines/media/0903-01_ants.png "0903年&01;_Ants")  
  
 「 流動外框，「 動畫的水平點，提供不確定的反覆存取伺服器處理序 visual 的參考。  
  
##### <a name="spinner-progress-ring"></a>微調按鈕 （進度環）  
 ![進度微調按鈕](../../extensibility/ux-guidelines/media/0903-02_spinner.png "0903年&02;_Spinner")  
  
 微調按鈕 （也稱為 「 進度環 」） 是不確定的進度指示器主要用於與內容相關的 UI。 顯示微調非常接近其相關的內容，例如文字分類標頭、 訊息、 或控制項。  
  
##### <a name="cursor-feedback"></a>資料指標的意見反應  
 2-7 秒之間的作業，提供資料指標的意見反應。 通常，這表示使用作業系統所提供將等待游標。 如需指引，請參閱 MSDN 文章[Cursors.Wait 屬性](https://msdn.microsoft.com/en-us/library/system.windows.input.cursors.wait\(v=vs.110\).aspx)。  
  
#### <a name="progress-indicator-locations"></a>進度指標位置  
  
##### <a name="status-bar"></a>狀態列  
 狀態列可提供應用程式的位置向使用者顯示訊息及有用的資訊，而不中斷使用者的工作。 通常顯示在視窗底部，進度的狀態將會包含有關進度的量值的訊息加上一個進度列指示器的工具提示窗格。  
  
 ![具有進度列的狀態列](../../extensibility/ux-guidelines/media/0903-03_statusbarprogressbar.png "0903年&03;_StatusBarProgressBar")  
  
 **具有進度列的狀態列**  
  
 ![具有傳訊的狀態列](../../extensibility/ux-guidelines/media/0903-04_statusbarmessage.png "0903年&04;_StatusBarMessage")  
  
 **狀態列文字描述**  
  
##### <a name="infobar"></a>資訊列  
 類似於狀態列，資訊列提供內容的通知和傳訊，也可以搭配具有不確定的進度指標，例如進度列或微調。 資訊列時，不應提供細微的層級進行或確定的進度指示。 請參閱[資訊列](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars)。  
  
 ![具有進度列和傳訊的資訊列](../../extensibility/ux-guidelines/media/0903-05_infobar.png "0903年&05;_InfoBar")  
  
 **具有進度列和文字描述的資訊列**  
  
 ![在視窗內的資訊列](../../extensibility/ux-guidelines/media/0903-06_infobarinwindow.png "0903年&06;_InfoBarInWindow")  
  
 **程式碼分析 視窗內的資訊列**  
  
##### <a name="inline"></a>內嵌  
 內嵌進度指示可以表示任何進度載入器類型。 進度列指示器通常搭配訊息，但這不是需求。  
  
 ![內嵌進度微調按鈕](../../extensibility/ux-guidelines/media/0903-07_inlinespinner.png "0903年&07;_InlineSpinner")  
  
 **微調結合文字描述**  
  
 ![內嵌堆疊進度列](../../extensibility/ux-guidelines/media/0903-08_inlinestackedprogress.png "0903年&08;_InlineStackedProgress")  
  
 **確定堆疊的進度列**  
  
 ![內嵌進度傳訊](../../extensibility/ux-guidelines/media/0903-09_inlinetext.png "0903年&09;_InlineText")  
  
 **伺服器總管內嵌文字︰ 重新整理...**  
  
##### <a name="tool-windows"></a>工具視窗  
 全域進度指示是由位於正下方的工具列上的不確定的進度列表示。  
  
 ![全域不確定的進度列](../../extensibility/ux-guidelines/media/0903-23_globalindeterminate.png "0903年&23;_GlobalIndeterminate")  
  
 **Team Explorer 全域不確定的進度列**  
  
##### <a name="dialogs"></a>對話方塊  
 對話方塊可以包含任何進度載入器類型。 進度指標可以是搭配訊息，以及結合多個層級表示細微及子程序的進度指示。  
  
 ![具有多個進度指標類型的對話方塊](../../extensibility/ux-guidelines/media/0903-11_dialog.png "0903年&11;_Dialog")  
  
 **與並行處理多個進度指標類型的 visual Studio 對話方塊**  
  
 ![具有進度載入器和傳訊的對話方塊](../../extensibility/ux-guidelines/media/0903-12_dialog2.png "0903年&12;_Dialog2")  
  
 **具有進度載入器和傳訊內嵌命令的 visual Studio 對話方塊**  
  
##### <a name="document-well"></a>完善的文件  
 文件也可以顯示多個進度載入器類型與控制項的組合。  
  
 ![文件進度傳訊也](../../extensibility/ux-guidelines/media/0903-13_documentwell.png "0903年&13;_DocumentWell")  
  
 **工具列下方的不確定的進度列**  
  
##### <a name="output-window"></a>輸出視窗  
 [輸出] 視窗也適用於處理程序的進展，以及透過內嵌文字訊息的進行中的進度狀態。 您應該使用 [狀態] 列，以及任何輸出視窗進度報告。  
  
 ![[輸出] 視窗中的進度傳訊](../../extensibility/ux-guidelines/media/0903-14_outputwindow.png "0903年&14;_OutputWindow")  
  
 **輸出視窗持續的程序的狀態，並等候訊息**  
  
##  <a name="a-namebkmkinfobarsa-infobars"></a><a name="BKMK_Infobars"></a>資訊列  
  
### <a name="overview"></a>概觀  
 資訊列授與使用者的注意其點接近指標，並使用共用的資料列控制確保一致的視覺外觀與互動。  
  
 ![資訊列](../../extensibility/ux-guidelines/media/0904-01_infobar.png "0904年&01;_Infobar")  
  
 **在 Visual Studio 中的資訊列**  
  
#### <a name="appropriate-uses-for-an-infobar"></a>會使用適當的資訊列  
  
-   目前內容相關的非封鎖但重要訊息給使用者  
  
-   表示 UI 處於特定狀態或條件，會帶來一些互動的影響，例如歷程偵錯  
  
-   若要通知使用者系統已偵測到的問題，例如擴充功能造成效能問題  
  
-   若要讓使用者能夠輕鬆地採取行動，例如當編輯器 中偵測到的檔案有混合定位點和空格  
  
##### <a name="do"></a>執行動作︰  
  
-   簡單地說，並在點保留的資料列的訊息文字。  
  
-   保持簡潔上連結和按鈕的文字。  
  
-   請確定您提供給使用者的 「 動作 」 選項最小，顯示必要的動作。  
  
##### <a name="dont"></a>不要︰  
  
-   您可以使用資訊列，讓標準應該放在工具列中的命令。  
  
-   使用資訊列來強制回應對話方塊取代。  
  
-   建立浮動在視窗外部訊息。  
  
-   使用多個資訊列在相同的視窗內的多個位置。  
  
#### <a name="can-multiple-infobars-show-at-the-same-time"></a>可以在相同的時間會顯示多個資訊列嗎？  
 是，多個資訊列可以顯示在相同的時間。 它們將顯示順序，先服務具有下列最上層和其他資訊列顯示上顯示第一個資料列。  
  
 使用者會看到三個資訊列最多一次之後，如果詳細的資訊列可供使用，資料列區域將會變成可捲動。  
  
### <a name="creating-an-infobar"></a>建立資料列  
 資料列有四個區段，從左到右︰  
  
-   **圖示︰**這是您可以在其中加入的任何圖示要顯示的資訊列，例如警告圖示。  
  
-   **文字︰**可以新增文字說明情況的案例/使用者，在文字內的連結必要。 請務必保留文字簡潔。  
  
-   **動作︰**連結和按鈕，使用者可以在您的資料列採取的動作，應該包含這一節。  
  
-   **[關閉] 按鈕︰**右邊最後一個區段都可以擁有 「 關閉 」 按鈕。  
  
#### <a name="creating-a-standard-infobar-in-managed-code"></a>在 managed 程式碼中建立標準的資訊列  
 InfoBarModel 類別可用來建立資料來源的資料列。 使用下列四個建構函式之一︰  
  
```  
public InfoBarModel(IEnumerable<IVsInfoBarTextSpan> textSpans, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);  
  
```  
  
```  
public InfoBarModel(string text, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);  
  
```  
  
```  
public InfoBarModel(IEnumerable<IVsInfoBarTextSpan> textSpans, IEnumerable<IVsInfoBarActionItem> actionItems, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);  
  
```  
  
```  
public InfoBarModel(string text, IEnumerable<IVsInfoBarActionItem> actionItems, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);  
```  
  
 以下是範例會建立 InfoBarModel 一些文字與超連結、 動作按鈕和圖示。  
  
 ![具有超連結的資訊列](../../extensibility/ux-guidelines/media/0904-02_infobarhyperlink.png "0904年&02;_InfobarHyperlink")  
  
```  
var infoBar = new InfoBarModel(  
    textSpans: new[]  
    {  
        new InfoBarTextSpan("This is a "),  
        new InfoBarHyperlink("hyperlink"),  
        new InfoBarTextSpan(" InfoBar.")  
    },  
    actionItems: new[]  
    {  
        new InfoBarButton("Click Me")  
    },  
    image: KnownMonikers.StatusInformation,  
    isCloseButtonVisible: true);  
  
```  
  
#### <a name="creating-a-standard-infobar-in-native-code"></a>在原生程式碼中建立標準的資訊列  
 實作 IVsInfoBar 介面，以便提供原生程式碼的資訊列。  
  
```  
public interface IVsInfoBar  
{  
    IVsInfoBarActionItemCollection ActionItems { get; }  
    ImageMoniker Image { get; }  
    bool IsCloseButtonVisible { get; }  
    IVsInfoBarTextSpanCollection TextSpans { get; }  
}  
  
```  
  
#### <a name="getting-an-infobar-uielement-from-an-infobar"></a>從資料列取得的資訊列 UIElement  
 InfoBarModel 或 IVsInfoBar 實作都必須轉換成 UIElement，若要顯示在 UI 中的資料模型。 UIElement 可以擷取與 SVsInfoBarUIFactory/IVsInfoBarUIFactory 服務。  
  
```  
private bool TryCreateInfoBarUI(IVsInfoBar infoBar, out IVsInfoBarUIElement uiElement)  
{  
    IVsInfoBarUIFactory infoBarUIFactory = serviceProvider.GetService(typeof(SVsInfoBarUIFactory)) as IVsInfoBarUIFactory;  
    if (infoBarUIFactory == null)  
    {  
        uiElement = null;  
        return false;  
    }  
  
    uiElement = infoBarUIFactory.CreateInfoBar(infoBar);  
    return uiElement != null;  
}  
```  
  
### <a name="placement"></a>放置  
 資訊列可以顯示在一或多個下列位置︰  
  
-   工具視窗  
  
-   內文件索引標籤  
  
> [!IMPORTANT]
>  就可以將資料列，提供關於全域內容的訊息。 這就之間工具列和文件也會出現。 建議您不要因為這會導致問題的 「 跳和 jerk 」 的 IDE，應該加以避免，除非絕對必要而且適當。  
  
#### <a name="placing-an-infobar-in-a-toolwindowpane"></a>將資料列放入 ToolWindowPane  
 ToolWindowPane.AddInfoBar(IVsInfoBar) 方法可以用來將資料列加入至 工具視窗。 這個 API 可新增 IVsInfoBar （哪些 InfoBarModel 是預設的實作），或 IVsUIElement。  
  
#### <a name="placing-an-infobar-in-a-document-or-non-toolwindowpane"></a>將資料列放在文件或非 ToolWindowPane  
 若要將資料列放入任何 IVsWindowFrame，使用 VSFPROPID_InfoBarHost 屬性 IVsInfoBarHost 取得框架，然後再加入資訊列 UIElement。  
  
```  
private void AddInfoBar(IVsWindowFrame frame, IVsUIElement uiElement)  
{  
    IVsInfoBarHost infoBarHost;  
    if (TryGetInfoBarHost(frame, out infoBarHost))  
    {  
        infoBarHost.AddInfoBar(uiElement);  
    }  
}  
private bool TryGetInfoBarHost(IVsWindowFrame frame, out IVsInfoBarHost infoBarHost)  
{  
    object infoBarHostObj;  
    if (ErrorHandler.Failed(frame.GetProperty((int)__VSFPROPID7.VSFPROPID_InfoBarHost, out infoBarHostObj)))  
    {  
        infoBarHost = null;  
        return false;  
    }  
  
    infoBarHost = infoBarHostObj as IVsInfoBarHost;  
    return infoBarHost != null;  
}  
  
```  
  
#### <a name="placing-an-infobar-in-the-main-window"></a>將資料列放在主視窗  
 若要將資料列放在主視窗中，使用 IVsShell 服務的 VSSPROPID_MainWindowInfoBarHost 取得主視窗的 IVsInfoBarHost 然後再加入資訊列 UIElement 給它。  
  
### <a name="will-i-know-when-the-user-takes-action-in-my-infobar"></a>我知道當使用者採取動作，在我的資訊列？  
 沒錯，我們會傳回每個事件動作的資訊列作者。 然後決定在 IDE 中根據使用者選取資料列採取動作的資訊列作者。 資訊列將從主應用程式的 [關閉] 按鈕已按下，自動移除，但如果之後要移除的其他資訊列需要關閉，則需要額外的工作。 遙測還需要個別記錄的每個資料列。  
  
#### <a name="receiving-infobar-events-in-a-toolwindowpane"></a>在 ToolWindowPane 接收事件的資訊列  
 ToolWindowPane 有兩個事件的資訊列。 關閉 ToolWindowPane 中的資訊列時，會引發 InfoBarClosed 事件。 按一下超連結或資料列內的按鈕時，會引發 InfoBarActionItemClicked 事件。  
  
#### <a name="receiving-infobar-events-directly-from-the-uielement"></a>資料列之事件的接收直接從 UIElement  
 IVsInfoBarUIElement.Advise 可以用於直接從資料列的 UIElement 訂閱事件。 實作 IVsInfoBarUIEvents 可讓作者收到關閉，click 事件。  
  
```  
public interface IVsInfoBarUIEvents  
{  
    void OnActionItemClicked(IVsInfoBarUIElement infoBarUIElement, IVsInfoBarActionItem actionItem);  
    void OnClosed(IVsInfoBarUIElement infoBarUIElement);  
}  
  
```  
  
##  <a name="a-namebkmkerrorvalidationa-error-validation"></a><a name="BKMK_ErrorValidation"></a>驗證錯誤  
 當使用者輸入不是可接受的例如必要的欄位則會略過，或輸入資料格式不正確的資訊時，最好是使用控制項的驗證或意見，而不是使用封鎖的快顯錯誤對話方塊控制項附近。  
  
### <a name="field-validation"></a>欄位驗證  
 表單和欄位驗證是由三個元件所組成︰ 一個控制項、 圖示和工具提示。 時數種類型的控制項可以使用這個方法，在文字方塊中將使用做為範例。  
  
 ![欄位驗證 （空白）](../../extensibility/ux-guidelines/media/0905-01_fieldvalidation.png "0905年&01;_FieldValidation")  
  
 如果這是必要欄位，應該要有浮水印文字，指出**\<必要 >**欄位背景應 light 黃色 (VSColor: `Environment.ControlEditRequiredBackground`) 和前景應該是灰色 (VSColor: `Environment.ControlEditRequiredHintText`):  
  
 ![欄位與 [必要] 標籤的驗證](../../extensibility/ux-guidelines/media/0905-02_fieldvalidationrequired.png "0905年&02;_FieldValidationRequired")  
  
 程式可以判斷控制項的狀態是*輸入的內容無效*當焦點移至另一個控制項，或當使用者按一下 [確定] 認可 按鈕，或當使用者儲存文件或表單。  
  
 無效的內容狀態決定後，控制項內部，或只是它旁邊會出現圖示。 描述錯誤的工具提示應該會出現在按鈕的圖示或控制項。 此外，用來建立無效的狀態控制項周圍的 1 個像素框線應該會出現。  
  
 ![欄位驗證版面配置規格](../../extensibility/ux-guidelines/media/0905-03_layoutspecs.png "0905年&03;_LayoutSpecs")  
  
 **欄位驗證版面配置規格**  
  
#### <a name="acceptable-variations-for-icon-location"></a>圖示位置可接受的變化  
 有了很多唯一的情況下，使用者要收到驗證錯誤的相關通知。 考慮控制項類型及組態的使用者介面中，選擇適合您狀況的圖示位置。  
  
 ![圖示位置可接受位置](../../extensibility/ux-guidelines/media/0905-04_iconlocation.png "0905年&04;_IconLocation")  
  
 **欄位驗證圖示位置可接受的變化**  
  
#### <a name="validation-requiring-a-round-trip-to-a-server-or-network-connection"></a>需要來回伺服器或網路連線的驗證  
 在某些情況下，往返伺服器，才能確認的內容，並務必以顯示使用者進行驗證和錯誤狀態。 下圖顯示此案例與建議的 UI 中的範例。  
  
 ![需要往返伺服器的驗證](../../extensibility/ux-guidelines/media/0905-05_roundtrip.png "0905年&05;_RoundTrip")  
  
 **需要往返伺服器的驗證**  
  
 請注意，為了要考慮到 [驗證]，就必須提供控制項右邊有足夠的可用空間 和 [重試] 文字。  
  
#### <a name="in-place-warning-text"></a>就地警告文字  
 當有足夠的空間可用來將錯誤訊息，接近控制項放在錯誤的狀態時，這是偏好使用單獨的工具提示。  
  
 ![就地警告](../../extensibility/ux-guidelines/media/0905-06_inplacewarning.png "0905年&06;_InPlaceWarning")  
  
 **就地警告文字**  
  
#### <a name="watermarks"></a>浮水印  
 有時候整個控制項或視窗，則在錯誤狀態。 在此情況下，使用浮水印，表示發生錯誤。  
  
 ![浮水印](../../extensibility/ux-guidelines/media/0905-07_watermark.png "0905年&07;_Watermark")  
  
 **浮水印欄位驗證**
