---
title: "如何：將控制項標記為安全控制項"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "安全控制項 [Visual Studio 中的 SharePoint 程式開發]"
  - "Visual Studio 中的 SharePoint 開發, 進階封裝工具"
  - "Visual Studio 中的 SharePoint 開發, 安全控制項"
ms.assetid: 813727d5-6750-407c-a23e-c38dd611e78c
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# 如何：將控制項標記為安全控制項
  就安全性而言，SharePoint 會將 Web 控制項區分為受保護使其不會遭受指令碼插入的 Web 控制項和未受保護的 Web 控制項。  受保護的控制項或「*安全控制項*」\(Safe Control\) 可以由未受信任的使用者來存取。  當您將組件加入至封裝時，可以在 SharePoint 專案項目的 \[安全控制項項目\] 屬性中，或者在 \[**封裝設計工具**\] 中，將控制項標記為安全。  如需詳細資訊，請參閱  
  
 [web.config 檔案設定變更](http://go.microsoft.com/fwlink/?LinkId=178965) 和 [註冊網頁組件的組件做為安全控制項](http://go.microsoft.com/fwlink/?LinkId=171013)。  
  
> [!IMPORTANT]  
>  這些程序用來當做說明用途。  只有當您確定控制項為安全時，才將其標記為安全。  
  
## 在安全控制項項目屬性中標記安全控制項  
  
#### 若要在安全控制項項目屬性中將控制項標記為安全或不安全  
  
1.  建立一個具有「視覺 Web 組件」專案的 SharePoint 方案。  
  
2.  將兩個控制項加入至 Web 組件：文字方塊和按鈕。  分別將其名稱保留為預設值：TextBox1 和 Button1。  
  
3.  將兩個項目加入至 Web 組件的 \[**安全控制項項目**\] 屬性。  若要進行此項操作，請選擇 \[**屬性**\] 視窗中 \[**安全控制項項目**\] 屬性旁邊的省略符號 \(![ASP.NET Mobile 設計工具橢圓形](~/docs/sharepoint/media/mwellipsis.gif "ASP.NET Mobile 設計工具橢圓形")\) 按鈕。  
  
     \[**安全控制項項目**\] 對話方塊隨即出現。  
  
4.  在 \[**安全控制項項目**\] 對話方塊中，按兩下 \[**加入**\] 按鈕，將兩個安全控制項項目加入至 \[**成員**\] 窗格：一個適用於按鈕，而另一個適用於文字方塊。  
  
5.  選擇第一個安全控制項項目，並將其 \[**安全**\] 屬性變更為 \[**False**\]、將其 \[**型別名稱**\] 屬性變更為 \[**Button1**\]，並將其 \[**防止指令碼威脅**\] 屬性變更為 \[**False**\]。  
  
     此步驟會將按鈕控制項識別為不安全控制項。  
  
6.  選擇清單中第二個安全控制項項目。  將其 \[**安全**\] 屬性值保留為 \[**True**\]、將其 \[**型別名稱**\] 屬性設定為 \[**TextBox1**\]，並將其 \[**防止指令碼威脅**\] 屬性設定為 \[**True**\]。  
  
     現在便會將文字方塊控制項標記為防止指令碼插入威脅的控制項。  
  
7.  選取 \[**確定**\] 按鈕來關閉對話方塊。  
  
## 在封裝設計工具中標記安全控制項  
  
#### 若要在封裝設計工具中將控制項標記為安全或不安全  
  
1.  建立一個具有「視覺 Web 組件」專案的 SharePoint 方案。  
  
2.  將兩個控制項加入至 Web 組件：文字方塊和按鈕。  分別將其名稱保留為預設值：TextBox1 和 Button1。  
  
     記下控制項的命名空間，以供稍後使用。  
  
3.  若要建置專案，請從功能表上選取 \[**建置**\]、\[**建置方案**\]。  
  
4.  建立另一個 SharePoint 方案。  
  
5.  在 \[**方案總管**\] 中，開啟 Package.Package 檔案的捷徑功能表，然後選擇 \[**開啟**\]，以開啟 \[**封裝設計工具**\]。  
  
6.  在 \[**封裝設計工具**\] 中，選擇 \[**進階**\] 索引標籤。  
  
7.  在 \[**其他組件**\] 下，選擇 \[**加入**\] 按鈕，並從清單中選取 \[**加入現有組件**\]。  
  
8.  在 \[**加入現有組件**\] 對話方塊中，選擇 \[**來源路徑**\] 旁邊的省略符號 \(![ASP.NET Mobile 設計工具橢圓形](~/docs/sharepoint/media/mwellipsis.gif "ASP.NET Mobile 設計工具橢圓形")\) 按鈕。  
  
9. 選擇在步驟 1 中建立的 SharePoint 方案組件，然後選擇 \[**開啟**\] 按鈕。  
  
10. 對於這個範例，將 \[**部署目標**\] 選項保留為 GlobalAssemblyCache。  
  
     此步驟會導致將組件部署至系統「全域組件快取」\(GAC\)。  如果您要將組件部署至 Web 應用程式 \(Bin\) 資料夾，則改為選取該選項。  如需詳細資訊，請參閱 [部署 SharePoint Foundation 中的 Web 組件](http://go.microsoft.com/fwlink/?LinkId=177509)。  
  
11. 在 \[**安全控制項**\] 方塊中，選擇 \[**按一下這裡加入新項目**\] 按鈕。  
  
12. 透過下表輸入屬性值。  
  
    |屬性名稱|值|  
    |----------|-------|  
    |命名空間|控制項的完整限定命名空間，例如 **BdcModelProject1.VisualWebPart1**。|  
    |類型名稱|Button1|  
    |組件名稱|強式組件名稱，例如：Microsoft.Office.SharePoint.ClientExtensions, Version\=14.0.0.0, Culture\=neutral, PublicKeyToken\=71e9bce111e9429c。|  
    |安全|清除 \[**安全**\] 核取方塊。|  
    |防止指令碼威脅|將 \[**防止指令碼威脅**\] 核取方塊保留在清除的狀態。|  
  
    > [!NOTE]  
    >  透過 \[**封裝設計工具**\] 的 \[**進階**\] 索引標籤為組件加入的 \[**組件名稱**\] 值不得為語彙基元，其必須為具備強式名稱的組件。  如需詳細資訊，請參閱[建立和使用強式名稱的組件](http://go.microsoft.com/fwlink/?LinkId=177513)。  
  
13. 選取 TAB 鍵建立另一個安全控制項項目。  
  
14. 重新選擇 \[**按一下這裡加入新項目**\] 按鈕。  
  
15. 透過下表輸入屬性值。  
  
    |屬性名稱|值|  
    |----------|-------|  
    |命名空間|控制項的完整限定命名空間，例如 **BdcModelProject1.VisualWebPart1**。|  
    |類型名稱|TextBox1|  
    |組件名稱|強式組件名稱，例如：Microsoft.Office.SharePoint.ClientExtensions, Version\=14.0.0.0, Culture\=neutral, PublicKeyToken\=71e9bce111e9429c。|  
    |安全|選取 \[**安全**\] 核取方塊。|  
    |防止指令碼威脅|選取 \[**防止指令碼威脅**\] 核取方塊。|  
  
16. 選取 TAB 鍵，然後選擇 \[**確定**\] 按鈕關閉對話方塊。  
  
## 請參閱  
 [提供專案項目中的封裝和部署資訊](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)   
 [封裝和部署 SharePoint 方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  