---
title: Controllare gli aggiornamenti delle distribuzioni
description: Informazioni sulla procedura di modifica della posizione in cui Visual Studio cerca un aggiornamento durante l'installazione da una rete.
ms.date: 04/06/2021
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 35C7AB05-07D5-4B38-BCAC-AB88444E7368
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: f15281db55381dadbfd3370eb10a04feeab9c3a5
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307570"
---
# <a name="control-updates-to-network-based-visual-studio-deployments"></a>Controllare gli aggiornamenti delle distribuzioni di rete di Visual Studio

Gli amministratori aziendali spesso creano un layout e lo ospitano in una condivisione file di rete da distribuire agli utenti finali. Questa pagina descrive come configurare correttamente le opzioni di layout di rete.

## <a name="controlling-where-visual-studio-looks-for-updates"></a>Controllo della posizione in cui Visual Studio cerca gli aggiornamenti

**Scenario 1: client installato originariamente da un layout, ma configurato per ricevere aggiornamenti dal percorso di layout di rete o dal Web**

Per impostazione predefinita, Visual Studio continua a cercare gli aggiornamenti online anche se l'installazione è stata originariamente distribuita da una condivisione di rete. Se un aggiornamento è disponibile sul Web, l'utente può installarlo. Anche se la cache di layout di rete viene esaminata prima per eventuali bit di prodotto aggiornati, se non vengono trovati, Visual Studio cerca e scarica i bit di prodotto aggiornati dal Web.

**Scenario 2: client installato in origine e che deve ricevere solo aggiornamenti dal layout di rete**

Se si vuole controllare dove il client Visual Studio cerca gli aggiornamenti, ad esempio se il computer client non ha accesso a Internet e si vuole assicurarsi che sia installato solo e sempre dal layout, è possibile configurare il percorso in cui il programma di installazione del client cerca i bit del prodotto aggiornati. È meglio assicurarsi che questa impostazione sia configurata correttamente prima che il client eserciti l'installazione iniziale dal layout.

1. Creare un layout offline:

   ```shell
   vs_enterprise.exe --layout C:\vsoffline --lang en-US
   ```

2. Copiarlo nella condivisione file in cui si vuole inserirlo:

   ```shell
   xcopy /e C:\vsoffline \\server\share\VS
   ```

3. Modificare il file nel layout e modificare il valore in modo che punti a una copia channelManifest.js`response.json` `channelUri` controllo dell'amministratore.

   Assicurarsi di usare le barre rovesciate come carattere di escape nel valore, come illustrato nell’esempio seguente:

   ```json
   "channelUri":"\\\\server\\share\\VS\\ChannelManifest.json"
   ```

   Gli utenti finali possono ora eseguire il programma di installazione da questa condivisione per installare Visual Studio.

   ```shell
   \\server\share\VS\vs_enterprise.exe
   ```

Quando un amministratore aziendale stabilisce che per gli utenti finali è il momento di eseguire l'aggiornamento a una versione più recente di Visual Studio, è possibile [aggiornare la posizione di layout](update-a-network-installation-of-visual-studio.md) in cui incorporare i file aggiornati, come segue.

1. Utilizzare un comando simile a quello che segue:

   ```shell
   vs_enterprise.exe --layout \\server\share\VS --lang en-US
   ```

2. Assicurarsi che il `response.json` file nel layout aggiornato contenga ancora le personalizzazioni, in particolare la modifica channelUri, come indicato di seguito:

   ```json
   "channelUri":"\\\\server\\share\\VS\\ChannelManifest.json"
   ```

Le installazioni esistenti di Visual Studio da questo layout eseguono la ricerca degli aggiornamenti in `\\server\share\VS\ChannelManifest.json`. Se il file channelManifest.json è più recente rispetto a quello installato dall'utente, Visual Studio informerà l'utente che è disponibile un aggiornamento.

Qualsiasi aggiornamento di installazione avviato dal client installerà automaticamente la versione aggiornata Visual Studio direttamente dal layout.

**Scenario 3: Client installato originariamente dal Web, ma ora deve ricevere solo aggiornamenti da un layout di rete**

In alcuni casi, il computer client potrebbe aver già installato Visual Studio dal Web, ma ora l'amministratore vuole che tutti gli aggiornamenti futuri provengono da un layout gestito. L'unico modo supportato per eseguire questa operazione è creare un layout di rete con la versione desiderata del prodotto e quindi nel computer client eseguire il programma di avvio automatico dal percorso _del layout_ (ad esempio `\\server\share\vs_enterprise.exe` ). Idealmente, l'installazione del client originale sarebbe stata eseguita usando il programma di avvio automatico dal layout di rete con channelURI configurato correttamente, ma anche l'esecuzione del programma di avvio automatico aggiornato dal percorso di layout di rete funzionerà. Una di queste azioni incorpora, nel computer client, una connessione con quel particolare percorso di layout. L'unica avvertenza per il corretto funzionamento di questo scenario è che "ChannelURI" nel file del layout deve essere uguale a ChannelURI impostato nel computer del client quando si è verificata `response.json` l'installazione originale. Molto probabilmente questo valore è stato originariamente impostato sul canale di [rilascio Internet.](https://aka.ms/vs/16/release/channel)

## <a name="controlling-notifications-in-the-visual-studio-ide"></a>Controllo delle notifiche nell'IDE di Visual Studio

::: moniker range="vs-2017"

Come descritto in precedenza, Visual Studio controlla l'eventuale presenza di aggiornamenti nel percorso da cui è stato installato (ad esempio, la condivisione di rete o Internet). Se è disponibile un aggiornamento, Visual Studio ne informa l'utente con un flag di notifica nell'angolo superiore destro della finestra.

   ![Flag di notifica per gli aggiornamenti](media/notification-flag.png)

::: moniker-end

::: moniker range=">=vs-2019"

Come descritto in precedenza, Visual Studio controlla l'eventuale presenza di aggiornamenti nel percorso da cui è stato installato (ad esempio, la condivisione di rete o Internet). Se è disponibile un aggiornamento, Visual Studio ne informa l'utente con un'icona di notifica nell'angolo inferiore destro della finestra.

   ![Icona di notifica nell'IDE Visual Studio](media/vs-2019/notification-bar.png "Icona di notifica nell'IDE Visual Studio")

::: moniker-end

È possibile disabilitare le notifiche se non si vuole che gli utenti finali siano informati degli aggiornamenti. Ad esempio, se si distribuiscono gli aggiornamenti attraverso un meccanismo di distribuzione centrale del software, è possibile voler disabilitare queste notifiche.

::: moniker range="vs-2017"

Poiché Visual Studio 2017 [archivia le voci del Registro di sistema in un registro privato](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance), non è possibile modificare direttamente il Registro di sistema nel modo consueto. Visual Studio include, tuttavia, un’utility `vsregedit.exe` che consente di modificare le impostazioni di Visual Studio. È possibile disattivare le notifiche con il comando seguente:

```shell
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

::: moniker-end

::: moniker range="vs-2019"

Poiché Visual Studio 2019 [archivia le voci del Registro di sistema in un registro privato](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance), non è possibile modificare direttamente il Registro di sistema nel modo consueto. Visual Studio include, tuttavia, un’utility `vsregedit.exe` che consente di modificare le impostazioni di Visual Studio. È possibile disattivare le notifiche con il comando seguente:

```shell
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

::: moniker-end

::: moniker range=">=vs-2022"

Poiché Visual Studio 2022 archivia le voci del Registro di sistema [in](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance)un registro privato, non è possibile modificare direttamente il Registro di sistema nel modo tipico. Visual Studio include, tuttavia, un’utility `vsregedit.exe` che consente di modificare le impostazioni di Visual Studio. È possibile disattivare le notifiche con il comando seguente:

```shell
vsregedit.exe set "C:\Program Files\Microsoft Visual Studio\2022\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

::: moniker-end

Accertarsi di sostituire la directory in modo che coincida con l'istanza installata che si vuole modificare.

> [!TIP]
> Usare [vswhere.exe](tools-for-managing-visual-studio-instances.md#detecting-existing-visual-studio-instances) per trovare un'istanza specifica di Visual Studio in una workstation client.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedi anche

* [Guida di Visual Studio Administrator](visual-studio-administrator-guide.md)
* [Abilitazione degli aggiornamenti dell'amministratore](enabling-administrator-updates.md)
* [Applicazione degli aggiornamenti dell'amministratore](applying-administrator-updates.md)
* [Usare i parametri della riga di comando per installare Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Strumenti per la gestione di istanze di Visual Studio](tools-for-managing-visual-studio-instances.md)
* [Visual Studio ciclo di vita e manutenzione del prodotto](/visualstudio/releases/2019/servicing/)
