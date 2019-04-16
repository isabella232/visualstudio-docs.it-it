---
title: Log delle modifiche (Visual Studio Tools per Unity, Windows) | Microsoft Docs
ms.custom: ''
ms.date: 04/02/2019
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: ea490b7e-fc0d-44b1-858a-a725ce20e396
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 8a8fd54b15381298542f710cbffa81cd9e0295fe
ms.sourcegitcommit: 36f5ffd6ae3215fe31837f4366158bf0d871f7a9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/08/2019
ms.locfileid: "59232762"
---
# <a name="change-log-visual-studio-tools-for-unity-windows"></a>Log delle modifiche (Visual Studio Tools per Unity, Windows)
Registro delle modifiche di Visual Studio Tools per Unity.

## <a name="4005"></a>4.0.0.5
 Data di rilascio: 27 febbraio 2019

### <a name="bug-fixes"></a>Correzioni di bug

-   **Integrazione:**

    -   Correzione del rilevamento della versione di Visual Studio con il pacchetto di installazione.

    -   Rimozione degli assembly inutilizzati dal pacchetto di installazione.

## <a name="4004"></a>4.0.0.4
 Data di rilascio: 13 febbraio 2019

### <a name="new-features"></a>Nuove funzionalità

-   **Integrazione:**

    -   Aggiunta del supporto per rilevare correttamente i processi Unity durante l'installazione e per consentire al motore di installazione di gestire meglio i blocchi di file.
    
    -   Aggiornamento dell'API ScriptableObject.

## <a name="4003"></a>4.0.0.3
 Data di rilascio: 31 gennaio 2019

### <a name="new-features"></a>Nuove funzionalità

-   **Generazione del progetto:**

    -   I campi pubblici e serializzati non causeranno più avvisi. Sono stati soppressi automaticamente gli avvisi del compilatore CS0649 e IDE0051 nei progetti di Unity che creavano questi messaggi.

-   **Integrazione:**

    -   Miglioramento dell'esperienza utente per visualizzare le istanze dell'editor di Unity e del lettore (le finestre sono ora ridimensionabili, usano margini uniformi e visualizzano un controllo di ridimensionamento). Aggiunta di informazioni dall'ID del processo per gli editor di Unity.
    
    -   Aggiornamento dell'API MonoBehaviour.
    
-   **Valutazione:**

    -   Aggiunta del supporto per le funzioni locali.
    
    -   Aggiunta del supporto per le pseudovariabili (identificatori di eccezione e oggetto).

### <a name="bug-fixes"></a>Correzioni di bug

-   **Integrazione:**

    -   Correzione di un problema con i temi e le immagini del moniker.

    -   Solo scrittura nella finestra di output durante il debug, durante l'aggiornamento automatico del database degli asset.

    -   Correzione dei ritardi dell'interfaccia utente con il filtraggio della procedura guidata MonoBehaviour.
    
-   **Debugger:**

    -   Correzione per la lettura di attributi personalizzati per argomenti denominati quando si usano versioni meno recenti del protocollo.

## <a name="4002"></a>4.0.0.2
 Data di rilascio: 23 gennaio 2019

### <a name="bug-fixes"></a>Correzioni di bug

-   **Integrazione:**

    -   Correzione della generazione di build sperimentale.

    -   Correzione della gestione degli eventi del file di progetto per ridurre al minimo la pressione sul thread dell'interfaccia utente.

    -   Correzione del provider di completamento con modifiche al testo in modalità batch.
    
-   **Debugger:**

    -   Correzione della visualizzazione di messaggi di debug utente nel debugger collegato.

## <a name="4001"></a>4.0.0.1
 Data di rilascio: 10 dicembre 2018

### <a name="new-features"></a>Nuove funzionalità

-   **Valutazione:**

    -   Sostituzione di NRefactory a favore di Roslyn per la valutazione delle espressioni.

    -   Aggiunta del supporto per i puntatori: dereferenziazione, cast e aritmetica dei puntatori (sono richiesti sia Unity 2018.2+ che il nuovo runtime).

    -   Aggiunta del supporto per la visualizzazione dei puntatori di matrici (come nel C++). In un'espressione per puntatori aggiungere una virgola e il numero di elementi che si vogliono visualizzare.

    -   Aggiunta del supporto per i costrutti async.

-   **Integrazione:**
    
    -   Aggiunta del supporto per l'aggiornamento automatico dei database degli asset Unity al momento del salvataggio. Questa funzionalità è abilitata per impostazione predefinita e verrà attivata una ricompilazione sul lato di Unity quando si salva uno script in Visual Studio. È possibile disabilitare questa funzionalità in Strumenti\Opzioni\Strumenti per Unity\Aggiorna il database degli asset di Unity durante il salvataggio.

### <a name="bug-fixes"></a>Correzioni di bug

-   **Integrazione:**

    -   Correzione dell'attivazione del bridge quando Visual Studio non è selezionato come editor esterno preferito.

    -   Correzione della valutazione delle espressioni con espressioni in formato non valido o non supportate.

## <a name="4000"></a>4.0.0.0
 Data di rilascio: 4 dicembre 2018

### <a name="new-features"></a>Nuove funzionalità

-   **Integrazione:**

    -   Aggiunta del supporto per Visual Studio 2019.

    -   Adozione del servizio immagini e del catalogo di Visual Studio, con supporto completo per ridimensionamento HDPI, immagini perfette al pixel e temi.

### <a name="deprecated-features"></a>Funzionalità deprecate

-   **Integrazione:**

    -   Da ora in poi, Visual Studio Tools per Unity supporterà solo Unity 5.2+ (con l'integrazione di Visual Studio predefinita di Unity).

    -   Da ora in poi, Visual Studio Tools per Unity supporterà solo Visual Studio 2015+.

    -   Rimozione del servizio di linguaggio, dell'elenco di errori e della barra di stato legacy.
    
    -   Rimozione della procedura guidata rapida Monobehaviour (a favore del supporto dedicato di IntelliSense).

## <a name="3903"></a>3.9.0.3
 Data di rilascio: 28 novembre 2018

### <a name="bug-fixes"></a>Correzioni di bug

-   **Integrazione:**

    -   Correzione di problemi di ricaricamento dei progetti e di IntelliSense durante l'aggiunta o la rimozione degli script che si trovano nel primissimo progetto.

## <a name="3902"></a>3.9.0.2
 Data di rilascio: 19 novembre 2018

### <a name="bug-fixes"></a>Correzioni di bug

-   **Debugger:**

    -   Correzione di un deadlock nella libreria usata per comunicare con il motore di debugger di Unity, che blocca Visual Studio o Unity, in particolare al raggiungimento di "Collega a Unity" o al riavvio del gioco.

## <a name="3901"></a>3.9.0.1
 Data di rilascio: 15 novembre 2018

### <a name="bug-fixes"></a>Correzioni di bug

-   **Integrazione:**

    -   Correzione dell'attivazione del plug-in Unity quando veniva selezionato un altro editor predefinito.

## <a name="3900"></a>3.9.0.0
 Data di rilascio: 13 novembre 2018

### <a name="bug-fixes"></a>Correzioni di bug

-   **Generazione del progetto:**

    -   Eseguito il rollback della soluzione alternativa per un bug delle prestazioni di Unity che è stato risolto da Unity.

## <a name="3807"></a>3.8.0.7
 Rilascio: 20 settembre 2018

### <a name="bug-fixes"></a>Correzioni di bug

-   **Debugger:**

    -   (Backporting dalla versione 3.9.0.2) Correzione di un deadlock nella libreria usata per comunicare con il motore di debugger di Unity, che blocca Visual Studio o Unity, in particolare al raggiungimento del collegamento a Unity o al riavvio del gioco.

## <a name="3806"></a>3.8.0.6
 Data di rilascio: 27 agosto 2018

### <a name="bug-fixes"></a>Correzioni di bug

-   **Integrazione:**

    -   Correzione di ricaricamento di progetti e soluzione.

## <a name="3805"></a>3.8.0.5
 Data di rilascio: 20 agosto 2018

### <a name="bug-fixes"></a>Correzioni di bug

-   **Integrazione:**

    -   Correzione dell'eliminazione della sottoscrizione di monitoraggio del progetto.

## <a name="3804"></a>3.8.0.4
 Data di rilascio: 14 agosto 2018

### <a name="new-features"></a>Nuove funzionalità

-   **Valutazione:**

    -   Aggiunta del supporto per i valori del puntatore.

    -   Aggiunta del supporto per metodi generici.

### <a name="bug-fixes"></a>Correzioni di bug

-   **Integrazione:**

    -   Ricarica rapida con modifica su più progetti.

## <a name="3803"></a>3.8.0.3
 Data di rilascio: 24 luglio 2018

### <a name="bug-fixes"></a>Correzioni di bug

-   **Generazione del progetto:**

    -   (Backporting dalla versione 3.9.0.0) Eseguito il rollback della soluzione alternativa per un bug delle prestazioni di Unity che è stato risolto da Unity.

## <a name="3802"></a>3.8.0.2
 Data di rilascio: 7 luglio 2018

### <a name="bug-fixes"></a>Correzioni di bug

-   **Generazione del progetto:**

    -   Soluzione alternativa temporanea per un bug delle prestazioni Unity: memorizzazione nella cache di MonoIsland durante la generazione di progetti.

## <a name="3801"></a>3.8.0.1
 Data di rilascio: 26 giugno 2018

### <a name="new-features"></a>Nuove funzionalità

-   **Debug:**

    -   Aggiunta del supporto per i comandi UserLog e UserBreak.

    -   Aggiunta del supporto di tipo-caricamento lazy (ottimizzazione della latenza del carico di rete e della risposta del debugger).

### <a name="bug-fixes"></a>Correzioni di bug

-   **Valutazione:**

    -   Ricerca metodo e valutazione dell'espressione dell'operatore binario migliorati.

## <a name="3800"></a>3.8.0.0
 Data di rilascio: 30 maggio 2018

### <a name="new-features"></a>Nuove funzionalità

-   **Debug:**

    -   Aggiunta del supporto per la visualizzazione delle variabili nei costrutti asincroni.

    -   Aggiunta del supporto per l'elaborazione di tipi nidificati quando si impostano i punti di interruzione, per impedire gli avvisi con i costrutti del compilatore.

-   **Integrazione:**

    -   Aggiunta del supporto per le grammatiche di TextMate per Shader (il carico di lavoro C++ non è più necessario per la colorazione del codice di Shader).

### <a name="bug-fixes"></a>Correzioni di bug

-   **Generazione del progetto:**

    -   Non convertire più pdb portabili a mdb quando si usa il nuovo runtime di Unity.

## <a name="3701"></a>3.7.0.1
 Data di rilascio: 7 maggio 2018

### <a name="bug-fixes"></a>Correzioni di bug

-   **Programma di installazione:**

    -   Correzione di un problema di dipendenza durante l'uso di build sperimentali.

## <a name="3700"></a>3.7.0.0
 Data di rilascio: 7 maggio 2018

### <a name="new-features"></a>Nuove funzionalità

-   **Debug:**

    -   Aggiunta del supporto per il debug orchestrato (debug di più lettori/editor con la stessa sessione di Visual Studio).

    -   Aggiunta del supporto per il debug del lettore USB Android.

    -   Aggiunta del supporto per il debug del lettore UWP/IL2CPP.

-   **Valutazione:**

    -   Aggiunta del supporto per gli identificatori esadecimali.

    -   Miglioramento dell'esperienza di valutazione della finestra delle espressioni di controllo.

### <a name="bug-fixes"></a>Correzioni di bug

-   **Integrazione:**

    -   Correzione dell'utilizzo delle impostazioni di eccezione.

-   **Generazione del progetto:**

    -   Esclusione delle unità di compilazione di gestione pacchetti dalla generazione.

## <a name="3605"></a>3.6.0.5
 Data di rilascio: 13 marzo 2018

### <a name="new-features"></a>Nuove funzionalità

-   **Generazione del progetto:**

    -   Aggiunta del supporto per il nuovo generatore di progetti in Unity 2018.1.

### <a name="bug-fixes"></a>Correzioni di bug

-   **Integrazione:**

    -   Correzione della gestione degli stati danneggiati con progetti personalizzati.

-   **Debugger:**

    -   Correzione dell'impostazione dell'istruzione successiva.

## <a name="3604"></a>3.6.0.4
 Data di rilascio: 5 marzo 2018

### <a name="bug-fixes"></a>Correzioni di bug

-   **Generazione del progetto:**

    -   Correzione del rilevamento della versione di Mono.

-   **Integrazione:**

    -   Correzione dei problemi di tempistica per l'attivazione di 2018.1 e plug-in.

## <a name="3603"></a>3.6.0.3
 Data di rilascio: 23 febbraio 2018

### <a name="new-features"></a>Nuove funzionalità

-   **Generazione del progetto:**

    -   Aggiunta del supporto per .NET Standard.

### <a name="bug-fixes"></a>Correzioni di bug

-   **Generazione del progetto:**

    -   Correzione del rilevamento del framework di destinazione Unity.

-   **Debugger:**

    -   Correzione dell'interruzione per eccezioni generate al di fuori del codice utente.

## <a name="3602"></a>3.6.0.2
 Data di rilascio: 7 febbraio 2018

### <a name="new-features"></a>Nuove funzionalità

-   **Integrazione:**

    -   Aggiornamento della superficie dell'API UnityMessage per 2017.3.

### <a name="bug-fixes"></a>Correzioni di bug

-   **Integrazione:**

    -   I progetti vengono ricaricati solo per modifiche esterne (con limitazione).

## <a name="3601"></a>3.6.0.1
 Data di rilascio: 24 gennaio 2018

### <a name="bug-fixes"></a>Correzioni di bug

-   **Integrazione:**

    -   Correzione della conversione automatica dei simboli di debug da pdb a mdb.

    -   Correzione della chiamata indiretta a EditorPrefs.GetBool con effetti sul controllo durante il tentativo di modifica delle dimensioni della matrice.

## <a name="3600"></a>3.6.0.0
 Data di rilascio: 10 gennaio 2018

### <a name="new-features"></a>Nuove funzionalità

-   **Generazione del progetto:**

    -   Aggiunta del supporto per il modello di riferimento MonoIsland 2018.1.

-   **Valutazione:**

    -   Aggiunta del supporto per l'identificatore $exception.

-   **Debugger:**

    -   Aggiunta del supporto per gli attributi DebuggerHidden/DebuggerStepThrough con il nuovo runtime di Unity.

-   **Procedure guidate:**

    -   Introduzione della versione 'Latest' per le procedure guidate.

### <a name="bug-fixes"></a>Correzioni di bug

-   **Generazione del progetto:**

    -   Correzione del calcolo del GUID di progetto per i progetti di lettore.

-   **Debugger:**

    -   Correzione di una race condition nella gestione degli eventi di interruzione.

-   **Procedure guidate:**

    -   Aggiornamento del contesto roslyn prima dell'inserimento del metodo.

## <a name="3503"></a>3.5.0.3
 Data di rilascio: 9 gennaio 2018

### <a name="bug-fixes"></a>Correzioni di bug

-   **Integrazione:**

    -   Correzione della conversione automatica dei simboli di debug da pdb a mdb.

## <a name="3502"></a>3.5.0.2
 Data di rilascio: 4 dicembre 2017

### <a name="new-features"></a>Nuove funzionalità

-   **Integrazione:**

    -   I progetti Unity vengono ora ricaricati automaticamente in Visual Studio quando si aggiunge o rimuove uno script da Unity.

-   **Debugger:**

    -   È stata aggiunta un'opzione che consente di eseguire il debug dell'editor di Unity tramite il debugger Mono condiviso da Xamarin e Visual Studio per Mac.

    -   È stato aggiunto il supporto per i file di simboli di debug portatili.

### <a name="bug-fixes"></a>Correzioni di bug

-   **Integrazione:**

    -   Sono stati corretti problemi relativi alle dipendenze di installazione.

    -   È stata corretta la mancata visualizzazione del menu della Guida dell'API di Unity.

-   **Generazione del progetto:**

    -   È stata corretta la generazione di un progetto giocatore quando si lavora a un gioco UWP con il back-end IL2CPP/.NET 4.6.

    -   È stato corretto il problema dell'aggiunta di estensioni dll in eccesso al nome del file di assembly.

    -   È stato corretto l'utilizzo del livello di compatibilità di un'API di un progetto specifico anziché del livello di compatibilità globale.

    -   Non forzare il flag Unity AllowAttachedDebuggingOfEditor Unity, il cui valore predefinito è ora 'true'.

## <a name="3402"></a>3.4.0.2
 Data di rilascio: 19 settembre 2017

### <a name="new-features"></a>Nuove funzionalità

-   **Generazione del progetto:**

    -   Supporto aggiunto per le unità di compilazione assembly.json.

    -   La copia delle assembly dell'unità per la cartella del progetto è stata arrestata.

-   **Debugger:**

    -   Supporto aggiunto per l'impostazione dell'istruzione successiva con il nuovo runtime dell'unità.

    -   Supporto aggiunto per il tipo di decimale con il nuovo runtime dell'unità.

    -   Supporto aggiunto per le conversioni implicite/esplicite.

### <a name="bug-fixes"></a>Correzioni di bug

-   **Valutazione:**

    -   Creazione della matrice di Fixed con dimensioni implicite.

    -   Il compilatore di Fixed ha generato degli elementi con variabili locali.

-   **Generazione del progetto:**

    -   Riferimento di Fixed a Microsoft.CSharp per il livello API 4.6.

## <a name="3302"></a>3.3.0.2
 Data di rilascio 15 agosto 2017

### <a name="bug-fixes"></a>Correzioni di bug

-   **Generazione del progetto:**

    -   È stata corretta la generazione della soluzione Visual Studio in Unity 5.5 e versioni precedenti.

## <a name="3300"></a>3.3.0.0
 Data di rilascio: 14 agosto 2017

### <a name="new-features"></a>Nuove funzionalità

-   **Valutazione:**

    -   Supporto aggiunto per la creazione di struct con il nuovo runtime dell'unità.

    -   Supporto minimo aggiunto per i puntatori.

### <a name="bug-fixes"></a>Correzioni di bug

-   **Valutazione:**

    -   Chiamata del metodo di Fixed sulle primitive.

    -   Valutazione del campo di Fixed con tipi contrassegnati con BeforeFieldInit.

    -   Chiamate non supportate di Fixed con operatori binari (sottrarre).

    -   Problemi di Fixed quando si aggiungono elementi all'espressione di controllo di Visual Studio.

-   **Generazione del progetto:**

    -   Riferimenti ai nomi assembly di Fixed con i file mcs.rsp.

    -   Fixed è definito con i livelli di API.

## <a name="3200"></a>3.2.0.0
 Data di rilascio: 10 maggio 2017

### <a name="new-features"></a>Nuove funzionalità

-   **Programma di installazione:**

    -   Supporto aggiunto per la pulizia della cache MEF.

### <a name="bug-fixes"></a>Correzioni di bug

-   **Editor del codice:**

    -   Classificazione/completamento di Fixed con gli attributi personalizzati.

    -   Sfarfallio di Fixed con messaggi di Unity.

## <a name="3100"></a>3.1.0.0
 Data di rilascio: 7 aprile 2017

### <a name="new-features"></a>Nuove funzionalità

-   **Debugger:**

    -   Aggiunto il supporto per il nuovo runtime di Unity, compatibile con .NET 4.6 / C# 6.

-   **Generazione del progetto:**

    -   Aggiunta del supporto per il profilo .NET 4.6.

    -   Aggiunta del supporto per i file con estensione mcs.rsp.

    -   Abilita sempre l'opzione di compilazione non sicura quando viene usato Unity 5.6.

    -   Aggiunto il supporto per la generazione del progetto "Player" quando si usa la piattaforma Windows Store e il back-end il2cpp.

### <a name="bug-fixes"></a>Correzioni di bug

-   **Editor del codice:**

    -   Corretta la posizione del cursore dopo l'inserimento del metodo con completamento automatico.

-   **Generazione del progetto:**

    -   Eliminata la post-elaborazione della versione dell'assembly.

## <a name="3001"></a>3.0.0.1
 Data di rilascio: 7 aprile 2017

### <a name="this-version-includes-all-new-features-and-bug-fixes-introduced-with-28x-series"></a>Questa versione include tutte le nuove funzionalità e correzioni di bug introdotte con la serie 2.8.x.

## <a name="2820---30-preview-3"></a>2.8.2.0 (3.0 anteprima) 3
 Data di rilascio: 25 gennaio 2017

### <a name="bug-fixes"></a>Correzioni di bug

-   **Generazione del progetto:**

    -   Corretta la regressione dove veniva fatto riferimento ai progetti Plugins due volte, prima come DLL binario e poi come riferimento al progetto.

## <a name="2810---30-preview-2"></a>2.8.1.0 (3.0 anteprima) 2
 Data di rilascio: 23 gennaio 2017

### <a name="bug-fixes"></a>Correzioni di bug

-   **Editor del codice:**

    -   Corretto un arresto anomalo all'avvio di una dichiarazione di attributo senza completamento parentesi graffa.

-   **Debugger:**

    -   Corretti i punti di interruzione delle funzioni con coroutine sotto il nuovo compilatore/runtime Unity.

    -   Aggiunto un avviso in caso di punto di interruzione non associabile (quando non viene trovato alcun percorso di origine corrispondente).

-   **Generazione del progetto:**

    -   Corretta la generazione di file csproj con caratteri speciali/localizzati.

    -   Corretti i riferimenti esterni ad Asset, ad esempio Libreria (come Facebook SDK).

-   **Varie:**

    -   Aggiunto il controllo per impedire l'esecuzione di Unity durante l'installazione o la disinstallazione.

    -   Eseguito il passaggio a https per l'uso della documentazione remota di Unity.

## <a name="2800---30-preview"></a>2.8.0.0 (3.0 anteprima)
 Data di rilascio: 17 novembre 2016

### <a name="new-features"></a>Nuove funzionalità

-   **Generale:**

    -   Aggiunto il supporto per l'installazione di Visual Studio 2017.

    -   Aggiunto il supporto per l'estensione di Visual Studio 2017.

    -   Aggiunto il supporto per la localizzazione.

-   **Editor del codice:**

    -   Aggiunto IntelliSense C# per i messaggi di Unity.

    -   Aggiunta la colorazione del codice C# per i messaggi di Unity.

-   **Debugger:**

    -   Aggiunto il supporto per le espressioni `is`, `as`, cast diretto, `default`, `new`.

    -   Aggiunto il supporto per le espressioni string concat.

    -   Aggiunto il supporto per la visualizzazione esadecimale di valori Integer.

    -   Aggiunto il supporto per la creazione di nuove variabili temporanee (istruzioni).

    -   Aggiunto il supporto per le conversioni implicite di primitive.

    -   Aggiunti messaggi di errore più efficaci quando un tipo è previsto o non trovato.

-   **Generazione del progetto:**

    -   Rimosso il suffisso CSharp dai nomi di progetto.

    -   Rimosso il riferimento a un file di destinazioni di MSBuild a livello di sistema.

-   **Procedure guidate:**

    -   Aggiunto il supporto per i messaggi di Unity in tipi non Behaviour come Editor o EditorWindow.

    -   Eseguito il passaggio a Roslyn per inserire e formattare i messaggi di Unity.

### <a name="bug-fixes"></a>Correzioni di bug

-   **Debugger:**

    -   Risolto un bug con arresto anomalo di Unity durante la valutazione di tipi generici.

    -   Corretta la gestione dei tipi nullable.

    -   Corretta la gestione delle enumerazioni.

    -   Corretta la gestione dei tipi di membro annidato.

    -   Corretto l'accesso all'indicizzatore raccolta.

    -   Corretto il supporto per il debug dei frame di iteratore con il nuovo compilatore C#.

-   **Generazione del progetto:**

    -   Corretto il bug che impediva la compilazione quando si usava Unity Web Player.

    -   Corretto il bug che impediva la compilazione durante la compilazione di uno script con nome file con codifica Web.

## <a name="2300"></a>2.3.0.0
 Data di rilascio: 14 luglio 2016

### <a name="new-features"></a>Nuove funzionalità

-   **Generale:**

    -   Aggiunta un'opzione per disabilitare i log della console Unity nell'elenco errori di Visual Studio.

    -   Aggiunta un'opzione per consentire la modifica delle proprietà del progetto generato.

-   **Debugger:**

    -   Aggiunti i visualizzatori stringa per testo, XML, HTML e JSON.

-   **Procedure guidate:**

    -   Aggiunti i MonoBehaviour mancanti.

### <a name="bug-fixes"></a>Correzioni di bug

-   **Generale:**

    -   Risolto un conflitto con ReSharper che impediva la visualizzazione di controlli all'interno delle impostazioni di Visual Studio.

    -   Risolto un conflitto con Xamarin che impediva il debug in alcuni casi.

-   **Debugger:**

    -   Risolto un problema che causava il blocco di Visual Studio durante il debug.

    -   Risolto un problema con i punti di interruzione di funzione in Visual Studio 2015.

    -   Risolti diversi problemi di valutazione delle espressioni.

## <a name="2200"></a>2.2.0.0
 Data di rilascio: 4 febbraio 2016

### <a name="new-features"></a>Nuove funzionalità

-   **Procedure guidate:**

    -   Aggiunta della ricerca intelligente nella procedura guidata **Implement Monobehaviour** .

    -   Le procedure guidate ora riconoscono il contesto. Ad esempio, i messaggi NetworkBehavior sono disponibili solo quando si lavora con NetworkBehavior.

    -   Aggiunta del supporto per i messaggi NetworkBehavior nelle procedure guidate.

-   **Interfaccia utente:**

    -   Aggiunta di un'opzione per configurare la visibilità dei messaggi MonoBehavior.

    -   Rimozione delle pagine delle proprietà di Visual Studio non rilevanti per i progetti Unity.

### <a name="bug-fixes"></a>Correzioni di bug

-   **Generazione del progetto:**

    -   Correzione dei riferimenti a UnityEngine e UnityEditor in Unity 4.6.

    -   Correzione della generazione dei file di progetto in caso di esecuzione di Unity su OSX.

    -   Correzione della gestione dei nomi di progetto contenenti caratteri cancelletto (#).

    -   Limitazione dei progetti generati a C# 4.

-   **Debugger:**

    -   Risolto un problema relativo alla valutazione delle espressioni durante il debug all'interno di un coroutine Unity.

    -   Risolto un problema che causava il blocco di Visual Studio durante il debug.

-   **Interfaccia utente:**

    -   Risolto un problema di incompatibilità con l'estensione di Visual Studio [Tabs Studio](https://tabsstudio.com/) .

-   **Programma di installazione:**

    -   Supporto dell'installazione a livello di computer di VSTU (installazione per tutti gli utenti) mediante la creazione di voci del Registro di sistema HKLM.

    -   Risoluzione dei problemi con la disinstallazione di VSTU quando viene installata la stessa versione di VSTU per più versioni diverse di Visual Studio. Ad esempio, quando sono installati sia VSTU **2015** 2.1.0.0 che VSTU **2013** 2.1.0.0.

## <a name="2100"></a>2.1.0.0
 Data di rilascio: 8 settembre 2015

### <a name="new-features"></a>Nuove funzionalità

-   Supporto di Unity 5.2

### <a name="bug-fixes"></a>Correzioni di bug

-   Visualizzazione di voci di menu in Unity < 4.2

-   Non viene più visualizzato un messaggio di errore quando Visual Studio blocca i file XMLS IntelliSense.

-   Gestione di punti di interruzione condizionali <\<Se modificato>> quando l'argomento condizionale non è un valore booleano.

-   Correzione dei riferimenti agli assembly UnityEngine e UnityEditor per le app di Windows Store.

-   Correzione dell'errore di esecuzione dell'istruzione nel debugger: Impossibile eseguire l'istruzione. Eccezione generale.

-   Correzione dei punti di interruzione dei passaggi in Visual Studio 2015.

## <a name="2000"></a>2.0.0.0
 Data di rilascio: 20 luglio 2015

### <a name="bug-fixes"></a>Correzioni di bug

-   **Integrazione con Unity:**

    -   Correzione della conversione dei simboli di debug creati con Visual Studio 2015 durante l'importazione di una DLL e dei relativi simboli di debug (PDB).

    -   Vengono generati sempre file MDB durante l'importazione di una DLL e dei relativi simboli di debug (PDB), tranne quando viene fornito anche un file MDB.

    -   Correzione dell'inquinamento della directory di progetto Unity con una directory obj.

    -   Correzione della generazione di riferimenti a System.Xml.Link e System.Runtime.Serialization.

    -   Aggiunta del supporto di più sottoscrittori agli hook delle API di generazione di file di progetto.

    -   Viene sempre completata la generazione di file di progetto anche quando uno dei file da generare è bloccato.

    -   Aggiunta del supporto dei caratteri jolly * nel filtro delle estensioni quando si specificano i file da includere nel progetto C#.

-   **Integrazione con Visual Studio:**

    -   Risolto un problema di compatibilità con Productivity Power Tools.

    -   Correzione della generazione di MonoBehavior nelle dichiarazioni di eventi e delegati.

-   **Debugger:**

    -   Correzione di un blocco potenziale durante il debug.

    -   Risolto un problema di mancata visualizzazione delle variabili locali in alcuni stack frame.

    -   Correzione del controllo delle matrici vuote.

## <a name="1990---20-preview-2"></a>1.9.9.0 (2.0 anteprima) 2
 Data di rilascio: 2 aprile 2015

### <a name="new-features"></a>Nuove funzionalità

-   **Esplora progetti Unity:**

    -   Ridenominazione automatica della classe quando si rinomina un file in Esplora progetti Unity (vedere la finestra di dialogo **Opzioni** ).

    -   Selezione automatica dei nuovi script creati in Esplora progetti Unity.

    -   Rilevamento dello script attivo in Esplora progetti Unity (vedere la finestra di dialogo **Opzioni** ).

    -   Doppia sincronizzazione di Esplora soluzioni di Visual Studio (vedere la finestra di dialogo **Opzioni** ).

    -   Adozione delle icone di Visual Studio in Esplora progetti Unity.

-   **Debugger:**

    -   Possibilità di selezionare la destinazione di debug attiva da un elenco di destinazioni salvate o usate di recente (vedere la finestra di dialogo **Opzioni** ).

    -   Creazione di punti di interruzione delle funzioni in metodi MonoBehavior e loro applicazione a più classi MonoBehavior.

    -   Supporto di Crea ID oggetto nel debugger.

    -   Supporto del numero di passaggi del punto di interruzione nel debugger.

    -   Supporto dell'interruzione in caso di eccezioni nel debugger (sperimentale. Vedere la finestra di dialogo **Opzioni** ).

    -   Supporto della creazione di oggetti e matrici durante la valutazione di espressioni nel debugger.

    -   Supporto dei confronti Null durante la valutazione di espressioni nel debugger.

    -   Possibilità di escludere membri obsoleti nelle finestre delle espressioni di controllo del debugger.

-   **Programma di installazione:**

    -   Ottimizzazione della registrazione delle estensioni di Visual Studio Tools per Unity.

    -   Installazione del pacchetto Visual Studio Tools per Unity per Unity 5.

-   **Documentazione:** Miglioramento delle prestazioni di generazione della documentazione.

-   **Procedure guidate:** Supporto dei nuovi metodi MonoBehavior per Unity 4.6 e Unity 5.

-   **Unity:** Ricerca di flag non sicuri e definizioni personalizzate nei file RSP durante la generazione dei file di progetto.

-   **Interfaccia utente:** Aggiunta della finestra di dialogo **Opzioni** di Visual Studio Tools per Unity in Visual Studio.

### <a name="bug-fixes"></a>Correzioni di bug

-   **Esplora progetti Unity:**

    -   Aggiornamento di Esplora progetti Unity dopo lo spostamento o la ridenominazione dei file in Esplora soluzioni di Visual Studio.

    -   Mantenimento delle selezioni quando i file vengono rinominati in Esplora progetti Unity.

    -   Disattivazione dell'espansione e della compressione automatiche quando si fa doppio clic sui file in Esplora progetti Unity.

    -   Possibilità di visualizzare in Esplora progetti Unity i nuovi file selezionati.

-   **Debugger:**

    -   Risoluzione di un possibile problema di blocco di Visual Studio durante la valutazione di espressioni nel debugger.

    -   Le chiamate dei metodi vengono sempre eseguite nel dominio corretto nel debugger.

-   **Unity:**

    -   Correzione del percorso di UnityVS.OpenFile con Unity 5.

    -   Correzione del percorso di pdb2mdb con Unity 5.

    -   Correzione di una possibile eccezione durante la generazione dei file di progetto.

    -   Correzione di un possibile problema di blocco durante l'esecuzione di Unity su OSX.

    -   Gestione delle eccezioni interne.

    -   Invio dei log della console di Unity all'elenco degli errori di Visual Studio.

-   **Documentazione:** Correzione della generazione della documentazione per la nuova documentazione di Unity.

-   **Progetto:** Spostamento e ridenominazione dei file con estensione meta di Unity quando necessario, anche in cartelle.

-   **Procedure guidate:** Correzione dell'ordine dei parametri dei metodi MonoBehavior durante la generazione del codice.

-   **Interfaccia utente:** Supporto dei temi di Visual Studio per il menu di scelta rapida e le icone.

## <a name="1980---20-preview"></a>1.9.8.0 (2.0 anteprima)
 Data di rilascio: 12 novembre 2014

### <a name="new-features"></a>Nuove funzionalità

-   Supporto per Visual Studio 2015.

-   Colorazione del codice per shader Unity in Visual Studio 2015.

-   Miglioramento della visualizzazione dei valori durante il debug:

    -   Miglioramento della visualizzazione per ArrayLists, elenchi, tabelle hash e dizionari.

    -   Visualizzazione di membri non pubblici e statici come categorie in espressioni di controllo e visualizzazioni locali.

    -   Miglioramento della visualizzazione di SerializedProperty di Unity per valutare solo il campo del valore valido per la proprietà.

    -   Supporto di DebuggerDisplayAttribute per classi e struct.

    -   Supporto di DebuggerTypeProxyAttribute.

-   Inserimento dei metodi MonoBehaviour mediante le procedure guidate per rispettare le convenzioni per la scrittura di codice degli utenti.

-   Implementazione del supporto per modelli di testo in fase di compilazione in progetti generati con UnityVS.

-   Implementazione del supporto per risorse ResX in progetti generati con UnityVS.

-   Supporto dell'apertura di shader Visual Studio da Unity.

### <a name="bug-fixes"></a>Correzioni di bug

-   Pulizia dei socket prima di avviare il gioco in Unity dopo l'attivazione di Connetti ed Esegui in Visual Studio. Questa correzione risolve alcuni problemi di stabilità della connessione tra Unity e Visual Studio quando si usano le opzioni Connetti ed Esegui.

-   Mancata chiamata nell'interfaccia del debugger del motore di script di Unity di metodi che tendono a bloccare Unity. Questa correzione risolve il blocco di Unity durante il collegamento del debugger.

-   Correzione della visualizzazione degli stack di chiamate quando non è disponibile alcun simbolo.

-   Mancata registrazione del callback di log se non è necessario.

## <a name="1920"></a>1.9.2.0
 Data di rilascio: 9 ottobre 2014

### <a name="new-features"></a>Nuove funzionalità

-   Miglioramento del rilevamento dei lettori di Unity.

-   Quando si usa lo strumento di apertura dei file, Unity passa il numero di riga nonché il nome del file.

-   Visualizzazione predefinita della documentazione di Unity online se non è disponibile documentazione locale.

### <a name="bug-fixes"></a>Correzioni di bug

-   Correzione di un potenziale arresto anomalo di Unity al raggiungimento di un punto di interruzione dopo il ricaricamento di un dominio.

-   Correzione delle eccezioni visualizzate nella console di Unity quando si chiudono le finestre Configurazione o Informazioni su, dopo il ricaricamento di un dominio.

-   Correzione del rilevamento di Unity a 64 bit in esecuzione in locale.

-   Correzione dei filtri dei metodi MonoBehaviour per ogni versione di Unity nelle procedure guidate.

-   Correzione di un bug per cui tutte le risorse venivano incluse nei file di progetto se il filtro delle estensioni era vuoto.

## <a name="1910"></a>1.9.1.0
 Data di rilascio: 22 settembre 2014

### <a name="new-features"></a>Nuove funzionalità

-   Ottimizzazione dell'associazione dei punti di interruzione a percorsi di origine.

-   Supporto per i metodi di overload nella valutazione di espressioni del debugger.

-   Supporto per il boxing delle primitive e dei tipi di valore nella valutazione di espressioni del debugger.

-   Supporto per la ricreazione dell'ambiente delle variabili locali C# durante il debug di metodi anonimi.

-   Eliminazione e ridenominazione dei file con estensione meta durante l'eliminazione o la ridenominazione di file da Visual Studio.

### <a name="bug-fixes"></a>Correzioni di bug

-   Correzione della gestione dei temi di Visual Studio. Nelle versioni precedenti le finestre di dialogo su temi neri possono apparire vuote.

-   Correzione del blocco di Unity durante la connessione del debugger quando Unity è in fase di ricompilazione.

-   Correzione dei punti di interruzione durante il debug di editor o lettori remoti compilati su un altro sistema.

-   Correzione di un possibile arresto anomalo di Visual Studio quando viene raggiunto un punto di interruzione.

-   Correzione dell'associazione dei punti di interruzione per evitare che vengano visualizzati come non caricati.

-   Correzione della gestione dell'ambito delle variabili nel debugger per evitare variabili live indicate come esterne all'ambito.

-   Correzione della ricerca di membri statici nella valutazione di espressioni del debugger.

-   Correzione della visualizzazione dei tipi nella valutazione di espressioni del debugger in modo da mostrare proprietà e campi statici.

-   Correzione della generazione della soluzione quando i nomi di progetto Unity includono caratteri speciali non accettati da Visual Studio (problema Connect #948666).

-   Correzione del pacchetto Visual Studio Tools per Unity in modo da arrestare immediatamente l'invio di eventi della console dopo la deselezione dell'opzione (problema Connect #933357).

-   Correzione del rilevamento dei riferimenti per rigenerare correttamente riferimenti a nuove API come UnityEngine.UI in progetti generati con UnityVS.

-   Correzione del programma di installazione in modo da richiedere che Visual Studio venga chiuso prima dell'installazione, per evitare installazioni danneggiate.

-   Correzione del programma di installazione in modo da installare gli assembly di riferimento di Unity come componenti autonomi appropriati, condivisi tra tutte le versioni di VSTU.

-   Correzione dell'apertura di script con VSTU nelle versioni a 64 bit di Unity.

## <a name="1900"></a>1.9.0.0
 Data di rilascio: 29 luglio 2014

### <a name="new-features"></a>Nuove funzionalità

-   Aggiunta della possibilità di immettere una porta e un IP personalizzati di cui eseguire il debug nella finestra di collegamento del debugger di Unity.

-   Aggiunta dell'opzione di configurazione che consente di impostare Unity per l'esecuzione o meno in background.

-   Aggiunta dell'opzione di configurazione che consente di generare i file di progetto e della soluzione oppure solo i file di progetto.

-   Destinazione di avvio: possibilità di scegliere il collegamento a Unity o il collegamento a Unity e l'esecuzione.

-   Visualizzazione di matrici multidimensionali nel debugger.

-   Gestione di nuove porte di debug dei lettori di Unity.

-   Gestione dei riferimenti a nuovi assembly di Unity, come gli assembly GUI di Unity 4.6.

-   Annullamento della costruzione delle chiusure in modo da visualizzare correttamente variabili locali durante il debug.

-   Annullamento della costruzione di variabili di iteratori generati negli argomenti durante il debug.

-   Mantenimento dello stato di Esplora progetti Unity dopo il ricaricamento di un progetto.

-   Aggiunta di un comando per sincronizzare Esplora progetti Unity con il documento corrente.

### <a name="bug-fixes"></a>Correzioni di bug

-   Correzione dei punti di interruzione condizionali le cui condizioni vengono impostate prima dell'avvio del debugger.

-   Correzione dei riferimenti a UnityEngine per evitare la generazione di avvisi.

-   Correzione dell'analisi delle versioni per versioni beta di Unity.

-   Correzione di un problema che comportava la mancata visualizzazione delle variabili nella finestra delle variabili locali al raggiungimento di un punto di interruzione o durante l'esecuzione di istruzioni.

-   Correzione delle descrizioni comando delle variabili in Visual Studio 2013.

-   Correzione della generazione della documentazione di IntelliSense per Unity 4.5.

-   Correzione della comunicazione tra Unity e Visual Studio dopo il ricaricamento di un dominio (riproduzione/arresto in Unity).

-   Correzione della gestione di parti dei temi di Visual Studio.

> [!IMPORTANT]
>  Poiché C# è il linguaggio predominante nell'ecosistema Unity (le nuove risorse di esempio sono in C#, la documentazione di Unity sarà relativa a C# per impostazione predefinita), è stato rimosso il supporto tecnico di base per UnityScript e Boo in modo da concentrarsi meglio sull'esperienza in C#. Di conseguenza, le soluzioni VSTU sono ora solo in C# e vengono caricate molto più rapidamente.

## <a name="1820"></a>1.8.2.0
 Data di rilascio: 7 gennaio 2014

### <a name="new-features"></a>Nuove funzionalità

-   Risoluzione di un problema nel livello di rete del motore di script di Unity in Mavericks per l'individuazione remota degli editor.

-   Gestione di nuove porte per individuare lettori remoti di Unity.

-   Riferimento all'assembly UnityEngine specifico della destinazione di compilazione corrente.

-   Aggiunta di un'impostazione che consente di filtrare i file da includere nei progetti generati.

-   Aggiunta di un'impostazione che consente di disabilitare l'invio dei log della console all'elenco degli errori di Visual Studio. Questa impostazione è utile quando si usa PlayMaker o Console Pro, in quanto potrebbe essere registrato un solo callback in Unity per la ricezione dei log della console.

-   Aggiunta di un'impostazione che consente di disabilitare la generazione di simboli di debug MDB. Questa impostazione è utile se si genera personalmente il file MDB.

### <a name="bug-fixes"></a>Correzioni di bug

-   Correzione di una regressione per cui file aperti in Visual Studio da Unity >= 4.2 perdevano IntelliSense.

-   Correzione delle finestre di dialogo di Visual Studio per la gestione dei temi personalizzati.

-   Correzione della chiusura del menu di scelta rapida dell'ambiente di programmazione di Unity.

-   Risoluzione di un problema di arresto anomalo in Unity quando l'assembly generato specifico della versione non è sincronizzato.

## <a name="1810"></a>1.8.1.0
 Data di rilascio: 21 novembre 2013

### <a name="new-features"></a>Nuove funzionalità

-   Modifica delle procedure guidate MonoBehaviour con le API di Unity 4.3.

-   Le procedure guidate MonoBehaviour filtrano le API di Unity a seconda della versione usata.

-   Aggiunta di un riferimento a System.Xml.Linq ai progetti per Unity > 4.1.

-   Miglioramento delle chiamate a Debug.Log in modo da non includere l'inizio dell'analisi dello stack nel messaggio.

### <a name="bug-fixes"></a>Correzioni di bug

-   Correzione di un bug per cui si generava un'interferenza con la gestione predefinita di file JavaScript in Visual Studio.

-   Definitiva correzione di un pixel bianco visualizzato in Visual Studio.

-   Correzione dell'eliminazione dell'assembly UnityVS.VersionSpecific se è contrassegnato come di sola lettura da un server SCM.

-   Correzione delle eccezioni durante la creazione di socket nel pacchetto UnityVS.

-   Correzione di un arresto anomalo in Visual Studio durante il caricamento di immagini predefinite da assembly di Visual Studio.

-   Correzione di un bug nella generazione di UnityVS.VersionSpecific per le compilazioni di origine di Unity.

-   Correzione di un possibile blocco durante l'apertura di un socket nel pacchetto Unity.

-   Correzione della gestione dei progetti di Unity il cui nome contiene un trattino (-).

-   Correzione dell'apertura di script da Unity in modo da non confondere l'ordine ALT+TAB per Unity 4.2 e versioni successive.

## <a name="1800"></a>1.8.0.0
 Data di rilascio: 24 settembre 2013

### <a name="new-features"></a>Nuove funzionalità

-   Drastico miglioramento della velocità di connessione del debugger.

-   Gestione automatica della navigazione a file e righe in Unity 4.2 e versioni successive.

-   Punti di interruzione condizionali.

-   Il generatore di file di progetto gestisce ora modelli T4.

-   Aggiornamento delle procedure guidate MonoBehavior con nuove API.

-   Documentazione di IntelliSense in C# per tipi Unity.

-   Valutazione di espressioni aritmetiche e logiche.

-   Migliore individuazione degli editor remoti per l'anteprima di debug remoto.

### <a name="bug-fixes"></a>Correzioni di bug

-   Correzione di un bug che determinava la perdita di un thread in Visual Studio dopo la disconnessione del debugger.

-   Correzione di un pixel bianco visualizzato in Visual Studio.

-   Correzione della gestione dei clic sull'icona della barra di stato.

-   Correzione della generazione di riferimenti con assembly nelle cartelle dei plug-in.

-   Correzione della creazione di socket dal pacchetto UnityVS in caso di eccezioni.

-   Correzione del rilevamento di nuove versioni di UnityVS.

-   Correzione della richiesta della gestione licenze alla scadenza della licenza.

-   Correzione di un bug che poteva rendere vuoto l'elenco dei processi nella finestra di Visual Studio per il collegamento del debugger al processo.

-   Correzione della modifica dei valori booleani nella visualizzazione locale.

## <a name="1220"></a>1.2.2.0
 Data di rilascio: 9 luglio 2013

### <a name="bug-fixes"></a>Correzioni di bug

-   Gestione dei nomi completi nell'analizzatore di espressioni.

-   Correzione di un blocco correlato alla gestione delle eccezioni per cui il motore di script di Unity invia dati di stack frame non corretti.

-   Correzione del processo di compilazione per destinazioni Web.

-   Correzione di un possibile errore che si verificava se Visual Studio era avviato e un file eliminato era incluso nell'elenco dei file da aprire all'avvio.

-   Correzione di UnityVS.OpenFile in modo da gestire file non di script, come gli shader compilati.

-   Viene ora fatto riferimento a Boo.Lang e UnityScript.Lang da tutti i progetti C#.

-   Correzione della generazione di riferimenti nei progetti se il progetto contiene caratteri speciali.

-   Risoluzione di un problema di Visual Studio per cui le chiamate dei metodi a progetti eliminati attivavano più MessageBox NullReferenceException.

-   Correzione della gestione degli assembly di Unity 4.2 Beta.

## <a name="1210"></a>1.2.1.0
 Data di rilascio: 9 aprile 2013

### <a name="bug-fixes"></a>Correzioni di bug

-   Correzione della distribuzione locale degli assembly di Unity per il completamento del codice in caso di un errore di I/O (come file di sola lettura o file bloccati da Visual Studio).

-   Correzione di una regressione quando l'apertura di uno script da Unity non individuava il file se questo era già aperto in Visual Studio.

-   Correzione di un problema di prestazioni della nuova gestione delle eccezioni.

-   Correzione dell'associazione dei punti di interruzione in alcune DLL esterne.

## <a name="1200"></a>1.2.0.0
 Data di rilascio: 25 marzo 2013

### <a name="new-features"></a>Nuove funzionalità

-   Drastico miglioramento della velocità di connessione del debugger.

-   Ottimizzazione di Gestione progetti per Unity per progetti di grandi dimensioni.

-   Applicazione delle impostazioni di Visual Studio per l'interruzione (o la non interruzione) in corrispondenza di eccezioni gestite e non gestite.

-   Applicazione dell'impostazione di Visual Studio per la chiamata di ToString in variabili locali.

-   Aggiunta del nuovo menu Debug -> Associa debugger Unity, che consente di eseguire il debug di lettori di Unity.

-   Mantenimento dei progetti personalizzati aggiunti alla soluzione UnityVS al momento della generazione dei file della soluzione.

-   Aggiunta dei nuovi tasti di scelta rapida CTRL+ALT+M -> CTRL+H per visualizzare la documentazione di Unity per la funzione o il membro di Unity in corrispondenza del punto di inserimento.

-   Considerazione dei file di risposta del compilatore (RSP) durante la compilazione da Visual Studio.

-   Annullamento della costruzione dei tipi generati dal compilatore per mostrare le variabili durante il debug dei metodi del generatore.

-   Semplificazione del debug remoto attraverso l'eliminazione della necessità di configurare una cartella condivisa in Unity. È ora sufficiente avere accesso al progetto di Unity da Windows.

-   Installazione di un profilo di Unity personalizzato come profilo di destinazione .NET standard. In questo modo, vengono corretti tutti i falsi positivi eventualmente indicati da ReSharper.

-   Risoluzione di un bug del motore di script di Unity, in modo che il debugger non generi un'interruzione in corrispondenza di thread registrati non correttamente.

-   Rielaborazione dello strumento di apertura dei file per evitare una race condition in Visual Studio per cui si dichiarava in grado di aprire i file ma si arrestava in modo anomalo alla richiesta di apertura dei file.

-   UnityVS richiede ora di aggiornare la compilazione quando durante la compilazione del progetto in Visual Studio e non più al momento del salvataggio dei file.

### <a name="bug-fixes"></a>Correzioni di bug

-   Correzione del profilo .NET personalizzato.

-   Correzione dell'integrazione dei temi, che corregge i problemi relativi al tema scuro di Visual Studio 2012.

-   Correzione del collegamento di comportamento rapido in Visual Studio 2012.

-   Correzione di un problema di esecuzione di istruzioni che poteva verificarsi durante il debug quando un thread non principale raggiungeva un punto di interruzione.

-   Correzione del completamento degli alias dei tipi da parte di UnityScript e Boo, tra cui int.

-   Correzione dell'eccezione durante la scrittura di una nuova stringa UnityScript o Boo.

-   Correzione delle eccezioni nei menu di Unity quando una soluzione non veniva caricata.

-   Correzione del bug UVS-48 per cui la digitazione di virgolette doppie produceva talvolta un errore e interrompeva la funzione (completamento del codice, evidenziazione della sintassi e così via).

-   Correzione del bug UVS-46: File di script aperto duplicato (UnityScript) facendo clic sull'Elenco errori di Visual Studio.

-   Correzione del bug UVS-42: Il logo di connettività di Unity sulla barra di stato non gestiva gli eventi del mouse in Visual Studio 2012.

-   Correzione del bug UVS-44: CTRL+MAIUSC+Q non è disponibile in Visual Studio 2012 per metodi MonoBehaviour rapidi.

-   Correzione del bug UVS-40: Gli elementi selezionati in Esplora progetti Unity non sono leggibili in caso di inattività della finestra nel tema scuro di Visual Studio 2012.

-   Correzione del bug UVS-39: Problema di suddivisione in token di stringhe con caratteri di escape.

-   Correzione del bug UVS-35: Viene richiamato ToString negli oggetti durante il controllo delle variabili.

-   Correzione del bug UVS-27: Incoerenza della finestra Vai al simbolo con il tema scuro in Visual Studio 2012.

-   Correzione del bug UVS-11: Variabili locali nelle coroutine.

## <a name="1100---beta-release"></a>1.1.0.0 - Versione beta
 Data di rilascio: 9 marzo 2013

## <a name="10130"></a>1.0.13.0
 Data di rilascio: 21 gennaio 2013

### <a name="bug-fixes"></a>Correzioni di bug

-   Correzione di un blocco di Visual Studio che poteva verificarsi se la destinazione oggetto del debug inviava eventi di thread non validi. Questo bug si verificava in genere durante il debug di un'istanza remota di Unity su OSX.

-   Correzione di un blocco di Visual Studio che poteva verificarsi se un'eccezione arrestava il debugger.

-   Correzione degli helper MonoBehavior quando un oggetto MonoBehavior C# è incluso in uno spazio dei nomi.

-   Correzione delle descrizioni comando del debugger per UnityScript in Visual Studio 2012.

-   Correzione della generazione di progetti in caso di modifica delle sole costanti di debug da Unity.

-   Correzione della navigazione tramite tastiera in Esplora progetti Unity.

-   Correzione della colorazione di UnityScript per stringhe con caratteri di escape.

-   Correzione dello strumento di apertura dei file in modo da indovinare meglio il nome del progetto se usato esternamente a Unity. Questo comportamento è necessario quando l'utente usa uno strumento di apertura dei file di terze parti in Unity che delega a UnityVS.

-   Correzione della gestione di messaggi lunghi inviati da Unity a UnityVS. Prima di questa correzione, i messaggi lunghi potevano provocare l'arresto anomalo della parte di messaggistica di UnityVS. Di conseguenza, talvolta UnityVS non era in grado di aprire un file da Unity.

## <a name="10120"></a>1.0.12.0
 Data di rilascio: 3 gennaio 2013

### <a name="bug-fixes"></a>Correzioni di bug

-   Correzione di un blocco di Visual Studio che poteva verificarsi durante l'eliminazione di un punto di interruzione.

-   Correzione di un bug per cui non era possibile raggiungere alcuni punti di interruzione dopo la ricompilazione di script di gioco da parte di Unity.

-   Correzione del debugger in modo da notificare correttamente a Visual Studio la mancata associazione dei punti di interruzione.

-   Correzione di un problema di registrazione che poteva impedire al debugger di Visual Studio di eseguire il debug di programmi nativi.

-   Correzione di un'eccezione che poteva verificarsi durante la valutazione di espressioni UnityScript e Boo.

-   Correzione di una regressione per cui la modifica del livello API di .NET in Unity non comportava l'attivazione di un aggiornamento dei file di progetto.

-   Correzione di un problema di un'API per cui il codice utente non poteva fare parte del gestore dei callback di log.

## <a name="10110"></a>1.0.11.0
 Data di rilascio: 28 novembre 2012

### <a name="new-features"></a>Nuove funzionalità

-   Supporto ufficiale di Unity 4.

-   Modifica di script da Gestione progetti per Unity.

-   Integrazione nella finestra Passa a di Visual Studio.

-   Analisi del messaggio della console di informazioni, per cui facendo clic nell'elenco degli errori si viene indirizzati al primo stack frame con simboli.

-   Aggiunta di un' [API](../cross-platform/customize-project-files-created-by-vstu.md) per consentire all'utente di partecipare alla generazione del progetto.

-   Aggiunta di un' [API](../cross-platform/share-the-unity-log-callback-with-vstu.md) per consentire all'utente di partecipare a LogCallback.

### <a name="bug-fixes"></a>Correzioni di bug

-   Correzione di una regressione nello sfondo di Esplora progetti Unity in Visual Studio 2012.

-   Correzione della generazione di progetti per gli utenti del profilo . NET completo.

-   Correzione della generazione di progetti per gli utenti della destinazione Web.

-   Correzione della generazione di progetti in modo da includere i simboli di compilazione DEBUG e TRACE come avviene in Unity.

-   Correzione dell'arresto anomalo durante l'uso di caratteri speciali nella finestra Vai al simbolo.

-   Correzione dell'arresto anomalo quando non è possibile inserire l'icona nella barra di stato di Visual Studio.

## <a name="10100"></a>1.0.10.0
 Data di rilascio: 9 ottobre 2012

### <a name="bug-fixes"></a>Correzioni di bug

-   Correzione dello sfondo di Esplora progetti Unity in Visual Studio 2010.

-   Correzione di un blocco di Visual Studio che poteva verificarsi se UnityVS tentava di collegare il debugger a un'istanza di Unity la cui interfaccia del debugger aveva subito un arresto anomalo in precedenza.

-   Correzione di un blocco di Visual Studio che poteva verificarsi quando era impostato un punto di interruzione e veniva eseguito un ricaricamento di AppDomain.

-   Correzione del modo in cui gli assembly vengono recuperati da Unity per evitare il blocco dei file e la confusione del processo di compilazione di Unity.

## <a name="1090"></a>1.0.9.0
 Data di rilascio: 3 ottobre 2012

### <a name="bug-fixes"></a>Correzioni di bug

-   Correzione della generazione di progetti quando il progetto di Unity include risorse JavaScript effettive.

-   Correzione di un errore di gestione nella valutazione di espressioni.

-   Correzione dell'impostazione di nuovi valori in campi di tipi di valore.

-   Correzione di possibili effetti collaterali quando si posiziona il puntatore su espressioni nell'editor di codice.

-   Correzione del modo in cui i tipi vengono cercati negli assembly caricati per la valutazione di espressioni.

-   Correzione del bug UVS-21: Valutazione dell'assegnazione su oggetti Unity senza effetto.

-   Correzione del bug UVS-21: Puntatore non valido durante la valutazione della chiamata di un metodo nell'API Math di Unity.

## <a name="1080"></a>1.0.8.0
 Data di rilascio: 26 settembre 2012

### <a name="bug-fixes"></a>Correzioni di bug

-   Correzione del modo in cui lo strumento di apertura dei file acquisiva il percorso del progetto in modo da garantire che sia in grado di aprire sia Visual Studio sia gli script.

-   Correzione di un bug relativo ai punti di interruzione creati durante l'esecuzione della sessione di debug, che poteva provocare il blocco di Visual Studio.

-   Correzione del modo in cui UnityVS viene registrato in Visual Studio 2010.

## <a name="1070"></a>1.0.7.0
 Data di rilascio: 14 settembre 2012

### <a name="new-features"></a>Nuove funzionalità

-   Supporto di Visual Studio 2012.

### <a name="bug-fixes"></a>Correzioni di bug

-   Correzione della generazione di file di progetto degli editor e dei plug-in in modo che corrisponda al comportamento di Unity.

-   Correzione della traduzione di simboli PDB in Unity 4.

> [!IMPORTANT]
>  A causa del supporto di Visual Studio 2012, è stato necessario rinominare alcuni file e spostarne altri. Il pacchetto UnityVS per importare Unity si chiama ora UnityVS 2010 o UnityVS 2012, rispettivamente per Visual Studio 2010 e Visual Studio 2012. Per questa versione è anche necessario che i file di progetto di UnityVS vengano rigenerati.

## <a name="1060---internal-build"></a>1.0.6.0 - Build interna
 Data di rilascio: 12 settembre 2012

## <a name="1050"></a>1.0.5.0
 Data di rilascio: 10 settembre 2012

### <a name="bug-fixes"></a>Correzioni di bug

-   Correzione della generazione dei file di progetto quando gli script o gli shader contengono un carattere XML non valido.

-   Correzione del rilevamento di istanze di Unity quando Unity è connesso al server delle risorse. Questo problema generava errori di apertura dei file da Unity e relativi alla connessione automatica del debugger di Visual Studio.

## <a name="1040"></a>1.0.4.0
 Data di rilascio: 5 settembre 2012

### <a name="new-features"></a>Nuove funzionalità

-   Conversione automatica dei simboli di debug in Unity.

     Se nella cartella Asset è presente un assembly DLL .NET con il file PDB associato, è sufficiente importare l'assembly perché UnityVS converta il file PDB in un file di simboli di debug riconosciuto dal motore di script di Unity e perché sia possibile passare agli assembly .NET da UnityVS.

### <a name="bug-fixes"></a>Correzioni di bug

-   Correzione dell'arresto anomalo di UnityVS durante il debug, causato da eccezioni generate da metodi o proprietà all'interno di Unity.

## <a name="1030"></a>1.0.3.0
 Data di rilascio: 4 settembre 2012

### <a name="new-features"></a>Nuove funzionalità

-   Nuova opzione di configurazione che consente di disabilitare l'utilizzo di UnityVS per aprire file da Unity.

### <a name="bug-fixes"></a>Correzioni di bug

-   Correzione della generazione di riferimenti a UnityEditor per progetti non di editor.

-   Correzione della definizione del simbolo UNITY_EDITOR per progetti non di editor.

-   Correzione di un arresto anomalo casuale di Visual Studio provocato dalla barra di stato personalizzata.

## <a name="1020"></a>1.0.2.0
 Data di rilascio: 30 agosto 2012

### <a name="bug-fixes"></a>Correzioni di bug

-   Correzione del conflitto con il debugger PythonTools.

-   Correzione dei riferimenti a Mono.Cecil.

-   Correzione di un bug relativo al modo in cui gli assembly di script vengono recuperato da Unity con Unity 4 b7.

## <a name="1010"></a>1.0.1.0
 Data di rilascio: 28 agosto 2012

### <a name="new-features"></a>Nuove funzionalità

-   Supporto di anteprima per Unity 4.0 Beta.

### <a name="bug-fixes"></a>Correzioni di bug

-   Correzione del controllo delle proprietà che generano eccezioni.

-   Correzione dell'ordine decrescente verso gli oggetti base durante il controllo degli oggetti.

-   Correzione dell'elenco a discesa vuoto per il punto di inserimento nella procedura guidata MonoBehavior.

-   Correzione del completamento per le DLL all'interno della cartella Asset per UnityScript e Boo.

## <a name="1000---initial-release"></a>1.0.0.0 - Versione iniziale
 Data di rilascio: 22 agosto 2012
