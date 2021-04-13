---
title: Creare un'installazione di rete
description: Informazioni sulla creazione di un punto di installazione di rete per la distribuzione di Visual Studio in un'organizzazione.
ms.date: 04/06/2021
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 4CABFD20-962E-482C-8A76-E4012052F701
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 6a93a8a41e4d2c4c91a55cfe91459f7a501b8efc
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/13/2021
ms.locfileid: "107296983"
---
# <a name="create-a-network-installation-of-visual-studio"></a>Creare un'installazione di rete di Visual Studio

A volte un amministratore aziendale desidera creare un punto di installazione di rete che contenga i file di Visual Studio che possono essere distribuiti nelle workstation client. Questo consente di semplificare gli scenari in cui i computer client possono avere autorizzazioni limitate o accesso limitato a Internet oppure quando i team interni desiderano eseguire test di compatibilità prima che la propria organizzazione sia standardizzata in una particolare versione del set di strumenti per sviluppatori. Visual Studio è stato progettato per consentire a un amministratore di _creare un layout di rete_ che essenzialmente crea una cache di file che si trova in una condivisione di rete statica interna che include tutti i file di Visual Studio per l'installazione iniziale e per tutti gli aggiornamenti futuri dei prodotti.

 > [!NOTE]
 >  - Se sono presenti più edizioni di Visual Studio in uso all'interno dell'organizzazione (ad esempio, Visual Studio 2019 Professional e Visual Studio 2019 Enterprise), è necessario creare una condivisione di installazione di rete separata per ogni edizione.
 >  - Si consiglia di decidere come si desidera che i client ricevano gli aggiornamenti del prodotto _prima_ di eseguire l'installazione iniziale del client.  Questo rende più semplice assicurarsi che le opzioni di configurazione siano impostate correttamente. Le scelte possibili includono che i client ottengano gli aggiornamenti dal percorso di layout di rete o da Internet. 
 >  - Il layout originale di installazione di Visual Studio e tutti gli aggiornamenti successivi del prodotto devono trovarsi nella stessa directory di rete per assicurarsi che la funzionalità di ripristino e disinstallazione funzioni correttamente. 

## <a name="download-the-visual-studio-bootstrapper"></a>Scaricare il programma di bootstrap di Visual Studio

Scaricare un file del programma di avvio automatico per l'edizione di Visual Studio desiderata. Assicurarsi di scegliere **Salva**, quindi scegliere **Apri cartella**.

::: moniker range="vs-2017"

Per ottenere il programma di avvio automatico più recente per Visual Studio 2017 versione 15,9, passare alla pagina [versioni precedenti di Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/) e scaricare uno dei seguenti file del programma di avvio automatico:

| Edizione | Nome file |
|-------------|-----------------------|
|Visual Studio 2017 Enterprise versione 15,9 | vs_enterprise.exe |
|Visual Studio 2017 Professional versione 15,9 | vs_professional.exe |
|Visual Studio 2017 Build Tools versione 15,9  | vs_buildtools.exe |

Altri programmi di avvio automatico supportati includono vs_feedbackclient.exe, vs_teamexplorer.exe, vs_testagent.exe, vs_testcontroller.exe e vs_testprofessional.exe.

::: moniker-end

::: moniker range="vs-2019"

Per iniziare, scaricare il programma di avvio automatico di Visual Studio 2019 dalla [pagina dei download di Visual Studio](https://visualstudio.microsoft.com/downloads) o dalla pagina delle versioni di visual [Studio 2019](https://docs.microsoft.com/visualstudio/releases/2019/history#installing-an-earlier-release) per la versione e l'edizione di Visual Studio selezionate.  Il file eseguibile di installazione &mdash; o, per essere più specifici, un file del programma di avvio automatico &mdash; corrisponderà o sarà simile a uno dei seguenti:

|Edizione | Scarica|
|-------------|-----------------------|
|Visual Studio Enterprise | [vs_enterprise.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2019) |
|Visual Studio Professional | [vs_professional.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2019) |
| Visual Studio Build Tools   | [vs_buildtools.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=buildtools&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019) |

Altri programmi di avvio automatico supportati includono [vs_teamexplorer.exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/4026077127d25d33789f3882998266946608d8ada378b6ed7c8fff8c07f3dde2/vs_TeamExplorer.exe), [vs_testagent.exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/1383bf8bcda3d0e986a2e42c14114aaea8a7b085d31aa0623c9f70b2bad130e4/vs_TestAgent.exe)e [vs_testcontroller.exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/54dcf24b76e7cd9fb8be0ac518a9dfba6daf18fe9b2aa1543411b1cda8820918/vs_TestController.exe).

::: moniker-end

::: moniker range="vs-2017"

>[!TIP]
>Se in precedenza è stato scaricato un file del programma di avvio automatico e si vuole verificare quale versione è, ecco come. In Windows aprire Esplora file, fare clic con il pulsante destro del mouse sul file del programma di avvio automatico, scegliere **Proprietà**, scegliere la scheda **Dettagli** , quindi visualizzare il numero di **versione del prodotto** . Per abbinare tale numero a una versione di Visual Studio, vedere i [numeri di build e le date di rilascio di Visual Studio](visual-studio-build-numbers-and-release-dates.md).

::: moniker-end

::: moniker range="vs-2019"

>[!TIP]
>Se in precedenza è stato scaricato un file del programma di avvio automatico e si vuole verificare quale versione è, ecco come. In Windows aprire Esplora file, fare clic con il pulsante destro del mouse sul file del programma di avvio automatico, scegliere **Proprietà**, scegliere la scheda **Dettagli** , quindi visualizzare il numero di **versione del prodotto** . Per abbinare tale numero a una versione di Visual Studio, vedere [versioni di Visual studio 2019](https://docs.microsoft.com/visualstudio/releases/2019/history).

::: moniker-end

## <a name="create-an-offline-installation-folder"></a>Creare una cartella di installazione offline

Per completare questo passaggio è necessaria una connessione Internet. 

Aprire un prompt dei comandi, passare alla directory in cui è stato scaricato il programma di avvio automatico e usare i parametri del programma di avvio automatico come definito nella pagina [usare i parametri della riga di comando per installare Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md) per creare e gestire la cache di installazione di rete. Esempi comuni di creazione di layout iniziali sono illustrati di seguito e negli [esempi di parametri della riga di comando per l'installazione di Visual Studio](../install/command-line-parameter-examples.md).  

   > [!IMPORTANT]
   > Un layout iniziale completo per le impostazioni locali di una singola lingua richiede circa 35 GB di spazio su disco per Visual Studio community e 42 GB per Visual Studio Enterprise. Per altre [impostazioni locali della lingua](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales) sono necessari circa mezzo GB ciascuno. Per altre informazioni, vedere la sezione [personalizzare il layout di rete](#customize-the-network-layout) . Tenere presente che anche gli aggiornamenti del layout successivi devono essere archiviati nello stesso percorso di rete, quindi si supponga che il contenuto della directory del percorso di layout di rete possa essere molto grande nel tempo.  
   
- Per creare un layout iniziale di Visual Studio Enterprise con tutte le lingue e tutte le funzionalità, eseguire:

  ```vs_enterprise.exe --layout c:\VSLayout```

- Per creare un layout iniziale di Visual Studio Professional con tutte le lingue e tutte le funzionalità, eseguire:

  ```vs_professional.exe --layout c:\VSLayout```

## <a name="modify-the-responsejson-file"></a>Modificare il file response.json

È possibile modificare il `response.json` file per impostare i valori predefiniti che vengono usati durante l'esecuzione del programma di installazione.  Ad esempio, è possibile configurare il `response.json` file per selezionare un set specifico di carichi di lavoro che devono essere selezionati automaticamente. È inoltre possibile configurare `response.json` per specificare se il client deve ricevere solo file aggiornati dal percorso di layout di rete. Per altre informazioni, vedere [automatizzare l'installazione di Visual Studio con un file di risposta](../install/automated-installation-with-response-file.md). 

Se si verifica un problema con il programma di avvio automatico di Visual Studio che genera un errore quando si associa a un `response.json` file, vedere [risolvere gli errori correlati alla rete quando si installa o si usa](../install/troubleshooting-network-related-errors-in-visual-studio.md#error-failed-to-parse-id-from-parent-process) la pagina di Visual Studio per altre informazioni.

## <a name="copy-the-layout-to-a-network-share"></a>Copiare il layout in una condivisione di rete

Ospitare il layout in una condivisione di rete in modo che possa essere eseguito dai computer client.

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

### <a name="save-your-layout-options"></a>Salvare le opzioni di layout

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

Prima di tutto è necessario comprendere che esistono due tipi di programma di avvio automatico di Visual Studio: uno che può essere caratterizzato dalle parole "più recenti", "Current", "Evergreen" e "Tip" e uno che significa essenzialmente "versione fissa". Entrambi i tipi di file del programma di avvio automatico hanno esattamente lo stesso nome e il modo migliore per distinguere il tipo è quello di prestare attenzione a dove è stato ottenuto. I programma di avvio automatico di Visual Studio disponibili nella [pagina dei download di Visual Studio](https://visualstudio.microsoft.com/downloads) sono considerati programmi di bootstrap di Visual Studio sempreverdi e installano sempre (o aggiornano) la versione più recente disponibile nel canale al momento dell'esecuzione del programma di avvio automatico. I programmi di avvio automatico di Visual Studio disponibili nella pagina [versioni di Visual studio 2019](https://docs.microsoft.com/visualstudio/releases/2019/history) o incorporati all'interno dell'aggiornamento dell'amministratore nel catalogo Microsoft Update installano una versione fissa specifica del prodotto. 

Se quindi si scarica un programma di avvio automatico di Visual Studio sempreverde oggi e lo si esegue sei mesi da adesso, verrà installata la versione di Visual Studio aggiornata al momento dell'esecuzione del programma di avvio automatico. È progettato per installare sempre i bit più recenti e tenerne aggiornati.

Se si scarica un programma di bootstrap a collegamento fisso o si esegue un aggiornamento dell'amministratore scaricato dal catalogo Microsoft, verrà sempre installata una versione specifica del prodotto, indipendentemente dal momento in cui è stato eseguito.

Infine, è possibile creare un layout di rete usando uno di questi programmi di avvio automatico e la versione che verrà creata nel layout dipende dal programma di avvio automatico che si sta usando, ad esempio, sarà una versione fissa o corrente. È quindi possibile aggiornare il layout di rete usando un programma di avvio automatico successivo oppure è possibile usare anche il pacchetto di aggiornamento dell'amministratore dal catalogo Microsoft Update. Indipendentemente da come si aggiorna il layout, il layout aggiornato risultante sarà una cache del pacchetto che contiene una versione specifica del prodotto e si comporterà come un programma di avvio automatico con collegamento fisso. Quindi, ogni volta che il client viene installato dal layout, il client installerà la versione specifica di Visual Studio presente nel layout (anche se è possibile che esista una versione più recente online). 

### <a name="how-to-get-support-for-your-offline-installer"></a>Come ottenere supporto per il programma di installazione offline

Se si verifica un problema con l'installazione offline, è importante segnalarlo a Microsoft. Il modo migliore per farlo è tramite lo strumento [Segnala un problema](../ide/how-to-report-a-problem-with-visual-studio.md). Con questo strumento è possibile inviare a Microsoft i dati di telemetria e i log necessari per diagnosticare e risolvere il problema.

Per i problemi correlati all'installazione è disponibile anche un'opzione di supporto che offre una [**chat per l'installazione**](https://visualstudio.microsoft.com/vs/support/#talktous) (solo in lingua inglese).

Sono disponibili anche altre opzioni per il supporto. Per un elenco, vedere la pagina [Commenti e suggerimenti](../ide/feedback-options.md).

## <a name="see-also"></a>Vedere anche

- [Guida di Visual Studio Administrator](visual-studio-administrator-guide.md)
- [Aggiornare un'installazione di rete di Visual Studio](update-a-network-installation-of-visual-studio.md)
- [Risolvere gli errori correlati alla rete quando si installa o si usa Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md)
- [Controllare gli aggiornamenti delle distribuzioni di rete di Visual Studio](controlling-updates-to-visual-studio-deployments.md)
- [Ciclo di vita e manutenzione del prodotto Visual Studio](/visualstudio/releases/2019/servicing/)
- [Aggiornare Visual Studio secondo una baseline di manutenzione](update-servicing-baseline.md)
- [Usare i parametri della riga di comando per installare Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
- [ID dei carichi di lavoro e dei componenti di Visual Studio](workload-and-component-ids.md)
- [Installare i certificati necessari per l'installazione offline di Visual Studio](install-certificates-for-visual-studio-offline.md)
