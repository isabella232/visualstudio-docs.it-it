---
title: Sbloccare il download di remote tools
ms.custom: ''
ms.date: 07/19/2018
ms.technology: vs-ide-debug
ms.topic: troubleshooting
helpviewer_keywords:
- remote debugging, unblock download
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e0586b8f0699ec2eca5843d59df1b6ddd7cecbd3
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/20/2018
ms.locfileid: "39180660"
---
# <a name="how-to-unblock-the-download-of-the-remote-tools-on-windows-server"></a>Procedura: sbloccare il download di remote tools in Windows Server

Le impostazioni di sicurezza predefinite in Internet Explorer in Windows Server possono rendere molto tempo per il download di componenti, ad esempio gli strumenti remoti.

* Sicurezza avanzata è abilitata in Internet Explorer, che impedisce l'apertura di siti Web e l'accesso a risorse web, a meno che il dominio che contiene la risorsa è esplicitamente consentito (vale a dire, attendibili). Anche se è possibile disabilitare questa impostazione, non è consigliabile, perché sia possibile presentare rischi per la sicurezza.

* In Windows Server 2016, un'impostazione predefinita in **Opzioni Internet** > **sicurezza** > **Internet**  >   **Livello personalizzato** > **Scarica** anche disabilita il download di file. Se si sceglie di scaricare gli strumenti remoti direttamente in Windows Server, è necessario abilitare il download di file.

Per scaricare gli strumenti di Windows Server, è consigliabile una delle operazioni seguenti:

* Scaricare remote tools in un computer diverso, ad esempio un in esecuzione Visual Studio e quindi copiare il *.exe* file da Windows Server.

* Eseguire il debugger remoto [da una condivisione file](../debugger/remote-debugging.md#fileshare_msvsmon) nel computer di Visual Studio.

* Scaricare gli strumenti remoti direttamente nel Server di Windows e accettare le richieste per aggiungere siti attendibili. Siti Web moderni includono spesso molte risorse di terze parti, in modo che ciò può comportare numerose richieste. Inoltre, tutti i collegamenti di reindirizzamento potrebbe essere necessario essere aggiunti manualmente. È possibile scegliere di aggiungere alcuni dei siti attendibili prima di iniziare il download. Passare a **Opzioni Internet > sicurezza > siti attendibili > siti** e aggiungere i seguenti siti.

  * VisualStudio.microsoft.com
  * download.visualstudio.microsoft.com
  * sulle: vuoto

  Per le versioni precedenti del debugger in my.visualstudio.com, aggiungere questi siti aggiuntivi per assicurarsi che tale account di accesso ha esito positivo:

  * microsoft.com
  * go.microsoft.com
  * download.microsoft.com
  * My.VisualStudio.com
  * Login.microsoftonline.com
  * Login.Live.com
  * Secure.aadcdn.microsoftonline-p.com
  * msft.STS.microsoft.com
  * auth.GFX.ms
  * app.vssps.visualstudio.com
  * vlscppe.microsoft.com
  * query.Prod.cms.RT.microsoft.com

    Se si sceglie di aggiungere questi domini durante il download di remote tools, scegli **Add** quando richiesto.

    ![Finestra di dialogo contenuto bloccato](../debugger/media/remotedbg-blocked-content.png)

    Quando si scarica il software, si ottengono alcune richieste aggiuntive di concedere autorizzazioni per caricare vari script del sito web e risorse. In my.visualstudio.com, è consigliabile aggiungere i domini aggiuntivi per assicurarsi che tale account di accesso ha esito positivo.