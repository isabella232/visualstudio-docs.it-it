---
title: Autorizzazione del proxy richiesta | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: troubleshooting
ms.assetid: c2d24ae1-9902-460e-b72a-0299eed9ee82
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 520c31f671aee05663a5471aca05cfe06313b168
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2019
ms.locfileid: "65847025"
---
# <a name="proxy-authorization-required"></a>Autorizzazione del proxy richiesta
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Il **autorizzazione del Proxy richiesta** generalmente errore si verifica quando gli utenti sono connessi alle risorse di Visual Studio online tramite un server proxy e il server proxy blocca le chiamate.

Per correggere questo errore, provare a eseguire uno o più delle operazioni seguenti:

- Riavviare Visual Studio. Verrà visualizzata una finestra di dialogo di autenticazione del proxy. Immettere le credenziali nella finestra di dialogo.

- Se il passaggio precedente non risolve il problema, è possibile che il server proxy usato non richiede le credenziali per gli indirizzi http://go.microsoft.com mentre le richiede per gli indirizzi *.visualStudio.com. Per questi server, è necessario aggiungere gli URL seguenti all'elenco consentiti per sbloccare gli scenari di accesso tutte in Visual Studio:

    - *.windows.net

    - *.microsoftonline.com

    - *.visualstudio.com

    - *.microsoft.com

    - *.live.com

- È possibile rimuovere il http://go.microsoft.com indirizzo dall'elenco di elementi consentiti in modo che la finestra di dialogo di autenticazione proxy per entrambi i http://go.microsoft.com indirizzo e l'endpoint server quando Visual Studio viene riavviato.

- Se si desidera usare le credenziali predefinite con il proxy, eseguire le operazioni seguenti:

   1. Trovare devenv.exe.config (file di configurazione devenv.exe) in: **%ProgramFiles%\Microsoft Visual Studio 14.0\Common7\IDE** (o **%ProgramFiles(x86)%\Microsoft Visual Studio 14.0\Common7\IDE**).

   2. Nel file di configurazione trovare il blocco `<system.net>` e aggiungere il codice seguente:

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress=" HYPERLINK "http://<yourproxy:port#" http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      Inserire l'indirizzo del proxy corretto per la rete in `proxyaddress="<http://<yourproxy:port#>`.

- Seguire le istruzioni in [questo post di blog](http://blogs.msdn.com/b/rido/archive/2010/05/06/how-to-connect-to-tfs-through-authenticated-web-proxy.aspx) per aggiungere il codice che consente di usare il proxy.
