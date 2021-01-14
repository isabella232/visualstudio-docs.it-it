---
title: Sbloccare il download di Remote Tools
description: Sbloccare il download di Remote Tools in Windows Server, che può richiedere molto tempo a causa delle impostazioni di sicurezza predefinite di IE.
ms.custom: SEO-VS-2020
ms.date: 07/19/2018
ms.topic: troubleshooting
helpviewer_keywords:
- remote debugging, unblock download
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 54d85ee7df7f4038cc78b10f83be79e524d3bfd2
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205645"
---
# <a name="how-to-unblock-the-download-of-the-remote-tools-on-windows-server"></a>Procedura: sbloccare il download di Remote Tools in Windows Server

Le impostazioni di sicurezza predefinite in Internet Explorer in Windows Server possono richiedere molto tempo per scaricare componenti come Remote Tools.

* La configurazione della sicurezza avanzata è abilitata in Internet Explorer, che impedisce l'apertura di siti Web e l'accesso alle risorse Web, a meno che il dominio contenente la risorsa non sia consentito in modo esplicito (ovvero attendibile). Sebbene sia possibile disabilitare questa impostazione, non è consigliabile perché può presentare un rischio per la sicurezza.

* In Windows Server 2016, un'impostazione predefinita in **Opzioni Internet**  >  **sicurezza**  >    >  **download livello personalizzato** Internet  >   Disabilita anche i download di file. Se si sceglie di scaricare Remote Tools direttamente su Windows Server, è necessario abilitare il download del file.

Per scaricare gli strumenti in Windows Server, è consigliabile eseguire una delle azioni seguenti:

* Scaricare Remote Tools in un computer diverso, ad esempio quello che esegue Visual Studio, quindi copiare il file con *estensione exe* in Windows Server.

* Eseguire il debugger remoto [da una condivisione file](../debugger/remote-debugging.md#fileshare_msvsmon) nel computer che esegue Visual Studio.

* Scaricare Remote Tools direttamente su Windows Server e accettare i prompt per aggiungere siti attendibili. I siti Web moderni includono spesso molte risorse di terze parti, che possono comportare numerose richieste. Inoltre, potrebbe essere necessario aggiungere manualmente eventuali collegamenti reindirizzati. È possibile scegliere di aggiungere alcuni dei siti attendibili prima di iniziare il download. Passare a **Opzioni Internet > sicurezza > siti attendibili > siti** e aggiungere i siti seguenti.

  * visualstudio.microsoft.com
  * download.visualstudio.microsoft.com
  * about:blank

  Per le versioni precedenti del debugger in my.visualstudio.com, aggiungere gli altri siti per assicurarsi che l'accesso venga eseguito correttamente:

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

    Quando si Scarica il software, si ottengono più richieste di concessione dell'autorizzazione per caricare diversi script e risorse del sito Web. In my.visualstudio.com è consigliabile aggiungere i domini aggiuntivi per assicurarsi che l'accesso abbia esito positivo.