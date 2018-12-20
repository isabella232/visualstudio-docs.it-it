---
title: Risoluzione dei problemi correlati alla rete o al proxy
description: Trovare soluzioni per gli errori correlati alla rete o al proxy che si riscontrano quando si installa o si usa Visual Studio protetto da un firewall o un server proxy.
ms.custom: ''
ms.date: 02/12/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: troubleshooting
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
- list of domains, locations, URLs, Visual Studio
- proxy errors, Visual Studio
ms.assetid: ''
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d344682f948421bf6d02ff14d41fa26fec1c3f32
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/07/2018
ms.locfileid: "53047616"
---
# <a name="troubleshooting-network-related-errors-when-you-install-or-use-visual-studio"></a>Risoluzione dei problemi correlati alla rete quando si installa o usa Visual Studio

Esistono soluzioni per la maggiore parte degli errori tipici correlati alla rete o al proxy che si riscontrano quando si installa o si usa Visual Studio protetto da un firewall o un server proxy.

## <a name="error-proxy-authorization-required"></a>Errore: "Necessaria autorizzazione proxy"

Generalmente questo errore si verifica quando gli utenti sono connessi a Internet tramite un server proxy e quest'ultimo blocca le chiamate di Visual Studio ad alcune risorse di rete.

### <a name="to-fix-this-proxy-error"></a>Per correggere l'errore del proxy

- Riavviare Visual Studio. Verrà visualizzata una finestra di dialogo di autenticazione del proxy. Immettere le credenziali quando richiesto nella finestra di dialogo.

- Se il riavvio di Visual Studio non risolve il problema, è possibile che il server proxy usato non richieda le credenziali per gli indirizzi http:&#47;&#47;go.microsoft.com, ma per gli indirizzi &#42;.visualStudio.com. Per questi server, valutare la possibilità di aggiungere gli URL seguenti all'elenco degli elementi consentiti per sbloccare tutti gli scenari di accesso in Visual Studio:

    - &#42;.windows.net

    - &#42;.microsoftonline.com

    - &#42;.visualstudio.com

    - &#42;.microsoft.com

    - &#42;.live.com

- In caso contrario, è possibile rimuovere l'indirizzo http:&#47;&#47;go.microsoft.com dall'elenco degli elementi consentiti in modo che al riavvio di Visual Studio venga visualizzata la finestra di dialogo di autenticazione del proxy per l'indirizzo http:&#47;&#47;go.microsoft.com e gli endpoint server.

    OR

- Se si vogliono usare le credenziali predefinite con il proxy, è possibile eseguire le azioni seguenti:

  1. Individuare **devenv.exe.config** (il file di configurazione di devenv.exe) in: **%Programmi%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE** o **%Programmi(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE**.

  2. Nel file di configurazione trovare il blocco `<system.net>` e quindi aggiungere il codice seguente:

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress=" HYPERLINK "http://<yourproxy:port#>" http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      È necessario inserire l'indirizzo del proxy corretto per la rete in `proxyaddress="<http://<yourproxy:port#>`.

     OR

- È anche possibile seguire le istruzioni nel post di blog [How to connect through an authenticated Web Proxy](https://blogs.msdn.microsoft.com/rido/2010/05/06/how-to-connect-to-tfs-through-authenticated-web-proxy/) (Come connettersi tramite un proxy Web autenticato), che illustra come aggiungere codice che consente di usare il proxy.

## <a name="error-the-underlying-connection-was-closed"></a>Errore: "Connessione sottostante chiusa"

Se si usa Visual Studio in una rete privata con un firewall, Visual Studio potrebbe non essere in grado di connettersi ad alcune risorse di rete. Queste risorse possono includere Azure DevOps Services per l'accesso e la gestione delle licenze, NuGet e servizi di Azure. Se Visual Studio non è in grado di connettersi a una di queste risorse, potrebbe essere visualizzato il messaggio di errore seguente:

  **Connessione sottostante chiusa: Errore imprevisto durante un'operazione di invio**

Visual Studio usa il protocollo Transport Layer Security (TLS) 1.2 per connettersi alle risorse di rete. Le appliance di sicurezza in alcune reti private bloccano determinate connessioni al server quando Visual Studio usa TLS 1.2.

### <a name="to-fix-this-connection-error"></a>Per correggere l'errore di connessione

Abilitare le connessioni per gli URL seguenti:

- https:&#47;&#47;management.core.windows.net

- https:&#47;&#47;app.vssps.visualstudio.com

- https:&#47;&#47;login.microsoftonline.com

- https:&#47;&#47;login.live.com

- https:&#47;&#47;go.microsoft.com

- https:&#47;&#47;graph.windows.net

- https:&#47;&#47;app.vsspsext.visualstudio.com

- &#42;.azurewebsites.net (per le connessioni Azure)

- &#42;.visualstudio.com

- cdn.vsassets.io (host di contenuti della rete CDN)

- &#42;. gallerycdn.vsassets.io (estensioni host di Azure DevOps Services)

- static2.sharepointonline.com (host di risorse usate da Visual Studio nel kit Office UI Fabric, ad esempio i tipi di carattere)

- &#42;.nuget.org (per le connessioni NuGet)

  > [!NOTE]
  > Gli URL di server NuGet di proprietà privata potrebbero non essere inclusi in questo elenco. È possibile controllare i server NuGet in uso in %APPData%\Nuget\NuGet.Config.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedere anche

* [Installare e usare Visual Studio protetto da un firewall o un server proxy](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)
* [Guida di Visual Studio Administrator](visual-studio-administrator-guide.md)
* [Installare Visual Studio 2017](install-visual-studio.md)
