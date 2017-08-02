---
title: "Visual Studio 中的 Python 安裝 | Microsoft Docs"
ms.custom: 
ms.date: 5/8/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ce3d3656-7ba2-490d-92df-0bb3e3badf92
caps.latest.revision: 11
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: 9cdd87d81f0b0f4748a25c7bb87fb840e246854c
ms.contentlocale: zh-tw
ms.lasthandoff: 05/10/2017

---

# <a name="installing-python-support-in-visual-studio"></a>在 Visual Studio 中安裝 Python 支援

若要為 Visual Studio 安裝 Python 支援，請遵循符合您 Visual Studio 版本之小節中的指示：

- [Visual Studio 2017](#visual-studio-2017)
- [Visual Studio 2015](#visual-studio-2015)
- [Visual Studio 2013 和更早版本](#visual-studio-2013-and-earlier)

請注意，針對 Visual Studio 2015 和更早版本，您需要另外安裝您所選的 Python 解譯器。 如需詳細資料，請參閱 [Python 環境](python-environments.md)。

在按照安裝步驟執行之後，若要快速測試 Python 支援，請按 Alt-I 開啟 Python Interactive 視窗，並輸入 `2+2`。 如果您沒有看到 `4` 的輸出，請重新檢查您的步驟。

> [!Tip]
> Python 工作負載包含很有用的 Cookiecutter 擴充功能，能提供探索範本、輸入範本選項，以及建立專案及檔案的圖形化使用者介面。 如需詳細資訊，請參閱[使用 Cookiecutter](cookiecutter.md)。

## <a name="visual-studio-2017"></a>Visual Studio 2017

1. 從 [https://www.visualstudio.com/vs/](https://www.visualstudio.com/vs/) 安裝 Visual Studio 2017。

1. 在 Visual Studio 安裝程式中，選取 [Web 與雲端] > [Python 開發] 工作負載。

    ![Visual Studio 安裝程式中的 Python 開發工作負載](~/python/media/installation-python-workload.png)

    > [!Note]
    > **資料科學和分析應用程式**工作負載中也包含 Python。

1. 在安裝程式的右側，選取 Python 解譯器，以及其他您想包含的相關工具。 例如，如果您計劃開發適用於 Python 的 C++ 延伸模組，請包括 [Python 原生開發工具] 選項。

    ![Visual Studio 安裝程式中的 Python 開發選項](~/python/media/installation-python-options.png)

## <a name="visual-studio-2015"></a>Visual Studio 2015

1. 從 [控制台] > [程式和功能]，選取 [Microsoft Visual Studio 2015]，再選取 [變更]，以執行 Visual Studio 安裝程式。

1. 在安裝程式中，選取 [修改]。

1. 選取 [程式語言] > [適用於 Visual Studio 的 Python 工具]，然後選取 [下一步]：

    ![Visual Studio 2015 安裝程式中的 PTVS 選項](~/python/media/installation-vs2015.png)    

1. 當 Visual Studio 安裝完成之後，請[安裝您所選的 Python 解譯器](python-environments.md#selecting-and-installing-python-interpreters)。

## <a name="visual-studio-2013-and-earlier"></a>Visual Studio 2013 和更早版本

1. 針對您的 Visual Studio 版本，安裝適當版本的「適用於 Visual Studio 的 Python 工具」：

    - Visual Studio 2013：[適用於 Visual Studio 2013 的 PTVS 2.2 (英文)](https://github.com/Microsoft/PTVS/releases/v2.2)。 Visual Studio 2013 中的 [檔案] > [新增專案] 對話方塊能提供您此程序的捷徑。
    - Visual Studio 2012：[適用於 Visual Studio 2012 的 PTVS 2.1 (英文)](https://pytools.codeplex.com/downloads/get/920478)
    - Visual Studio 2010：[適用於 Visual Studio 2010 的 PTVS 2.1 (英文)](https://pytools.codeplex.com/downloads/get/920479)

1. [安裝您所選的 Python 解譯器](python-environments.md#selecting-and-installing-python-interpreters)。

## <a name="install-locations"></a>安裝位置

根據預設，系統會為電腦上的所有使用者安裝 Python 支援。

針對 Visual Studio 2017，Python 工作負載會安裝在 `%ProgramFiles(x86)%\Microsoft Visual Studio\2017\<VS_edition>Common7\IDE\Extensions\Microsoft\Python`，其中 &lt;VS_edition&gt; 將會是 Community、Professional 或 Enterprise。

針對 Visual Studio 2015 和更早版本，安裝路徑如下：

- 32 位元：
  - 路徑：`%Program Files(x86)%\Microsoft Visual Studio <VS_ver>\Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio\<PTVS_ver>`
  - 路徑的登錄位置：`HKEY_LOCAL_MACHINE\Software\Microsoft\PythonTools\<VS_ver>\InstallDir`
- 64 位元︰
  - 路徑：`%Program Files%\Microsoft Visual Studio <VS_ver>\Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio\<PTVS_ver>`
  - 路徑的登錄位置：`HKEY_LOCAL_MACHINE\Software\Wow6432Node\Microsoft\PythonTools\<VS_ver>\InstallDir`

其中：

- &lt;VS_ver&gt;：    
    - 針對 Visual Studio 2015 為 14.0
    - 針對 Visual Studio 2013 為 12.0
    - 針對 Visual Studio 2012 為 11.0
    - 針對 Visual Studio 2010 為 10.0
- &lt;PTVS_ver&gt; 為版本號碼，如 2.2、2.1、2.0、1.5、1.1 或 1.0。

### <a name="user-specific-installations-15-and-earlier"></a>使用者特定安裝 (1.5 和更早版本)

適用於 Visual Studio 1.5 和更早版本的 Python 工具，僅允許針對目前的使用者進行安裝，此情況下的安裝路徑為 `%LocalAppData%\Microsoft\VisualStudio\<VS_ver>\Extensions\Microsoft\Python Tools for Visual Studio\<PTVS_ver>`，其中 &lt;VS_ver&gt; 和 &lt;PTVS_ver&gt; 的狀況與上述相同。

