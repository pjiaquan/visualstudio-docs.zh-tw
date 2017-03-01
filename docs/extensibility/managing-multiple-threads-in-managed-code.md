---
title: "如何︰ 管理多個執行緒在 Managed 程式碼 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59730063-cc29-4dae-baff-2234ad8d0c8f
caps.latest.revision: 7
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
ms.sourcegitcommit: 477f57bbca9c49e7d7d13155fc1f6e55ee4667a8
ms.openlocfilehash: 417dc6e5285859424dfa3b482a90f1a141cff163
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-managing-multiple-threads-in-managed-code"></a>如何︰ 管理多個執行緒在 Managed 程式碼
如果您有受管理的 VSPackage 擴充功能，會呼叫非同步方法，或在 Visual Studio UI 執行緒以外的執行緒上執行的作業，您應該遵循的指導方針，如下所示。 您可以讓 UI 執行緒回應，因為它不需要等待工作完成的另一個執行緒上。 您可讓您的程式碼更有效率，因為您不需要額外的執行緒所佔用的堆疊空間，您可以讓它更可靠、 更容易偵錯，因為您避免死結和當機。  
  
 一般情況下，您可以從 UI 執行緒切換至不同的執行緒，或反之亦然。 方法傳回時，目前的執行緒是從它初次呼叫的執行緒。  
  
> [!IMPORTANT]
>  下列指導方針使用 Api 中<xref:Microsoft.VisualStudio.Threading>的命名空間，特別是，<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>類別。</xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> </xref:Microsoft.VisualStudio.Threading> 這個命名空間中的 Api 是新[!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)]。 您可以取得的執行個體<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>從<xref:Microsoft.VisualStudio.Shell.ThreadHelper>屬性`ThreadHelper.JoinableTaskFactory`。</xref:Microsoft.VisualStudio.Shell.ThreadHelper> </xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>  
  
## <a name="switching-from-the-ui-thread-to-a-background-thread"></a>從 UI 執行緒切換到背景執行緒  
  
1.  如果您是在 UI 執行緒上，而且您想要在背景執行緒上的非同步工作，請使用 Task.Run():  
  
    ```c#  
    await Task.Run(async delegate{  
        // Now you’re on a separate thread.  
    });  
    // Now you’re back on the UI thread.  
  
    ```  
  
2.  如果您是在 UI 執行緒上，而且您想要使用背景執行緒上執行工作時，以同步方式阻擋<xref:System.Threading.Tasks.TaskScheduler>屬性`TaskScheduler.Default`內<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>::</xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A> </xref:System.Threading.Tasks.TaskScheduler>  
  
    ```c#  
    // using Microsoft.VisualStudio.Threading;  
    ThreadHelper.JoinableTaskFactory.Run(async delegate {  
        await TaskScheduler.Default;  
        // You're now on a separate thread.  
        DoSomethingSynchronous();  
        await OrSomethingAsynchronous();  
    });  
    ```  
  
## <a name="switching-from-a-background-thread-to-the-ui-thread"></a>從背景執行緒切換至 UI 執行緒  
  
1.  如果您是在背景執行緒，而且您想要執行 UI 執行緒上，使用<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>::</xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>  
  
    ```c#  
    // Switch to main thread  
    await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
    ```  
  
     您可以使用<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>方法，以切換至 UI 執行緒。</xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> 這個方法會將訊息張貼至 UI 執行緒與目前的非同步方法的接續，並也會與執行緒架構，以便設定正確的優先順序，並且避免死結的其餘部分通訊。  
  
     如果您的背景執行緒方法不是非同步，而且無法進行非同步，您仍然可以使用`await`語法來包裝您的工作切換至 UI 執行緒<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>，如這個範例所示︰</xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>  
  
    ```c#  
    ThreadHelper.JoinableTaskFactory.Run(async delegate {  
        // Switch to main thread  
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
        // Do your work on the main thread here.  
    });  
    ```
