---
title: "提供的服務 (原始檔控制 VSPackage) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "原始檔控制套件的服務"
  - "原始檔控制套件服務"
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# 提供的服務 (原始檔控制 VSPackage)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

服務是透過此功能共用之間 Visual Studio 的整合式的開發環境 \(IDE\)，其已安裝的 VSPackages 和 VSPackages 之間的主要機制。  如需詳細的服務和它們的重要性，在 Visual Studio 的 IDE 中的詳細說明，請參閱[使用並提供服務](../../extensibility/using-and-providing-services.md)。  
  
## 原始檔控制服務  
 Visual Studio 提供兩個的層級的服務、 IDE 層級的服務和套件層級的服務。  Visual Studio 的 IDE 原本的型別會提供 IDE 層級的服務。  原始檔控制套件會使用某些服務。  原始檔控制套件，為 VSPackage 共用它的原始檔控制功能，藉由提供它自己的私用的原始檔控制服務。  原始檔控制套件封裝頁面實作的合約，可由 Visual Studio 的 IDE 的形式的原始檔控制相關介面的集合。  
  
## 請參閱  
 [設計元素](../../extensibility/internals/source-control-vspackage-design-elements.md)