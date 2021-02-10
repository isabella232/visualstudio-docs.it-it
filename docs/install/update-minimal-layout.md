---
title: Aggiornare Visual Studio usando un layout offline minimo
description: Informazioni su come aggiornare Visual Studio usando un layout minimo offline.
ms.date: 07/21/2020
ms.custom: seodec18
ms.topic: how-to
ms.assetid: ''
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 199771b1cda2049d6508832d7d2264558104a566
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935703"
---
# <a name="update-visual-studio-using-a-minimal-offline-layout"></a>Aggiornare Visual Studio usando un layout offline minimo

Per i computer che non sono connessi a Internet, la creazione di un layout minimo è il modo più semplice e rapido per aggiornare le istanze di Visual Studio offline.

Lo strumento di layout minimo genera un layout personalizzato in base alle esigenze del team. Gli amministratori dell'organizzazione possono utilizzare questo strumento per creare i layout di aggiornamento per la maggior parte delle versioni di Visual Studio 2017 e 2019. A differenza di un layout di Visual Studio completo, un layout minimo contiene solo i pacchetti aggiornati, quindi è sempre più piccolo e più veloce da generare e distribuire. È possibile ridurre ulteriormente le dimensioni del layout di aggiornamento specificando solo le lingue, i carichi di lavoro e i componenti desiderati.

## <a name="how-to-generate-a-minimal-layout"></a>Come generare un layout minimo

> [!IMPORTANT]
> Queste istruzioni presuppongono che siano stati creati e usati in precedenza i layout. Per ulteriori informazioni su come eseguire questa operazione, vedere la pagina relativa all' [aggiornamento di un'installazione di rete di Visual Studio](update-a-network-installation-of-visual-studio.md) .
>
> Per comprendere meglio il ciclo di vita di Visual Studio, vedere la pagina [ciclo di vita del prodotto e manutenzione di Visual Studio](/visualstudio/releases/2019/servicing) .
>

Questo strumento Crea layout di aggiornamento per Visual Studio 2017 (15,9) e versioni successive. Il layout può essere distribuito in rete/computer offline per aggiornare le istanze di Visual Studio. Durante la [normale creazione del layout](update-a-network-installation-of-visual-studio.md), vengono scaricati tutti i pacchetti per la versione specifica. La creazione del layout normale è necessaria per il ripristino, la disinstallazione e altre operazioni standard nelle istanze di Visual Studio. Il layout minimo Scarica solo i pacchetti aggiornati, quindi è più piccolo e più semplice da copiare nei computer offline.

### <a name="installing-the-minimal-layout-tool"></a>Installazione dello strumento di layout minimo
 
 1. Per prima cosa, scaricare lo strumento di layout minimo disponibile [qui](https://aka.ms/vs/installer/minimallayout). Assicurarsi di scegliere **Salva** quando richiesto, quindi selezionare **Esegui**.

     ![Salva lo strumento di layout minimo](media/save-minimal-layout.png)

 2. Quindi, accettare la richiesta di controllo dell'account utente facendo clic su **Sì**.

     ![Accetta controllo account utente](media/accept-user-account-control.png)

 3. Lo strumento di layout minimo verrà installato in `C:\Program Files (x86)\Microsoft Visual Studio\MinimalLayout` .

### <a name="how-to-use-the-minimal-layout-tool"></a>Come usare lo strumento di layout minimo

`MinimalLayout.exe` USA i comandi e le opzioni seguenti per generare il layout. Per eseguire lo strumento è necessario almeno un comando. Di seguito viene illustrato come eseguire lo strumento:

```MinimalLayout.exe [command] <options>...```

#### <a name="commands"></a>Comandi
* **Anteprima**: usare questo comando per visualizzare in anteprima il numero di pacchetti che verrà scaricato e lo spazio totale usato per creare questo layout. 
* **Genera**: usare questo comando per generare il layout minimo per l'aggiornamento di Visual Studio.
* **Rigenera**: usare questo comando per rigenerare un layout usando un file di risposta layout minimo esistente. Ogni layout minimo produce un `MinimalLayout.json` file di risposta che contiene i parametri di input del layout minimo originali. Per rigenerare il layout minimo, è possibile usare il comando **Rigenera** e un `MinimalLayout.json` file di risposta. Questa opzione è utile se si vuole creare un layout minimo per un nuovo aggiornamento di Visual Studio in base al file di risposta del layout minimo precedente.

   Per questo comando `MinimalLayout.json` è necessario un percorso di file da un layout già generato. 

    ```cmd
    MinimalLayout.exe regenerate --filePath C:\MinimalLayout\MinimalLayout.json
    ```

* **Verify**: usare questo comando per determinare se la cartella di layout è danneggiata.
* **Correzione**: usare questo comando per correggere una cartella di layout danneggiata, inclusa la sostituzione di eventuali pacchetti mancanti dalla cartella di layout.

::: moniker range="vs-2019"

#### <a name="options"></a>Opzioni 

|Opzioni    |Descrizione    |Obbligatorio/facoltativo |Esempio |
|:----------|:-----------|:------------|:--------------|
|--targetLocation &lt; dir&gt; |Specifica una directory in cui creare un layout minimo offline.       |Necessario        |--targetLocation c:\VSLayout\ |
|--baseVersion &lt; versione&gt;|Il layout minimo offline verrà generato a partire da questa versione.   |Necessario|--baseVersion 16.4.0 |
|--targetVersion &lt; versione&gt;|Il layout minimo offline verrà generato fino a questa versione.|Necessario|--targetVersion 16.4.4|
|--lingue    |Specifica le lingue da includere nel layout minimo offline. È possibile specificare più valori, separati da spazi.    |Necessario    |--lingue en-US fr-FR |
|-- &lt; ID ProductID&gt;    |ID del prodotto da cui verrà generato il layout minimo offline. <br> <ul><li>Microsoft.VisualStudio.Product.Enterprise</li><li>Microsoft.VisualStudio.Product.Professional</li><li>Microsoft.VisualStudio.Product.BuildTools</li><li>Microsoft.VisualStudio.Product.TestAgent</li><li>Microsoft.VisualStudio.Product.TestController</li><li>Microsoft.VisualStudio.Product.TeamExplorer</li></ul>|Necessario|--productId Microsoft. VisualStudio. Product. Enterprise |
|--FilePath    |Percorso del file MinimalLayout.jssu file da un layout già creato. Questa opzione viene usata solo con il comando Regenerate.     |Obbligatorio per il comando Regenerate    |--FilePath C:\VSLayout\minimalLayout.json <br><br> **Si noti che il comando Regenerate accetta solo--FilePath come opzione.** |
|--aggiungere &lt; uno o più ID di carico di lavoro o componente&gt;    |Specifica uno o più ID di carico di lavoro o componente da aggiungere. I componenti aggiuntivi possono essere aggiunti a livello globale usando--includeRecommended e/o <br> --includeOptional. È possibile specificare più carichi di lavoro o ID componente separati da uno spazio.    |Facoltativo    |--aggiungere Microsoft. VisualStudio. workload. ManagedDesktop Microsoft. VisualStudio. workload. NetWeb Component. GitHub. VisualStudio |
|--includeRecommended    |include i componenti consigliati per tutti i carichi di lavoro installati, ma non i componenti facoltativi.    |Facoltativo    |Per un carico di lavoro specifico: <br> --aggiungere Microsoft. VisualStudio. workload. ManagedDesktop; includeRecommended <br><br> Per applicare a tutti i carichi di lavoro:--includeRecommended |
|--includeOptional |Include i componenti facoltativi per tutti i carichi di lavoro installati, inclusi i componenti consigliati.    |Facoltativo    |Per un carico di lavoro specifico: <br>--aggiungere Microsoft. VisualStudio. workload. ManagedDesktop; includeOptional <br><br> Per applicare a tutti i carichi di lavoro:--includeOptional |

::: moniker-end

::: moniker range="vs-2017"

#### <a name="options"></a>Opzioni 

|Opzioni    |Descrizione    |Obbligatorio/facoltativo |Esempio |
|:----------|:-----------|:------------|:--------------|
|--targetLocation &lt; dir&gt; |Specifica una directory in cui creare un layout minimo offline.       |Necessario        |--targetLocation c:\VSLayout\ |
|--baseVersion &lt; versione&gt;|Il layout minimo offline verrà generato a partire da questa versione.   |Necessario|--baseVersion 15.0.0 |
|--targetVersion &lt; versione&gt;|Il layout minimo offline verrà generato fino a questa versione.|Necessario|--targetVersion 15.9.31|
|--lingue    |Specifica le lingue da includere nel layout minimo offline. È possibile specificare più valori, separati da spazi.    |Necessario    |--lingue en-US fr-FR |
|-- &lt; ID ProductID&gt;    |ID del prodotto da cui verrà generato il layout minimo offline. <br> <ul><li>Microsoft.VisualStudio.Product.Enterprise</li><li>Microsoft.VisualStudio.Product.Professional</li><li>Microsoft.VisualStudio.Product.BuildTools</li><li>Microsoft.VisualStudio.Product.TestAgent</li><li>Microsoft.VisualStudio.Product.TestController</li><li>Microsoft.VisualStudio.Product.TeamExplorer</li></ul>|Necessario|--productId Microsoft. VisualStudio. Product. Enterprise |
|--FilePath    |Percorso del file MinimalLayout.jssu file da un layout già creato. Questa opzione viene usata solo con il comando Regenerate.     |Obbligatorio per il comando Regenerate    |--FilePath C:\VSLayout\minimalLayout.json <br><br> **Si noti che il comando Regenerate accetta solo--FilePath come opzione.** |
|--aggiungere &lt; uno o più ID di carico di lavoro o componente&gt;    |Specifica uno o più ID di carico di lavoro o componente da aggiungere. I componenti aggiuntivi possono essere aggiunti a livello globale usando--includeRecommended e/o <br> --includeOptional. È possibile specificare più carichi di lavoro o ID componente separati da uno spazio.    |Facoltativo    |--aggiungere Microsoft. VisualStudio. workload. ManagedDesktop Microsoft. VisualStudio. workload. NetWeb Component. GitHub. VisualStudio |
|--includeRecommended    |include i componenti consigliati per tutti i carichi di lavoro installati, ma non i componenti facoltativi.    |Facoltativo    |Per un carico di lavoro specifico: <br> --aggiungere Microsoft. VisualStudio. workload. ManagedDesktop; includeRecommended <br><br> Per applicare a tutti i carichi di lavoro:--includeRecommended |
|--includeOptional |Include i componenti facoltativi per tutti i carichi di lavoro installati, inclusi i componenti consigliati.    |Facoltativo    |Per un carico di lavoro specifico: <br>--aggiungere Microsoft. VisualStudio. workload. ManagedDesktop; includeOptional <br><br> Per applicare a tutti i carichi di lavoro:--includeOptional |

::: moniker-end

### <a name="generating-a-minimal-layout"></a>Generazione di un layout minimo

> [!IMPORTANT]
>  Queste istruzioni presuppongono che sia stato creato in precedenza un layout di installazione di rete. Per ulteriori informazioni su come eseguire questa operazione, vedere la pagina [creare un'installazione di rete di Visual Studio](create-a-network-installation-of-visual-studio.md) .

Creare un layout minimo usando il comando **genera** per l'intervallo di versioni specificato. Sarà inoltre necessario conoscerne il productId, le lingue e i carichi di lavoro specifici necessari. Questo layout minimo aggiornerà tutte le istanze di Visual Studio dalla versione di base fino a includere la versione di destinazione.

Prima di creare il layout, è possibile individuare le dimensioni totali del download e il numero di pacchetti inclusi usando il comando **Anteprima** . Questo comando accetta le stesse opzioni del comando **generate** e i dettagli vengono scritti nella console.

Verranno esaminati alcuni esempi di come visualizzare in anteprima, generare e rigenerare un layout minimo:

::: moniker range="vs-2019"

- In primo luogo, di seguito è riportato un esempio di come visualizzare in anteprima un layout per Visual Studio Enterprise versioni 16.4.0 in 16.4.4 solo per l'inglese.

    ```cmd
    MinimalLayout.exe preview --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --languages en-US
    ```

- Di seguito viene illustrato come generare lo stesso layout con un carico di lavoro.

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US
    ```

- Di seguito viene illustrato come rigenerare un layout minimo offline usando un file di risposta esistente. 

    ```cmd
    MinimalLayout.exe regenerate -filepath c:\VSLayout\MinimalLayout.json
    ```

Un paio di altri esempi di utilizzo del comando **generate** :

- Ecco come aggiungere un carico di lavoro aggiuntivo e includere solo i pacchetti consigliati. 

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Professional --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop Microsoft.VisualStudio.Workload.NetWeb;includeRecommended --languages en-US
    ```

- Infine, ecco come includere più lingue nel layout minimo. 

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US fr-FR
    ```

::: moniker-end

::: moniker range="vs-2017"

- In primo luogo, di seguito è riportato un esempio di come visualizzare in anteprima un layout per Visual Studio Enterprise versioni 15.0.0 in 15.9.31 solo per l'inglese.

    ```cmd
    MinimalLayout.exe preview --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 15.0.0 --targetVersion 15.9.31 --languages en-US
    ```

- Di seguito viene illustrato come generare lo stesso layout con un carico di lavoro.

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 15.0.0 --targetVersion 15.9.31 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US
    ```

- Di seguito viene illustrato come rigenerare un layout minimo offline usando un file di risposta esistente. 

    ```cmd
    MinimalLayout.exe regenerate -filepath c:\VSLayout\MinimalLayout.json
    ```

Un paio di altri esempi di utilizzo del comando **generate** :

- Ecco come aggiungere un carico di lavoro aggiuntivo e includere solo i pacchetti consigliati. 

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Professional --baseVersion 15.0.0 --targetVersion 15.9.31 --add Microsoft.VisualStudio.Workload.ManagedDesktop Microsoft.VisualStudio.Workload.NetWeb;includeRecommended --languages en-US
    ```

- Infine, ecco come includere più lingue nel layout minimo. 

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 15.0.0 --targetVersion 15.9.31 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US fr-FR
    ```

::: moniker-end

### <a name="how-to-maintain-a-minimal-layout"></a>Come mantenere un layout minimo

Usare i comandi **Verify** e **Fix** per mantenere il layout minimo dopo che è stato creato. Il comando **Verify** determina se nel layout minimo sono presenti pacchetti danneggiati o mancanti. Se si verificano problemi dopo l'esecuzione del comando **Verify** , utilizzare il comando **Fix** per correggere i pacchetti mancanti o danneggiati.

- Di seguito viene illustrato come verificare se un layout contiene pacchetti danneggiati o mancanti: 

    ```cmd
    MinimalLayout.exe Verify --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop --includeRecommended --languages en-US
    ```

- Di seguito viene illustrato come correggere il layout:

    ```cmd
    MinimalLayout.exe fix --targetLocation C:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeRecommended --languages en-US
    ```

>[!NOTE] 
> Questo layout non può essere usato per ripristinare un'installazione di Visual Studio. Per ripristinare un'istanza esistente di Visual Studio, vedere [Repair Visual Studio](repair-visual-studio.md).
>

### <a name="how-to-use-a-minimal-offline-layout-to-update-an-existing-installation-of-visual-studio"></a>Come usare un layout minimo offline per aggiornare un'installazione esistente di Visual Studio

Dopo aver generato un layout minimo, è possibile copiare l'intera cartella di layout minima in un computer client. Questa operazione è necessaria se il computer non ha accesso alla cartella di layout minima nel percorso originale.

Passare alla cartella e identificare il nome dell'applicazione del programma di avvio automatico. Il nome dell'applicazione del programma di avvio automatico dipende dal valore di ProductId specificato durante la generazione del layout minimo. Per esempi comuni, vedere la tabella seguente.

|Valore ProductId    |Nome applicazione|
|:-----------|:------------|
|Microsoft.VisualStudio.Product.Enterprise    |vs_enterprise.exe|
|Microsoft.VisualStudio.Product.Professional    |vs_professional.exe|
|Microsoft.VisualStudio.Product.BuildTools    |vs_buildtools.exe|

L'aggiornamento viene applicato a un'istanza di Visual Studio in due passaggi. Per iniziare, aggiornare il Programma di installazione di Visual Studio, quindi aggiornare Visual Studio.

1. **Aggiornare il Programma di installazione di Visual Studio** 

    Eseguire il comando seguente, sostituendo `vs_enterprise.exe`  con il nome corretto dell'applicazione del programma di avvio automatico, se necessario. 

    ```cmd
    vs_enterprise.exe --quiet --update --offline C:\VSLayout\vs_installer.opc
    ```

2. **Aggiornare l'applicazione di Visual Studio**

    Per aggiornare Visual Studio, è necessario specificare il installPath dell'istanza di Visual Studio che si vuole aggiornare. Se sono installate più istanze di Visual Studio, è necessario aggiornarle separatamente. È consigliabile specificare l' `–noWeb` opzione con il comando Aggiorna per impedire l'installazione di componenti che non sono nel layout minimo. In questo modo è possibile evitare di lasciare Visual Studio in uno stato inutilizzabile.

    Eseguire il comando seguente, sostituendo il parametro della riga di comando installPath in modo appropriato. Assicurarsi di usare anche il nome corretto dell'applicazione del programma di avvio automatico.

    ```cmd
    vs_enterprise.exe update --noWeb --quiet --installpath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise"
    ```

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedi anche

* [Installa Visual Studio](install-visual-studio.md)
* [Guida di Visual Studio Administrator](visual-studio-administrator-guide.md)
* [Usare i parametri della riga di comando per installare Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Strumenti per il rilevamento e la gestione di istanze di Visual Studio](tools-for-managing-visual-studio-instances.md)
* [Come definire impostazioni in un file di risposta](automated-installation-with-response-file.md)
* [Controllare gli aggiornamenti delle distribuzioni di rete di Visual Studio](controlling-updates-to-visual-studio-deployments.md)
* [Ciclo di vita e manutenzione del prodotto Visual Studio](/visualstudio/releases/2019/servicing/)
