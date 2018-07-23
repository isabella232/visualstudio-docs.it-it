---
title: 'Procedura: rispondere per il debug Just-In-Time | Microsoft Docs'
ms.custom: ''
ms.date: 05/23/17
ms.technology: vs-ide-debug
ms.topic: troubleshooting
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fd3f565d8bb58ae290b0b569bb61d4cb57e8edaa
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/20/2018
ms.locfileid: "39179775"
---
# <a name="how-to-respond-to-the-just-in-time-debugger"></a>Procedura: rispondere per il debug Just-In-Time

L'attività da eseguire quando viene visualizzato il Just-in-Time nella finestra di dialogo debugger dipendono da ciò che si sta tentando di eseguire:

#### <a name="if-you-want-to-fix-or-debug-the-error-visual-studio-users"></a>Se si desidera risolvere o eseguire il debug dell'errore (utenti di Visual Studio)

- È necessario disporre [installato Visual Studio](http://visualstudio.microsoft.com) per visualizzare le informazioni dettagliate sull'errore e provare a eseguirne il debug. Per altre informazioni, vedere [eseguire il Debug con il Debugger JIT](../debugger/debug-using-the-just-in-time-debugger.md). Se è Impossibile risolvere l'errore e correggere l'app, contattare il proprietario dell'app per risolvere l'errore.

#### <a name="if-you-want-to-prevent-the-just-in-time-debugger-dialog-box-from-appearing"></a>Se si desidera evitare che la finestra di dialogo Debugger JIT

È possibile intervenire per evitare il Just-in-Time finestra di dialogo Debugger venga visualizzato. Se l'app gestisce l'errore, è possibile eseguire normalmente l'app.

1. (App web) Se si sta provando a eseguire un'app web, è possibile disabilitare il debug degli script.

    Per Internet Explorer o Microsoft Edge, disabilitare il debug degli script nella finestra di dialogo Opzioni Internet. È possibile accedere a queste impostazioni dal **Pannello di controllo** > **rete e Internet** > **Opzioni Internet** (i passaggi esatti dipendono le versione di Windows e browser).

    ![JITInternetOptions](../debugger/media/jitinternetoptions.png "JITInternetOptions")

    Riaprire la pagina web in cui è stato trovato l'errore. Se la modifica di questa impostazione non risolve il problema, contattare il proprietario dell'app web per risolvere il problema.

3. (Utenti di visual Studio) Se si è installato Visual Studio (o se si dispone di installato in precedenza e averla rimossa), [Just-in-Time di disabilitare il debug](../debugger/debug-using-the-just-in-time-debugger.md) e provare a eseguire nuovamente l'app.

    > [!IMPORTANT]
    > Se si disabilita Just-in-Time di debug e l'app rileva un'eccezione non gestita (errore), possano vedere invece una finestra di dialogo di errore standard o l'app verrà arrestarsi in modo anomalo o un blocco. L'app non verrà eseguite normalmente fino a quando non viene risolto l'errore (per utente o il proprietario dell'app).

2. (ASP.NET e IIS) Se si ospita un'app Web ASP.NET in IIS, disabilitare il debug sul lato server.

    In Gestione IIS, fare clic sul nodo del server e scegliere **passa a visualizzazione funzionalità**. Sotto la sezione ASP.NET, scegliere **compilazione con .NET** e quindi assicurarsi che si sceglie **False** come il comportamento di Debug (i passaggi sono diversi nelle versioni precedenti di IIS).

## <a name="see-also"></a>Vedere anche
 [Debugger Basics](../debugger/getting-started-with-the-debugger.md) (Nozioni di base sul debugger)
