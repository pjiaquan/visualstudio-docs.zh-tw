---
title: "在部署 Visual Studio 時自動套用產品金鑰 | Microsoft Docs"
ms.custom: 
ms.date: 3/10/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d79260be-6234-4fd3-89b5-a9756b4a93c1
caps.latest.revision: 10
author: TerryGLee
ms.author: tglee
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: af9699b63fdfb81a274affb78856817520c38b05
ms.openlocfilehash: 36a774583f5125ecc09210c9ad5da15ec800f870
ms.lasthandoff: 04/03/2017

---
# <a name="automatically-apply-product-keys-when-deploying-visual-studio"></a>在部署 Visual Studio 時自動套用產品金鑰
您能以程式設計的方式套用您的產品金鑰，做為用來自動化部署 Visual Studio 的一部分指令碼。 產品金鑰能在 Visual Studio 安裝期間或完成安裝後，以程式設計方式設定在裝置上。  

## <a name="apply-the-license-during-installation"></a>在安裝期間套用授權  
 請使用 `--productKey` 參數以在進行 Visual Studio 安裝程序時套用產品金鑰。 此安裝程式參數可以與 `--quiet parameter` 參數搭配使用，以在已授權的狀態下為終端使用者安裝 Visual Studio。 若要使用 `--productKey` 參數，請開啟命令提示字元。 執行安裝程式 (例如 vs_enterprise.exe 或 vs_professional.exe)，然後使用包含或不含破折號的產品金鑰 (25 個字元) 來設定 `--productKey` 參數：  

 這是以 AAAAABBBBBCCCCCDDDDDEEEEEEE 產品金鑰安裝 Visual Studio 2015 Enterprise 的命令範例：  

 `vs_enterprise.exe [any other setup parameters] --productKey AAAAABBBBBCCCCCDDDDDDEEEEEE`  

## <a name="apply-the-license-after-installation"></a>在安裝後套用授權  
 您可以在目標電腦上以無訊息模式使用 storePID.exe 公用程式，使用產品金鑰來啟用已安裝的 Visual Studio 版本。 StorePID.exe 是隨 Visual Studio 一起安裝的公用程式，安裝位置在 **\<drive>:\\\Program Files (x86)\Microsoft Visual Studio 15.0\Common7\IDE\StorePID.exe**。  

 藉由使用 System Center 代理程式或提高權限的命令提示字元，後面加上 (包括破折號) 產品金鑰和 Microsoft 產品代碼 (MPC)，以較高的權限執行 StorePID.exe。 請務必包含產品金鑰的破折號！  

 `StorePID.exe [product key including the dashes] [MPC]`  

 這是安裝 Visual Studio 2017 Enterprise 的範例命令列，其中 MPC 為 08860 且產品金鑰為 "AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE"：  

 `C:\Program Files (x86)\Microsoft Visual Studio 15.0\Common7\IDE\StorePID.exe AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 08860`  

 下表列出每個 Visual Studio 版本的 MPC 代碼：  

|Visual Studio 版本 | MPC |  
|---------------------------|---------|
|Visual Studio Enterprise 2017|08860|  
|Visual Studio Professional 2017|08862|  
|Visual Studio Test Professional 2017|08866|
|Visual Studio Enterprise 2015|07060|  
|Visual Studio Professional 2015|07062|  
|Visual Studio Test Professional 2015|07066|  
|Visual Studio Ultimate 2013|06181|  
|Visual Studio Premium 2013|06191|  
|Visual Studio Professional 2013|06177|  
|Visual Studio Test Professional 2013|06194|  

如果 StorePID.exe 成功套用產品金鑰，會傳回 0。 如果遇到錯誤，則會傳回 1 到 6 的數字。  

## <a name="see-also"></a>另請參閱  
 * [安裝 Visual Studio](../install/install-visual-studio.md)
 * [建立 Visual Studio 的離線安裝](../install/create-an-offline-installation-of-visual-studio.md)

