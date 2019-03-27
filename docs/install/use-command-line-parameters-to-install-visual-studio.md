---
title: Usare i parametri della riga di comando per installare Visual Studio
titleSuffix: ''
description: Informazioni su come usare i parametri della riga di comando per controllare o personalizzare l'installazione di Visual Studio.
ms.date: 02/12/2019
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- command-line parameters
- switches
- command prompt
ms.assetid: 480f3cb4-d873-434e-a8bf-82cff7401cf2
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: e8d0fd308d7a5dcdea926cbd710f1a7a362738f1
ms.sourcegitcommit: 3d37c2460584f6c61769be70ef29c1a67397cf14
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/21/2019
ms.locfileid: "58325318"
---
# <a name="use-command-line-parameters-to-install-visual-studio"></a>Usare i parametri della riga di comando per installare Visual Studio

Quando si installa Visual Studio da un prompt dei comandi, è possibile usare diversi parametri della riga di comando per controllare o personalizzare l'installazione. Dalla riga di comando è possibile eseguire le azioni seguenti:

- Avviare l'installazione con determinate opzioni preselezionate.
- Automatizzare il processo di installazione.
- Creare una cache (layout) dei file di installazione per riutilizzarli in seguito.

Insieme alle opzioni della riga di comando viene usato il programma di bootstrap dell'installazione, ovvero un file di dimensioni ridotte (circa 1 MB) che avvia il processo di download. Il programma di avvio automatico è il primo eseguibile che viene avviato quando si esegue il download dal sito di Visual Studio. Usare i collegamenti seguenti per accedere direttamente al programma di bootstrap della versione più recente per l'edizione del prodotto da installare:

- [Visual Studio 2017 Enterprise](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=15&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2017)
- [Visual Studio 2017 Professional](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=15&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2017)
- [Visual Studio 2017 Community](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=15&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2017)

## <a name="command-line-parameters"></a>Parametri della riga di comando

 Per i parametri della riga di comando di Visual Studio non viene fatta distinzione tra maiuscole e minuscole.

> Sintassi: `vs_enterprise.exe [command] <options>...`

(Sostituire `vs_enterprise.exe` con l'edizione del prodotto da installare.

>[!TIP]
> Per altri esempi di utilizzo della riga di comando per l'installazione di Visual Studio, vedere la pagina [Esempi di parametri della riga di comando](command-line-parameter-examples.md).

| **Comando** | **Descrizione** |
| ----------------------- | --------------- |
| (vuoto) | Installa il prodotto. |
| `modify` | Modifica un prodotto installato. |
| `update` | Aggiorna un prodotto installato. |
| `repair` | Ripristina un prodotto installato. |
| `uninstall` | Disinstalla un prodotto installato. |
| `export` | **Novità della versione 15.9**: esporta le selezioni di installazione in un file di configurazione dell'installazione. **Nota**: Può essere usato solo con vs_installer.exe. |

## <a name="install-options"></a>Opzioni di installazione

| **Opzione di installazione** | **Descrizione** |
| ----------------------- | --------------- |
| `--installPath <dir>` | La directory di installazione per l'istanza su cui intervenire. Per il comando di installazione, è **facoltativa** e si tratta della posizione in cui verrà installata l'istanza. Per gli altri comandi, è **obbligatoria** e si tratta della posizione in cui era installata l'istanza installata in precedenza. |
| `--addProductLang <language-locale>` | **Facoltativa**: durante un'operazione di installazione o modifica, determina i Language Pack dell'interfaccia utente da installare nel prodotto. Può essere presente più volte nella riga di comando se vengono aggiunti più Language Pack. Se non è presente, l'installazione usa le impostazioni locali del computer. Per altre informazioni, vedere la sezione [Elenco delle impostazioni locali delle lingue](#list-of-language-locales) in questa pagina.|
| `--removeProductLang <language-locale>` | **Facoltativa**: durante un'operazione di installazione o modifica, determina i Language Pack dell'interfaccia utente da rimuovere dal prodotto. Può essere presente più volte nella riga di comando se vengono aggiunti più Language Pack. Per altre informazioni, vedere la sezione [Elenco delle impostazioni locali delle lingue](#list-of-language-locales) in questa pagina.|
| `--add <one or more workload or component IDs>` | **Facoltativa**: uno o più ID di carichi di lavoro o componenti da aggiungere. Vengono installati i componenti necessari dell'elemento, ma non i componenti consigliati o facoltativi. È possibile controllare i componenti aggiuntivi a livello globale tramite `--includeRecommended` e/o `--includeOptional`. Per includere più carichi di lavoro o componenti, ripetere il comando `--add` (ad esempio, `--add Workload1 --add Workload2`). Per un controllo più capillare, è possibile aggiungere `;includeRecommended` o `;includeOptional` all'ID (ad esempio, `--add Workload1;includeRecommended` o `--add Workload2;includeRecommended;includeOptional`). Per altre informazioni, vedere la pagina [ID dei carichi di lavoro e dei componenti](workload-and-component-ids.md). È possibile ripetere questa opzione se necessario.|
| `--remove <one or more workload or component IDs>` | **Facoltativa**: uno o più ID di carichi di lavoro o componenti da rimuovere. Per altre informazioni, vedere la pagina [ID dei carichi di lavoro e dei componenti](workload-and-component-ids.md). È possibile ripetere questa opzione se necessario.|
| `--in <path>` | **Facoltativa**: URI o percorso di un file di risposta.  |
| `--all` | **Facoltativa**: indica se installare tutti i carichi di lavoro e i componenti per un prodotto. |
| `--allWorkloads` | **Facoltativa**: installa tutti i carichi di lavoro e i componenti, nessun componente consigliato o facoltativo. |
| `--includeRecommended` | **Facoltativa**: include i componenti consigliati per tutti i carichi di lavoro installati, ma non i componenti facoltativi. I carichi di lavoro sono specificati con `--allWorkloads` o `--add`. |
| `--includeOptional` | **Facoltativa**: include i componenti facoltativi per tutti i carichi di lavoro installati, ma non i componenti consigliati. I carichi di lavoro sono specificati con `--allWorkloads` o `--add`.  |
| `--quiet, -q` | **Facoltativa**: consente di non visualizzare alcuna interfaccia utente durante l'installazione. |
| `--passive, -p` | **Facoltativa**: consente di visualizzare l'interfaccia utente senza richiedere alcuna interazione da parte dell'utente. |
| `--norestart` | **Facoltativa**: se presente, i comandi con `--passive` o `--quiet` non riavviano automaticamente il computer (se necessario).  Viene ignorata se non vengono specificate né `--passive` né `--quiet`.  |
| `--nickname <name>` | **Facoltativa**: definisce il nome alternativo da assegnare a un prodotto installato. La lunghezza del nome alternativo non può superare i 10 caratteri.  |
| `--productKey` | **Facoltativa**: definisce il codice Product Key da usare per un prodotto installato. È composto da 25 caratteri alfanumerici in formato `xxxxx-xxxxx-xxxxx-xxxxx-xxxxx` o `xxxxxxxxxxxxxxxxxxxxxxxxx`. |
| `--help, --?, -h, -?` | Visualizza una versione offline di questa pagina. |
| `--config <path>` | **Facoltativa** e **novità della versione 15.9**: durante un'operazione di installazione o modifica, determina i carichi di lavoro e i componenti da aggiungere in base a un file di configurazione dell'installazione precedentemente salvato. Questa operazione aggiunge elementi e non rimuove alcun carico di lavoro o componente se non è presente nel file. Inoltre, gli elementi che non si applicano al prodotto non verranno aggiunti. Durante un'operazione di esportazione, ciò determina la posizione in cui salvare il file di configurazione di installazione. |

> [!IMPORTANT]
> quando si specificano più carichi di lavoro e componenti, è necessario ripetere l'opzione della riga di comando `--add` o `--remove` per ogni elemento.

## <a name="layout-options"></a>Opzioni di layout

| **Opzioni di layout** | **Descrizione** |
| ----------------------- | --------------- |
| `--layout <dir>` | Specifica una directory per creare una cache di installazione offline. Per altre informazioni, vedere [Creare un'installazione di rete di Visual Studio](create-a-network-installation-of-visual-studio.md).|
| `--lang <one or more language-locales>` | **Facoltativa**: viene usata con `--layout` per preparare una cache di installazione offline con i pacchetti di risorse con le lingue specificate. Per altre informazioni, vedere la sezione [Elenco delle impostazioni locali delle lingue](#list-of-language-locales) in questa pagina.|
| `--add <one or more workload or component IDs>` | **Facoltativa**: uno o più ID di carichi di lavoro o componenti da aggiungere. Vengono installati i componenti necessari dell'elemento, ma non i componenti consigliati o facoltativi. È possibile controllare i componenti aggiuntivi a livello globale tramite `--includeRecommended` e/o `--includeOptional`. Per un controllo più capillare, è possibile aggiungere `;includeRecommended` o `;includeOptional` all'ID (ad esempio, `--add Workload1;includeRecommended` o `--add Workload2;includeOptional`). Per altre informazioni, vedere la pagina [ID dei carichi di lavoro e dei componenti](workload-and-component-ids.md). <br/>**Nota**: se viene usato `--add`, vengono scaricati solo i carichi di lavoro e i componenti specificati (con le relative dipendenze). Se non viene specificato `--add`, vengono scaricati nel layout tutti i componenti e i carichi di lavoro.|
| `--includeRecommended` | **Facoltativa**: include i componenti consigliati per tutti i carichi di lavoro installati, ma non i componenti facoltativi. I carichi di lavoro sono specificati con `--allWorkloads` o `--add`. |
| `--includeOptional` | **Facoltativa**: include i componenti consigliati *e* facoltativi per tutti i carichi di lavoro inclusi nel layout. I carichi di lavoro sono specificati con `--add`.  |
| `--keepLayoutVersion` | **Novità della versione 15.3, facoltativa**: consente di applicare le modifiche al layout senza aggiornare la versione del layout. |
| `--verify` | **Novità della versione 15.3, facoltativa**: consente di verificare il contenuto di un layout. Vengono elencati eventuali file danneggiati o mancanti. |
| `--fix` | **Novità della versione 15.3, facoltativa**: consente di verificare il contenuto di un layout.  Se alcuni file risultano danneggiati o mancanti, vengono scaricati di nuovo. Per correggere un layout, è necessario l'accesso a Internet. |
| `--clean <one or more paths to catalogs>` | **Novità della versione 15.3, facoltativa**: rimuove le versioni precedenti dei componenti da un layout aggiornato a una versione più recente. |

| **Opzioni di installazione avanzate** | **Descrizione** |
| ----------------------- | --------------- |
| `--channelId <id>` | **Facoltativa**: ID del canale per l'istanza da installare. È obbligatorio per il comando di installazione e viene ignorato per gli altri comandi se è specificata l'opzione `--installPath`. |
| `--channelUri <uri>` | **Facoltativa**: URI del manifesto del canale. Se non si desiderano aggiornamenti, `--channelUri` può puntare a un file inesistente, ad esempio, --channelUri C:\nonesiste.chman. Può essere usato per il comando di installazione e viene ignorato per gli altri comandi. |
| `--installChannelUri <uri>` | **Facoltativa**: URI del manifesto del canale da usare per l'installazione. L'URI specificato da `--channelUri` (che deve essere specificato quando si specifica `--installChannelUri`) viene usato per rilevare gli aggiornamenti. Può essere usato per il comando di installazione e viene ignorato per gli altri comandi. |
| `--installCatalogUri <uri>` | **Facoltativa**: URI del manifesto del catalogo da usare per l'installazione. Se specificato, il gestore del canale prova a scaricare il manifesto del catalogo da questo URI prima di usare l'URI nel manifesto del canale di installazione. Questo parametro viene usato per supportare l'installazione offline, in cui verrà creata la cache di layout con il catalogo dei prodotti già scaricato. Può essere usato per il comando di installazione e viene ignorato per gli altri comandi. |
| `--productId <id>` | **Facoltativa**: ID del prodotto per l'istanza che verrà installata. Prepopolata nelle condizioni di normale installazione. |
| `--wait` | **Facoltativa**: il processo attenderà il termine dell'installazione prima di restituire un codice di uscita. Ciò è utile nell'automazione delle installazioni quando è necessario attendere il completamento dell'installazione per gestire il codice da essa restituito. |
| `--locale <language-locale>` | **Facoltativa**: modifica la lingua di visualizzazione dell'interfaccia utente per il programma di installazione. L'impostazione verrà resa persistente. Per altre informazioni, vedere la sezione [Elenco delle impostazioni locali delle lingue](#list-of-language-locales) in questa pagina.|
| `--cache` | **Novità della versione 15.2, facoltativa**: se presente, i pacchetti verranno mantenuti dopo l'installazione per eventuali ripristini successivi. Sostituisce l'impostazione dei criteri globali usata per installazioni successive, correzioni o modifiche. I criteri predefiniti prevedono di memorizzare i pacchetti nella cache. Questa impostazione viene ignorata per il comando di disinstallazione. Per altre informazioni, leggere come [disabilitare o spostare la cache dei pacchetti](disable-or-move-the-package-cache.md). |
| `--nocache` | **Novità della versione 15.2, facoltativa**: se presente, i pacchetti verranno eliminati dopo essere stati installati o riparati. Verranno nuovamente scaricati solo se necessario ed eliminati di nuovo dopo l'uso. Sostituisce l'impostazione dei criteri globali usata per installazioni successive, correzioni o modifiche. I criteri predefiniti prevedono di memorizzare i pacchetti nella cache. Questa impostazione viene ignorata per il comando di disinstallazione. Per altre informazioni, leggere come [disabilitare o spostare la cache dei pacchetti](disable-or-move-the-package-cache.md). |
| `--noUpdateInstaller` | **Novità della versione 15.2, facoltativa**: se presente, impedisce al programma di installazione di aggiornarsi quando è specificata la modalità non interattiva. Il programma di installazione non riuscirà a eseguire il comando e restituirà un codice di uscita diverso da zero se è noUpdateInstaller con modalità non interattiva quando è richiesto un aggiornamento del programma di installazione. |
| `--noWeb` | **Novità della versione 15.3, facoltativa**: Se presente, il programma di installazione di Visual Studio usa i file nella directory di layout per installare Visual Studio. Se un utente tenta di installare i componenti che non sono inclusi nel layout, l'installazione ha esito negativo.  Per altre informazioni, vedere [Distribuzione da un'installazione di rete](create-a-network-installation-of-visual-studio.md). <br/><br/> **Importante**: questa opzione non impedisce al programma di installazione di Visual Studio di controllare la disponibilità di aggiornamenti. Per altre informazioni, vedere [Controllare gli aggiornamenti delle distribuzioni di rete di Visual Studio](controlling-updates-to-visual-studio-deployments.md).|
| `--path <name>=<path>` | **Novità della versione 15.7, facoltativa**: usata per specificare percorsi di installazione personalizzati. I nomi di percorso supportati sono shared, cache e install. |
| `--path cache=<path>` | **Novità della versione 15.7, facoltativa**: usa il percorso specificato per scaricare i file di installazione. Questo percorso può essere impostato solo la prima volta in cui viene installato Visual Studio. Esempio: `--path cache="C:\VS\cache"` |
| `--path shared=<path>` | **Novità della versione 15.7, facoltativa**: contiene i file condivisi per le installazioni side-by-side di Visual Studio. Alcuni strumenti e SDK vengono installati in un percorso dell'unità, mentre altri potrebbero sostituire questa impostazione ed essere installati in un'altra unità. Esempio: `--path shared="C:\VS\shared"` <br><br>Importante: può essere impostata una sola volta e in occasione della prima installazione di Visual Studio. |
| `--path install=<path>` | **Novità della versione 15.7, facoltativa**: Equivalente a `–-installPath`. In particolare, `--installPath "C:\VS"` e `--path install="C:\VS"` sono equivalenti. È possibile usarne solo uno per volta. |

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
| Zh-cn | Cinese semplificato |
| Zh-tw | Cinese tradizionale |

## <a name="error-codes"></a>Codici di errore

A seconda del risultato dell'operazione, la variabile di ambiente `%ERRORLEVEL%` viene impostata su uno dei valori seguenti:

| **Valore** | **Risultato** |
| --------- | ---------- |
| 0 | L'operazione è riuscita |
| 1602 | L'operazione è stata annullata |
| 3010 | L'operazione è riuscita, ma è necessario riavviare per poter usare l'installazione |
| 5004 | L'operazione è stata annullata |
| 5007 | L'operazione è stata bloccata. Il computer non soddisfa i requisiti |
| Altro | Si è verificata una condizione di errore. Per altre informazioni, vedere i log |

Durante ogni operazione nella directory `%TEMP%` vengono generati diversi file di log che indicano lo stato di avanzamento dell'installazione. Ordinare la cartella per data e cercare i file che iniziano con `dd_bootstrapper`, `dd_client` e `dd_setup` per individuare quelli che si riferiscono rispettivamente al programma di avvio automatico, all'app del programma di installazione e al motore di installazione.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedere anche

- [Esempi di parametri della riga di comando per l'installazione di Visual Studio](command-line-parameter-examples.md)
- [Creare un'installazione offline di Visual Studio](create-an-offline-installation-of-visual-studio.md)
- [Automatizzare l'installazione di Visual Studio con un file di risposta](automated-installation-with-response-file.md)
- [ID dei carichi di lavoro e dei componenti di Visual Studio](workload-and-component-ids.md)