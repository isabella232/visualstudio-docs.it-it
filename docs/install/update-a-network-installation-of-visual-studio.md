---
title: Aggiornare un'installazione di rete
description: Informazioni su come aggiornare un'installazione di Visual Studio basata su rete tramite il comando --layout
ms.date: 10/07/2019
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 1AF69C0E-0AC9-451B-845D-AE4EDBCEA65C
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 2157a6142f95b6ffe34503a8ee80419fcb9ca506
ms.sourcegitcommit: 535ef05b1e553f0fc66082cd2e0998817eb2a56a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/07/2019
ms.locfileid: "72018819"
---
# <a name="update-a-network-based-installation-of-visual-studio"></a>Aggiornare un'installazione di rete di Visual Studio

È possibile aggiornare un layout di installazione di rete di Visual Studio con gli ultimi aggiornamenti di prodotto in modo che possa essere usato sia come punto di installazione per l'aggiornamento più recente di Visual Studio sia per gestire installazioni già distribuite in workstation client.

## <a name="how-to-update-a-network-layout"></a>Come aggiornare un layout di rete

Per aggiornare la condivisione di installazione di rete in modo che includa gli aggiornamenti più recenti, eseguire il comando `--layout` per scaricare in modo incrementale i pacchetti aggiornati.

::: moniker range="vs-2017"

**Novità nella versione 15.3**: Se si seleziona un layout parziale al momento della creazione del layout di rete, tali impostazioni vengono salvate. Gli eventuali comandi relativi al layout future usano le opzioni precedenti più eventuali nuove opzioni specificate. Se tuttavia si usa un layout di una versione precedente, per aggiornarne il contenuto usare gli stessi parametri della riga di comando adottati durante la prima creazione del layout di installazione di rete (ad esempio gli stessi carichi di lavoro e le stesse lingue).

::: moniker-end

::: moniker range="vs-2019"

Se si seleziona un layout parziale al momento della creazione del layout di rete, tali impostazioni vengono salvate. Gli eventuali comandi relativi al layout future usano le opzioni precedenti più eventuali nuove opzioni specificate.

::: moniker-end

Se si ospita un layout in una condivisione file, è necessario aggiornare una copia privata del layout (ad esempio, c:\VSLayout) e quindi, dopo aver scaricato tutto il contenuto aggiornato, copiarlo nella condivisione file (ad esempio, \\server \ Products \ VS). In caso contrario, se un utente esegue l'installazione durante l'aggiornamento del layout, è probabile che non sia in grado di ottenere tutto il contenuto del layout perché non è ancora stato interamente aggiornato.

Ora si prendono in esame alcuni esempi di creazione e aggiornamento di un layout:

* In primo luogo, ecco un esempio di come creare un layout con un carico di lavoro solo per la lingua inglese:

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --lang en-US
  ```

* Di seguito viene illustrato come aggiornare il medesimo layout a una versione più recente. Non è necessario specificare i parametri della riga di comando aggiuntivi. Le impostazioni precedenti sono state salvate e verranno utilizzate da tutti i successivi comandi di layout in questa cartella di layout.

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout
  ```

* Di seguito viene illustrato come aggiornare il layout a una versione più recente in modo automatico. L'operazione di layout esegue il processo di installazione in una nuova finestra della console. La finestra viene lasciata aperta in modo gli utenti possano visualizzare il risultato finale e un riepilogo degli eventuali errori verificatisi. Se si esegue un'operazione di layout in modo automatico (ad esempio, è disponibile uno script che viene eseguito regolarmente per aggiornare il layout alla versione più recente), usare il parametro `--passive` e il processo chiuderà automaticamente la finestra.

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout --passive
  ```

* Ecco come aggiungere un carico di lavoro aggiuntivo e la lingua localizzata.  Questo comando aggiunge il carico di lavoro *Sviluppo di Azure*.  Il Desktop gestito e Azure sono ora inclusi in questo layout.  Sono incluse per tutti questi carichi di lavoro anche le risorse di lingua per l'inglese e tedesco.  E il layout viene aggiornato all'ultima versione disponibile.

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --lang de-DE
  ```

    > [!IMPORTANT]
    > Un'operazione di aggiornamento non installa i componenti facoltativi appena aggiunti, anche se questi componenti vengono inclusi in una sezione "add" di un [file di risposta](automated-installation-with-response-file.md). Questo si verifica perché l'operazione di aggiunta non viene usata durante un aggiornamento.
    >
    > **Soluzione temporanea**: eseguire un'operazione di modifica separata dopo un aggiornamento per installare i componenti mancanti.

* E infine, ecco come aggiungere un carico di lavoro aggiuntivo e la lingua localizzata senza aggiornare la versione. Questo comando aggiunge il carico di lavoro *Sviluppo ASP.NET e Web*.  I carichi di lavoro di Desktop gestito, Azure e Sviluppo ASP.NET e Web sono ora inclusi in questo layout. Sono incluse per tutti questi carichi di lavoro anche le risorse di lingua per inglese, tedesco e francese.  Tuttavia, il layout non è stato aggiornato all'ultima versione disponibile durante l'esecuzione di questo comando. Rimane alla versione esistente.

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.NetWeb --lang fr-FR --keepLayoutVersion
  ```

## <a name="how-to-deploy-an-update-to-client-machines"></a>Come distribuire un aggiornamento in computer client

A seconda del tipo di configurazione dell'ambiente di rete, un aggiornamento può essere distribuito da un amministratore aziendale o avviato da un computer client.

* Gli utenti possono aggiornare un'istanza di Visual Studio installata da una cartella di installazione offline:
  * Eseguire il programma di installazione di Visual Studio.
  * Fare clic su **Aggiorna**.

::: moniker range="vs-2017"

* Gli amministratori possono aggiornare distribuzioni client di Visual Studio senza alcuna interazione da parte dell'utente con due comandi separati:
  * Aggiornare prima il programma di installazione di Visual Studio: <br>```vs_enterprise.exe --quiet --update```
  * Aggiornare quindi l'applicazione Visual Studio: <br>```vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" --quiet --wait --norestart```

::: moniker-end

::: moniker range="vs-2019"

* Gli amministratori possono aggiornare distribuzioni client di Visual Studio senza alcuna interazione da parte dell'utente con due comandi separati:
  * Aggiornare prima il programma di installazione di Visual Studio: <br>```vs_enterprise.exe --quiet --update```
  * Aggiornare quindi l'applicazione Visual Studio: <br>```vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" --quiet --wait --norestart```

::: moniker-end

> [!NOTE]
> Usare il [comando vswhere.exe](tools-for-managing-visual-studio-instances.md) per identificare il percorso di installazione di un'istanza esistente di Visual Studio in un computer client.
>
> [!TIP]
> Per informazioni dettagliate su come controllare il momento in cui le notifiche di aggiornamento vengono visualizzate agli utenti, vedere [Controllare gli aggiornamenti delle distribuzioni di rete di Visual Studio](controlling-updates-to-visual-studio-deployments.md).

## <a name="how-to-verify-a-layout"></a>Come verificare un layout

Utilizzare `--verify` per eseguire la verifica della cache offline fornita. Controlla se i file del pacchetto sono mancanti o non validi. Al termine della verifica, stampa l'elenco di file mancanti e non validi.

```cmd
vs_enterprise.exe --layout <layoutDir> --verify
```

È possibile richiamare il vs_enterprise.exe all'interno di layoutDir.

> [!NOTE]
> Alcuni file di metadati importanti che sono necessari per l’opzione `--verify` devono essere nella cache offline del layout. Se tali file di metadati non sono presenti, non è possibile eseguire "--verify" e il programma di installazione restituisce un errore. Se si verifica questo errore, ricreare un nuovo layout offline in una cartella diversa (o nella stessa cartella della cache offline). Pertanto, scopo, eseguire il medesimo comando relativo al layout utilizzato per creare il layout iniziale offline. Ad esempio `vs_enterprise.exe --layout <layoutDir>`.

Microsoft offre periodicamente aggiornamenti per Visual Studio, di conseguenza la versione del nuovo layout creato potrebbe non essere la stessa del layout iniziale.

> [!NOTE]
> La verifica funziona solo per la versione più recente di una versione secondaria specifica di Visual Studio. Quando viene rilasciata una nuova versione, la verifica non funziona per le versioni con livello patch precedente appartenenti alla stessa versione secondaria.

## <a name="how-to-fix-a-layout"></a>Come correggere un layout

Utilizzare `--fix` per eseguire la stessa verifica come `--verify` e inoltre tentare di risolvere i problemi identificati. Il processo `--fix` richiede una connessione a Internet, quindi verificare che il computer sia connesso a Internet prima di richiamare `--fix`.

```cmd
vs_enterprise.exe --layout <layoutDir> --fix
```

È possibile richiamare il vs_enterprise.exe all'interno di layoutDir.

## <a name="how-to-remove-older-versions-from-a-layout"></a>Come rimuovere le versioni precedenti da un layout

Dopo aver eseguito gli aggiornamenti del layout per una cache offline, nella cartella della cache del layout possono essere presenti alcuni pacchetti obsoleti, non più necessari per l'installazione di Visual Studio più recente. È possibile utilizzare l’opzione `--clean` per rimuovere i pacchetti obsoleti da una cartella della cache offline.

A tale scopo, è necessario utilizzare i percorsi file per i manifesti dei cataloghi che contengono tali pacchetti obsoleti. È possibile trovare che il catalogo dei manifesti in una cartella "Archive" nella cache offline del layout. Vengono salvati presente quando si aggiorna un layout. Nella cartella "Archive", sono presenti una o più cartelle denominate "GUID", ciascuna delle quali contiene un manifesto di catalogo obsoleto. Il numero di cartelle "GUID" deve essere pari al numero degli aggiornamenti apportati alla cache offline.

Alcuni file vengono salvati all'interno di ciascuna cartella "GUID". I due file di maggior interesse sono un file "catalog.json" e un file "version.txt". Il file "catalog.json" è il manifesto di catalogo obsoleto è necessario passare all’opzione `--clean`. Il file version.txt dell’altra versione contiene la versione di questo manifesto del catalogo obsoleto. In base al numero di versione, è possibile decidere se si desidera rimuovere pacchetti obsoleti da questo manifesto del catalogo. È possibile eseguire la stessa operazione procedendo con le altre cartelle "GUID". Dopo deciso in merito a cataloghi di cui eseguire la pulizia, eseguire il `--clean` comando specificando i percorsi file per tali cataloghi.

Gli esempi seguenti illustrano come utilizzare l’opzione --clean:

```cmd
vs_enterprise.exe --layout <layoutDir> --clean <file-path-of-catalog1> <file-path-of-catalog2> …
```

```cmd
vs_enterprise.exe --layout <layoutDir> --clean <file-path-of-catalog1> --clean <file-path-of-catalog2> …
```

È possibile richiamare il vs_enterprise.exe all'interno di &lt;layoutDir&gt;. Di seguito è riportato un esempio:

```cmd
c:\VSLayout\vs_enterprise.exe --layout c:\VSLayout --clean c:\VSLayout\Archive\1cd70189-fc55-4583-8ad8-a2711e928325\Catalog.json --clean c:\VS2017Layout\Archive\d420889f-6aad-4ba4-99e4-ed7833795a10\Catalog.json
```

Quando si esegue questo comando, il programma di installazione analizza la cartella della cache offline per trovare l'elenco di file che verranno rimossi. Quindi, si avrà la possibilità di esaminare i file che verranno eliminati e confermarne l'eliminazione.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedere anche

* [Installare Visual Studio](install-visual-studio.md)
* [Guida dell'amministratore di Visual Studio](visual-studio-administrator-guide.md)
* [Usare i parametri della riga di comando per installare Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Strumenti per il rilevamento e la gestione di istanze di Visual Studio](tools-for-managing-visual-studio-instances.md)
* [Controllare gli aggiornamenti delle distribuzioni di rete di Visual Studio](controlling-updates-to-visual-studio-deployments.md)
* [Ciclo di vita del prodotto e manutenzione di Visual Studio](/visualstudio/releases/2019/servicing/)
