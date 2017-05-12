---
title: "實作智慧主機協助程式介面 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "智慧主機協助程式介面, 實作"
ms.assetid: b9c44246-4d4d-469e-91be-00c8f5796fa5
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# 實作智慧主機協助程式介面
因為它提供了介面的實作所需的智慧標籤的載入， [IDebugDocumentHelper 介面](../winscript/reference/idebugdocumenthelper-interface.md) 介面大幅簡化建立使用中的偵錯的智慧型主機工作。  
  
 若要使用 `IDebugDocumentHelper`的智慧型主機，主應用程式必須執行三個動作:  
  
1.  `CoCreate` 進行偵錯的處理常式，並使用 [IProcessDebugManager 介面](../winscript/reference/iprocessdebugmanager-interface.md) 介面加入您的應用程式部署至可偵錯應用程式的清單。  
  
2.  使用 [IProcessDebugManager::CreateDebugDocumentHelper](../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md) 方法，建立每一個指令碼物件的偵錯資料 Helper，。  確定文件名稱、父資料、文字和指令碼區塊中定義。  
  
3.  實作在物件上 [IActiveScriptSiteDebug 介面](../winscript/reference/iactivescriptsitedebug-interface.md) 介面實作 Active Scripting 需要 [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) 的介面。  在 `IActiveScriptSiteDebug` 介面完全委派的唯一的重要方法 Helper。  
  
 或者，如果，它需要對語法色彩、文件建立內容和其他擴充功能，其他控制項的主應用程式可以實作介面 [IDebugDocumentHost 介面](../winscript/reference/idebugdocumenthost-interface.md) 。  
  
 在智慧型主機 Helper 的主要限制在於它只能處理內容變更或壓縮的檔案，並將這些物件加入之後 \(但是在文件可以展開\)。  對於許多智慧型主機，然而，它所提供的功能完全所需的結果。  
  
 下列各節將詳細說明每個步驟。  
  
## 建立應用程式物件  
 在使用前智慧型主機 Helper，建立 [IDebugApplication 介面](../winscript/reference/idebugapplication-interface.md) 物件表示在偵錯工具中執行應用程式所需的。  
  
#### 建立應用程式物件  
  
1.  建立處理序的執行個體來偵錯使用 `CoCreateInstance`的處理常式。  
  
2.  請呼叫 [IProcessDebugManager::CreateApplication](../winscript/reference/iprocessdebugmanager-createapplication.md)。  
  
3.  您可以使用 [IDebugApplication::SetName](../winscript/reference/idebugapplication-setname.md)，設定應用程式的名稱。  
  
4.  您可以使用 [IProcessDebugManager::AddApplication](../winscript/reference/iprocessdebugmanager-addapplication.md)，加入可偵錯的應用程式清單中的應用程式物件。  
  
     程式碼概略說明，處理序，但不包含錯誤檢查或其他強固的程式設計技巧。  
  
    ```  
    CoCreateInstance(CLSID_ProcessDebugManager, NULL,  
          CLSCTX_INPROC_SERVER | CLSCTX_INPROC_HANDLER  
          | CLSCTX_LOCAL_SERVER,  
    IID_IProcessDebugManager, (void **)&g_ppdm);  
    g_ppdm->CreateApplication(&g_pda);  
    g_pda->SetName(L"My cool application");  
    g_ppdm->AddApplication(g_pda, &g_dwAppCookie);  
    ```  
  
## 使用 IDebugDocumentHelper  
  
#### 使用 Helper \(最小的步驟序列\)  
  
1.  針對每個主應用程式文件，建立使用 [IProcessDebugManager::CreateDebugDocumentHelper](../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md)的 Helper。  
  
2.  呼叫 Helper 的 [IDebugDocumentHelper::Init](../winscript/reference/idebugdocumenthelper-init.md) ，為命名，文件屬性，依此類推。  
  
3.  請改為使用父 Helper 的 [IDebugDocumentHelper::Attach](../winscript/reference/idebugdocumenthelper-attach.md) 文件 \(或 null 的，如果文件是根目錄\) 定義文件的位置在樹狀結構並讓它顯示為偵錯工具。  
  
4.  呼叫 [IDebugDocumentHelper::AddDBCSText](../winscript/reference/idebugdocumenthelper-adddbcstext.md) 或 [IDebugDocumentHelper::AddUnicodeText](../winscript/reference/idebugdocumenthelper-addunicodetext.md) 定義文件的文字。  \(這些物件可以多次呼叫，如果文件累加下載，瀏覽器中的情況下\)。  
  
5.  呼叫定義每個指令碼區塊和關聯的指令碼引擎的範圍的 [IDebugDocumentHelper::DefineScriptBlock](../winscript/reference/idebugdocumenthelper-definescriptblock.md) 。  
  
## 實作 IActiveScriptSiteDebug  
 若要實作 [IActiveScriptSiteDebug::GetDocumentContextFromPosition](../winscript/reference/iactivescriptsitedebug-getdocumentcontextfromposition.md)，請取得 Helper 具有特定網站對應，然後取得這份文件的開頭位移指定的來源內容，如下所示:  
  
```  
pddh->GetScriptBlockInfo(dwSourceContext, NULL, &ulStartPos, NULL);  
```  
  
 接著，請使用 Helper 建立字元的位移指定的建立新的資料內容:  
  
```  
pddh->CreateDebugDocumentContext(ulStartPos + uCharacterOffset, cChars, &pddcNew);  
```  
  
 若要實作 [IActiveScriptSiteDebug::GetRootApplicationNode](../winscript/reference/iactivescriptsitedebug-getrootapplicationnode.md)，請呼叫 `IDebugApplication::GetRootNode` \(繼承自 [IRemoteDebugApplication::GetRootNode](../winscript/reference/iremotedebugapplication-getrootnode.md)\)。  
  
 若要實作 [IDebugDocumentHelper::GetDebugApplicationNode](../winscript/reference/idebugdocumenthelper-getdebugapplicationnode.md)，傳回您最初建立使用同處理序偵錯處理常式的 `IDebugApplication` 。  
  
## 選擇性 IDebugDocumentHost 介面  
 主應用程式可以提供 [IDebugDocumentHost 介面](../winscript/reference/idebugdocumenthost-interface.md) 的實作使用 [IDebugDocumentHelper::SetDebugDocumentHost](../winscript/reference/idebugdocumenthelper-setdebugdocumenthost.md) 提供給 Helper 的其他控制項。  這個主機介面可讓您執行的特定重要事項:  
  
-   將文字 [IDebugDocumentHelper::AddDeferredText](../winscript/reference/idebugdocumenthelper-adddeferredtext.md) 使用，讓主應用程式不需要立即提供實際字元。  在字元為真的需要， Helper 將會在主應用程式的 [IDebugDocumentHost::GetDeferredText](../winscript/reference/idebugdocumenthost-getdeferredtext.md) 。  
  
-   覆寫 Helper 提供的預設語法標色。  Helper 呼叫 [IDebugDocumentHost::GetScriptTextAttributes](../winscript/reference/idebugdocumenthost-getscripttextattributes.md) 判斷字元範圍的顏色標示，就會回溯它的預設實作，如果主應用程式傳回 `E_NOTIMPL`。  
  
-   為了協助程式所建立的文件內容控制項提供一個未知藉由實作 [IDebugDocumentHost::OnCreateDocumentContext](../winscript/reference/idebugdocumenthost-oncreatedocumentcontext.md)。  如此可讓主應用程式覆寫預設文件內容實作的功能。  
  
-   提供 Document 檔案系統上的路徑名稱。  某些偵錯 UI 使用這允許使用者編輯和儲存對文件所作的變更。  在文件中儲存完成之後，[IDebugDocumentHost::NotifyChanged](../winscript/reference/idebugdocumenthost-notifychanged.md) 呼叫以告知主應用程式。  
  
## 請參閱  
 [動態指令碼偵錯概觀](../winscript/active-script-debugging-overview.md)