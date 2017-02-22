---
title: "VS Shell 部署 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: be8f2ffe-a322-4ac0-9c9e-873bd28e5d5e
caps.latest.revision: 2
caps.handback.revision: 2
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# VS Shell 部署
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

隔離的殼層可讓您判斷哪一個 Visual Studio 的功能需要您定義域專屬語言和該方案應顯示的方式進行互動。  如需有關隔離的 Visual Studio 命令介面的詳細資訊，請參閱[自訂獨立的 Shell](../extensibility/customizing-the-isolated-shell.md)。  您可以找到有關如何自訂隔離的殼層中[Customizing the Isolated Shell](http://msdn.microsoft.com/zh-tw/d75463cd-1155-42e4-8b7a-046ed6becbbf)。  
  
### 若要設定 Visual Studio 的介面做為部署目標  
  
1.  在**DslPackage**專案中，開啟**source.extension.tt**。  
  
2.  在`<SupportedProducts>`插入：  
  
    ```  
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>  
    ```  
  
     取代 *MyIsolatedShell* 與隔離的殼層封裝的名稱。