---
title: Ottimizzare il caricamento delle soluzioni in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 08/31/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- startup time [Visual Studio]
- optimizing startup time [Visual Studio]
- speed up start time [Visual Studio]
ms.assetid: 84989983-84bc-4f81-97a8-2131e3a25138
caps.latest.revision: "4"
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vs.performancecenter
ms.technology: vs-ide-general
ms.openlocfilehash: 2102fc026b566c89108f0d74dcf604020653e358
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="optimize-solution-loading-in-visual-studio"></a>Ottimizzare il caricamento delle soluzioni in Visual Studio
Molte soluzioni contengono un numero elevato di progetti che influisce sul tempo di caricamento delle soluzioni. Negli ambienti di team, tuttavia, gli sviluppatori lavorano in genere su un sottoinsieme di progetti senza la necessità di caricare tutti i singoli progetti.

Visual Studio 2017 supporta il **caricamento leggero delle soluzioni**. Quando la modalità di caricamento leggero delle soluzioni è abilitata, Visual Studio 2017 carica un piccolo sottoinsieme di progetti anziché caricare tutti i progetti di una soluzione di grandi dimensioni. La maggior parte delle funzionalità IDE di uso comune possono essere usate in modalità di caricamento leggero delle soluzioni consentendo di compilare ed eseguire le ricerche e il debug nell'intera soluzione. La principale funzionalità non supportata in modalità di caricamento leggero delle soluzioni è Modifica e continuazione.

> [!NOTE]
> Questo contenuto si applica a Visual Studio 2017 Update 3

Per le soluzioni di grandi dimensioni con più di 30 progetti, il caricamento leggero delle soluzioni carica le soluzioni, in media, al doppio della velocità. Sebbene la maggior parte delle funzionalità IDE funzioni in modalità di caricamento leggero delle soluzioni, alcune funzionalità IDE possono richiedere il caricamento di tutti i progetti. In questi casi, Visual Studio carica automaticamente l'intera soluzione per consentire l'uso della funzionalità. Nel peggiore dei casi, vengono caricati tutti i progetti in modalità di caricamento leggero. 

Se si usa una funzionalità IDE in un progetto non caricato, Visual Studio carica automaticamente il progetto o i progetti appropriati. Ad esempio, se si tenta di creare o aprire un diagramma classi per un progetto non aperto, Visual Studio carica automaticamente i progetti appropriati. Nelle sezioni seguenti viene fatto riferimento all'elenco dettagliato delle funzionalità.

Le sezioni seguenti descrivono come abilitare il caricamento leggero delle soluzioni e offrono informazioni utili per decidere se abilitare o meno la funzionalità.

## <a name="enable-or-disable-lightweight-solution-load"></a>Abilitare o disabilitare il caricamento leggero delle soluzioni

È possibile fare clic con il pulsante destro del mouse sul nome della soluzione in Esplora soluzioni e selezionare **Abilita il caricamento leggero delle soluzioni**. Dopo aver selezionato l'opzione, è necessario chiudere e riaprire la soluzione per attivare il carico leggero delle soluzioni.

> [!NOTE]
> La procedura per disabilitare il caricamento leggero delle soluzioni è simile. Per disabilitare il caricamento leggero delle soluzioni, selezionare **Disabilita il caricamento leggero delle soluzioni**, quindi chiudere e riaprire la soluzione. 

![Esplora soluzioni](../ide/media/VSIDE_LSL_Solution_Setting.png)

## <a name="global_solution_load_settings"></a>Configurare le impostazioni globali per il caricamento leggero delle soluzioni

È possibile disabilitare o configurare il caricamento leggero delle soluzioni per tutte le soluzioni scegliendo **Strumenti > Opzioni > Progetti e soluzioni**.

![Finestra di dialogo Strumenti Opzioni](../ide/media/VSIDE_LightweightSolutionLoad.png)

## <a name="how-does-lightweight-solution-load-work-behind-the-scenes"></a>Funzionamento del caricamento leggero delle soluzioni

Quando si carica la soluzione, Visual Studio carica solo i progetti aperti precedentemente. Tutti gli altri progetti sono visibili in Esplora soluzioni ma non vengono caricati. Quando si espande un progetto o si fa clic con il pulsante destro del mouse su un progetto, Visual Studio carica automaticamente il progetto. Il caricamento automatico dei progetti richiede in genere meno di un secondo, ma può risultare più lungo per alcuni progetti.
Visual Studio abilita tuttavia le funzionalità IDE come la ricerca, il debug, la compilazione e il controllo del codice sorgente disponibili nell'intera soluzione. È possibile, ad esempio, effettuare una ricerca nell'intera soluzione anche se sono stati caricati soltanto alcuni progetti in modalità di caricamento leggero. 

Quando si espandono più progetti, Visual Studio memorizza l'elenco dei progetti espansi. Quando la soluzione viene riaperta, Visual Studio carica automaticamente i progetti espansi in precedenza.

## <a name="visual-studio-prompts-developers-likely-to-see-significant-performance-gains"></a>Visual Studio offre agli sviluppatori vantaggi significativi in termini di prestazioni

In base ai dati di telemetria di Visual Studio, la modalità di caricamento leggero delle soluzioni offre vantaggi significativi per le soluzioni di grandi dimensioni con più di 30 progetti. Per questa ragione si consiglia agli sviluppatori che usano soluzioni di grandi dimensioni di provare la modalità di caricamento leggero delle soluzioni. La maggior parte degli sviluppatori che prova per la prima volta la modalità di caricamento leggero delle soluzioni finisce con l'usarla regolarmente. 

I dati di telemetria relativi all'utilizzo di Visual Studio vengono costantemente tenuti sotto controllo per migliorare l'euristica e offrire la modalità di caricamento leggero delle soluzioni agli sviluppatori che potrebbero trarne maggiori vantaggi. 

## <a name="visual-studio-makes-recommendations-to-turn-on-lightweight-solution-load-based-on-heuristics"></a>Visual Studio suggerisce l'attivazione del caricamento leggero delle soluzioni in base all'euristica

Per impostazione predefinita, Visual Studio attiva la modalità di caricamento leggero delle soluzioni per gli utenti che hanno maggiore possibilità di trarne vantaggio. Se si usano più soluzioni, Visual Studio offre la modalità di caricamento leggero delle soluzioni alle soluzioni che possono trarne maggiori vantaggi in termini di prestazioni. Se si seleziona l'opzione della modalità di caricamento leggero che **consente a Visual Studio di scegliere l'opzione migliore per la soluzione** (opzione predefinita), Visual Studio potrebbe aprire la soluzione in modalità di caricamento leggero in base all'euristica. Una barra messaggi indica se la soluzione è in modalità di caricamento leggero. Quando viene visualizzata la barra dei messaggi, è possibile visualizzare altre informazioni o aggiornare le impostazioni.

![Finestra popup](../ide/media/VSIDE_LSL_Popup.png)

## <a name="ide-features-fully-supported-in-lightweight-mode"></a>Funzionalità IDE completamente supportate in modalità di caricamento leggero

|Funzionalità|Supportata in modalità di caricamento leggero|
|-|-|-|
|IntelliSense|Sì|
|Cerca|Sì|
|Debug|Sì|
|Compilazione|Sì|
|Esplorazione codice (Vai a definizione e Trova tutti i riferimenti)|Sì|
|CodeLens|Sì|
|Analisi codice statico|Sì|
|Distribuisci e Pubblica|Sì|
|Aggiunta e rimozione dei riferimenti|Sì|
|Multitargeting|Sì|
|IntelliTrace|Sì|
|Live Unit Testing|Sì|
|IntelliTest|Sì|
|Microsoft Fakes|Sì|
|Modifica e continuazione|Non supportato|
|Testing unità|Richiede il caricamento dei progetti di test seguito dalla compilazione di una soluzione|

## <a name="scenarios-in-which-lightweight-solution-loads-the-appropriate-projects-to-complete-the-operation"></a>Scenari in cui il caricamento leggero delle soluzioni carica il progetto o i progetti appropriati per completare l'operazione

Se un progetto in una soluzione non viene usato, il progetto non viene caricato in modalità di caricamento leggero. Per alcune funzionalità, i progetti aggiuntivi vengono caricati automaticamente per supportare lo scenario della funzionalità. (Si intende ridurre al minimo l'elenco degli scenari. ) Per questi scenari, Visual Studio carica i progetti oppure richiede di caricare i progetti necessari.

|Categoria|Problema|
|-|-|-|
|Unit test|I progetti non caricati non vengono visualizzati nell'elenco dei progetti di test per le procedure guidate "Crea IntelliTest" e "Crea unit test". </br>È necessario caricare i progetti per cui si vuole creare test (è possibile espandere il nodo del progetto per caricare il progetto).|
|Diagrammi classi|Se si crea o si apre un diagramma classi di un progetto, Visual Studio carica automaticamente i progetti che sono dipendenze dirette del progetto. </br>Se non viene caricata l'intera soluzione, viene disattivata la convalida degli elementi obsoleti a cui fa riferimento un diagramma di convalida delle dipendenze.|

## <a name="scenarios-in-which-lightweight-solution-loads-the-entire-solution"></a>Scenari in cui il caricamento leggero delle soluzioni carica l'intera soluzione 

Per alcune funzionalità, Visual Studio carica automaticamente l'intera soluzione per supportare lo scenario. Questa azione garantisce la disponibilità di tutte le funzionalità. Ad esempio, alcune operazioni TFS possono richiedere il caricamento dell'intera soluzione. Per rendere disponibili tutte le funzionalità, Visual Studio carica l'intera soluzione.

|Categoria|Scenario|
|-|-|-|
|Comando SCC TFS nel nodo della soluzione|Se viene attivato un comando SCC nel nodo della soluzione in Esplora soluzioni, Visual Studio carica automaticamente l'intera soluzione prima di eseguire il comando.|
|Caricamento del progetto|Se la soluzione contiene progetti .NET Core e progetti condivisi, Visual Studio carica sempre automaticamente questi progetti durante il caricamento iniziale delle soluzioni. Questi progetti non supportano attualmente la modalità di caricamento leggero.|
|Gestione configurazione della soluzione|Se si usa Gestione configurazione della soluzione o la compilazione batch, Visual Studio carica automaticamente l'intera soluzione per offrire un'esperienza completa.|
|Gestione pacchetti NuGet|Se si apre l'interfaccia utente o la console di Gestione pacchetti NuGet, Visual Studio carica automaticamente l'intera soluzione per offrire un'esperienza completa.|

## <a name="known-issues"></a>Problemi noti

È possibile che alcuni scenari non funzionino in modalità di caricamento leggero delle soluzioni e richiedano il caricamento di progetti aggiuntivi o dell'intera soluzione. Questo problema è in fase di risoluzione. 

|Categoria|Problema|Soluzione alternativa|
|-|-|-|-|
|IntelliSense|IntelliSense potrebbe non essere aggiornato dopo una modifica della configurazione, ad esempio dopo la modifica di una build di versione in debug e viceversa. L'impatto dipende dalle differenze di codice causate dalla modifica della configurazione.|Ricaricare la soluzione dopo la modifica della configurazione.|
|Limitazioni del refactoring per i progetti C#/VB|Le correzioni del codice che modificano i file di progetto potrebbero non essere eseguite automaticamente la prima volta.|Se è necessario eseguire correzioni del codice nei file dei progetti, caricare i progetti. La modalità di caricamento leggero non esegue correzioni per i progetti non caricati.|
|Individuazione di unit test|I test individuati nei progetti posticipati non vengono eseguiti quando un progetto viene caricato manualmente.|Ricompilare il progetto per individuare nuovamente i test e rieseguire i test selezionati.|
|Live Unit Testing (LUT)|È possibile che in modalità di caricamento leggero delle soluzioni LUT non sia attivato. LUT non è attivato perché richiede il caricamento di uno dei progetti di test.|Caricare un progetto di test per attivare Live Unit Testing per la soluzione.|
|Ricerca in Esplora soluzioni|1.    In modalità di caricamento leggero delle soluzioni la funzione di ricerca di Esplora soluzioni non effettua la ricerca all'interno dei file e non sono disponibili risultati sulla progressione, ovvero nell'albero della ricerca vengono visualizzati solo i file ma non le classi, i metodi, ecc.</br>2.    Tutti i file appartenenti a un progetto vengono visualizzati come elenco semplice anziché come visualizzazione albero. Quando i file appartengono a una cartella di un progetto, viene visualizzato il percorso relativo del file anziché il nome del file nella visualizzazione ricerca.</br>Non sono disponibili menu di scelta rapida per le voci relative ai file nella visualizzazione di ricerca.|Caricare l'intera soluzione in una modalità diversa dalla modalità di caricamento leggero delle soluzioni per usare la normale funzionalità di ricerca di Esplora soluzioni.</br>È anche possibile usare la funzionalità di ricerca IDE di Visual Studio.|
|Visualizzatore oggetti per i progetti C++|Il Visualizzatore oggetti visualizza i riferimenti all'assembly/WinMD solo per i progetti caricati.|Caricare i progetti di cui visualizzare le informazioni nel Visualizzatore oggetti.|

> [!Note]
> Grazie alle partnership, le estensioni più comuni, inclusa Resharper, funzionano correttamente con il caricamento leggero delle soluzioni.

Diverse innovazioni ottimizzano le prestazioni del tempo di caricamento delle soluzioni per gli sviluppatori. Poiché si tratta di una nuova funzionalità, i suggerimenti dei clienti vengono esaminati attentamente e vengono risolti i problemi noti. Grazie per la collaborazione. È possibile contattare il team di ottimizzazione del caricamento delle soluzioni all'indirizzo lslsupport@microsoft.com

## <a name="see-also"></a>Vedere anche
[Suggerimenti sulle prestazioni di Visual Studio](../ide/visual-studio-performance-tips-and-tricks.md)
