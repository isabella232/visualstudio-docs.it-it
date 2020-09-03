---
title: Autorizzazione del proxy richiesta | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: troubleshooting
ms.assetid: c2d24ae1-9902-460e-b72a-0299eed9ee82
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 848817691d7fae32f2240e3d6cac4451c4ce58c4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "74297814"
---
# <a name="proxy-authorization-required"></a>Autorizzazione del proxy richiesta
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

L'errore di **autorizzazione del proxy richiesto** in genere si verifica quando gli utenti sono connessi alle risorse di Visual Studio online tramite un server proxy e il server proxy blocca le chiamate.

Per correggere l'errore, provare a eseguire uno o più dei passaggi seguenti:

- Riavviare Visual Studio. Verrà visualizzata una finestra di dialogo di autenticazione del proxy. Immettere le credenziali nella finestra di dialogo.

- Se il passaggio precedente non risolve il problema, è possibile che il server proxy usato non richiede le credenziali per gli indirizzi https://go.microsoft.com mentre le richiede per gli indirizzi *.visualStudio.com. Per questi server, è necessario aggiungere gli URL seguenti all'elenco Consenti per sbloccare tutti gli scenari di accesso in Visual Studio:

  - *.windows.net

  - *.microsoftonline.com

  - , ma non per gli indirizzi

  - *.microsoft.com

  - *.live.com

- È possibile rimuovere l' https://go.microsoft.com indirizzo dall'elenco Consenti per visualizzare la finestra di dialogo di autenticazione del proxy per l' https://go.microsoft.com indirizzo e gli endpoint server al riavvio di Visual Studio.

- Se si desidera usare le credenziali predefinite con il proxy, seguire questa procedura:

   1. Trovare devenv.exe.config (file di configurazione devenv.exe) in: **%ProgramFiles%\Microsoft Visual Studio 14.0\Common7\IDE** (o **%ProgramFiles(x86)%\Microsoft Visual Studio 14.0\Common7\IDE**).

   2. Nel file di configurazione trovare il blocco `<system.net>` e aggiungere il codice seguente:

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress=" HYPERLINK "http://<yourproxy:port#" http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      Inserire l'indirizzo proxy corretto per la rete in `proxyaddress="<http://<yourproxy:port#>` .

- Seguire le istruzioni in [questo post di Blog](https://blogs.msdn.microsoft.com/rido/2010/05/06/how-to-connect-to-tfs-through-authenticated-web-proxy/) per aggiungere il codice che consente di usare il proxy.
