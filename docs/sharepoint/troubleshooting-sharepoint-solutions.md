---
caps.handback.revision: 41
---
# SharePoint 方案疑難排解
  當您使用偵錯 SharePoint 解決方案時，則可能會發生下列的 \[問題\] 或 \[警示[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]偵錯工具。  如需詳細資訊，請參閱 [NIB: Debugging SharePoint 2007 Workflow Solutions](http://msdn.microsoft.com/zh-tw/3a5392f3-66f3-48be-956e-02de23fa6247).  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
## 在沙箱化 Visual Web 組件中的語彙基元限制  
 在沙箱化的方案中的視覺的 web 組件無法處理標準的權杖，例如 $SPUrl，SharePoint 執行階段支援。  如此一來，URL 未解決，請與您無法預覽 visual web 組件設計工具中的 \[設計\] 檢視中的內容，如果您直接在中參考它的指令碼項目，例如在下列範例中：  
  
```  
<script src=”<% $SPUrl:~site/SiteAssets/ListOperations.js %>"></script>  
```  
  
 若要解決這項限制，並解析語彙基元，請參閱它使用常值：  
  
```  
<asp:literal ID="Literal1" runat="server" Text="<script src='" />  
<asp:literal ID="Literal2" runat="server" Text="<% $SPUrl:~site/SiteAssets/ListOperations.js %>" />  
<asp:literal ID="Literal3" runat="server" Text="' type='text/javascript' ></script>" />  
```  
  
## 專案和專案項目的名稱中的字元限制  
 專案和專案項目名稱可以包含在 SharePoint 2010 的部署路徑中有效的字元。  不可以有任何其他字元。  
  
### 錯誤訊息  
 「 無效字元 」 錯誤訊息。  
  
### 解析度  
 SharePoint 專案和專案項目的名稱，請使用下列字元：  
  
-   英數字元的 ASCII 字元  
  
-   空間  
  
-   句號 \(.\)  
  
-   逗號 \(，\)  
  
-   底線 \(\_\)  
  
-   破折號 \(\-\)  
  
-   反斜線 \(\\\)  
  
 當專案在封裝中時，驗證規則會驗證要部署的每個檔案的部署路徑屬性包含這些有效的字元。  
  
## 建立自訂的欄位時發生錯誤  
 在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，在 XML 中定義自訂欄位。  如果欄位不是定義或參照之使用特定的格式，就可能發生錯誤。  
  
### 錯誤訊息  
 在封裝階段 「 無效字元 」 錯誤訊息。  
  
### 解析度  
 欄位定義的識別碼必須是 GUID，碼加上括號，如下列範例所示：  
  
```  
<Field ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"   
    Type="Note"   
    Name="PatientName"   
    DisplayName="Patient Name"   
    Group="A Custom Group">  
</Field>.  
```  
  
 如下列範例所示，必須使用空的元素格式來定義內容的型別中的欄位參照 \(\< FieldRef \/ \>\)，不是使用 \[開始\/結束項目 \(\< FieldRef \>\< \/ FieldRef \>\)：  
  
```  
<FieldRef ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"   
    Name="PatientName"   
    DisplayName="Patient Name"   
    Required="TRUE"/>  
```  
  
 如果欄位的來源 XML 格式不正確、 不是有效的 XML 檔案，或一些其他問題的展示區，錯誤 「 無法剖析檔案" 就會發生。  
  
## 新的非英文網站定義並不會出現在網站建立頁面部署之後  
 您建立和使用非英文版的部署網站定義之後 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\(也就是使用地區設定版本  [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]不是 1033年\)、   **SharePoint 自訂** 索引標籤未出現在 **範本選擇** 方塊和新的 「 網站 」 範本不會出現在 **新的 SharePoint 網站**頁面。  
  
### 錯誤訊息  
 無。  
  
### 解析度  
 這個問題之所以發生是因為不正確的值，在**路徑** webtemp 站台定義設定檔，例如 webtemp\_SiteDefinitionProject1.xml 的屬性。  在**路徑** webtemp 檔案，位於屬性 **部署位置**，適當的地區設定變更 1033年  [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)].  例如，若要使用日本的地區設定將值變更為 1041年。  如需詳細資訊，請參閱[由 Microsoft 的地區設定識別碼指派](http://go.microsoft.com/fwlink/?LinkID=165561) MSDN 網站上。  
  
## 在工作流程專案部署全新的系統上時，就會出現錯誤  
 如果您部署工作流程專案中的，就會發生這個問題[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]上的乾淨系統。  清理系統是電腦上具有全新安裝[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]和 SharePoint 但沒有部署工作流程專案。  
  
### 錯誤訊息  
 找不到 SharePoint 清單: 工作流程的歷程記錄。  
  
### 解析度  
 這個錯誤發生是因為遺漏的工作流程的歷程記錄清單。  開發環境是全新的系統，因為沒有工作流程部署，尚不存在的工作流程的歷程記錄清單。  若要解決這個問題，請重新開啟工作流程精靈中，會導致工作流程的歷程記錄清單，以建立。  
  
##### 若要重新輸入工作流程精靈  
  
1.  在**方案總管\] 中**，選擇 \[工作流程\] 節點。  
  
2.  在**屬性** 視窗中，選擇 \[上一個省略符號按鈕的任何屬性的省略號 \(...\) 按鈕。  
  
## 使用者必須重新整理瀏覽器中的應用程式頁面，而偵錯\] 以檢視更新映像  
 如果您正在偵錯的 SharePoint 方案包含應用程式網頁與控制項顯示影像，例如，  [!INCLUDE[TLA2#tla_html](../sharepoint/includes/tla2sharptla-html-md.md)]圖像控制項，您必須重新整理網頁在瀏覽器中顯示的影像所做的任何變更。  
  
## 錯誤: 站台位置不正確  
 如果發生這個問題，可以[!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)]尚未安裝。  如果您沒有指定在 SharePoint 網站的系統管理員存取權，可能也會發生它 **SharePoint 自訂精靈**。  
  
### 錯誤訊息  
  
-   SharePoint 網站位置不是有效的。  
  
### 解析度  
  
-   安裝 [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)].  
  
-   請確定您需要 SharePoint 網站的系統管理員存取權。  如需詳細資訊，請參閱[!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)]線上文章 [入口網站的存取權授與](http://go.microsoft.com/fwlink/?LinkId=98310)。  
  
## 站台刪除 Web 事件不會發生在事件接收者專案中  
 當您建立一個事件接收器專案，並選取特定的 Web 事件，例如，"站台正被刪除" 永遠不會發生這個事件。  
  
### 錯誤訊息  
 無。  
  
### 解析度  
 因為功能範圍必須是 「 網站 」，就會發生這個問題 處理站台層級的事件，但預設事件接收器專案的功能領域會是 \[網站\]。  受影響的 Web 事件為：  
  
-   站台正在刪除 \(WebDeleting\)  
  
-   站台已被刪除 \(WebDeleted\)  
  
-   站台正在移動 \(WebMoving\)  
  
-   移動站台 \(WebMoved\)  
  
 若要修正這個問題，變更功能的範圍事件接收者，如下所示。  
  
##### 若要變更的事件接收器的功能領域  
  
1.  在**方案總管\] 中**，開啟事件接收者.feature 檔案，在 **功能設計工具** 藉由連按兩下檔案，或開啟其快顯功能表，然後選擇 **開啟**。  
  
2.  下一步\]，選擇箭號**範圍**，然後選擇 **站台**中出現的清單。  
  
## 變更的商務資料連線模型專案中的識別項名稱之後，就會出現部署錯誤  
 如果您變更商務資料連線 \(BDC\) 模型中實體的識別項名稱，然後再嘗試部署方案，就會發生這個問題。  
  
### 錯誤訊息  
  
-   \<*模型名稱*\> 有下列的外部內容的型別啟動錯誤...  
  
-   使用名稱 IMetadataObject ' \<*模型名稱*\>' 在欄位 'name' 有值 重複的...  
  
### 解析度  
 若要解決這個問題，請以手動方式刪除的模型，然後重新部署方案。  您可以使用其中一種下列工具來刪除模型：  
  
-   SharePoint 2010 中央系統管理。  如需詳細資訊，請參閱 [BDC 模型管理](http://go.microsoft.com/fwlink/?LinkID=181472)在 Microsoft TechNet 網站上。  
  
-   Windows PowerShell。  您可以在命令提示字元中輸入此命令來刪除模型： **Remove\-SPBusinessDataCatalogModel**.  如需詳細資訊，請參閱[一般 cmdlet \(SharePoint 伺服器 2010\)](http://go.microsoft.com/fwlink/?LinkID=182375)在 Microsoft TechNet 網站上。  
  
## 當您嘗試在 SharePoint 中檢視 Visual Web 組件時，會出現錯誤  
 會發生這個問題時**路徑**的使用者控制項的屬性不是以字串"CONTROLTEMPLATES\\"。  
  
### 錯誤訊息  
  
-   檔案 ' \/\_CONTROLTEMPLATES\/*\< 專案名稱 \>*\/*\< 網頁組件名稱 \>*\/*\< 使用者控制項名稱 \>*.ascx' 不存在。  
  
-   伺服器發生錯誤 '\/' 應用程式。  
  
### 解析度  
  
##### 如果要解決這個問題  
  
1.  在**方案總管\] 中**，選擇 \[使用者控制項檔案，其副檔名為.ascx。  
  
2.  功能表列上，選擇**檢視**，  **\[屬性\] 視窗**。  
  
3.  在**屬性** \] 視窗中，展開 **部署位置**節點。  
  
4.  確保值**路徑**以字串"CONTROLTEMPLATES\\"開頭的屬性。  
  
## 執行匯入的可重複使用工作流程，其中包含 \[任務表單欄位時，就會出現錯誤  
 如果您匯入工作流程，其中包含有一個欄位的任務表單，然後從中匯入它相同的系統上執行新的工作流程，就會發生這個問題。  
  
### 錯誤訊息  
 在部署步驟啟動功能時發生錯誤: 欄位識別碼為 *Guid*\] 功能中定義 \[*Guid*\] 在目前的網站集合或子網站中，找不到。  
  
### 解析度  
 這個錯誤是發生是因為匯入可重複使用工作流程專案中的欄位識別碼衝突的結果[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]不會變更任務表單欄位識別碼。  如果您部署包含原始的工作流程的相同伺服器上匯入工作流程時，就會發生欄位 ID 衝突。  
  
 若要解決這個問題，請使用 \[尋找及取代\] 功能來變更所有匯入工作流程檔案中的欄位識別碼屬性的值。  
  
## 錯誤時，會出現命名，匯入執行清單執行個體  
 如果您重新命名匯入的清單執行個體，然後將它設為執行中，就會發生這個問題 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
### 錯誤訊息  
 建置錯誤： 在部署步驟啟動功能時發生錯誤: 檔案 Template\\Features\\ *import project* *feature* *name*\] \\Files\\Lists\\ \[*old* *list name*\] \\Schema.xml 不存在。  
  
### 解析度  
 當您匯入清單執行個體時，則會將名為 CustomSchema 屬性加入至清單執行個體的 Elements.xml 檔案。  Elements.xml 包含自訂的 schema.xml 清單執行個體的路徑。  當您重新命名清單執行個體，在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]、 自訂的 schema.xml 的部署路徑變更，但不是更新路徑的 CustomSchema 屬性值。  如此一來，清單執行個體中找不到 schema.xml 檔案啟動功能時，會將 CustomSchema 屬性所指定的舊路徑。  
  
 若要解決這個問題，請更新 schema.xml 檔案，在 CustomSchema 屬性中的部署位置的路徑。  
  
## SharePoint 偵錯工作階段被 IIS 終止  
 如果您在設定中斷點，就會發生這個問題 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]SharePoint 解決方案中，選擇 \[F5 鍵以執行它，，然後維持在超過 90 秒的中斷點。  
  
### 錯誤訊息  
 正在進行偵錯 Web 伺服器處理序已終止網際網路資訊服務 \(IIS\)。  若要避免發生這個問題，可以在 IIS 中設定應用程式集區抓取設定。  請參閱說明以取得詳細資訊。  
  
### 解析度  
 根據預設，IIS 應用程式集區會等待回應之前關閉應用程式的應用程式的 90 秒。  此程序就是所謂的"ping" 應用程式。  若要解決這個問題，您可以增加的等待時間，或停用應用程式完全 ping。  
  
##### 若要存取 IIS 應用程式集區設定  
  
1.  開啟 IIS 管理員\]。  
  
2.  在**連線** 窗格中，展開 \[SharePoint 伺服器\] 節點，然後選擇 **應用程式集區**節點。  
  
3.  在**應用程式集區** 頁面上，選擇 \[SharePoint 應用程式集區 \(通常是 「 SharePoint\-80"\)，然後在 **動作** 窗格中，選擇 **進階設定**連結。  
  
4.  若要增加 IIS 逾時之前的等待時間，請變更值 **Ping 回應時間上限 \(秒\)** 為大於 90 秒的值。  
  
5.  若要停用 IIS ping，設定**已啟用 Ping** 到 **，則為 False**。  
  
## 自動撤回在 SharePoint 中的分葉失去關聯的清單執行個體  
 如果您執行下列步驟，就會發生這個問題。  
  
1.  建立清單執行個體已經在清單定義 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  選擇 F5 鍵以執行方案。  
  
3.  停止偵錯，或關閉 SharePoint 網站。  
  
4.  重新開啟 SharePoint 網站，並開啟清單執行個體。  
  
### 錯誤訊息  
 伺服器發生錯誤 '\/' 應用程式。  
  
### 解析度  
 這是因為您關閉偵錯工作階段的 SharePoint 解決方案，之後自動撤回功能 retracts 方案。  撤銷刪除 SharePoint 清單定義，但並不會刪除清單的執行個體。  基礎清單定義所需的清單執行個體。  
  
 若要解決這個問題，部署方案，功能表列，選擇**建置**， **部署**。 \(沒有偵錯方案中選擇 \[F5 鍵。\) 然後，刪除 SharePoint 中的清單執行個體。  
  
## 匯出的版本取代原始的 SharePoint 解決方案  
 如果您匯出的 SharePoint 解決方案時，匯入成方案 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，然後將方案部署回相同的站台已匯出，就會取代原始的 SharePoint 解決方案。  如果您將方案部署至伺服器並沒有在其上啟動原始方案，則不會發生這個問題。  
  
### 錯誤訊息  
 無。  
  
### 解析度  
 若要避免覆寫已匯出的網站上的方案，變更 SolutionID 的 Guid 和功能的識別碼中的所有匯入功能[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]專案。  
  
## 偵錯開始時，就會出現錯誤  
 當您啟動偵錯的 SharePoint 解決方案，在 Visual Studio 中時，錯誤會指出 Visual Studio 無法載入 Web.config 檔，因為指定的索引鍵不在字典中。  
  
### 錯誤訊息  
 無法載入 Web.config 組態檔。  檢查任何格式不正確的 XML 項目的檔案，並再試一次。  發生以下錯誤: 指定的索引鍵不在字典中。  
  
### 解析度  
 若要解決這個問題，請確認 SharePoint 專案在 Visual Studio 中的網站 URL 屬性值符合指派給 web 應用程式的替代存取對應的 「 預設 」 區域的 URL。  您無法使用另一個區域，例如內部網路 url 來解決錯誤。  站台必須符合專案的 URL 和預設區域中的 URL。  若要存取替代存取對應，請開啟 SharePoint 2010 中央系統管理公用程式，請選擇**應用程式管理** 的連結，並接著，在  **Web 應用程式**，選擇 **設定替代存取對應**連結。  如需詳細資訊，請參閱[的 Web 應用程式的建立區域](http://go.microsoft.com/fwlink/?LinkId=192274)。  
  
## 請參閱  
 [SharePoint 封裝和部署疑難排解](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md)   
 [建置和偵錯 SharePoint 方案](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [Visual Studio 偵錯](../debugger/debugging-in-visual-studio.md)  
  
  