---
title: "CA1063：必須正確實作 IDisposable | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ImplementIDisposableCorrectly"
  - "CA1063"
helpviewer_keywords: 
  - "CA1063"
  - "ImplementIDisposableCorrectly"
ms.assetid: 12afb1ea-3a17-4a3f-a1f0-fcdb853e2359
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1063：必須正確實作 IDisposable
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|ImplementIDisposableCorrectly|  
|CheckId|CA1063|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## 原因  
 未正確實作 `IDisposable`。  此處列出造成這個問題的部分原因：  
  
-   在類別 \(Class\) 中重新實作 IDisposable。  
  
-   已重新覆寫 Finalize。  
  
-   已覆寫 Dispose。  
  
-   Dispose\(\) 不是 public、sealed 或名為 Dispose。  
  
-   Dispose\(bool\) 不是 protected、virtual 或 unsealed。  
  
-   在 unsealed 型別中，Dispose\(\) 必須呼叫 Dispose\(true\)。  
  
-   如為 unsealed 型別，Finalize 實作 \(Implementation\) 不會呼叫任一個 Dispose\(bool\) 或是類別完成項。  
  
 若這些模式中的任何一個違反了此規則，將會觸發此警告。  
  
 每個未密封的根 IDisposable 型別必須提供它自己的 protected virtual void Dispose\(bool\) 方法。  Dispose\(\) 必須呼叫 Dipose\(true\)，而 Finalize 必須呼叫 Dispose\(false\)。  如果您正在建立未密封的根 IDisposable 型別，則必須定義 Dispose\(bool\) 並呼叫它。  如需詳細資訊，請參閱 .NET Framework 文件之[Framework 設計方針](../Topic/Framework%20Design%20Guidelines.md) 一節中的[Cleaning Up Unmanaged Resources](../Topic/Cleaning%20Up%20Unmanaged%20Resources.md)。  
  
## 規則描述  
 所有 IDisposable 型別都應該正確實作 Dispose 模式。  
  
## 如何修正違規  
 檢查程式碼，並判斷下列哪一個解決方式可以修正此違規。  
  
-   從 {0} 實作的介面清單中移除 IDisposable，並改為覆寫基底類別 \(Base Class\) Dispose 實作。  
  
-   從型別 {0} 中移除完成項、覆寫 Dispose\(bool disposing\)，以及在判斷 'disposing' 為 false 的程式碼區塊中撰寫最終處理的程式碼邏輯。  
  
-   移除 {0}、覆寫 Dispose\(bool disposing\)，以及在判斷 'disposing' 為 true 的程式碼區塊中撰寫處置邏輯。  
  
-   請確認 {0} 已宣告為 public 和 sealed。  
  
-   將 {0} 重新命名為 'Dispose'，並確認已將它宣告為 public 和 sealed。  
  
-   確定 {0} 已宣告為 protected、virtual 和 unsealed。  
  
-   修改 {0}，它就會呼叫 Dispose\(true\)，接著在目前的物件執行個體 \(Instance\) 上呼叫 GC.SuppressFinalize \(在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中為 'this' 或 'Me'\)，然後傳回。  
  
-   修改 {0}，它就會呼叫 Dispose\(false\) 然後傳回。  
  
-   如果您正在撰寫非密封的 IDisposable 根類別，請確定 IDisposable 的實作遵循本節稍早說明的模式。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## 虛擬程式碼範例  
 下列的虛擬程式碼會提供在類別中如何使用 Managed 資源和原生資源，實作 Dispose\(bool\) 的範例。  
  
```  
public class Resource : IDisposable   
{  
    private IntPtr nativeResource = Marshal.AllocHGlobal(100);  
    private AnotherResource managedResource = new AnotherResource();  
  
// Dispose() calls Dispose(true)  
    public void Dispose()  
    {  
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
    // NOTE: Leave out the finalizer altogether if this class doesn't   
    // own unmanaged resources itself, but leave the other methods  
    // exactly as they are.   
    ~Resource()   
    {  
        // Finalizer calls Dispose(false)  
        Dispose(false);  
    }  
    // The bulk of the clean-up code is implemented in Dispose(bool)  
    protected virtual void Dispose(bool disposing)  
    {  
        if (disposing)   
        {  
            // free managed resources  
            if (managedResource != null)  
            {  
                managedResource.Dispose();  
                managedResource = null;  
            }  
        }  
        // free native resources if there are any.  
        if (nativeResource != IntPtr.Zero)   
        {  
            Marshal.FreeHGlobal(nativeResource);  
            nativeResource = IntPtr.Zero;  
        }  
    }  
}  
```