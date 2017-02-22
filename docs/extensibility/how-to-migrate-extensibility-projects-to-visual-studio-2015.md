---
title: "如何︰ 將移轉至 Visual Studio 2015 的擴充性專案 | Microsoft Docs"
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
  - "Visual Studio SDK，升級"
ms.assetid: 22491cdc-8f04-4e1c-8eb4-ff33798ec792
caps.latest.revision: 25
caps.handback.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
---
# 如何︰ 將移轉至 Visual Studio 2015 的擴充性專案
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

以下是如何升級您的擴充功能。  
  
> [!IMPORTANT]
>  如果您想要維護針對舊版的 Visual Studio 擴充功能方案的版本，請務必製作複本，您在升級之前。 它可能很難的升級的版本返回先前的狀態。  
  
#### 若要升級的擴充性解決方案  
  
1.  您想要升級，請開啟新的版本中使用的複本。 您會建議您，在升級後將無法回復。  
  
2.  在升級完成後，變成新版本的 devenv.exe 外部程式的路徑。 以滑鼠右鍵按一下專案節點中的 **方案總管\] 中**, ，然後選擇 \[ **屬性**。 在 **偵錯** 索引標籤上，尋找由文字方塊 **啟動外部程式** devenv.exe 的路徑變更至 Visual Studio 2015 的路徑，看起來應該像這樣︰  
  
     **%ProgramFiles%\\Microsoft visual Studio 14.0\\Common7\\IDE\\devenv.exe**  
  
3.  加入 Microsoft.VisualStudio.Shell.14.0.dll 的參考。 \(以滑鼠右鍵按一下專案節點中的 **方案總管\] 中** ，然後選擇 \[ **參考或將**。 選取 **延伸** 索引標籤，然後檢查 **Microsoft.VisualStudio.Shell.14.0**。\)  
  
4.  建置方案。 內建的檔案都會部署至︰  
  
     **%LOCALAPPDATA%\\Microsoft\\VisualStudio.14.0Exp\\Extensions\\ \< 作者名稱 \> \\ \< 專案名稱 \> \\ \< 專案版本 \> \\**。  
  
#### 若要更新 NuGet VS SDK 參考組件的擴充性專案  
  
1.  判斷您的專案需要 VS SDK 參考組件。  在 **方案總管\] 中**, ，展開專案的 **參考** 節點並檢閱專案參考的清單。  VS SDK 參考組件會有前置詞 **Microsoft.VisualStudio** 名稱 \(例如︰ Microsoft.VisualStudio.Shell.14.0\)。  
  
2.  從專案移除 VS SDK 參考組件，請選取圖形，以滑鼠右鍵按一下並 **移除**。  
  
3.  新增 VS SDK 參考組件的 NuGet 版本。  在 **方案總管參考** 節點，開啟 **Manage NuGet Packages...** \] 對話方塊。  如果您想要深入了解此對話方塊，請參閱 [使用對話方塊管理 NuGet 套件](http://docs.nuget.org/Consume/Package-Manager-Dialog)。 VS SDK 參考組件會發佈在 [nuget.org](http://www.nuget.org) 由 [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility)。  
  
4.  使用 **nuget.org** 做為您 **套件來源**, ，搜尋符合所需的參考組件的 NuGet 封裝名稱 \(例如︰ Microsoft.VisualStudio.Shell.14.0\) 並將它安裝在您的專案。  NuGet 可以新增多個參考組件，以滿足初始的組件相依性。  
  
     如果想要的話，您可以加入所有 VS SDK 參考組件一次安裝 VS SDK [中繼封裝](http://www.nuget.org/packages/VSSDK_Reference_Assemblies)。  
  
5.  您也可以切換為使用 VS SDK 建置工具的 NuGet 版本。 這個 NuGet 封裝是 [Microsoft.VSSDK.BuildTools](http://www.nuget.org/packages/Microsoft.VSSDK.BuildTools) 並一次加入至您的專案將包含所需的工具和目標檔案，讓您的電腦上建立擴充性專案，而不需要安裝 VS SDK。  
  
> [!NOTE]
>  不需要您更新現有擴充性專案使用 NuGet 參考組件和工具。  他們可以繼續使用參考組件和 VS SDK 中隨附的工具來建置。