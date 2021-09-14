---
title: Sbloccare il download degli strumenti remoti
description: Sbloccare il download degli strumenti remoti in Windows Server, che può richiedere molto tempo a causa delle impostazioni di sicurezza predefinite di IE.
ms.custom: SEO-VS-2020
ms.date: 07/19/2018
ms.topic: troubleshooting
helpviewer_keywords:
- remote debugging, unblock download
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 8ec0b81a6e97faf6a3dae42ea90a66cb62fb57c7
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627894"
---
# <a name="how-to-unblock-the-download-of-the-remote-tools-on-windows-server"></a>Procedura: Sbloccare il download degli strumenti remoti in Windows Server

Le impostazioni di sicurezza predefinite in Internet Explorer in Windows Server possono richiedere molto tempo per scaricare componenti come gli strumenti remoti.

* La configurazione della sicurezza avanzata è abilitata in Internet Explorer, che impedisce l'apertura di siti Web e l'accesso alle risorse Web, a meno che il dominio che contiene la risorsa non sia esplicitamente consentito (ovvero attendibile). Anche se è possibile disabilitare questa impostazione, non è consigliabile perché può presentare un rischio per la sicurezza.

* In Windows Server 2016, un'impostazione predefinita in **Internet Options**  >  **Security**  >  **Internet**  >  **Custom Level**  >  **Downloads** disabilita anche i download di file. Se si sceglie di scaricare gli strumenti remoti direttamente in Windows Server, è necessario abilitare il download dei file.

Per scaricare gli strumenti in Windows Server, è consigliabile eseguire una delle azioni seguenti:

* Scaricare gli strumenti remoti in un computer diverso, ad esempio quello che esegue Visual Studio, quindi copiare il *file*.exein Windows Server.

* Eseguire il debugger remoto [da una condivisione file](../debugger/remote-debugging.md#fileshare_msvsmon) nel computer Visual Studio remoto.

* Scaricare gli strumenti remoti direttamente in Windows Server e accettare le richieste di aggiunta di siti attendibili. I siti Web moderni includono spesso molte risorse di terze parti, che possono comportare molte richieste. Inoltre, potrebbe essere necessario aggiungere manualmente tutti i collegamenti reindirizzati. È possibile scegliere di aggiungere alcuni siti attendibili prima di iniziare il download. Passare a **Opzioni Internet > sicurezza > siti attendibili > siti** e aggiungere i siti seguenti.

  * visualstudio.microsoft.com
  * download.visualstudio.microsoft.com
  * about:blank

  Per le versioni precedenti del debugger in my.visualstudio.com, aggiungere questi altri siti per assicurarsi che l'accesso sia riuscito:

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

    Se si sceglie di aggiungere questi domini durante il download degli strumenti remoti, scegliere **Aggiungi** quando richiesto.

    ![Finestra di dialogo Contenuto bloccato](../debugger/media/remotedbg-blocked-content.png)

    Quando si scarica il software, si ottengono più richieste per concedere l'autorizzazione per caricare vari script e risorse del sito Web. In my.visualstudio.com, è consigliabile aggiungere i domini aggiuntivi per assicurarsi che l'accesso funzioni correttamente.