---
description: Dopo aver seguito i passaggi descritti qui per risolvere il problema e prima di riprovare a eseguire il debug, potrebbe anche essere necessario reimpostare IIS.
title: Il server Web non è configurato correttamente | Microsoft Docs
ms.date: 09/20/2017
ms.topic: error-reference
f1_keywords:
- vs.debug.remote.projnotconfigured
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 288210ac250be0dd92ec409a4b1d45075c0baf2e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122134064"
---
# <a name="error-the-web-server-is-not-configured-correctly"></a>Errore: il server Web non è configurato in modo corretto

Dopo aver seguito i passaggi descritti qui per risolvere il problema e prima di riprovare a eseguire il debug, potrebbe anche essere necessario reimpostare IIS. A tale scopo, aprire un prompt dei comandi amministratore e digitare `iisreset` .

Per risolvere il problema, seguire questa procedura:

1. Se l'app Web ospitata nel server è configurata come build di rilascio, ripubblicare come build di debug e verificare che il file web.config contenga nell'elemento `debug=true` di compilazione. Reimpostare IIS e riprovare.

    Ad esempio, se si usa un profilo di pubblicazione per una build di rilascio, modificarlo in Debug e ripubblicare. In caso contrario, l'attributo debug verrà impostato su `false` durante la pubblicazione.

2. (IIS) Verificare che il percorso fisico sia corretto. In IIS questa impostazione è presente in Basic **Impostazioni > Physical Path** (Percorso fisico di base) (o Advanced **Impostazioni** nelle versioni precedenti di IIS).

    Il percorso fisico potrebbe non essere corretto se l'applicazione Web è stata copiata in un computer diverso, rinominata manualmente o spostata. Reimpostare IIS e riprovare.

3. Se si esegue il debug in Visual Studio, verificare che nelle proprietà sia selezionato il server corretto. Aprire **Proprietà > server web > o** Proprietà > **debug** a seconda del tipo di progetto. Per un progetto Web Forms, aprire Pagine **delle proprietà > opzioni di avvio > Server**).

    Se si usa un server esterno (personalizzato), ad esempio IIS, l'URL deve essere corretto. In caso contrario, selezionare IIS Express e riprovare.

4. (IIS) Verificare che nel server sia installata ASP.NET versione corretta di .

    Le versioni non corrispondenti ASP.NET in IIS e nel progetto Visual Studio possono causare questo problema. Potrebbe essere necessario impostare la versione del framework in web.config. Per installare ASP.NET in IIS, usare Installazione [guidata piattaforma Web (WebPI).](https://www.microsoft.com/web/downloads/platform.aspx) Vedere anche [IIS 8.0 Using ASP.NET 3.5 and ASP.NET 4.5 (Iis 8.0 Using ASP.NET 3.5 and ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) or, for ASP.NET Core, Host on Windows with IIS ( Host in Windows [con IIS).](https://docs.asp.net/en/latest/publishing/iis.html)

4. Se il limite in IIS è troppo basso e sono presenti troppe connessioni, potrebbe essere `maxConnection` necessario aumentare il limite di [connessione](/iis/configuration/system.applicationhost/sites/sitedefaults/limits).

## <a name="see-also"></a>Vedi anche
- [Debug remoto di ASP.NET in un computer IIS remoto](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)
- [Debug di applicazioni Web: errori e risoluzione dei problemi](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
