---
title: "在部署 Visual Studio 時自動套用產品金鑰 | Microsoft Docs"
ms.custom: 
ms.date: 05/06/2017
ms.reviewer: tims
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: 493ea235a3d89a04a4c6accfa491e622792e4397
ms.contentlocale: zh-tw
ms.lasthandoff: 05/10/2017

---
# <a name="automatically-apply-product-keys-when-deploying-visual-studio"></a>在部署 Visual Studio 時自動套用產品金鑰
您能以程式設計的方式套用您的產品金鑰，做為用來自動化部署 Visual Studio 的一部分指令碼。 產品金鑰能在 Visual Studio 安裝期間或完成安裝後，以程式設計方式設定在裝置上。

## <a name="apply-the-license-after-installation"></a>在安裝後套用授權
 您可以在目標電腦上以無訊息模式使用 `StorePID.exe` 公用程式，利用產品金鑰來啟用已安裝的 Visual Studio 版本。 `StorePID.exe` 是與 Visual Studio 2017 一起安裝的公用程式，其預設位置如下： <br> `C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE`

 使用 System Center 代理程式或提高權限的命令提示字元，以較高的權限執行 `StorePID.exe`，後面再加上產品金鑰 (包含破折號) 和 Microsoft 產品代碼 (MPC)。 請務必包含產品金鑰的破折號。

 ```
 StorePID.exe [product key including the dashes] [MPC]
 ```

 以下範例命令列可利用產品金鑰 `AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE` 來套用 Visual Studio 2017 Enterprise (其 MPC 為 08860) 的授權，並安裝於預設位置：

 ```cmd
 "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\StorePID.exe" AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 08860
 ```

 下表列出每個 Visual Studio 版本的 MPC 代碼：

| Visual Studio 版本                | MPC   |
|--------------------------------------|-------|
| Visual Studio Enterprise 2017        | 08860 |
| Visual Studio Professional 2017      | 08862 |
| Visual Studio Test Professional 2017 | 08866 |

如果 `StorePID.exe` 成功套用產品金鑰，將傳回值為 0 的 `%ERRORLEVEL%`。 如果發生錯誤，則會根據錯誤狀況傳回代碼：

| 錯誤                     | 程式碼 |
|---------------------------|------|
| `PID_ACTION_SUCCESS`      | 0    |
| `PID_ACTION_NOTINSTALLED` | 1    |
| `PID_ACTION_INVALID`      | 2    |
| `PID_ACTION_EXPIRED`      | 3    |
| `PID_ACTION_INUSE`        | 4    |
| `PID_ACTION_FAILURE`      | 5    |
| `PID_ACTION_NOUPGRADE`    | 6    |

## <a name="see-also"></a>另請參閱
 * [安裝 Visual Studio](../install/install-visual-studio.md)
 * [建立 Visual Studio 的離線安裝](../install/create-an-offline-installation-of-visual-studio.md)

