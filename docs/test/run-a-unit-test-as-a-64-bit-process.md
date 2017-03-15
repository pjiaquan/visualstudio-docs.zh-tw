---
title: "以 64 位元處理序的形式執行單元測試 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "單元測試, 建立"
  - "單元測試, 執行"
ms.assetid: d23a9ee7-58e3-4e8b-a38c-b2207ea73fea
caps.latest.revision: 25
ms.author: "mlearned"
manager: "douge"
caps.handback.revision: 25
---
# 以 64 位元處理序的形式執行單元測試
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

如果您有 64 位元電腦，現在就可以透過 64 位元處理序來執行單元測試以及擷取程式碼涵蓋範圍資訊。  
  
## 以 64 位元處理序的形式執行單元測試  
  
#### 若要以 64 位元處理序的形式執行單元測試  
  
1.  如果您的程式碼或測試編譯為 32 位元\/x86，但是現在要當做 64 位元處理序來執行，請將它們重新編譯為 \[**任何 CPU**\] 或 \[**64 位元**\] \(選擇性\)。  
  
    > [!TIP]
    >  為了達到最大彈性，您應該使用 \[**任何 CPU**\] 組態來編譯測試專案。  然後，您就可以在 32 和 64 位元代理程式上執行。  使用 \[**64 位元**\] 組態來編譯測試專案並沒有任何優點。  
  
2.  從 Visual Studio 的功能表上，選取 \[**測試**\]，然後選取 \[**設定**\]，然後選取 \[**處理器架構**\]。  選取 **x64** 以 64 位元處理序執行測試。  
  
     \-或\-  
  
     指定 `<TargetPlatform>x64</TargetPlatform>` 在 .runsettings 檔案。  這個方法的優點是您可以指定設定的群組不同檔案和快速切換不同設定的設定。  您也可以複製到方案之間的設定。  如需詳細資訊，請參閱[使用 .runsettings 檔案設定單元測試](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)。  
  
## 請參閱  
 [使用測試總管執行單元測試](../test/run-unit-tests-with-test-explorer.md)   
 [對程式碼進行單元測試](../test/unit-test-your-code.md)   
 [指定 Visual Studio 測試的測試設定](/devops-test-docs/test/specifying-test-settings-for-visual-studio-tests)