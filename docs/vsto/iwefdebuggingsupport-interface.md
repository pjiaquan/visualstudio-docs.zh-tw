---
title: "IWefDebuggingSupport 介面"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: 0bd1c6a6-67a5-4478-b942-8b937b28f723
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# IWefDebuggingSupport 介面
  實作由偵錯環境，例如 Visual Studio，協助應用程式偵錯 Office 的。  在偵錯工作階段期間， Office 應用程式，例如 Word 或 Excel，從 Visual Studio 的這個介面會呼叫介面的方法在某些點。  
  
## 語法  
  
```  
[  
    uuid(ccaf1a90-ce1c-4199-9cd6-b40c5c57a671),  
    oleautomation  
]  
interface IWefDebuggingSupport : IUnknown  
{  
    HRESULT SetWefProcessId(  
        [in] DWORD dwProcessId);  
    HRESULT GetAutoInsertExtensions(  
        [out, retval] SAFEARRAY(BSTR)* psaExtensionNames);  
}  
```  
  
## 方法  
 下表列出 IWefDebuggingSupport 介面定義的方法。  
  
|名稱|描述|  
|--------|--------|  
|[GetAutoInsertExtensions 方法](../vsto/getautoinsertextensions-method.md)|取得有關在偵錯期間，要自動插入的應用程式資訊的 Office 專案中。|  
|[SetWefProcessId 方法](../vsto/setwefprocessid-method.md)|提供會執行 Web Extension Framework \(WEF\) 內容的處理序識別項。|  
  
  