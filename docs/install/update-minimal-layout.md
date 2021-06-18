---
title: Aggiornare Visual Studio usando un layout offline minimo
description: Informazioni su come aggiornare Visual Studio un layout offline minimo.
ms.date: 05/18/2021
ms.custom: seodec18
ms.topic: how-to
ms.assetid: ''
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 1c3a6254c3205038be3d56c64de091e659d2bbd5
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306735"
---
# <a name="update-visual-studio-using-a-minimal-offline-layout"></a>Aggiornare Visual Studio usando un layout offline minimo

Per i computer che non sono connessi a Internet, la creazione di un layout minimo è il modo più semplice e rapido per aggiornare le istanze Visual Studio offline.

Lo strumento di layout minimo genera un layout personalizzato in base alle esigenze del team. Gli amministratori aziendali possono usare questo strumento per creare layout di aggiornamento per la maggior parte delle versioni Visual Studio 2017 e 2019. A differenza di un layout Visual Studio completo, un layout minimo contiene solo i pacchetti aggiornati, quindi è sempre più piccolo e veloce da generare e distribuire. È possibile ridurre ulteriormente le dimensioni del layout di aggiornamento specificando solo le lingue, i carichi di lavoro e i componenti desiderati.

## <a name="how-to-generate-a-minimal-layout"></a>Come generare un layout minimo

> [!IMPORTANT]
> Queste istruzioni presuppongono che i layout siano stati creati e usati in precedenza. Per altre informazioni su come eseguire questa operazione, vedere la pagina Aggiornare [un'installazione di](update-a-network-installation-of-visual-studio.md) Visual Studio rete.
>
> Per una migliore comprensione del ciclo di vita Visual Studio, vedere la pagina Visual Studio Ciclo di [vita e manutenzione del](/visualstudio/releases/2019/servicing) prodotto.
>

Questo strumento crea layout di aggiornamento per Visual Studio 2017 (15.9) e così via. Il layout può essere distribuito in computer di rete/offline per aggiornare Visual Studio istanze. Durante [la normale creazione del layout,](update-a-network-installation-of-visual-studio.md)vengono scaricati tutti i pacchetti per quella particolare versione. La normale creazione del layout è necessaria per il ripristino, la disinstallazione e altre operazioni standard Visual Studio istanze. Il layout minimo scarica solo i pacchetti aggiornati, quindi è più piccolo e più facile da copiare nei computer offline.

### <a name="installing-the-minimal-layout-tool"></a>Installazione dello strumento di layout minimo

 1. Per prima cosa, scaricare lo strumento di layout minimo disponibile [qui.](https://aka.ms/vs/installer/minimallayout) Assicurarsi di scegliere **Salva quando** richiesto, quindi selezionare **Esegui**.

     ![Salvare lo strumento di layout minimo](media/save-minimal-layout.png)

 2. Accettare quindi la richiesta Di controllo dell'account utente facendo clic **su Sì.**

     ![Accettare il controllo dell'account utente](media/accept-user-account-control.png)

 3. Lo strumento di layout minimo verrà installato in `C:\Program Files (x86)\Microsoft Visual Studio\MinimalLayout` .

### <a name="how-to-use-the-minimal-layout-tool"></a>Come usare lo strumento di layout minimo

`MinimalLayout.exe` usa i comandi e le opzioni seguenti per generare il layout. Per eseguire lo strumento è necessario almeno un comando. Ecco come si eseguirà lo strumento:

```MinimalLayout.exe [command] <options>...```

#### <a name="commands"></a>Comandi

* **Anteprima:** usare questo comando per visualizzare in anteprima il numero di pacchetti scaricati e lo spazio totale usato per creare questo layout.
* **Genera**: usare questo comando per generare il layout minimo per l'aggiornamento Visual Studio.
* **Rigenera: usare** questo comando per rigenerare un layout usando un file di risposta di layout minimo esistente. Ogni layout minimo produce un `MinimalLayout.json` file di risposta, che contiene i parametri di input del layout minimi originali. È possibile usare il **comando Rigenera** e un file di risposta `MinimalLayout.json` per rigenerare il layout minimo. Ciò è utile se si vuole creare un layout minimo per un nuovo aggiornamento Visual Studio in base al file di risposta del layout minimo precedente.

   Per questo comando è necessario `MinimalLayout.json` un percorso di file da un layout già generato.

   ```shell
   MinimalLayout.exe regenerate --filePath C:\MinimalLayout\MinimalLayout.json
   ```

* **Verify**: usare questo comando per determinare se la cartella di layout è danneggiata.
* **Correzione:** usare questo comando per correggere una cartella di layout danneggiata, inclusa la sostituzione di eventuali pacchetti mancanti dalla cartella di layout.

#### <a name="options"></a>Opzioni

::: moniker range=">=vs-2019"

| Opzioni                                             | Descrizione                                                                                                                                                                                                                                                                                                                                                                                                                                 | Obbligatorio/facoltativo               | Esempio                                                                                                                                                          |
|-----------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| --targetLocation &lt; dir&gt;                        | Specifica una directory in cui creare un layout offline minimo.                                                                                                                                                                                                                                                                                                                                                                          | Obbligatoria                        | --targetLocation c:\VSLayout\                                                                                                                                    |
| --baseVersion &lt; versione&gt;                       | Il layout offline minimo verrà generato a partire da questa versione.                                                                                                                                                                                                                                                                                                                                                                    | Obbligatoria                        | --baseVersion 16.4.0                                                                                                                                             |
| --targetVersion &lt; versione&gt;                     | Il layout offline minimo verrà generato fino a questa versione e inclusa.                                                                                                                                                                                                                                                                                                                                                              | Obbligatoria                        | --targetVersion 16.4.4                                                                                                                                           |
| --languages                                         | Specifica le lingue da includere nel layout offline minimo. È possibile specificare più valori, separati da spazi.                                                                                                                                                                                                                                                                                                                    | Obbligatoria                        | --languages en-US fr-FR                                                                                                                                          |
| --productIds &lt; uno o più ID prodotto&gt;        | ID dei prodotti da cui verrà generato il layout offline minimo, separati da virgole. <br> <ul><li>Microsoft.VisualStudio.Product.Enterprise</li><li>Microsoft.VisualStudio.Product.Professional</li><li>Microsoft.VisualStudio.Product.BuildTools</li><li>Microsoft.VisualStudio.Product.TestAgent</li><li>Microsoft.VisualStudio.Product.TestController</li><li>Microsoft.VisualStudio.Product.TeamExplorer</li></ul> | Obbligatoria                        | --productIds Microsoft.VisualStudio.Product.Enterprise,Microsoft.VisualStudio.Product.Professional                                                               |
| --filePath                                          | Il percorso del file MinimalLayout.jsfile da un layout già creato. Questa opzione viene usata solo con il comando Rigenera.                                                                                                                                                                                                                                                                                                          | Obbligatorio per il comando Rigenera | --filePath C:\VSLayout\minimalLayout.jssu <br><br> **Si noti che il comando Rigenera accetta solo --filePath come opzione.**                                      |
| --add &lt; one or more workload or component ID&gt; | Specifica uno o più ID di carico di lavoro o componente da aggiungere. È possibile aggiungere componenti aggiuntivi a livello globale usando --includeRecommended e/o <br> –-includeOptional. È possibile specificare più carichi di lavoro o ID componente, separati da uno spazio.                                                                                                                                                                                                   | Facoltativo                        | --add Microsoft.VisualStudio.Workload.ManagedDesktop Microsoft.VisualStudio.Workload.NetWeb Component.GitHub.VisualStudio                                        |
| --includeRecommended                                | include i componenti consigliati per tutti i carichi di lavoro installati, ma non i componenti facoltativi.                                                                                                                                                                                                                                                                                                                                  | Facoltativo                        | Per un carico di lavoro specifico: <br> --add Microsoft.VisualStudio.Workload. ManagedDesktop;includeRecommended <br><br> Per applicare a tutti i carichi di lavoro: --includeRecommended |
| --includeOptional                                   | Include i componenti facoltativi per tutti i carichi di lavoro installati, inclusi i componenti consigliati.                                                                                                                                                                                                                                                                                                                                | Facoltativo                        | Per un carico di lavoro specifico: <br>--add Microsoft.VisualStudio.Workload. ManagedDesktop;includeOptional <br><br> Per applicare a tutti i carichi di lavoro: --includeOptional         |

::: moniker-end

::: moniker range="vs-2017"

| Opzioni                                             | Descrizione                                                                                                                                                                                                                                                                                                                                                                                                                                 | Obbligatorio/facoltativo               | Esempio                                                                                                                                                          |
|-----------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| --targetLocation &lt; dir&gt;                        | Specifica una directory in cui creare un layout offline minimo.                                                                                                                                                                                                                                                                                                                                                                          | Obbligatoria                        | --targetLocation c:\VSLayout\                                                                                                                                    |
| --baseVersion &lt; versione&gt;                       | Il layout offline minimo verrà generato a partire da questa versione.                                                                                                                                                                                                                                                                                                                                                                    | Obbligatoria                        | --baseVersion 15.0.0                                                                                                                                             |
| --targetVersion &lt; versione&gt;                     | Il layout offline minimo verrà generato fino a questa versione e inclusa.                                                                                                                                                                                                                                                                                                                                                              | Obbligatoria                        | --targetVersion 15.9.31                                                                                                                                          |
| --languages                                         | Specifica le lingue da includere nel layout offline minimo. È possibile specificare più valori, separati da spazi.                                                                                                                                                                                                                                                                                                                    | Obbligatoria                        | --languages en-US fr-FR                                                                                                                                          |
| --productIds &lt; uno o più ID prodotto&gt;        | ID dei prodotti da cui verrà generato il layout offline minimo, separati da virgole. <br> <ul><li>Microsoft.VisualStudio.Product.Enterprise</li><li>Microsoft.VisualStudio.Product.Professional</li><li>Microsoft.VisualStudio.Product.BuildTools</li><li>Microsoft.VisualStudio.Product.TestAgent</li><li>Microsoft.VisualStudio.Product.TestController</li><li>Microsoft.VisualStudio.Product.TeamExplorer</li></ul> | Obbligatoria                        | --productIds Microsoft.VisualStudio.Product.Enterprise,Microsoft.VisualStudio.Product.Professional                                                               |
| --filePath                                          | Il percorso del file MinimalLayout.jsfile da un layout già creato. Questa opzione viene usata solo con il comando Rigenera.                                                                                                                                                                                                                                                                                                          | Obbligatorio per il comando Rigenera | --filePath C:\VSLayout\minimalLayout.jssu <br><br> **Si noti che il comando Rigenera accetta solo --filePath come opzione.**                                      |
| --add &lt; one or more workload or component ID&gt; | Specifica uno o più ID di carico di lavoro o componente da aggiungere. È possibile aggiungere componenti aggiuntivi a livello globale usando --includeRecommended e/o <br> –-includeOptional. È possibile specificare più carichi di lavoro o ID componente, separati da uno spazio.                                                                                                                                                                                                   | Facoltativo                        | --add Microsoft.VisualStudio.Workload.ManagedDesktop Microsoft.VisualStudio.Workload.NetWeb Component.GitHub.VisualStudio                                        |
| --includeRecommended                                | include i componenti consigliati per tutti i carichi di lavoro installati, ma non i componenti facoltativi.                                                                                                                                                                                                                                                                                                                                  | Facoltativo                        | Per un carico di lavoro specifico: <br> --add Microsoft.VisualStudio.Workload. ManagedDesktop;includeRecommended <br><br> Per applicare a tutti i carichi di lavoro: --includeRecommended |
| --includeOptional                                   | Include i componenti facoltativi per tutti i carichi di lavoro installati, inclusi i componenti consigliati.                                                                                                                                                                                                                                                                                                                                | Facoltativo                        | Per un carico di lavoro specifico: <br>--add Microsoft.VisualStudio.Workload. ManagedDesktop;includeOptional <br><br> Per applicare a tutti i carichi di lavoro: --includeOptional         |

::: moniker-end

### <a name="generating-a-minimal-layout"></a>Generazione di un layout minimo

> [!IMPORTANT]
> Queste istruzioni presuppongono che sia stato creato in precedenza un layout di installazione di rete. Per altre informazioni su come eseguire questa operazione, vedere la pagina Creare un'installazione [di rete di Visual Studio.](create-a-network-installation-of-visual-studio.md)

Creare un layout minimo usando il **comando generate** per l'intervallo specificato di versioni. È anche necessario conoscere il productId, le lingue e tutti i carichi di lavoro specifici necessari. Questo layout minimo aggiornerà qualsiasi Visual Studio dalla versione di base fino alla versione di destinazione inclusa.

Prima di creare il layout, è possibile trovare le dimensioni totali del download e il numero di pacchetti inclusi usando il **comando di** anteprima. Questo comando accetta le stesse opzioni del **comando generate** e i dettagli vengono scritti nella console.

Di seguito vengono illustrati alcuni esempi di come visualizzare in anteprima, generare e rigenerare un layout minimo:

::: moniker range=">=vs-2019"

* Prima di tutto, ecco un esempio di come visualizzare in anteprima un layout per Visual Studio Enterprise versioni da 16.4.0 a 16.4.4 solo per l'inglese.

  ```shell
  MinimalLayout.exe preview --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --languages en-US
  ```

* Ecco come generare lo stesso layout con un solo carico di lavoro.

  ```shell
  MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US
  ```

* Ecco come rigenerare un layout offline minimo usando un file di risposta esistente.

  ```shell
  MinimalLayout.exe regenerate -filepath c:\VSLayout\MinimalLayout.json
  ```

Altri esempi che usano il **comando generate:**

* Ecco come aggiungere un altro carico di lavoro e includere solo i pacchetti consigliati.

  ```shell
  MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Professional --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop Microsoft.VisualStudio.Workload.NetWeb;includeRecommended --languages en-US
  ```

* È anche possibile generare un layout offline minimo che supporta più prodotti.

  ```shell
  MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise,Microsoft.VisualStudio.Product.Professional --baseVersion 16.4.0 --targetVersion 16.4.4 --languages en-US
  ```

* Infine, ecco come includere più lingue nel layout minimo.

  ```shell
  MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US fr-FR
  ```

::: moniker-end

::: moniker range="vs-2017"

* Prima di tutto, ecco un esempio di come visualizzare in anteprima un layout per Visual Studio Enterprise versioni da 15.0.0 a 15.9.31 solo per l'inglese.

  ```shell
  MinimalLayout.exe preview --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 15.0.0 --targetVersion 15.9.31 --languages en-US
  ```

* Ecco come generare lo stesso layout con un solo carico di lavoro.

  ```shell
  MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 15.0.0 --targetVersion 15.9.31 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US
  ```

* Ecco come rigenerare un layout offline minimo usando un file di risposta esistente.

  ```shell
  MinimalLayout.exe regenerate -filepath c:\VSLayout\MinimalLayout.json
  ```

Altri esempi che usano il **comando generate:**

* Ecco come aggiungere un altro carico di lavoro e includere solo i pacchetti consigliati.

  ```shell
  MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Professional --baseVersion 15.0.0 --targetVersion 15.9.31 --add Microsoft.VisualStudio.Workload.ManagedDesktop Microsoft.VisualStudio.Workload.NetWeb;includeRecommended --languages en-US
  ```

* È anche possibile generare un layout offline minimo che supporta più prodotti.

  ```shell
  MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise,Microsoft.VisualStudio.Product.Professional --baseVersion 15.0.0 --targetVersion 15.9.31 --languages en-US
  ```

* Infine, ecco come includere più lingue nel layout minimo.

  ```shell
  MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 15.0.0 --targetVersion 15.9.31 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US fr-FR
  ```

::: moniker-end

### <a name="how-to-maintain-a-minimal-layout"></a>Come mantenere un layout minimo

Usare i **comandi verify** e **fix** per mantenere il layout minimo dopo la creazione. Il **comando verify** determina se sono presenti pacchetti danneggiati o mancanti nel layout minimo. Se si verificano problemi dopo l'esecuzione del **comando verify,** usare il comando **fix** per correggere i pacchetti mancanti o danneggiati.

* Ecco come verificare se in un layout sono presenti pacchetti danneggiati o mancanti:

  ```shell
  MinimalLayout.exe Verify --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop --includeRecommended --languages en-US
  ```

* Ecco come correggere il layout:

  ```shell
  MinimalLayout.exe fix --targetLocation C:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeRecommended --languages en-US
  ```

>[!NOTE]
> Questo layout non può essere usato per ripristinare un'Visual Studio installazione. Per ripristinare un'istanza esistente di Visual Studio, vedere [Ripristinare Visual Studio](repair-visual-studio.md).
>

### <a name="how-to-use-a-minimal-offline-layout-to-update-an-existing-installation-of-visual-studio"></a>Come usare un layout offline minimo per aggiornare un'installazione esistente di Visual Studio

Dopo aver generato un layout minimo, è possibile copiare l'intera cartella di layout minima in un computer client. Questa operazione è necessaria se il computer non ha accesso alla cartella di layout minima nel percorso originale.

Passare alla cartella e identificare il nome dell'applicazione del programma di avvio automatico. Il nome dell'applicazione del programma di avvio automatico dipende dal valore ProductId specificato durante la generazione del layout minimo. Per esempi comuni, vedere la tabella seguente.

| Valore ProductId                             | Nome applicazione    |
|---------------------------------------------|---------------------|
| Microsoft.VisualStudio.Product.Enterprise   | vs_enterprise.exe   |
| Microsoft.VisualStudio.Product.Professional | vs_professional.exe |
| Microsoft.VisualStudio.Product.BuildTools   | vs_buildtools.exe   |

L'aggiornamento viene applicato a un'Visual Studio in due passaggi. Per iniziare, aggiornare il Programma di installazione di Visual Studio, quindi aggiornare Visual Studio.

::: moniker range="vs-2017"

1. **Aggiornare il Programma di installazione di Visual Studio**

    Eseguire il comando seguente, sostituendo con il nome dell'applicazione del programma di avvio `vs_enterprise.exe`  automatico corretto, se necessario.

    ```shell
    vs_enterprise.exe --quiet --update --offline C:\VSLayout\vs_installer.opc
    ```

2. **Aggiornare l'Visual Studio applicazione**

    Per aggiornare Visual Studio, è necessario specificare installPath dell'istanza Visual Studio che si vuole aggiornare. Se sono installate più istanze Visual Studio, ognuna deve essere aggiornata separatamente. È consigliabile specificare l'opzione con il comando update per impedire l'installazione di componenti `–noWeb` che non hanno il layout minimo. Ciò impedisce di lasciare Visual Studio in uno stato inutilizzabile.

    Eseguire il comando seguente, sostituendo il parametro della riga di comando installPath in modo appropriato. Assicurarsi di usare anche il nome corretto dell'applicazione del programma di avvio automatico.

    ```shell
    vs_enterprise.exe update --noWeb --quiet --installpath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise"
    ```

::: moniker-end

::: moniker range="vs-2019"

1. **Aggiornare il Programma di installazione di Visual Studio**

    Eseguire il comando seguente, sostituendo con il nome dell'applicazione del programma di avvio `vs_enterprise.exe`  automatico corretto, se necessario.

    ```shell
    vs_enterprise.exe --quiet --update --offline C:\VSLayout\vs_installer.opc
    ```

2. **Aggiornare l'Visual Studio applicazione**

    Per aggiornare Visual Studio, è necessario specificare installPath dell'istanza Visual Studio che si vuole aggiornare. Se sono installate più istanze Visual Studio, ognuna deve essere aggiornata separatamente. È consigliabile specificare l'opzione con il comando update per impedire l'installazione di componenti `–noWeb` che non hanno il layout minimo. Ciò impedisce di lasciare Visual Studio in uno stato inutilizzabile.

    Eseguire il comando seguente, sostituendo il parametro della riga di comando installPath in modo appropriato. Assicurarsi di usare anche il nome corretto dell'applicazione del programma di avvio automatico.

    ```shell
    vs_enterprise.exe update --noWeb --quiet --installpath "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise"
    ```

::: moniker-end

::: moniker range=">=vs-2022"

1. **Aggiornare il Programma di installazione di Visual Studio**

    Eseguire il comando seguente, sostituendo con il nome dell'applicazione del programma di avvio `vs_enterprise.exe`  automatico corretto, se necessario.

    ```shell
    vs_enterprise.exe --quiet --update --offline C:\VSLayout\vs_installer.opc
    ```

2. **Aggiornare l'Visual Studio applicazione**

    Per aggiornare Visual Studio, è necessario specificare installPath dell'istanza Visual Studio che si vuole aggiornare. Se sono installate più istanze Visual Studio, ognuna deve essere aggiornata separatamente. È consigliabile specificare l'opzione con il comando update per impedire l'installazione di componenti `–noWeb` che non hanno il layout minimo. Ciò impedisce di lasciare Visual Studio in uno stato inutilizzabile.

    Eseguire il comando seguente, sostituendo il parametro della riga di comando installPath in modo appropriato. Assicurarsi di usare anche il nome corretto dell'applicazione del programma di avvio automatico.

    ```shell
    vs_enterprise.exe update --noWeb --quiet --installpath "C:\Program Files\Microsoft Visual Studio\2022\Enterprise"
    ```

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedi anche

* [Installa Visual Studio](install-visual-studio.md)
* [Guida di Visual Studio Administrator](visual-studio-administrator-guide.md)
* [Usare i parametri della riga di comando per installare Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Strumenti per il rilevamento e la gestione di istanze di Visual Studio](tools-for-managing-visual-studio-instances.md)
* [Come definire impostazioni in un file di risposta](automated-installation-with-response-file.md)
* [Controllare gli aggiornamenti delle distribuzioni di rete di Visual Studio](controlling-updates-to-visual-studio-deployments.md)
* [Visual Studio ciclo di vita e manutenzione del prodotto](/visualstudio/releases/2019/servicing/)
