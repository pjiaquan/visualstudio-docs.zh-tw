---
title: "How to: 實作巢狀的專案 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "巢狀的專案中實作"
  - "專案 [Visual Studio SDK]，巢狀結構"
ms.assetid: d20b8d6a-f0e0-4115-b3a3-edda893ae678
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# How to: 實作巢狀的專案
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

當您建立巢狀的專案類型有幾個額外步驟必須實作。  父專案會使某些方案之中擁有其巢狀 \(子系\) 專案的同一個任務上。  父專案為專案加入方案類似的容器。  特別是，有幾個解決方案，並以巢狀專案的階層架構的父專案必須引發的事件。  建立巢狀的專案的下列程序將說明這些事件。  
  
### 若要建立巢狀的專案  
  
1.  整合式的開發環境 \(IDE\) 載入父專案的專案檔和啟動資訊，藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>介面。  父專案，建立並加入至方案。  
  
    > [!NOTE]
    >  在這個時候，就太早在父專案，若要建立巢狀的專案，因為必須先建立父專案，您可以建立子專案的程序。  這個序列中，父專案可以將設定套用到子專案而必要時，子專案可以取得父專案中的資訊。  此順序是如果有需要在原始程式碼控制 \(SCC\) 和方案總管\] 中的用戶端。  
  
     父專案必須等到<xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A>專案，才可以建立巢狀 \(其子\) 之前，由 IDE 呼叫的方法。  
  
2.  IDE 呼叫`QueryInterface`在父專案的<xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject>。  如果這個呼叫成功，IDE 呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A>之父代，若要開啟的所有巢狀專案的父專案的方法。  
  
3.  父專案的呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnBeforeOpeningChildren%2A>方法來通知關於巢狀專案的接聽程式即將被建立。  比方說，SCC，正在接聽這些事件，以瞭解是否發生的方案和專案的建立程序中的步驟的順序。  如果步驟發生故障，解決方案可能無法登錄與原始程式碼控制正確。  
  
4.  父專案的呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProject%2A>方法或<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProjectEx%2A>上它的子專案的每一個方法。  
  
     您傳遞<xref:Microsoft.VisualStudio.Shell.Interop.__VSADDVPFLAGS>到`AddVirtualProject`方法，以指示虛擬 \(巢狀\) 專案應該加入專案\] 視窗中，從組建中，排除加入至原始程式碼控制，依此類推。  `VSADDVPFLAGS`可讓您控制巢狀專案的可視性，並指出哪些功能可與它相關聯。  
  
     如果您重新載入先前已存在一個專案儲存在父專案的專案檔案中，父專案的呼叫中的 GUID 的子專案`AddVirtualProjectEx`。  之間唯一的差別`AddVirtualProject`和`AddVirtualProjectEX` ，就是`AddVirtualProjectEX`有參數能讓父專案，可以指定每個執行個體`guidProjectID`子專案，若要啟用<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfGuid%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfProjref%2A>才能正確運作。  
  
     如果沒有 GUID 可用，例如當您新增新的巢狀的專案時，方案會為專案加入至父代時隨之變更。  它負責將該專案的專案檔中的 GUID 的父專案。  如果您刪除巢狀的專案時，也可以刪除該專案的 GUID。  
  
5.  IDE 呼叫`M:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren`在父專案的每一個子專案上的方法。  
  
     父專案必須實作`IVsParentProject`如果您想要將巢狀化的專案。  但是父代專案永遠不會呼叫`QueryInterface`的`IVsParentProject`即使它附帶底下所屬的父專案。  方案會處理呼叫`IVsParentProject` ，如果它實作時，會呼叫`OpenChildren`來建立巢狀的專案。  `AddVirtualProjectEX`從通稱為`OpenChildren`。  它應該永遠不會由父專案，若要保留階層建立事件的順序呼叫。  
  
6.  IDE 呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>的子專案上的方法。  
  
7.  父專案的呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpeningChildren%2A>告知父代的子專案已建立的接聽程式的方法。  
  
8.  IDE 呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpenProject%2A>在父專案後已開啟所有的子專案上的方法。  
  
     如果尚未存在，父專案會建立每個巢狀專案 GUID 藉由呼叫`CoCreateGuid`。  
  
    > [!NOTE]
    >  `CoCreateGuid`COM API 時呼叫的 GUID，就會被建立。  如需詳細資訊，請參閱`CoCreateGuid`與 MSDN Library 中的 Guid。  
  
     父專案會儲存此 GUID，要擷取下次在 IDE 中開啟專案檔中。  如需詳細資訊，與相關的電話的步驟 4，請參閱`AddVirtualProjectEX`擷取`guidProjectID`的子專案。  
  
9. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>為父項目識別碼，然後呼叫方法依慣例您委派中巢狀專案。  <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>擷取節點形成巢狀的專案，您想要委派在其上父代呼叫時的屬性。  
  
     因為父和子專案具現化以程式設計的方式，您可以在此時設定巢狀專案的屬性。  
  
    > [!NOTE]
    >  不僅沒有巢狀專案中，從收到的內容資訊，而且您也可以要求父專案是否有任何的內容，該項目，藉由檢查<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>。  如此一來，在您可以將額外的動態說明屬性和特定的功能表選項加入個別的巢狀專案。  
  
10. 階層架構的開發都顯示在 \[方案總管\] 中，內含呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>方法。  
  
     您將階層架構傳遞至透過環境`GetNestedHierarchy`來建置的方案總管\] 中顯示的階層架構。  如此一來，方案會知道專案存在，並可由組建管理員\] 中，管理建築或可允許將受原始程式碼控制專案中的檔案。  
  
11. 專案 1 的所有巢狀的專案建立之後，程式控制權轉移回至方案，並 Project2 個使用相同的處理程序。  
  
     有子系的子專案，就會發生這個相同的程序，來建立巢狀的專案。  如此一來，如果 BuildProject1，也就是專案 1 的子系，子專案，則會建立之後 BuildProject1 及 Project2 之前。  程序遞迴，而且階層是從上向下。  
  
     因為使用者關閉方案或特定專案本身，其他的方法上，當關閉巢狀的專案`IVsParentProject`， <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.CloseChildren%2A>，就會呼叫。  父專案包裝呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.RemoveVirtualProject%2A>方法以<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeClosingChildren%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterClosingChildren%2A>告知解決方案事件的接聽程式關閉巢狀的專案的方法。  
  
 您實作巢狀的專案時要考慮的其他幾個概念處理下列主題：  
  
 [卸載並重新載入巢狀專案的考量](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)  
  
 [巢狀專案的精靈支援](../../extensibility/internals/wizard-support-for-nested-projects.md)  
  
 [實作命令處理巢狀專案](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)  
  
 [篩選巢狀專案 AddItem 對話方塊](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)  
  
## 請參閱  
 [加入項目來加入新項目對話方塊](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [註冊專案和項目範本](../../extensibility/internals/registering-project-and-item-templates.md)   
 [檢查清單︰ 建立新的專案類型](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [內容參數](../../extensibility/internals/context-parameters.md)   
 [精靈 \(。Vsz\) 檔案](../../extensibility/internals/wizard-dot-vsz-file.md)