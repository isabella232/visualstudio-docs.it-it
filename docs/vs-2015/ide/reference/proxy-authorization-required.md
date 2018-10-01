---
title: Autorizzazione del proxy richiesta | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c2d24ae1-9902-460e-b72a-0299eed9ee82
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 855fa85a8135ceac60f262fc5510fad4aa34b006
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47526959"
---
# <a name="proxy-authorization-required"></a>Autorizzazione del proxy richiesta
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [richiesta autorizzazione Proxy](https://docs.microsoft.com/visualstudio/ide/reference/proxy-authorization-required).  
  
  
Generalmente questo errore si verifica quando gli utenti sono connessi a Visual Studio Online tramite un server proxy e il server proxy blocca le chiamate. Visual Studio Online viene usato per mantenere l'utente connesso all'IDE.  
  
## <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Riavviare Visual Studio. Verrà visualizzata una finestra di dialogo di autenticazione del proxy. Immettere le credenziali nella finestra di dialogo.  
  
-   Se il passaggio precedente non risolve il problema, è possibile che il server proxy usato non richiede le credenziali per gli indirizzi http://go.microsoft.com mentre le richiede per gli indirizzi *.visualStudio.com. Per questi server, è necessario aggiungere l'elenco seguente nell'elenco degli elementi consentiti per sbloccare tutti gli scenari di accesso in Visual Studio:  
  
    -   *.windows.net  
  
    -   *.microsoftonline.com  
  
    -   *.visualstudio.com  
  
    -   *.microsoft.com  
  
    -   *.live.com  
  
-   In caso contrario, è possibile rimuovere il http://go.microsoft.com indirizzo dall'elenco elementi consentiti in modo che la finestra di dialogo di autenticazione proxy per entrambi i http://go.microsoft.com indirizzo e l'endpoint server quando Visual Studio viene riavviato.  
  
-   OR  
  
-   Se si desidera usare le credenziali predefinite con il proxy, è possibile eseguire le operazioni seguenti:  
  
    1.  Trovare devenv.exe.config (file di configurazione devenv.exe) in: **%ProgramFiles%\Microsoft Visual Studio 14.0\Common7\IDE** (o **%ProgramFiles(x86)%\Microsoft Visual Studio 14.0\Common7\IDE**).  
  
    2.  Nel file di configurazione trovare il blocco `<system.net>` e aggiungere il codice seguente:  
  
        ```xml  
        <defaultProxy enabled="true" useDefaultCredentials="true">  
            <proxy bypassonlocal="True" proxyaddress=" HYPERLINK "http://<yourproxy:port#" http://<yourproxy:port#>"/>  
        </defaultProxy>  
  
        ```  
  
         È necessario inserire l'indirizzo del proxy corretto per la rete in `proxyaddress="<http://<yourproxy:port#>`.  
  
-   OR  
  
-   Si possono anche seguire le istruzioni in [questo post](http://blogs.msdn.com/b/rido/archive/2010/05/06/how-to-connect-to-tfs-through-authenticated-web-proxy.aspx) per aggiungere il codice che consente di usare il proxy.



