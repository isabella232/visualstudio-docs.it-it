---
title: Risoluzione dei problemi correlati alla rete o al proxy
description: Trovare soluzioni per gli errori correlati alla rete o al proxy che si riscontrano quando si installa o si usa Visual Studio protetto da un firewall o un server proxy.
ms.date: 10/29/2019
ms.topic: troubleshooting
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
- list of domains, locations, URLs, Visual Studio
- proxy errors, Visual Studio
ms.assetid: ''
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 5e7d54b4e7777b3569031e96760699e7c075245f
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306826"
---
# <a name="troubleshoot-network-related-errors-when-you-install-or-use-visual-studio"></a>Risolvere gli errori relativi alla rete quando si installa o si usa Visual Studio

Esistono soluzioni per la maggiore parte degli errori tipici correlati alla rete o al proxy che si riscontrano quando si installa o si usa Visual Studio protetto da un firewall o un server proxy.

## <a name="error-proxy-authorization-required"></a>Errore: "Autorizzazione del proxy richiesta"

Generalmente questo errore si verifica quando gli utenti sono connessi a Internet tramite un server proxy e quest'ultimo blocca le chiamate di Visual Studio ad alcune risorse di rete.

### <a name="to-fix-this-proxy-error"></a>Per correggere l'errore del proxy

- Riavviare Visual Studio. Verrà visualizzata una finestra di dialogo di autenticazione del proxy. Immettere le credenziali quando richiesto nella finestra di dialogo.

- Se il riavvio di Visual Studio non risolve il problema, è possibile che il server proxy usato non richieda le credenziali per gli indirizzi http:&#47;&#47;go.microsoft.com, ma le richieda per gli indirizzi &#42;.visualStudio.microsoft.com. Per questi server, valutare la possibilità di aggiungere gli URL seguenti a un elenco di indirizzi consentiti per sbloccare tutti gli scenari di accesso in Visual Studio:

  - &#42;.windows.net

  - &#42;.microsoftonline.com

  - &#42;.visualstudio.microsoft.com

  - &#42;.microsoft.com

  - &#42;.live.com

- In caso contrario, è possibile rimuovere l'indirizzo http:&#47;&#47;go.microsoft.com dall'elenco di indirizzi consentiti in modo che al riavvio di Visual Studio la finestra di dialogo di autenticazione del proxy venga visualizzata sia per l'indirizzo http:&#47;&#47;go.microsoft.com sia per gli endpoint server.

  -OPPURE-

- Se si vogliono usare le credenziali predefinite con il proxy, è possibile eseguire le azioni seguenti:

::: moniker range="vs-2017"

  1. Individuare **devenv.exe.config** (il file di configurazione di devenv.exe) in: **%Programmi%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE** o **%Programmi(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE**.

  2. Nel file di configurazione trovare il blocco `<system.net>` e quindi aggiungere il codice seguente:

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress="http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      È necessario inserire l'indirizzo del proxy corretto per la rete in `proxyaddress="<http://<yourproxy:port#>`.

     > [!NOTE]
     > Per altre informazioni, vedere le pagine Elemento [ &lt; defaultProxy &gt; (impostazioni di rete)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings/) e [ &lt; Elemento proxy &gt; (impostazioni di rete).](/dotnet/framework/configure-apps/file-schema/network/proxy-element-network-settings)

::: moniker-end

::: moniker range=">=vs-2019"

  1. Individuare **devenv.exe.config** (il file di configurazione di devenv.exe) in: **%Programmi%\Microsoft Visual Studio\2019\Enterprise\Common7\IDE** o **%Programmi(x86)%\Microsoft Visual Studio\2019\Enterprise\Common7\IDE**.

  2. Nel file di configurazione trovare il blocco `<system.net>` e quindi aggiungere il codice seguente:

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress="http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      È necessario inserire l'indirizzo del proxy corretto per la rete in `proxyaddress="<http://<yourproxy:port#>`.

     > [!NOTE]
     > Per altre informazioni, vedere le pagine Elemento [ &lt; defaultProxy &gt; (impostazioni di rete)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings/) e [ &lt; Elemento proxy &gt; (impostazioni di rete).](/dotnet/framework/configure-apps/file-schema/network/proxy-element-network-settings)

::: moniker-end

## <a name="error-disconnected-from-visual-studio-when-attempting-to-report-a-problem"></a>Errore: "Disconnesso da Visual Studio" durante il tentativo di segnalare un problema

Questo errore si verifica in genere quando un utente è connesso a Internet tramite un server proxy e il server proxy blocca le chiamate Visual Studio ad alcune risorse di rete.

### <a name="to-fix-this-proxy-error"></a>Per correggere l'errore del proxy

1. Trovare **feedback.exe.config** (il file di configurazione feedback.exe) in: **%ProgramFiles(x86)%\Microsoft Visual Studio\Installer** o **%ProgramFiles%\Microsoft Visual Studio\Installer**.

2. Nel file di configurazione verificare se è presente il codice seguente. Se il codice non è presente, aggiungerlo prima dell'ultima `</configuration>` riga.

   ```xml
   <system.net>
       <defaultProxy useDefaultCredentials="true" />
   </system.net>
   ```

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

- &#42;.visualstudio.microsoft.com

- cdn.vsassets.io (host di contenuti della rete CDN)

- &#42;. gallerycdn.vsassets.io (estensioni host di Azure DevOps Services)

- static2.sharepointonline.com (host di risorse usate da Visual Studio nel kit Office UI Fabric, ad esempio i tipi di carattere)

- &#42;.nuget.org (per le connessioni NuGet)

  > [!NOTE]
  > Gli URL di server NuGet di proprietà privata potrebbero non essere inclusi in questo elenco. È possibile controllare i server NuGet in uso in %APPData%\Nuget\NuGet.Config.

## <a name="error-failed-to-parse-id-from-parent-process"></a>Errore: "Impossibile analizzare l'ID dal processo padre"

Questo messaggio di errore può essere visualizzato quando si usa un programma Visual Studio bootstrap e un response.jssu un file in un'unità di rete. L'origine dell'errore è controllo dell'account utente in Windows.

Ecco perché può verificarsi questo errore: un'unità di rete mappata o una condivisione [UNC](/dotnet/standard/io/file-path-formats#unc-paths) è collegata al token di accesso di un utente. Quando controllo dell'account utente è abilitato,  vengono creati due [token di](/windows/win32/secauthz/access-tokens) accesso utente: uno con accesso amministratore e uno *senza* accesso come amministratore. Quando viene creata un'unità di rete o una condivisione, viene collegato il token di accesso corrente dell'utente. Poiché il programma di avvio automatico deve essere eseguito come amministratore, non sarà in grado di accedere all'unità di rete o alla condivisione se l'unità o la condivisione non è collegata a un token di accesso utente con accesso come amministratore.

### <a name="to-fix-this-error"></a>Per correggere l'errore

È possibile usare il comando `net use` oppure modificare l'impostazione di controllo dell'Criteri di gruppo utente. Per altre informazioni su queste soluzioni alternative e su come implementarle, vedere gli articoli del supporto tecnico Microsoft seguenti:

* [Le unità mappate non sono disponibili da un prompt con privilegi elevati quando Controllo dell'account utente è configurato su "Richiedi credenziali" in Windows](https://support.microsoft.com/help/3035277/mapped-drives-are-not-available-from-an-elevated-prompt-when-uac-is-co)
* [I programmi potrebbero non essere in grado di accedere ad alcuni percorsi di rete dopo l'attivazione di Controllo account utente nei sistemi operativi Windows](https://support.microsoft.com/en-us/help/937624/programs-may-be-unable-to-access-some-network-locations-after-you-turn)

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedi anche

* [Installare e usare Visual Studio protetto da un firewall o un server proxy](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)
* [Guida di Visual Studio Administrator](visual-studio-administrator-guide.md)
* [Installa Visual Studio](install-visual-studio.md)
