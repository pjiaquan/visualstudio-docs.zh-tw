---
title: "使用 3D 資產來打造遊戲和應用程式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.graphics"
ms.assetid: 910d673b-c884-4eeb-9928-0e89f3d38cb6
caps.latest.revision: 24
caps.handback.revision: 24
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
---
# 使用 3D 資產來打造遊戲和應用程式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本文件說明您可以用來建立或修改 3D 模型、材質，以及 DirectX 架構遊戲與應用程式的著色器的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 工具。  
  
## Visual Studio 中的 DirectX 應用程式開發  
 A DirectX 應用程式通常會結合程式設計邏輯、DirectX 應用程式開發介面和高階著色語言 \(HLSL\) 程式，以及音訊和 3D 視覺化資產，以呈現豐富的互動式多媒體經驗。  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 包含的工具可用於處理影像和材質、3D 模型和著色器，而不需要離開 IDE 使用其他工具。  Visual Studio 工具特別適用於建立*預留位置*資產，當您在偵錯應用程式時，可以用來測試程式碼或組建原型，之後再委任準備好實際執行的資產，以及檢查和修改準備好實際執行的資產。  
  
 以下是有關可在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中使用之資產類型的詳細資訊。  
  
### 影像和材質  
 影像和材質在遊戲和應用程式中提供色彩和視覺化細節。  在立體圖形中，材質提供多種格式、類型和幾何來支援不同的用途。  例如，法線地圖會針對更詳細的立體模型光源提供個別像素曲面法線，而立方體地圖會在所有方向提供材質做為 Sky\-Boxing、反射和球面材質對應等用途。  紋理可以提供 MIP 對應以支援有效的轉譯成不同的詳細程度，而且可支援不同的色頻和色彩順序。  紋理可以用各種壓縮格式加以儲存，能夠佔用很少的圖形專用記憶體和更有效率地協助 GPU 存取紋理。  
  
 您可以使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 影像編輯器處理許多常見型別和格式的影像和材質。  
  
### 3D 模型  
 立體模型會在遊戲和應用程式中建立空間和圖形。  至少，模型會將立體空間點 \(稱為「*頂點*」\(Vertex\)\) 的位置與索引資料一起編碼，以定義表示模型形狀的線條或三角形。  可以將其他資料與這些頂點產生關聯，例如色彩資訊、法線向量或應用程式特定屬性。  每個模型還可能定義物件的屬性，例如，使用哪一個著色器計算物件表面的外觀，或是套用哪一個材質給它。  
  
 您可以使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 模型編輯器處理數種常見格式的 3D 模型。  
  
### 著色器  
 著色器是微小且屬於特定領域的程式，其執行於圖形處理單元 \(GPU\)。  著色器決定 3D 模型如何轉換成螢幕上的圖形，以及這些圖形的每個像素如何被上色。  藉由建立著色器並將其套用至遊戲或應用程式中的物件，您可以賦予物件獨特的外觀。  
  
 您可以使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 著色器設計工具 \(圖形著色器設計工具\) 建立自訂視覺效果，而不需要知道 HLSL 程式設計。  
  
> [!NOTE]
>  如需如何開始 DirectX 程式設計的詳細資訊，請參閱 [DirectX](http://go.microsoft.com/fwlink/p/?LinkId=224633)。  如需如何偵錯 DirectX 架構應用程式的詳細資訊，請參閱 [圖形診斷 \(偵錯 DirectX 圖形\)](../debugger/visual-studio-graphics-diagnostics.md)。  
  
## DirectX 版本相容性  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 使用 DirectX 呈現 2D 和 3D 資產。  您可以選取 DirectX 11 產生器或 視窗中進階 Windows Advanced Rasterization Platform \(WARP\) \(WARP\) 軟體產生器。  DirectX 11 產生器在 DirectX 11 與 DirectX 10 GPUs 提供高效能及硬體加速的呈現。  WARP 產生器有助於確定您的資產適用於各種不同的電腦，包括未配備現代化圖形硬體的電腦，以及採用整合圖形硬體的電腦。  如需 WARP 的詳細資訊，請參閱 [Windows Advanced Rasterization Platform \(WARP\) Guide](http://go.microsoft.com/fwlink/p/?LinkId=224634)。  
  
## 相關主題  
  
|標題|說明|  
|--------|--------|  
|[使用紋理和影像](../designers/working-with-textures-and-images.md)|描述如何使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 來處理影像和材質。|  
|[使用 3D 模型](../designers/working-with-3-d-models.md)|說明如何使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 來處理立體模型。|  
|[使用著色器](../designers/working-with-shaders.md)|說明如何使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 著色器設計工具來建立和修改自訂著色器效果。|  
|[在遊戲或應用程式中使用 3D 資產](../designers/using-3-d-assets-in-your-game-or-app.md)|說明如何在遊戲或應用程式中使用資產 \(這是使用影像編輯器、模型編輯器或著色器設計工具所建立的\)。|