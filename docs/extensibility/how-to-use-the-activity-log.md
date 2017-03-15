---
title: "如何︰ 使用活動記錄檔 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSPackages，偵錯"
  - "VSPackages 疑難排解"
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
caps.latest.revision: 29
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 29
---
# 如何︰ 使用活動記錄檔
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSPackages 可以將訊息寫入活動記錄檔。 這項功能是特別適用於零售環境中的偵錯 Vspackage。  
  
> [!TIP]
>  永遠開啟活動記錄檔。 Visual Studio 會保留一個循環緩衝區的上次一百個以上的項目，以及有一般性的組態資訊的前十個項目。  
  
### 若要將項目寫入活動記錄檔  
  
1.  插入這個程式碼的 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> 方法或任何其他方法，只是 VSPackage 建構函式中︰  
  
    ```c#  
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (log == null) return;  
  
    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,  
        this.ToString(),  
        string.Format(CultureInfo.CurrentCulture,  
        "Called for: {0}", this.ToString()));  
    ```  
  
     此程式碼可取得 <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> 服務，並將它轉換成 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> 介面。<xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A> 寫入活動記錄，使用目前文化特性的內容將資訊項目。  
  
2.  當載入 VSPackage 時 （通常時叫用命令，或在開啟的視窗） 時，文字會寫入活動記錄檔。  
  
### 查看活動記錄檔  
  
1.  尋找 Visual Studio 資料的子資料夾中的活動記錄︰ *%appdata%*\\Microsoft\\VisualStudio\\14.0\\ActivityLog.XML...  
  
2.  使用任何文字編輯器中開啟活動記錄檔。 以下是典型的項目︰  
  
    ```  
    Called for: Company.MyApp.MyAppPackage ...  
    ```  
  
## 穩固程式設計  
 活動記錄檔是一項服務，因為活動記錄檔是 VSPackage 建構函式中無法使用。  
  
 您應該取得活動記錄檔之前寫入它。 不要快取或儲存供日後使用的活動記錄檔。  
  
## 請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>   
 [疑難排解 Vspackage](../extensibility/troubleshooting-vspackages.md)   
 [Vspackage](../extensibility/internals/vspackages.md)