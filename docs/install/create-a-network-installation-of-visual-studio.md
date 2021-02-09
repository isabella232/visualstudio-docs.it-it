---
title: Creare un'installazione di rete
description: Informazioni sulla creazione di un punto di installazione di rete per la distribuzione di Visual Studio in un'organizzazione.
ms.date: 08/27/2020
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 4CABFD20-962E-482C-8A76-E4012052F701
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: b572a6854d505704accd79cc4da2ac4e52c193d6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99850172"
---
# <a name="create-a-network-installation-of-visual-studio"></a>Creare un'installazione di rete di Visual Studio

In genere un amministratore aziendale crea un punto di installazione di rete per la distribuzione nelle workstation client. Visual Studio è stato progettato in modo da consentire di memorizzare nella cache i file per l'installazione iniziale insieme a tutti gli aggiornamenti di prodotto in una singola cartella. Questo processo è anche definito _creazione di un layout_.

Tale operazione è stata effettuata per consentire alle workstation client di poter utilizzare il medesimo percorso di rete per gestire l'installazione anche se non è stato ancora eseguito l’aggiornamento alla versione più recente per la manutenzione.

 > [!NOTE]
 > Se nell'azienda sono in uso più versioni di Visual Studio (ad esempio, Visual Studio Professional e Visual Studio Enterprise), è necessario creare una condivisione di installazione di rete separata per ogni edizione.

## <a name="download-the-visual-studio-bootstrapper"></a>Scaricare il programma di bootstrap di Visual Studio

Scaricare un file del programma di avvio automatico per l'edizione di Visual Studio desiderata. Assicurarsi di scegliere **Salva**, quindi scegliere **Apri cartella**.

::: moniker range="vs-2017"

Per ottenere un programma di avvio automatico per Visual Studio 2017, vedere la pagina di download di [versioni precedenti di Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/) per informazioni dettagliate su come eseguire questa operazione.

Il file eseguibile di installazione &mdash; o, per essere più specifici, il file del programma di avvio automatico &mdash; deve corrispondere o essere simile a uno dei seguenti.

| Edizione | Nome file |
|-------------|-----------------------|
|Visual Studio Enterprise | **vs_enterprise.exe** |
|Visual Studio Professional | **vs_professional.exe** |
|Visual Studio Build Tools   | **vs_buildtools.exe** |

Altri programmi di avvio automatico supportati includono **vs_feedbackclient.exe**, **vs_teamexplorer.exe**, **vs_testagent.exe**, **vs_testcontroller.exe** e **vs_testprofessional.exe**.

::: moniker-end

::: moniker range="vs-2019"

Il file eseguibile di installazione &mdash; o, per essere più specifici, un file del programma di avvio automatico &mdash; deve corrispondere o essere simile a uno dei seguenti.

|Edizione | Scarica|
|-------------|-----------------------|
|Visual Studio Enterprise | [**vs_enterprise.exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2019) |
|Visual Studio Professional | [**vs_professional.exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2019) |
| Visual Studio Build Tools   | [**vs_buildtools.exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=buildtools&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019) |

Altri programmi di avvio automatico supportati includono [vs_teamexplorer.exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/4026077127d25d33789f3882998266946608d8ada378b6ed7c8fff8c07f3dde2/vs_TeamExplorer.exe), [vs_testagent.exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/1383bf8bcda3d0e986a2e42c14114aaea8a7b085d31aa0623c9f70b2bad130e4/vs_TestAgent.exe)e [vs_testcontroller.exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/54dcf24b76e7cd9fb8be0ac518a9dfba6daf18fe9b2aa1543411b1cda8820918/vs_TestController.exe).

::: moniker-end

>[!TIP]
>Se in precedenza è stato scaricato un file del programma di avvio automatico e si vuole verificarne la versione, ecco come. In Windows aprire Esplora file, fare clic con il pulsante destro del mouse sul file del programma di avvio automatico, scegliere **Proprietà**, scegliere la scheda **Dettagli** , quindi visualizzare il numero di **versione del prodotto** . Per abbinare tale numero a una versione di Visual Studio, vedere la pagina relativa ai [numeri di build e alle date di rilascio di Visual Studio](visual-studio-build-numbers-and-release-dates.md) .

## <a name="create-an-offline-installation-folder"></a>Creare una cartella di installazione offline

Per completare questo passaggio è necessaria una connessione Internet. Per creare un'installazione offline con tutte le lingue e tutte le funzionalità, usare un comando simile a uno degli esempi seguenti.

   > [!IMPORTANT]
   > Un layout completo per le impostazioni locali di una singola lingua richiede circa 35 GB di spazio su disco per Visual Studio community e 42 GB per Visual Studio Enterprise. Per altre [impostazioni locali della lingua](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales) sono necessari circa mezzo GB ciascuno. Per altre informazioni, vedere la sezione [personalizzare il layout di rete](#customize-the-network-layout) .
   >
   > [!TIP]
   > Assicurarsi di eseguire il comando dalla directory Download. In genere il percorso di questa cartella è `C:\Users\<username>\Downloads` in un computer con Windows 10.

- Per Visual Studio Enterprise, eseguire:

  ```vs_enterprise.exe --layout c:\VSLayout```

- Per For Visual Studio Professional, eseguire:

  ```vs_professional.exe --layout c:\VSLayout```

## <a name="modify-the-responsejson-file"></a>Modificare il file response.json

È possibile modificare il file response.json per impostare i valori predefiniti da usare quando viene eseguito il programma di installazione.  È possibile ,ad esempio, configurare il file `response.json` per selezionare un set specifico di carichi di lavoro selezionato in modo automatico. Per informazioni dettagliate, vedere [Automatizzare l'installazione di Visual Studio con un file di risposta](automated-installation-with-response-file.md).

Se si verifica un problema con il programma di avvio automatico di Visual Studio che genera un errore quando lo si associa a un response.jssu file, vedere la sezione "Impossibile analizzare l'ID dal processo padre" della pagina [risolvere gli errori correlati alla rete quando si installa o si usa Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md#error-failed-to-parse-id-from-parent-process) per altre informazioni sulle operazioni da eseguire.

## <a name="copy-the-layout-to-a-network-share"></a>Copiare il layout in una condivisione di rete

Inserire il layout in una condivisione di rete affinché possa essere eseguito anche da altri computer.

L'esempio seguente usa [xcopy](/windows-server/administration/windows-commands/xcopy/). È anche possibile usare [robocopy](/windows-server/administration/windows-commands/robocopy/), se lo si preferisce.

::: moniker range="vs-2017"

Esempio:

```cmd
xcopy /e c:\VSLayout \\server\products\VS2017
```

::: moniker-end

::: moniker range="vs-2019"

```cmd
xcopy /e c:\VSLayout \\server\products\VS2019
```

::: moniker-end

> [!IMPORTANT]
> Per evitare un errore, assicurarsi che il tracciato di layout completo sia composto da meno di 80 caratteri.

## <a name="customize-the-network-layout"></a>Personalizzare il layout di rete

Sono disponibili varie opzioni per personalizzare il layout di rete. È possibile, ad esempio, creare un layout parziale che contenga solo un set specifico di [impostazioni locali delle lingue](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales), [carichi di lavoro, componenti e relative dipendenze consigliate o facoltative](workload-and-component-ids.md). Questa soluzione potrebbe essere utile se si prevede di distribuire nelle workstation client solo un subset di carichi di lavoro. I parametri della riga di comando tipici per la personalizzazione del layout includono:

* `--add` per specificare gli [ID dei carichi di lavoro o dei componenti](workload-and-component-ids.md). <br>Se si usa `--add`, verranno scaricati solo i carichi di lavoro e i componenti specificati con `--add`.  Se non si usa `--add`, verranno scaricati tutti i carichi di lavoro e i componenti.
* `--includeRecommended` per includere tutti i componenti consigliati per gli ID di carico di lavoro specificati.
* `--includeOptional` per includere tutti i componenti consigliati e facoltativi per gli ID di carico di lavoro specificati.
* `--lang` per specificare le [impostazioni locali delle lingue](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales).

Gli esempi seguenti illustrano come creare un layout parziale personalizzato.

* Per scaricare tutti i carichi di lavoro e tutti i componenti per una sola lingua, eseguire:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --lang en-US
    ```

* Per scaricare tutti i carichi di lavoro e tutti i componenti per più lingue, eseguire:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --lang en-US de-DE ja-JP
    ```

* Per scaricare un solo carico di lavoro per tutte le lingue, eseguire:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --includeRecommended
    ```

* Per scaricare due carichi di lavoro e un solo componente facoltativo per tre lingue, eseguire:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended --lang en-US de-DE ja-JP
    ```

* Per scaricare due carichi di lavoro e tutti i relativi componenti consigliati:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended
    ```

* Per scaricare due carichi di lavoro e tutti i relativi componenti consigliati e facoltativi, eseguire:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeOptional
    ```

::: moniker range="vs-2017"

### <a name="new-in-version-153"></a>Novità della versione 15.3

::: moniker-end

::: moniker range="vs-2019"

### <a name="save-your-layout-options"></a>Salvare le opzioni di layout

::: moniker-end

Quando si esegue un comando relativo al layout, le opzioni specificate vengono salvate (ad esempio le lingue e i carichi di lavoro). I comandi successivi relativi al layout includeranno tutte le opzioni precedenti.  Ecco un esempio di un layout con un carico di lavoro solo per la lingua inglese:

```cmd
vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --lang en-US
```

Quando si intende aggiornare il layout in questione a una versione più recente, non è necessario specificare i parametri della riga di comando aggiuntivi. Le impostazioni precedenti sono salvate e utilizzate da tutti i successivi comandi di layout in questa cartella di layout.  Il comando seguente aggiornerà il layout parziale esistente.

```cmd
vs_enterprise.exe --layout c:\VSLayout
```

Ecco un esempio di come eseguire questa operazione quando si desidera aggiungere un carico di lavoro aggiuntivo. In questo caso, verrà aggiunto il carico di lavoro di Azure e una lingua localizzata.  Il Desktop gestito e Azure sono ora inclusi in questo layout.  Sono incluse per tutti questi carichi di lavoro anche le risorse di lingua per inglese e tedesco. E il layout viene aggiornato all'ultima versione disponibile.

```cmd
vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --lang de-DE
```

Se si desidera aggiornare un layout esistente a un layout completo, utilizzare l’opzione --all, come illustrato nell'esempio seguente.

```cmd
vs_enterprise.exe --layout c:\VSLayout --all
```

## <a name="deploy-from-a-network-installation"></a>Eseguire la distribuzione da un'installazione di rete

Gli amministratori possono distribuire Visual Studio nelle workstation client nell'ambito di uno script di installazione. In alternativa, gli utenti che hanno i diritti di amministratore possono installare Visual Studio nel proprio computer direttamente dalla condivisione.

* Gli utenti possono effettuare l'installazione eseguendo il comando seguente: <br>

    ```cmd
    \\server\products\VS\vs_enterprise.exe
    ```

* Gli amministratori possono effettuare l'installazione in modalità automatica eseguendo il comando seguente:

    ```cmd
    \\server\products\VS\vs_enterprise.exe --quiet --wait --norestart
    ```

> [!IMPORTANT]
> Per evitare un errore, assicurarsi che il tracciato di layout completo sia composto da meno di 80 caratteri.

> [!TIP]
> Se Visual Studio viene eseguito nell'ambito di un file batch, l'opzione `--wait` garantisce che il processo `vs_enterprise.exe` attenda il completamento dell'installazione prima di restituire un codice di uscita.
>
> Questa opzione è particolarmente utile se l'amministratore aziendale vuole eseguire altre azioni sull'installazione completa (ad esempio, [applicare un codice Product Key a un'installazione eseguita correttamente](automatically-apply-product-keys-when-deploying-visual-studio.md)) tuttavia occorre attendere il termine dell’installazione per gestire il corice di ritorno da tale installazione.
>
> Se non si usa `--wait`, il processo `vs_enterprise.exe` verrà terminato prima del completamento dell'installazione e non verrà restituito un codice di uscita esatto che rappresenti lo stato dell'operazione di installazione.
>

::: moniker range="vs-2019"
> [!IMPORTANT]
> Per le installazioni offline, se viene visualizzato un messaggio di errore che indica che non è possibile trovare un prodotto corrispondente ai parametri seguenti, assicurarsi di usare l' `--noweb` opzione con la versione 16.3.5 o successiva.
>
::: moniker-end

Quando si installa da un layout, viene acquisito il contenuto che viene installato dal layout. Se tuttavia si seleziona un componente non presente nel layout, il componente viene acquisito da Internet.  Se si desidera impedire che l’installazione di Visual Studio scarichi i contenuti mancanti nel layout, utilizzare l’opzione `--noWeb`. Se viene usato `--noWeb` ma nel layout non è presente almeno uno dei contenuti selezionati per l'installazione, il programma di installazione ha esito negativo.

> [!TIP]
> Se si desidera eseguire l'installazione da un'origine offline in un computer connesso a Internet, specificare entrambe le `--noWeb` `--noUpdateInstaller` Opzioni e. Il primo impedisce di scaricare i carichi di lavoro aggiornati, i componenti e così via. Quest'ultimo impedisce l'aggiornamento automatico del programma di installazione dal Web.

> [!IMPORTANT]
> L' `--noWeb` opzione non interrompe l'installazione di Visual Studio in un computer connesso a Internet dalla verifica della disponibilità di aggiornamenti. Per altre informazioni, vedere la pagina [Controllare gli aggiornamenti delle distribuzioni di rete di Visual Studio](controlling-updates-to-visual-studio-deployments.md).

### <a name="error-codes"></a>Codici di errore

Se è stato usato il parametro `--wait`, a seconda del risultato dell'operazione, la variabile di ambiente `%ERRORLEVEL%` viene impostata su uno dei valori seguenti:

[!INCLUDE[install-error-codes-md](includes/install-error-codes-md.md)]

## <a name="update-a-network-install-layout"></a>Aggiornare un layout di installazione di rete

Man mano che diventano disponibili nuovi aggiornamenti di prodotto, è possibile scegliere di [aggiornare il layout di installazione di rete](update-a-network-installation-of-visual-studio.md) in modo da integrare i pacchetti aggiornati.

## <a name="how-to-create-a-layout-for-a-previous-visual-studio-release"></a>Come creare un layout per una versione precedente di Visual Studio

::: moniker range="vs-2017"

> [!NOTE]
> I programmi di bootstrap di Visual Studio disponibili in [visualstudio.microsoft.com](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) scaricano e installano la versione più recente di Visual Studio disponibile ogni volta che vengono eseguiti.
>
> Pertanto se si scarica un *programma di bootstrap* di Visual Studio oggi e lo si esegue tra sei mesi, viene installata la versione di Visual Studio disponibile al momento dell'esecuzione del programma di bootstrap.
>
> Se invece si crea un *layout* e si esegue l'installazione dal layout, viene installata la versione specifica di Visual Studio presente nel layout. Anche nel caso in cui sia disponibile online una versione più recente.

::: moniker-end

::: moniker range="vs-2019"

> [!NOTE]
> I programmi di bootstrap di Visual Studio disponibili in [visualstudio.microsoft.com](https://visualstudio.microsoft.com/downloads) scaricano e installano la versione più recente di Visual Studio disponibile ogni volta che vengono eseguiti.
>
> Pertanto se si scarica un *programma di bootstrap* di Visual Studio oggi e lo si esegue tra sei mesi, viene installata la versione di Visual Studio disponibile al momento dell'esecuzione del programma di bootstrap.
>
> Se invece si crea un *layout* e si esegue l'installazione dal layout, viene installata la versione specifica di Visual Studio presente nel layout. Anche nel caso in cui sia disponibile online una versione più recente.

::: moniker-end

Se è necessario creare un layout per una versione precedente di Visual Studio, passare a [https://my.visualstudio.com](https://my.visualstudio.com) per scaricare le versioni "fisse" del programma di avvio automatico di Visual Studio.

### <a name="how-to-get-support-for-your-offline-installer"></a>Come ottenere supporto per il programma di installazione offline

Se si verifica un problema con l'installazione offline, è importante segnalarlo a Microsoft. Il modo migliore per farlo è tramite lo strumento [Segnala un problema](../ide/how-to-report-a-problem-with-visual-studio.md). Con questo strumento è possibile inviare a Microsoft i dati di telemetria e i log necessari per diagnosticare e risolvere il problema.

Per i problemi correlati all'installazione è disponibile anche un'opzione di supporto che offre una [**chat per l'installazione**](https://visualstudio.microsoft.com/vs/support/#talktous) (solo in lingua inglese).

Sono disponibili anche altre opzioni per il supporto. Per un elenco, vedere la pagina [Commenti e suggerimenti](../ide/feedback-options.md).

## <a name="see-also"></a>Vedi anche

- [Guida di Visual Studio Administrator](visual-studio-administrator-guide.md)
- [Aggiornare un'installazione di rete di Visual Studio](update-a-network-installation-of-visual-studio.md)
- [Risolvere gli errori correlati alla rete quando si installa o si usa Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md)
- [Controllare gli aggiornamenti delle distribuzioni di rete di Visual Studio](controlling-updates-to-visual-studio-deployments.md)
- [Ciclo di vita e manutenzione del prodotto Visual Studio](/visualstudio/releases/2019/servicing/)
- [Aggiornare Visual Studio secondo una baseline di manutenzione](update-servicing-baseline.md)
- [Usare i parametri della riga di comando per installare Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
- [ID dei carichi di lavoro e dei componenti di Visual Studio](workload-and-component-ids.md)
- [Installare i certificati necessari per l'installazione offline di Visual Studio](install-certificates-for-visual-studio-offline.md)