---
title: "使用適用於 Visual Studio 的 Python 工具進行跨平台遠端偵錯 | Microsoft Docs"
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa667357-763f-4ce6-8e47-48f9337658a8
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
translationtype: Human Translation
ms.sourcegitcommit: 7d726441c2d6953bd7b50451bec7fff05d5d71b0
ms.openlocfilehash: 7634da4bdc2b0186f410acb4eaf57a70ddea3e91
ms.lasthandoff: 03/10/2017

---

# <a name="remotely-debugging-python-code"></a>對 Python 程式碼進行遠端偵錯

適用於 Visual Studio 的 Python 工具 (PTVS) 可在 Windows 電腦的本機或遠端啟動 Python 應用程式並進行偵錯 (請參閱[遠端偵錯](../debugger/remote-debugging.md))。 它也可在其他作業系統、裝置或使用 [ptvsd 程式庫](https://pypi.python.org/pypi/ptvsd)的 Python 實作 (不同於 CPython) 上進行遠端偵錯。

使用 ptvsd 時，進行偵錯的 Python 程式碼會裝載 Visual Studio 可以附加到的偵錯伺服器。 這需要稍微修改您的程式碼以匯入和啟用伺服器，並可能需要遠端電腦上的網路或防火牆組態允許 TCP 連線。

如需遠端偵錯的簡介，請參閱[深入探討︰跨平台遠端偵錯 (英文)](https://youtu.be/y1Qq7BrV6Cc) (youtube.com，6 分 22 秒)。

> [!VIDEO https://www.youtube.com/embed/y1Qq7BrV6Cc]

## <a name="preparing-the-script-for-debugging"></a>準備偵錯指令碼

1. 在遠端電腦上使用下列程式碼建立 Python 檔案︰

  ```python
  import random

  guesses_made = 0
  name = raw_input('Hello! What is your name?\n')
  number = random.randint(1, 20)
  print 'Well, {0}, I am thinking of a number between 1 and 20.'.format(name)

  while guesses_made < 6:
      guess = int(raw_input('Take a guess: '))
      guesses_made += 1
      if guess < number:
          print 'Your guess is too low.'
      if guess > number:
          print 'Your guess is too high.'
      if guess == number:
          break
  if guess == number:
      print 'Good job, {0}! You guessed my number in {1} guesses!'.format(name, guesses_made)
  else:
      print 'Nope. The number I was thinking of was {0}'.format(number)
  ```
 
1. 使用 `pip install ptvsd`，將 `ptvsd` 封裝安裝到您的環境。

1. 盡早在指令碼中的其他程式碼之前加入下列程式碼，以啟用遠端偵錯。 (雖然不是嚴格要求，但在呼叫 `enable_attach` 函式前，無法對繁衍 (Spawn) 的任何背景執行緒進行偵錯。)

   ```python
   import ptvsd
   ptvsd.enable_attach(secret='my_secret')
   ```

   傳遞給 `enable_attach` 的 `secret` 參數用來限制執行中指令碼的存取。 在附加時，您必須在 Visual Studio 中指定它，否則將拒絕連線。 若要停用它並允許任何人連線，請使用 `enable_attach(secret=None)`。

1. 在遠端電腦上儲存檔案並啟動指令碼。 請注意，`enable_attach` 的呼叫會在背景執行，並等待連入連線。 如有需要，可以在 `enable_attach` 之後呼叫 `wait_for_attach` 函式來封鎖程式，直到偵錯工具附加為止。

除了 `enable_attach` 和`wait_for_attach` 以外，ptvsd 也提供協助程式函式 `break_into_debugger`，其在偵錯工具附加時可做為程式設計的中斷點。 還有一個 `is_attached` 函式會在偵錯工具附加時傳回 `True` (請注意，在呼叫其他 `ptvsd` 之前，不需檢查這個結果)。

## <a name="attaching-remotely-from-python-tools"></a>從 Python 工具遠端附加

在這些步驟中，我們將設定中斷點以停止遠端程序。

1. 在本機電腦上建立遠端檔案的複本，然後在 Visual Studio 中開啟它。 檔案所在位置並不重要，但其名稱應符合將附加到的遠端電腦上的指令碼名稱。

1. 選取 [偵錯 (Debug)] > [附加至處理序 (Attach to Process)] 以開啟 [附加至處理序 (Attach to Process)] 對話方塊。

1. 將 [傳輸 (Transport)] 設為 [Python 遠端偵錯 (Python remote debugging)] 。

1. 在 [限定詞 (Qualifier)] 欄位中輸入遠端電腦的位址，然後按 Enter。 這樣應該會列出該電腦上的可用處理序︰

![輸入限定詞並列出處理序](media/remote-debugging-qualifier.png)

1. 這個階段的錯誤通常是密碼不符、`ptvsd` 版本與 PTVS 使用的不符或無法建立連線。 無法連線的常見原因之一，是遠端電腦的防火牆封鎖偵錯伺服器連接埠 (預設值為 5678) 開啟。 您可以重新設定防火牆，或使用不同的連接埠；後者可透過在 `address` 參數的 `enable_attach` 呼叫中明確地指定它來完成，例如︰

  ```python
  ptvsd.enable_attach(secret = 'my_secret', address = ('0.0.0.0', 8080))
  ```

  位址格式與標準 Python 模組通訊端針對 `AF_INET` 類型的通訊端使用的相同；如需詳細資訊，請參閱其[文件 (英文)](http://docs.python.org/3/library/socket.html#socket-families)。 

1. 當處理序出現在清單時，連按兩下它以進行連接。 Visual Studio 會顯示其偵錯工具，指令碼則持續執行。 針對上述範例指令碼，輸入數字將會叫用中斷點︰

    ![已叫用中斷點](media/remote-debugging-breakpoint-hit.png)

1. 此時您可以使用所有的一般 PTVS 偵錯功能。 

1. 當您停止偵錯時，Visual Studio 會中斷連結您的指令碼，但指令碼將繼續在遠端電腦上執行。 偵錯伺服器也會繼續在其背景執行緒上執行，因此之後您可以使用相同的程序重新附加到處理序。


## <a name="securing-the-debugger-connection-with-ssl"></a>使用 SSL 保護偵錯工具連線

根據預設，與 PTVS 遠端偵錯伺服器的連線未受到任何方式的保護；擁有密碼的所有人都可以連線，並以純文字傳遞所有的資料。 因此，網路上其他人可以窺探資料，或甚至執行攔截式 (MITM) 攻擊。 為避免在透過不安全的網路或網際網路偵錯時發生這種情況，偵錯伺服器支援 SSL。 

若要使用 SSL 保護通道，您將需要 SSL 憑證。 您可以自行產生自我簽署的憑證，如 [Python 標準模組的文件 (英文)`ssl` ](http://docs.python.org/3/library/ssl.html#self-signed-certificates) 所述。 為避免 MITM 攻擊，這類產生的憑證也必須加入到執行 PTVS 的 Windows 電腦上的 CA 根存放區。 這項作業可以使用憑證管理員 (certmgr.msc) 完成，如[如何匯出憑證和/或私密金鑰？(英文)](https://answers.microsoft.com/en-us/windows/forum/windows_10-security/how-do-i-export-certificates-andor-private-keys/7722900a-e848-4076-bc50-9e2f5e3c66ac) 所述。 請注意，您必須有一個匯入用的個別憑證檔案 (不要與私密金鑰合併在一個檔案中)。 

產生及註冊憑證和私密金鑰檔之後，您必須更新指令碼中的 `enable_attach` 呼叫才能使用它們。 這項作業是透過 `certfile` 和 `keyfile` 參數完成，而這些參數對標準 Python 函式 `ssl.wrap_socket` 而言具有相同的意義。 例如，如果憑證檔案的名稱是 `my_cert.cer`，金鑰檔案的名稱是 `my_cert.key`，請使用︰ 

```python
ptvsd.enable_attach(secret='my_secret', certfile='my_cert.cer', keyfile='my_cert.key')
```

附加程序與前述相同，唯一不同的是在 [限定詞 (Qualifier)] 中不使用 `tcp://` 配置，改用 `tcps://`： 

![選擇使用 SSL 進行遠端偵錯傳輸](media/remote-debugging-qualifier-ssl.png)

如果您沒有將憑證加入 CA 根存放區，將會出現警告訊息︰ 

![SSL 憑證警告](media/remote-debugging-ssl-warning.png)

您可以選擇略過此訊息並繼續進行偵錯；通道仍然會加密以防止竊聽，但忽略該警告會導致 MITM 攻擊的可能性。

