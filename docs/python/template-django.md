---
title: "Visual Studio 中適用於 Python 的 Django Web 專案範本 | Microsoft Docs"
ms.custom: 
ms.date: 5/8/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c479be58-13eb-4d77-9a27-c97ddc290963
caps.latest.revision: 1
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
ms.openlocfilehash: 4a5db2deb3633e8305dbf83cbe6ba8c0e3344c72
ms.contentlocale: zh-tw
ms.lasthandoff: 05/10/2017

---

# <a name="django-web-project-template"></a>Django Web 專案範本

[Django (英文)](https://www.djangoproject.com/) 是高階的 Python 架構，專為快速、安全且可擴充的網頁程式開發所設計。 Visual Studio 中的 Python 支援可提供專案範本來設定 Django 架構 Web 應用程式的結構。 若要在 Visual Studio 中使用範本，請選取 [檔案] > [新增] > [專案]，搜尋「Django」，然後選取 [Django Web 專案] 範本。 產生的專案會包含未定案程式碼，以及預設的 SQLite 資料庫。 [空白 Django Web 專案] 範本和上述範本相似，但不包含資料庫。

Visual Studio 針對 Django 專案提供完整的 IntelliSense：

- 傳入範本的內容變數：

    ![內容變數的 IntelliSense](media/template-django-intellisense.png)

- 標記和篩選內建及使用者定義項目：

    ![標記和篩選的 IntelliSense](media/template-django-intellisense-filter.png)

- 內嵌 CSS 和 JavaScript 的語法著色：

    ![CSS IntelliSense](media/template-django-intellisense-css.png)

    ![JavaScript IntelliSense](media/template-django-intellisense-js.png)


Visual Studio 也針對 Django 專案提供完整的[偵錯支援](debugging.md)： 

![中斷點](media/template-django-debugging.png)

## <a name="django-management-console"></a>Django 管理主控台

Django 管理主控台可透過 [專案] 功能表上 (或是在 [方案總管] 中以滑鼠右鍵按一下專案) 的各種命令來存取。

- **開啟 Django 殼層...**：在您的應用程式內容中開啟可讓您操作模型的殼層

    ![主控台](media/template-django-console-shell.png)

- **Django 同步 DB**︰在互動式的視窗中執行 `manage.py syncdb`：

    ![主控台](media/template-django-console-sync-db.png)

- **收集靜態**：執行 `manage.py collectstatic --noinput` 以將所有靜態檔案複製到由 `settings.py` 中的 `STATIC_ROOT` 所指定的路徑。 請注意，[發佈至 Microsoft Azure](template-web.md#publishing-to-azure-app-service)時，發佈作業會自動收集靜態檔案。

    ![主控台](media/template-django-console-collect-static.png)

- **驗證**：執行 `manage.py validate`，這會報告由 `settings.py` 中的 `INSTALLED_APPS` 所指定之已安裝模組中的所有驗證錯誤：

    ![主控台](media/template-django-console-validate.png)
