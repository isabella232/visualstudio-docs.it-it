---
title: Usare i parametri della riga di comando per installare Visual Studio
titleSuffix: ''
description: Informazioni su come usare i parametri della riga di comando per controllare o personalizzare l'installazione di Visual Studio.
ms.date: 10/22/2019
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- command-line parameters
- switches
- command prompt
ms.assetid: 480f3cb4-d873-434e-a8bf-82cff7401cf2
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 7210a2834dda749cfe1d89b9093cd627b7c0ae1b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114361"
---
# <a name="use-command-line-parameters-to-install-visual-studio"></a>Usare i parametri della riga di comando per installare Visual Studio

Quando si installa Visual Studio da un prompt dei comandi, è possibile usare diversi parametri della riga di comando per controllare o personalizzare l'installazione. Dalla riga di comando è possibile eseguire le azioni seguenti:

- Avviare l'installazione con determinate opzioni preselezionate.
- Automatizzare il processo di installazione.
- Creare una cache (layout) dei file di installazione per riutilizzarli in seguito.

Le opzioni della riga di comando vengono utilizzate insieme al programma di avvio automatico di installazione, ovvero il file di piccole dimensioni (1 MB) che avvia il processo di download. Il programma di avvio automatico è il primo eseguibile che viene avviato quando si esegue il download dal sito di Visual Studio.

::: moniker range="vs-2017"

Per ottenere un programma di avvio automatico per Visual Studio 2017, vedere la pagina di download delle versioni precedenti di [**Visual Studio**](https://visualstudio.microsoft.com/vs/older-downloads/) per informazioni dettagliate su come eseguire questa operazione.

::: moniker-end

::: moniker range="vs-2019"

Usare i collegamenti seguenti per accedere direttamente al programma di bootstrap della versione più recente per l'edizione del prodotto da installare:

- [Visual Studio 2019 Enterprise](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2019+rc)
- [Visual Studio 2019 Professional](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2019+rc)
- [Visual Studio 2019 Community](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2019+rc)

::: moniker-end


Il file del programma di avvio automatico deve corrispondere o essere simile a uno dei seguenti nomi:

* vs_enterprise.exe
* vs_professional.exe
* vs_community.exe

>[!TIP]
>Se in precedenza hai scaricato un file del programma di avvio automatico e vuoi verificarne la versione, ecco come. In Windows aprire Esplora file, fare clic con il pulsante destro del mouse sul file del programma di avvio automatico, scegliere **Proprietà**, scegliere la scheda **Dettagli** e quindi visualizzare il numero di versione del **prodotto.** Per far corrispondere tale numero a una versione di Visual Studio, vedere la pagina Numeri di build e date di [rilascio](visual-studio-build-numbers-and-release-dates.md) di Visual Studio.To match that number to a release of Visual Studio, see the Visual Studio build numbers and release dates page.

## <a name="command-line-parameters"></a>Parametri della riga di comando

 Per i parametri della riga di comando di Visual Studio non viene fatta distinzione tra maiuscole e minuscole.

> Sintassi: `vs_enterprise.exe [command] <options>...`

Sostituire `vs_enterprise.exe` come appropriato per l'edizione del prodotto che si sta installando. (In alternativa, è `vs_installer.exe`possibile utilizzare .)

>[!TIP]
> Per altri esempi di utilizzo della riga di comando per l'installazione di Visual Studio, vedere la pagina [Esempi di parametri della riga di comando](command-line-parameter-examples.md).

::: moniker range="vs-2017"

| **Comando** | **Descrizione** |
| ----------------------- | --------------- |
| (vuoto) | Installa il prodotto. |
| `modify` | Modifica un prodotto installato. |
| `update` | Aggiorna un prodotto installato. |
| `repair` | Ripristina un prodotto installato. |
| `uninstall` | Disinstalla un prodotto installato. |
| `export` | **Novità della versione 15.9:** esporta la selezione dell'installazione in un file di configurazione dell'installazione. **Nota**: Può essere utilizzato solo con vs_installer.exe. |

::: moniker-end

::: moniker range="vs-2019"

| **Comando** | **Descrizione** |
| ----------------------- | --------------- |
| (vuoto) | Installa il prodotto. |
| `modify` | Modifica un prodotto installato. |
| `update` | Aggiorna un prodotto installato. |
| `repair` | Ripristina un prodotto installato. |
| `uninstall` | Disinstalla un prodotto installato. |
| `export` | esporta le selezioni di installazione in un file di configurazione dell'installazione. **Nota**: Può essere utilizzato solo con vs_installer.exe. |

::: moniker-end

## <a name="install-options"></a>Opzioni di installazione

::: moniker range="vs-2017"

| **Opzione di installazione** | **Descrizione** |
| ----------------------- | --------------- |
| `--installPath <dir>` | La directory di installazione per l'istanza su cui intervenire. Per il comando di installazione, è **facoltativa** e si tratta della posizione in cui verrà installata l'istanza. Per gli altri comandi, è **obbligatoria** e si tratta della posizione in cui era installata l'istanza installata in precedenza. |
| `--addProductLang <language-locale>` | **Facoltativa**: durante un'operazione di installazione o modifica, determina i Language Pack dell'interfaccia utente da installare nel prodotto. Può essere presente più volte nella riga di comando se vengono aggiunti più Language Pack. Se non è presente, l'installazione usa le impostazioni locali del computer. Per altre informazioni, vedere la sezione [Elenco delle impostazioni locali delle lingue](#list-of-language-locales) in questa pagina.|
| `--removeProductLang <language-locale>` | **Facoltativa**: durante un'operazione di installazione o modifica, determina i Language Pack dell'interfaccia utente da rimuovere dal prodotto. Può essere presente più volte nella riga di comando se vengono aggiunti più Language Pack. Per altre informazioni, vedere la sezione [Elenco delle impostazioni locali delle lingue](#list-of-language-locales) in questa pagina.|
| `--add <one or more workload or component IDs>` | **Facoltativa**: uno o più ID di carichi di lavoro o componenti da aggiungere. Vengono installati i componenti necessari dell'elemento, ma non i componenti consigliati o facoltativi. È possibile controllare i componenti aggiuntivi a livello globale tramite `--includeRecommended` e/o `--includeOptional`. Per includere più carichi di lavoro o componenti, ripetere il comando `--add` (ad esempio, `--add Workload1 --add Workload2`). Per un controllo più capillare, è possibile aggiungere `;includeRecommended` o `;includeOptional` all'ID (ad esempio, `--add Workload1;includeRecommended` o `--add Workload2;includeRecommended;includeOptional`). Per altre informazioni, vedere la pagina [ID dei carichi di lavoro e dei componenti](workload-and-component-ids.md). È possibile ripetere questa opzione se necessario.|
| `--remove <one or more workload or component IDs>` | **Facoltativo:** uno o più ID del carico di lavoro o dei componenti da rimuovere. Per altre informazioni, vedere la pagina [ID dei carichi di lavoro e dei componenti](workload-and-component-ids.md). È possibile ripetere questa opzione se necessario.|
| `--in <path>` | **Facoltativo:** URI o percorso di un file di risposta.  |
| `--all` | **Facoltativa**: se devono essere installati tutti i carichi di lavoro e i componenti per un prodotto. |
| `--allWorkloads` | **Facoltativa**: installa tutti i carichi di lavoro e i componenti, nessun componente consigliato o facoltativo. |
| `--includeRecommended` | **Facoltativo:** include i componenti consigliati per tutti i carichi di lavoro installati, ma non i componenti facoltativi. I carichi di lavoro sono specificati con `--allWorkloads` o `--add`. |
| `--includeOptional` | **Facoltativo:** include i componenti facoltativi per tutti i carichi di lavoro installati, ma non i componenti consigliati. I carichi di lavoro sono specificati con `--allWorkloads` o `--add`.  |
| `--quiet, -q` | **Facoltativo:** non visualizzare alcuna interfaccia utente durante l'esecuzione dell'installazione. |
| `--passive, -p` | **Facoltativo**: consente di visualizzare l'interfaccia utente, ma di non richiedere alcuna interazione da parte dell'utente. |
| `--norestart` | **Facoltativo**: Se `--passive` presente, i comandi con o `--quiet` non riavviano automaticamente la macchina (se necessario).  Viene ignorata se non vengono specificate né `--passive` né `--quiet`.  |
| `--nickname <name>` | **Facoltativo:** definisce il nickname da assegnare a un prodotto installato. Il soprannome non può avere più di 10 caratteri.  |
| `--productKey` | **Facoltativo:** definisce il codice Product Key da utilizzare per un prodotto installato. È composto da 25 caratteri alfanumerici nel formato `xxxxx-xxxxx-xxxxx-xxxxx-xxxxx` o `xxxxxxxxxxxxxxxxxxxxxxxxx`. |
| `--help, --?, -h, -?` | Visualizza una versione offline di questa pagina. |
| `--config <path>` | **Facoltativo** e **novità della versione 15.9**: Durante un'installazione o un'operazione di modifica, determina i carichi di lavoro e i componenti da aggiungere in base a un file di configurazione di installazione precedentemente salvato. Questa operazione è additiva e non rimuoverà alcun carico di lavoro o componente se non sono presenti nel file. Inoltre, gli articoli che non si applicano al prodotto non verranno aggiunti. Durante un'operazione di esportazione, ciò determina la posizione in cui salvare il file di configurazione di installazione. |

::: moniker-end

::: moniker range="vs-2019"

| **Opzione di installazione** | **Descrizione** |
| ----------------------- | --------------- |
| `--installPath <dir>` | La directory di installazione per l'istanza su cui intervenire. Per il comando di installazione, è **facoltativa** e si tratta della posizione in cui verrà installata l'istanza. Per gli altri comandi, è **obbligatoria** e si tratta della posizione in cui era installata l'istanza installata in precedenza. |
| `--addProductLang <language-locale>` | **Facoltativa**: durante un'operazione di installazione o modifica, determina i Language Pack dell'interfaccia utente da installare nel prodotto. Può essere presente più volte nella riga di comando se vengono aggiunti più Language Pack. Se non è presente, l'installazione usa le impostazioni locali del computer. Per altre informazioni, vedere la sezione [Elenco delle impostazioni locali delle lingue](#list-of-language-locales) in questa pagina.|
| `--removeProductLang <language-locale>` | **Facoltativa**: durante un'operazione di installazione o modifica, determina i Language Pack dell'interfaccia utente da rimuovere dal prodotto. Può essere presente più volte nella riga di comando se vengono aggiunti più Language Pack. Per altre informazioni, vedere la sezione [Elenco delle impostazioni locali delle lingue](#list-of-language-locales) in questa pagina.|
| `--add <one or more workload or component IDs>` | **Facoltativa**: uno o più ID di carichi di lavoro o componenti da aggiungere. Vengono installati i componenti necessari dell'elemento, ma non i componenti consigliati o facoltativi. È possibile controllare i componenti aggiuntivi a livello globale tramite `--includeRecommended` e/o `--includeOptional`. Per includere più carichi di lavoro o componenti, ripetere il comando `--add` (ad esempio, `--add Workload1 --add Workload2`). Per un controllo più capillare, è possibile aggiungere `;includeRecommended` o `;includeOptional` all'ID (ad esempio, `--add Workload1;includeRecommended` o `--add Workload2;includeRecommended;includeOptional`). Per altre informazioni, vedere la pagina [ID dei carichi di lavoro e dei componenti](workload-and-component-ids.md). È possibile ripetere questa opzione se necessario.|
| `--remove <one or more workload or component IDs>` | **Facoltativo:** uno o più ID del carico di lavoro o dei componenti da rimuovere. Per altre informazioni, vedere la pagina [ID dei carichi di lavoro e dei componenti](workload-and-component-ids.md). È possibile ripetere questa opzione se necessario.|
| `--in <path>` | **Facoltativo:** URI o percorso di un file di risposta.  |
| `--all` | **Facoltativa**: se devono essere installati tutti i carichi di lavoro e i componenti per un prodotto. |
| `--allWorkloads` | **Facoltativa**: installa tutti i carichi di lavoro e i componenti, nessun componente consigliato o facoltativo. |
| `--includeRecommended` | **Facoltativo:** include i componenti consigliati per tutti i carichi di lavoro installati, ma non i componenti facoltativi. I carichi di lavoro sono specificati con `--allWorkloads` o `--add`. |
| `--includeOptional` | **Facoltativo:** include i componenti facoltativi per tutti i carichi di lavoro installati, ma non i componenti consigliati. I carichi di lavoro sono specificati con `--allWorkloads` o `--add`.  |
| `--quiet, -q` | **Facoltativo:** non visualizzare alcuna interfaccia utente durante l'esecuzione dell'installazione. |
| `--passive, -p` | **Facoltativo**: consente di visualizzare l'interfaccia utente, ma di non richiedere alcuna interazione da parte dell'utente. |
| `--norestart` | **Facoltativo**: Se `--passive` presente, i comandi con o `--quiet` non riavviano automaticamente la macchina (se necessario).  Viene ignorata se non vengono specificate né `--passive` né `--quiet`.  |
| `--nickname <name>` | **Facoltativo:** definisce il nickname da assegnare a un prodotto installato. Il soprannome non può avere più di 10 caratteri.  |
| `--productKey` | **Facoltativo:** definisce il codice Product Key da utilizzare per un prodotto installato. È composto da 25 caratteri alfanumerici nel formato `xxxxx-xxxxx-xxxxx-xxxxx-xxxxx` o `xxxxxxxxxxxxxxxxxxxxxxxxx`. |
| `--help, --?, -h, -?` | Visualizza una versione offline di questa pagina. |
| `--config <path>` | **Facoltativo:** durante un'operazione di installazione o modifica, vengono determinati i carichi di lavoro e i componenti da aggiungere in base a un file di configurazione dell'installazione salvato in precedenza. Questa operazione è additiva e non rimuoverà alcun carico di lavoro o componente se non sono presenti nel file. Inoltre, gli articoli che non si applicano al prodotto non verranno aggiunti. Durante un'operazione di esportazione, ciò determina la posizione in cui salvare il file di configurazione di installazione. |

::: moniker-end

> [!IMPORTANT]
> quando si specificano più carichi di lavoro e componenti, è necessario ripetere l'opzione della riga di comando `--add` o `--remove` per ogni elemento.

## <a name="layout-options"></a>Opzioni di layout

::: moniker range="vs-2017"

| **Opzioni di layout** | **Descrizione** |
| ----------------------- | --------------- |
| `--layout <dir>` | Specifica una directory per creare una cache di installazione offline. Per altre informazioni, vedere [Creare un'installazione di rete di Visual Studio](create-a-network-installation-of-visual-studio.md).|
| `--lang <one or more language-locales>` | **Facoltativa**: viene usata con `--layout` per preparare una cache di installazione offline con i pacchetti di risorse con le lingue specificate. Per altre informazioni, vedere la sezione [Elenco delle impostazioni locali delle lingue](#list-of-language-locales) in questa pagina.|
| `--add <one or more workload or component IDs>` | **Facoltativa**: uno o più ID di carichi di lavoro o componenti da aggiungere. Vengono installati i componenti necessari dell'elemento, ma non i componenti consigliati o facoltativi. È possibile controllare i componenti aggiuntivi a livello globale tramite `--includeRecommended` e/o `--includeOptional`. Per un controllo più capillare, è possibile aggiungere `;includeRecommended` o `;includeOptional` all'ID (ad esempio, `--add Workload1;includeRecommended` o `--add Workload2;includeOptional`). Per altre informazioni, vedere la pagina [ID dei carichi di lavoro e dei componenti](workload-and-component-ids.md). <br/>**Nota**: se viene usato `--add`, vengono scaricati solo i carichi di lavoro e i componenti specificati (con le relative dipendenze). Se `--add` non viene specificato, tutti i carichi di lavoro e i componenti vengono scaricati nel layout.|
| `--includeRecommended` | **Facoltativo:** include i componenti consigliati per tutti i carichi di lavoro installati, ma non i componenti facoltativi. I carichi di lavoro sono specificati con `--allWorkloads` o `--add`. |
| `--includeOptional` | **Facoltativo**: include i componenti consigliati *e* facoltativi per tutti i carichi di lavoro inclusi nel layout. I carichi di lavoro sono specificati con `--add`.  |
| `--keepLayoutVersion` | **Novità in 15.3, facoltativa**: è possibile applicare le modifiche al layout senza aggiornare la versione del layout. |
| `--verify` | **Novità in 15.3, facoltativa**: è possibile verificare i contenuti di un layout. Vengono elencati eventuali file danneggiati o mancanti. |
| `--fix` | **Novità in 15.3, facoltativa**: è possibile verificare i contenuti di un layout. Se i file sono danneggiati o mancanti, vengono scaricati nuovamente. Per correggere un layout, è necessario l'accesso a Internet. |
| `--clean <one or more paths to catalogs>` | **Novità in 15.3, facoltativa**: rimozione delle versioni precedenti dei componenti da un layout che è stato aggiornato a una versione più recente. |

| **Opzioni di installazione avanzate** | **Descrizione** |
| ----------------------- | --------------- |
| `--channelId <id>` | **Facoltativa**: ID del canale per l'istanza che da installare. Questa operazione è necessaria per il comando `--installPath` install e viene ignorata per altri comandi, se specificata. |
| `--channelUri <uri>` | **Facoltativo:** l'URI del manifesto del canale. Se gli aggiornamenti non `--channelUri` sono desiderati, è possibile fare un punto a un file inesistente (ad esempio, --channelUri C:'nonExist.chman). Questo può essere utilizzato per il comando di installazione; viene ignorato per altri comandi. |
| `--installChannelUri <uri>` | **Facoltativo:** URI del manifesto del canale da utilizzare per l'installazione. L'URI specificato da `--channelUri` (che deve essere specificato quando si specifica `--installChannelUri`) viene usato per rilevare gli aggiornamenti. Questo può essere utilizzato per il comando di installazione; viene ignorato per altri comandi. |
| `--installCatalogUri <uri>` | **Facoltativo:** URI del manifesto del catalogo da utilizzare per l'installazione. Se specificato, il gestore del canale prova a scaricare il manifesto del catalogo da questo URI prima di usare l'URI nel manifesto del canale di installazione. Questo parametro viene usato per supportare l'installazione offline, in cui verrà creata la cache di layout con il catalogo dei prodotti già scaricato. Questo può essere utilizzato per il comando di installazione; viene ignorato per altri comandi. |
| `--productId <id>` | **Facoltativa**: ID del prodotto per l'istanza che verrà installata. Questo è pre-popolato in condizioni di installazione normali. |
| `--wait` | **Facoltativa**: il processo attenderà fino al completamento dell'installazione prima di restituire un codice di uscita. Ciò è utile nell'automazione delle installazioni quando è necessario attendere il completamento dell'installazione per gestire il codice da essa restituito. |
| `--locale <language-locale>` | **Facoltativa**: modifica la lingua di visualizzazione dell'interfaccia utente per il programma di installazione. L'impostazione verrà resa persistente. Per altre informazioni, vedere la sezione [Elenco delle impostazioni locali delle lingue](#list-of-language-locales) in questa pagina.|
| `--cache` | **Novità di 15.2, facoltativa**: se presente, i pacchetti verranno mantenuti anche dopo l'installazione per eventuali ripristini successivi. Sostituisce l'impostazione dei criteri globali usata per installazioni successive, correzioni o modifiche. I criteri predefiniti prevedono di memorizzare i pacchetti nella cache. Questa impostazione viene ignorata per il comando di disinstallazione. Per altre informazioni, leggere come [disabilitare o spostare la cache dei pacchetti](disable-or-move-the-package-cache.md). |
| `--nocache` | **Novità in 15.2, facoltativa**: se presente, i pacchetti vengono eliminati dopo essere stati installati o riparati. Verranno scaricati di nuovo solo se necessario ed eliminati di nuovo dopo l'uso. Sostituisce l'impostazione dei criteri globali usata per installazioni successive, correzioni o modifiche. I criteri predefiniti prevedono di memorizzare i pacchetti nella cache. Questa impostazione viene ignorata per il comando di disinstallazione. Per altre informazioni, leggere come [disabilitare o spostare la cache dei pacchetti](disable-or-move-the-package-cache.md). |
| `--noUpdateInstaller` | **Novità in 15.2, facoltativa**: se è presente, impedisce al programma di installazione di aggiornarsi quando è specificata la modalità non interattiva. Il programma di installazione non riuscirà a eseguire il comando e restituirà un codice di uscita diverso da zero se è noUpdateInstaller con modalità non interattiva quando è richiesto un aggiornamento del programma di installazione. |
| `--noWeb` | **Novità di 15.3, facoltativo:** se presente, il programma di installazione di Visual Studio usa i file nella directory di layout per installare Visual Studio. Se un utente tenta di installare componenti non nel layout, l'installazione non riesce.  Per altre informazioni, vedere [Distribuzione da un'installazione di rete](create-a-network-installation-of-visual-studio.md). <br/><br/> **Importante**: questa opzione non impedisce al programma di installazione di Visual Studio di verificare la disponibilità di aggiornamenti. Per altre informazioni, vedere [Controllare gli aggiornamenti delle distribuzioni di rete di Visual Studio](controlling-updates-to-visual-studio-deployments.md). |
| `--path <name>=<path>` | **Novità della versione 15.7 (facoltativo)**: vengono usati per specificare percorsi d'installazione personalizzati. I nomi di percorso supportati sono shared, cache e install. |
| `--path cache=<path>` | **Novità della versione 15.7 (facoltativo)**: vengono usati i percorsi specificati per scaricare i file d'installazione. Questo percorso può essere impostato solo la prima volta in cui viene installato Visual Studio. Esempio: `--path cache="C:\VS\cache"` |
| `--path shared=<path>` | **Novità della versione 15.7 (facoltativo)**: sono contenuti file condivisi per installazioni side-by-side di Visual Studio. Alcuni strumenti e SDK vengono installati in un percorso dell'unità, mentre altri potrebbero sostituire questa impostazione ed essere installati in un'altra unità. Esempio: `--path shared="C:\VS\shared"` <br><br>Importante: l'impostazione può essere eseguita una sola volta e in occasione della prima installazione di Visual Studio. |
| `--path install=<path>` | **Novità della versione 15.7 (facoltativo)**: equivalente a `–-installPath`. In particolare, `--installPath "C:\VS"` e `--path install="C:\VS"` sono equivalenti. È possibile utilizzare solo uno di questi comandi alla volta. |

::: moniker-end

::: moniker range="vs-2019"

| **Opzioni di layout** | **Descrizione** |
| ----------------------- | --------------- |
| `--layout <dir>` | Specifica una directory per creare una cache di installazione offline. Per altre informazioni, vedere [Creare un'installazione di rete di Visual Studio](create-a-network-installation-of-visual-studio.md).|
| `--lang <one or more language-locales>` | **Facoltativa**: viene usata con `--layout` per preparare una cache di installazione offline con i pacchetti di risorse con le lingue specificate. Per altre informazioni, vedere la sezione [Elenco delle impostazioni locali delle lingue](#list-of-language-locales) in questa pagina.|
| `--add <one or more workload or component IDs>` | **Facoltativa**: uno o più ID di carichi di lavoro o componenti da aggiungere. Vengono installati i componenti necessari dell'elemento, ma non i componenti consigliati o facoltativi. È possibile controllare i componenti aggiuntivi a livello globale tramite `--includeRecommended` e/o `--includeOptional`. Per un controllo più capillare, è possibile aggiungere `;includeRecommended` o `;includeOptional` all'ID (ad esempio, `--add Workload1;includeRecommended` o `--add Workload2;includeOptional`). Per altre informazioni, vedere la pagina [ID dei carichi di lavoro e dei componenti](workload-and-component-ids.md). <br/>**Nota**: se viene usato `--add`, vengono scaricati solo i carichi di lavoro e i componenti specificati (con le relative dipendenze). Se `--add` non viene specificato, tutti i carichi di lavoro e i componenti vengono scaricati nel layout.|
| `--includeRecommended` | **Facoltativo:** include i componenti consigliati per tutti i carichi di lavoro installati, ma non i componenti facoltativi. I carichi di lavoro sono specificati con `--allWorkloads` o `--add`. |
| `--includeOptional` | **Facoltativo**: include i componenti consigliati *e* facoltativi per tutti i carichi di lavoro inclusi nel layout. I carichi di lavoro sono specificati con `--add`.  |
| `--keepLayoutVersion` | **Facoltativo**: Applica le modifiche al layout senza aggiornare la versione del layout. |
| `--verify` | **Facoltativo:** verificare il contenuto di un layout. Vengono elencati eventuali file danneggiati o mancanti. |
| `--fix` | **Facoltativo:** verificare il contenuto di un layout.  Se i file sono danneggiati o mancanti, vengono scaricati nuovamente. Per correggere un layout, è necessario l'accesso a Internet. |
| `--clean <one or more paths to catalogs>` | **Facoltativo:** rimuove le versioni precedenti dei componenti da un layout aggiornato a una versione più recente. |

| **Opzioni di installazione avanzate** | **Descrizione** |
| ----------------------- | --------------- |
| `--channelId <id>` | **Facoltativa**: ID del canale per l'istanza che da installare. Questa operazione è necessaria per il comando `--installPath` install e viene ignorata per altri comandi, se specificata. |
| `--channelUri <uri>` | **Facoltativo:** l'URI del manifesto del canale. Se gli aggiornamenti non `--channelUri` sono desiderati, è possibile fare un punto a un file inesistente (ad esempio, --channelUri C:'nonExist.chman). Questo può essere utilizzato per il comando di installazione; viene ignorato per altri comandi. |
| `--installChannelUri <uri>` | **Facoltativo:** URI del manifesto del canale da utilizzare per l'installazione. L'URI specificato da `--channelUri` (che deve essere specificato quando si specifica `--installChannelUri`) viene usato per rilevare gli aggiornamenti. Questo può essere utilizzato per il comando di installazione; viene ignorato per altri comandi. |
| `--installCatalogUri <uri>` | **Facoltativo:** URI del manifesto del catalogo da utilizzare per l'installazione. Se specificato, il gestore del canale prova a scaricare il manifesto del catalogo da questo URI prima di usare l'URI nel manifesto del canale di installazione. Questo parametro viene usato per supportare l'installazione offline, in cui verrà creata la cache di layout con il catalogo dei prodotti già scaricato. Questo può essere utilizzato per il comando di installazione; viene ignorato per altri comandi. |
| `--productId <id>` | **Facoltativa**: ID del prodotto per l'istanza che verrà installata. Questo è pre-popolato in condizioni di installazione normali. |
| `--wait` | **Facoltativa**: il processo attenderà fino al completamento dell'installazione prima di restituire un codice di uscita. Ciò è utile nell'automazione delle installazioni quando è necessario attendere il completamento dell'installazione per gestire il codice da essa restituito. |
| `--locale <language-locale>` | **Facoltativa**: modifica la lingua di visualizzazione dell'interfaccia utente per il programma di installazione. L'impostazione verrà resa persistente. Per altre informazioni, vedere la sezione [Elenco delle impostazioni locali delle lingue](#list-of-language-locales) in questa pagina.|
| `--cache` | **Facoltativo**: Se presente, i pacchetti verranno conservati dopo l'installazione per le riparazioni successive. Sostituisce l'impostazione dei criteri globali usata per installazioni successive, correzioni o modifiche. I criteri predefiniti prevedono di memorizzare i pacchetti nella cache. Questa impostazione viene ignorata per il comando di disinstallazione. Per altre informazioni, leggere come [disabilitare o spostare la cache dei pacchetti](disable-or-move-the-package-cache.md). |
| `--nocache` | **Facoltativo**: Se presente, i pacchetti verranno eliminati dopo l'installazione o la riparazione. Verranno scaricati di nuovo solo se necessario ed eliminati di nuovo dopo l'uso. Sostituisce l'impostazione dei criteri globali usata per installazioni successive, correzioni o modifiche. I criteri predefiniti prevedono di memorizzare i pacchetti nella cache. Questa impostazione viene ignorata per il comando di disinstallazione. Per altre informazioni, leggere come [disabilitare o spostare la cache dei pacchetti](disable-or-move-the-package-cache.md). |
| `--noUpdateInstaller` | **Facoltativo**: Se presente, impedisce al programma di installazione di aggiornarsi quando viene specificato quiet. Il programma di installazione non riuscirà a eseguire il comando e restituirà un codice di uscita diverso da zero se è noUpdateInstaller con modalità non interattiva quando è richiesto un aggiornamento del programma di installazione. |
| `--noWeb` | **Facoltativo:** se presente, il programma di installazione di Visual Studio usa i file nella directory di layout per installare Visual Studio.Optional : If present, Visual Studio setup uses the files in your layout directory to install Visual Studio. Se un utente tenta di installare componenti non nel layout, l'installazione non riesce.  Per altre informazioni, vedere [Distribuzione da un'installazione di rete](create-a-network-installation-of-visual-studio.md). <br/><br/> **Importante**: questa opzione non impedisce al programma di installazione di Visual Studio di verificare la disponibilità di aggiornamenti. Per altre informazioni, vedere [Controllare gli aggiornamenti delle distribuzioni di rete di Visual Studio](controlling-updates-to-visual-studio-deployments.md). **Novità della versione 16.3.5:** questa opzione consente di evitare errori e migliora le prestazioni con le installazioni e gli aggiornamenti offline.|
| `--path <name>=<path>` | **Facoltativo**: Consente di specificare percorsi di installazione personalizzati per l'installazione. I nomi di percorso supportati sono shared, cache e install. |
| `--path cache=<path>` | **Facoltativo**: utilizza il percorso specificato per scaricare i file di installazione. Questo percorso può essere impostato solo la prima volta in cui viene installato Visual Studio. Esempio: `--path cache="C:\VS\cache"` |
| `--path shared=<path>` | **Facoltativo:** contiene i file condivisi per le installazioni side-by-side di Visual Studio. Alcuni strumenti e SDK vengono installati in un percorso dell'unità, mentre altri potrebbero sostituire questa impostazione ed essere installati in un'altra unità. Esempio: `--path shared="C:\VS\shared"` <br><br>Importante: l'impostazione può essere eseguita una sola volta e in occasione della prima installazione di Visual Studio. |
| `--path install=<path>` | **Facoltativo**: `–-installPath`Equivalente a . In particolare, `--installPath "C:\VS"` e `--path install="C:\VS"` sono equivalenti. È possibile utilizzare solo uno di questi comandi alla volta. |

::: moniker-end

## <a name="list-of-workload-ids-and-component-ids"></a>Elenco di ID di carichi di lavoro e ID di componenti

Per un elenco degli ID di componenti e carichi di lavoro ordinati per prodotto Visual Studio, vedere la pagina [ID dei carichi di lavoro e dei componenti di Visual Studio](workload-and-component-ids.md).

## <a name="list-of-language-locales"></a>Elenco delle impostazioni locali delle lingue

| **Impostazioni locali** | **Lingua** |
| ----------------------- | --------------- |
| Cs-cz | Ceco |
| De-de | Tedesco |
| En-us | Inglese |
| Es-es | Spagnolo |
| Fr-fr | Francese |
| It-it | Italiano |
| Ja-jp | Giapponese |
| Ko-kr | Coreano |
| Pl-pl | Polacco |
| Pt-br | Portoghese (Brasile) |
| Ru-ru | Russo |
| Tr-tr | Turco |
| Zh-cn | Cinese (semplificato) |
| Zh-tw | Cinese (tradizionale) |

## <a name="error-codes"></a>Codici di errore

A seconda del risultato dell'operazione, la variabile di ambiente `%ERRORLEVEL%` viene impostata su uno dei valori seguenti:

[!INCLUDE[install-error-codes-md](includes/install-error-codes-md.md)]

Durante ogni operazione nella directory `%TEMP%` vengono generati diversi file di log che indicano lo stato di avanzamento dell'installazione. Ordinare la cartella per data e cercare i file che iniziano con `dd_bootstrapper`, `dd_client` e `dd_setup` per individuare quelli che si riferiscono rispettivamente al programma di avvio automatico, all'app del programma di installazione e al motore di installazione.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedere anche

- [Esempi di parametri della riga di comando per l'installazione di Visual Studio](command-line-parameter-examples.md)
- [Creare un'installazione offline di Visual StudioCreate an offline installation of Visual Studio](create-an-offline-installation-of-visual-studio.md)
- [Automatizzare l'installazione di Visual Studio con un file di risposta](automated-installation-with-response-file.md)
- [ID dei carichi di lavoro e dei componenti di Visual Studio](workload-and-component-ids.md)
