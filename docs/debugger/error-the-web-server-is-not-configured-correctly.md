---
title: 'Errore: il server Web non è configurato correttamente | Microsoft Docs'
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 711297ef00c064c482ed3a86b896566b6e019534
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85460325"
---
# <a name="error-the-web-server-is-not-configured-correctly"></a>Errore: il server Web non è configurato in modo corretto

Dopo aver eseguito i passaggi descritti qui per risolvere il problema e prima di riprovare a eseguire il debug, potrebbe essere necessario reimpostare IIS. A tale scopo, aprire un prompt dei comandi dell'amministratore e digitare `iisreset` .

Per risolvere il problema, seguire questa procedura:

1. Se l'app Web ospitata nel server è configurata come build di rilascio, viene ripubblicata come build di debug e verifica che il file web.config contenuto `debug=true` nell'elemento di compilazione. Ripristinare IIS e riprovare.

    Se ad esempio si usa un profilo di pubblicazione per una build di rilascio, modificarlo in debug e ripubblicazione. In caso contrario, l'attributo debug verrà impostato su `false` quando si esegue la pubblicazione.

2. IIS Verificare che il percorso fisico sia corretto. In IIS è possibile trovare questa impostazione in **impostazioni di base > percorso fisico** (o **Impostazioni avanzate** nelle versioni precedenti di IIS).

    Il percorso fisico potrebbe non essere corretto se l'applicazione Web è stata copiata in un computer diverso, rinominata o spostata manualmente. Ripristinare IIS e riprovare.

3. Se si esegue il debug in locale in Visual Studio, verificare che nelle proprietà sia selezionato il server corretto. (Aprire **proprietà > server > Web** o **Proprietà > eseguire il debug** a seconda del tipo di progetto. Per un progetto Web Form, aprire **pagine delle proprietà > opzioni di avvio > server**).

    Se si utilizza un server esterno (personalizzato), ad esempio IIS, l'URL deve essere corretto. In caso contrario, selezionare IIS Express e riprovare.

4. IIS Verificare che nel server sia installata la versione corretta di ASP.NET.

    La mancata corrispondenza delle versioni di ASP.NET in IIS e nel progetto di Visual Studio può causare questo problema. Potrebbe essere necessario impostare la versione del Framework in web.config. Per installare ASP.NET in IIS, usare l' [installazione guidata piattaforma Web (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx). Vedere anche [iis 8,0 con ASP.NET 3,5 e ASP.NET 4,5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) o, per ASP.NET Core, [host in Windows con IIS](https://docs.asp.net/en/latest/publishing/iis.html).

4. Se il `maxConnection` limite in IIS è troppo basso e si dispone di un numero eccessivo di connessioni, potrebbe essere necessario [aumentare il limite di connessione](/iis/configuration/system.applicationhost/sites/sitedefaults/limits).

## <a name="see-also"></a>Vedere anche
- [Debug remoto di ASP.NET in un computer IIS remoto](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)
- [Debug di applicazioni Web: errori e risoluzione dei problemi](../debugger/debugging-web-applications-errors-and-troubleshooting.md)