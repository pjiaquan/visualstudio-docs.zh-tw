---
title: "註冊自訂的偵錯引擎 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "偵錯引擎註冊"
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# 註冊自訂的偵錯引擎
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

偵錯引擎必須本身登錄為 class factory 遵循 COM 慣例，以及註冊使用 Visual Studio 透過 Visual Studio 登錄子機碼。  
  
> [!NOTE]
>  舉例說明如何註冊偵錯引擎可以找到在 TextInterpreter 範例中，建置的 [Tutorial: Building a Debug Engine Using ATL COM](http://msdn.microsoft.com/zh-tw/9097b71e-1fe7-48f7-bc00-009e25940c24)。  
  
## DLL 伺服器處理序  
 一般而言，偵錯引擎會在它自己的 DLL 中實作為 COM 伺服器。 這表示，Visual Studio 才能存取它，偵錯引擎必須註冊 com 其 class factory 的 CLSID。 然後偵錯引擎必須登錄本身的 Visual Studio 以建立任何屬性 （也稱為度量） 偵錯引擎支援。 偵錯引擎支援的功能而不同的度量資訊會寫入至 Visual Studio 登錄子機碼的偵錯引擎選擇。  
  
 [SDK 協助程式進行偵錯](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) 描述不只登錄位置需要註冊偵錯引擎。此外也說明 dbgmetric.lib 程式庫，其中包含一些實用的函式和 c \+ \+ 開發人員，讓管理更容易登錄的宣告。  
  
### 範例  
 以下是典型的範例 （來自 TextInterpreter 的範例） 示範如何使用 `SetMetric` 函式 （dbgmetric.lib\) 來註冊使用 Visual Studio 偵錯引擎。 Dbgmetric.lib 中，也會定義傳入的度量。  
  
> [!NOTE]
>  TextInterpreter 是基本的偵錯引擎。不會實作，因此不會註冊和 — 任何其他功能。 更完整的偵錯引擎會有一整份 `SetMetric` 呼叫或其對等項目，一個用於偵錯引擎的每項功能支援。  
  
```  
// Define base registry subkey to Visual Studio.  
static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0";  
  
HRESULT CTextInterpreterModule::RegisterServer(BOOL bRegTypeLib, const CLSID * pCLSID)  
{  
    SetMetric(metrictypeEngine, __uuidof(Engine), metricName, L"Text File", false, strRegistrationRoot);  
    SetMetric(metrictypeEngine, __uuidof(Engine), metricCLSID, CLSID_Engine, false, strRegistrationRoot);  
    SetMetric(metrictypeEngine, __uuidof(Engine), metricProgramProvider, CLSID_MsProgramProvider, false, strRegistrationRoot);  
  
    return base::RegisterServer(bRegTypeLib, pCLSID);  
}  
```  
  
## 請參閱  
 [建立自訂的偵錯引擎](../../extensibility/debugger/creating-a-custom-debug-engine.md)   
 [SDK 協助程式進行偵錯](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Tutorial: Building a Debug Engine Using ATL COM](http://msdn.microsoft.com/zh-tw/9097b71e-1fe7-48f7-bc00-009e25940c24)