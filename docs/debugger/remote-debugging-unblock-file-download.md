---
title: Sbloccare il download di Remote Tools
ms.date: 07/19/2018
ms.topic: troubleshooting
helpviewer_keywords:
- remote debugging, unblock download
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8a243033bf5831952d83fdf688302651e02b76b7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62903024"
---
# <a name="how-to-unblock-the-download-of-the-remote-tools-on-windows-server"></a>Procedura: sbloccare il download di Remote Tools in Windows Server

Le impostazioni di sicurezza predefinite in Internet Explorer in Windows Server possono richiedere molto tempo per scaricare componenti come Remote Tools.

* La configurazione della sicurezza avanzata è abilitata in Internet Explorer, che impedisce l'apertura di siti Web e l'accesso alle risorse Web, a meno che il dominio contenente la risorsa non sia consentito in modo esplicito (ovvero attendibile). Sebbene sia possibile disabilitare questa impostazione, questa impostazione non è consigliata perché può presentare un rischio per la sicurezza.

* In Windows Server 2016, un'impostazione predefinita in **Opzioni Internet**  >  **sicurezza**  >  **Internet**  >  **download livello personalizzato**Internet  >  **Downloads** Disabilita anche i download di file. Se si sceglie di scaricare Remote Tools direttamente su Windows Server, è necessario abilitare il download del file.

Per scaricare gli strumenti in Windows Server, è consigliabile eseguire una delle operazioni seguenti:

* Scaricare Remote Tools in un computer diverso, ad esempio quello che esegue Visual Studio, quindi copiare il file con *estensione exe* in Windows Server.

* Eseguire il debugger remoto [da una condivisione file](../debugger/remote-debugging.md#fileshare_msvsmon) nel computer che esegue Visual Studio.

* Scaricare Remote Tools direttamente su Windows Server e accettare i prompt per aggiungere siti attendibili. I siti Web moderni includono spesso molte risorse di terze parti, pertanto questo può causare numerose richieste. Inoltre, potrebbe essere necessario aggiungere manualmente eventuali collegamenti reindirizzati. È possibile scegliere di aggiungere alcuni dei siti attendibili prima di iniziare il download. Passare a **Opzioni Internet > sicurezza > siti attendibili > siti** e aggiungere i siti seguenti.

  * visualstudio.microsoft.com
  * download.visualstudio.microsoft.com
  * about:blank

  Per le versioni precedenti del debugger in my.visualstudio.com, aggiungere questi siti aggiuntivi per assicurarsi che l'accesso venga eseguito correttamente:

  * microsoft.com
  * go.microsoft.com
  * download.microsoft.com
  * my.visualstudio.com
  * login.microsoftonline.com
  * login.live.com
  * secure.aadcdn.microsoftonline-p.com
  * msft.sts.microsoft.com
  * auth.gfx.ms
  * app.vssps.visualstudio.com
  * vlscppe.microsoft.com
  * query.prod.cms.rt.microsoft.com

    Se si sceglie di aggiungere questi domini durante il download di Remote Tools, scegliere **Aggiungi** quando richiesto.

    ![Finestra di dialogo contenuto bloccato](../debugger/media/remotedbg-blocked-content.png)

    Quando si Scarica il software, si ottengono richieste aggiuntive per concedere l'autorizzazione per caricare vari script e risorse del sito Web. In my.visualstudio.com è consigliabile aggiungere i domini aggiuntivi per assicurarsi che l'accesso abbia esito positivo.