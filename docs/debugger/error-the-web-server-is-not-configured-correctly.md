---
title: 'Errore: Il server web non è configurato correttamente | Microsoft Docs'
ms.date: 09/20/2017
ms.topic: troubleshooting
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fc0c61b766b6f93fd1321b15861000d7c628f124
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62850408"
---
# <a name="error-the-web-server-is-not-configured-correctly"></a>Errore: Il server Web non è configurato in modo corretto

Dopo aver valutato i passaggi descritti in questa sezione per risolvere il problema e prima di riprovare a eseguire il debug, è necessario anche reimpostare IIS. È possibile farlo aprendo un prompt dei comandi di amministratore e digitando `iisreset`.

Eseguire questi passaggi per risolvere il problema:

1. Se l'app web ospitata nel server è configurato come una build di rilascio, pubblicare di nuovo come una build di Debug e verificare che il file Web. config contenga `debug=true` nell'elemento di compilazione. Reimpostare IIS, quindi riprovare.

    Ad esempio, se si usa un profilo di pubblicazione per una build di rilascio, modificarla su Debug e pubblicare di nuovo. In caso contrario, l'attributo di debug verrà impostato `false` quando si pubblica.

2. (IIS) Verificare che il percorso fisico sia corretto. In IIS, questa impostazione in disponibile **impostazioni di base > percorso fisico** (o **impostazioni avanzate** nelle versioni precedenti di IIS).

    Il percorso fisico potrebbe essere inesatti se l'applicazione web è stato copiato in un computer diverso, rinominato manualmente o spostata. Reimpostare IIS, quindi riprovare.

3. Se si esegue il debug in locale in Visual Studio, verificare che il server corretto sia selezionato nelle proprietà. (Aprire **proprietà > Web > server** oppure **proprietà > eseguire il Debug** a seconda del tipo di progetto. Per un progetto di Web Form, aprire **pagine delle proprietà > Opzioni di avvio > Server**).

    Se si usa un server (personalizzato) esterno, ad esempio IIS, l'URL deve essere corretta. In caso contrario, selezionare IIS Express e riprovare.

4. (IIS) Assicurarsi che la versione corretta di ASP.NET sia installata nel server.

    Le versioni non corrispondenti di ASP.NET in IIS e nel progetto di Visual Studio possono causare questo problema. Si potrebbe essere necessario impostare la versione di framework nel file Web. config. Per installare ASP.NET in IIS, usare il [installazione guidata piattaforma Web (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx). Vedere anche [IIS 8.0 Using ASP.NET 3.5 e ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) o, per ASP.NET Core [Host in Windows con IIS](https://docs.asp.net/en/latest/publishing/iis.html).

4. Se il `maxConnection` limite in IIS è troppo basso e si dispone di un numero eccessivo di connessioni, potrebbe essere necessario [aumentare il limite di connessione](/iis/configuration/system.applicationhost/sites/sitedefaults/limits).

## <a name="see-also"></a>Vedere anche
- [Debug remoto di ASP.NET in un computer remoto con IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)
- [Debug di applicazioni Web: Errori e risoluzione dei problemi](../debugger/debugging-web-applications-errors-and-troubleshooting.md)