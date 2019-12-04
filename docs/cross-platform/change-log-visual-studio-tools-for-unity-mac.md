---
title: Registro modifiche (Visual Studio Tools per Unity, Mac) | Microsoft Docs
ms.custom: ''
ms.date: 12/02/2019
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 33a6ac54-d997-4308-b5a0-af7387460849
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: fe317d446ddc9196df02dfafcf0397f8815574c3
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/03/2019
ms.locfileid: "74771543"
---
# <a name="change-log-visual-studio-tools-for-unity-mac"></a>Registro modifiche (Visual Studio Tools per Unity, Mac)

Registro delle modifiche di Visual Studio Tools per Unity.

## <a name="2420"></a>2.4.2.0

Rilasciata il 3 dicembre 2019

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Correzione della diagnostica con le interfacce definite dall'utente.

  - Correzione delle descrizioni rapide con espressioni in formato non valido.
  
## <a name="2410"></a>2.4.1.0

Rilasciata il 6 novembre 2019

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione:**

  - Aggiunta del supporto per i processi in background di Unity. Il debugger è in grado di connettersi automaticamente al processo principale invece che a un processo figlio.

  - Aggiunta di una descrizione comando rapida per i messaggi Unity, che visualizza la documentazione associata.

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Correzione dell'analizzatore del confronto dei tag `UNT0002` con espressioni di chiamata e binarie avanzate.

### <a name="deprecated-features"></a>Funzionalità deprecate

- **Integrazione:**

  - In futuro, Visual Studio Tools per Unity supporterà solo Visual Studio 2017 +.

## <a name="2400"></a>2.4.0.0

Rilasciata il 15 ottobre 2019

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione:**

  - È stato aggiunto un silenziatore per `IDE0060` (parametro non usato) per tutti i messaggi Unity.

  - Aggiunta di una descrizione comando rapida per i campi contrassegnati con `TooltipAttribute`. Questa operazione funzionerà anche per una semplice funzione di accesso get usando questo campo.

## <a name="2330"></a>2.3.3.0

Rilasciata il 23 settembre 2019

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione:**

  - È stato aggiunto un nuovo silenziatore per IDE0060, per impedire che l'IDE visualizzi una correzione rapida per rimuovere i parametri non usati.
    - `USP0005` per `IDE0060`: i messaggi Unity vengono richiamati dal runtime di Unity.

## <a name="2320"></a>2.3.2.0

Rilasciata il 16 settembre 2019

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione:**

  - È stata approfondita la comprensione di Visual Studio per i progetti Unity con l'aggiunta di una nuova diagnostica specifica di Unity. Inoltre, l'IDE è stata resa più intelligente eliminando la diagnostica C# generale non applicabile ai progetti Unity. Ad esempio, l'IDE non visualizzerà una correzione rapida per modificare una variabile di controllo in `readonly` che impedisce di modificare la variabile nell'editor di Unity.
    - `UNT0001`: i messaggi Unity vengono chiamati dal runtime anche se sono vuoti, non dichiararli per evitare l'elaborazione del uncesseray da parte del runtime di Unity.
    - `UNT0002`: il confronto dei tag con l'uguaglianza delle stringhe è più lento del metodo CompareTag incorporato.
    - `UNT0003`: l'utilizzo del formato generico di getComponent è preferibile per l'indipendenza dai tipi.
    - `UNT0004`: il messaggio di aggiornamento è dipendente dalla frequenza dei frame e deve usare Time. deltaTime anziché time. fixedDeltaTime.
    - `UNT0005`: il messaggio FixedUpdate è indipendente dalla frequenza dei frame e deve usare Time. fixedDeltaTime anziché time. deltaTime.
    - `UNT0006`: è stata rilevata una firma del metodo non corretta per questo messaggio Unity.
    - `UNT0007`: Unity esegue l'override dell'operatore di confronto null per gli oggetti Unity, che non è compatibile con la coalescenza null.
    - `UNT0008`: Unity esegue l'override dell'operatore di confronto null per gli oggetti Unity che non è compatibile con la propagazione Null.
    - `UNT0009`: quando si applica l'attributo InitializeOnLoad a una classe, è necessario fornire un costruttore statico. L'attributo InitializeOnLoad garantisce che verrà chiamato all'avvio dell'editor.
    - `UNT0010`: la creazione di monobehaviors deve essere realizzata solo tramite AddComponent (). un MonoBehaviour è un componente e deve essere associato a un GameObject.
    - `UNT0011`: ScriptableObject deve essere creato solo con CreateInstance (). Gli ScriptableObject devono essere creati dal motore di Unity per gestire i metodi relativi ai messaggi di Unity.
    - `USP0001` per `IDE0029`: gli oggetti Unity non devono usare la coalesone null.
    - `USP0002` per `IDE0031`: gli oggetti Unity non devono usare la propagazione Null.
    - `USP0003` per `IDE0051`: i messaggi Unity vengono richiamati dal runtime di Unity.
    - `USP0004` per `IDE0044`: i campi con un attributo SerializeField non devono essere resi di sola lettura.

## <a name="2310"></a>2.3.1.0

Rilasciata il 4 settembre 2019

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Valutazione:**

  - Aggiunta del supporto per una visualizzazione dei tipi migliore, ad esempio `List<object>` anziché `List'1[[System.Object, <corlib...>]]`.

  - Aggiunta del supporto per l'accesso ai membri del puntatore, ad esempio `p->data->member`.

  - Aggiunto il supporto per le conversioni implicite negli inizializzatori di matrice, ad esempio `new byte [] {1,2,3,4}`.

  - Aggiunta del supporto per l'editor esadecimale quando si esaminano le matrici di byte e le stringhe.

## <a name="2300"></a>2.3.0.0

Rilasciata il 13 agosto 2019

### <a name="bug-fixes"></a>Correzioni di bug

- **Valutazione:**

  - Correzione dei problemi di esecuzione delle eccezioni.

  - Correzione della valutazione di pseudo-identificatori (ad esempio $exception).

  - Impedisci arresto anomalo quando si dereferenziano indirizzi non validi.  

  - Correzione del problema relativo agli AppDomain scaricati.

## <a name="2200"></a>2.2.0.0

Data di rilascio: 25 luglio 2019

### <a name="bug-fixes"></a>Correzioni di bug

- **Valutazione:**

  - Correzione dell'ispezione con tipi IntPtr.

- **Debugger:**

  - Correzione della gestione dei punti di intercettazione e dei punti di interruzione delle funzioni.

## <a name="2130"></a>2.1.3.0

Data di rilascio: 9 luglio 2019

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Debugger:**

  - Aggiunta del supporto per intercettare sottoclassi di eccezioni.

  - Aggiunta del supporto per il protocollo MDS 2.51.

- **Integrazione:**

  - Aggiunta del supporto per file con estensione asmdef.

  - Passaggio alla modalità di ridenominazione quando si aggiunge un file da un modello (per simulare il comportamento dell'editor Unity).

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Correzione della gestione dei messaggi in formato non corretto durante la comunicazione con lettori di Unity.

- **Valutazione:**

  - Gestione semplificata degli spazi dei nomi nelle espressioni.

## <a name="2120"></a>2.1.2.0

Data di rilascio: 2 luglio 2019

### <a name="bug-fixes"></a>Correzioni di bug

- **Valutazione:**

  - Correzione della segnalazione degli errori con espressioni non analizzabili.

## <a name="2110"></a>2.1.1.0

Data di rilascio: 27 giugno 2019

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione:**

  - Aggiornamento dell'API MonoBehaviour alla versione 2019.1.

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Correzione delle prestazioni di Esplora progetti Unity.

  - Correzione degli avvisi e degli errori per l'output quando è abilitata la compilazione leggera.

  - Correzione delle prestazioni per la compilazione leggera.

## <a name="2100"></a>2.1.0.0

Data di rilascio: 20 giugno 2019

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione:**

  - Disabilitazione della compilazione completa per i progetti Unity, a favore dell'uso di errori e avvisi IntelliSense. Indeed Unity crea una soluzione di Visual Studio con progetti di libreria di classi che rappresentano le operazioni eseguite internamente da Unity. Detto questo, il risultato della compilazione in Visual Studio non viene mai usato o acquisito da Unity perché la pipeline di compilazione è chiusa. La compilazione in Visual Studio utilizza inutilmente risorse. Se gli strumenti o la configurazione usati richiedono una configurazione completa perché ne sono dipendenti, è possibile disabilitare questa ottimizzazione: Strumenti/Opzioni/Strumenti per Unity/Disabilita la compilazione completa dei progetti.
  
  - Aggiunta del supporto per i pacchetti Unity in Esplora progetti Unity. Sono visibili solo i pacchetti a cui viene fatto riferimento (usando il file manifest.json nella cartella `Packages`) e i pacchetti locali (incorporati nella cartella `Packages`).

## <a name="2021"></a>2.0.2.1

Data di rilascio: 30 maggio 2019

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione:**

  - Aggiunta dell'icona personalizzata per le destinazioni di esecuzione di Unity.

## <a name="2020"></a>2.0.2.0

Data di rilascio: 2 aprile 2019

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione:**

  - Aggiunta del supporto per l'aggiornamento automatico dei database degli asset Unity al momento del salvataggio. Questa funzionalità è abilitata per impostazione predefinita e verrà attivata una ricompilazione sul lato di Unity quando si salva uno script in Visual Studio. È possibile disabilitare questa funzionalità in Strumenti\Opzioni\Strumenti per Unity\Aggiorna il database degli asset di Unity durante il salvataggio.

  - Aggiunta del supporto per l'impostazione dell'installazione preferita di Unity per la documentazione offline.

  - Aggiunta del menu di scelta rapida per il nuovo editor.

### <a name="bug-fixes"></a>Correzioni di bug

- **Debugger:**

  - Correzione del filtraggio degli assembly e dell'ispezione dei frame con frame vuoti.

## <a name="2011"></a>2.0.1.1
 
 Data di rilascio: 26 marzo 2019

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Mono impostato temporaneamente come debugger predefinito e unico debugger utilizzabile per questa specifica versione.

## <a name="2006"></a>2.0.0.6

Data di rilascio: 26 marzo 2019

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione:**

  - Aggiunta del supporto per "Collega a Unity e gioca".

## <a name="2005"></a>2.0.0.5

Data di rilascio: 20 marzo 2019

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Generazione del progetto:**

  - Mantenere le proprietà esterne durante l'elaborazione del file di soluzione.
  
- **Valutazione:**

  - Aggiunta del supporto per nomi completi di alias (solo lo spazio dei nomi globale per il momento). L'analizzatore di espressioni accetta quindi ora i tipi nel formato global::namespace.type.

  - Aggiunta del supporto per il formato `pointer[index]`, semanticamente identico al formato `*(pointer+index)` per la dereferenziazione del puntatore.

## <a name="2004"></a>2.0.0.4

Data di rilascio: 5 marzo 2019

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione:**

  - Aggiornamento dell'API `ScriptableObject`.

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Rimozione di spazi dei nomi dai modelli.

## <a name="2003"></a>2.0.0.3
 
 Data di rilascio: 5 marzo 2019

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Generazione del progetto:**

  - I campi pubblici e serializzati non causeranno più avvisi. Gli avvisi del compilatore `CS0649` e `IDE0051` sono stati eliminati automaticamente nei progetti Unity che hanno creato questi messaggi.

- **Integrazione:**

  - Richiesta di collegamento a un'istanza specifica se sono in esecuzione più processi Unity.

- **Valutazione:**

  - Aggiunta del supporto per le funzioni locali.

### <a name="bug-fixes"></a>Correzioni di bug

- **Debugger:**

  - Correzione per la lettura di attributi personalizzati per argomenti denominati quando si usano versioni meno recenti del protocollo.

## <a name="2002"></a>2.0.0.2

Data di rilascio: 4 febbraio 2019

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione:**

  - Aggiornamento dell'API MonoBehaviour.

### <a name="bug-fixes"></a>Correzioni di bug

- **Debugger:**

  - Correzione dell'impostazione di valori primitivi nel debugger.

## <a name="2001"></a>2.0.0.1

Data di rilascio: 4 dicembre 2018

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Correzione del contenimento del pacchetto di installazione.

## <a name="2000"></a>2.0.0.0
 Data di rilascio: 4 dicembre 2018

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Debugger:**

  - Sostituzione del debugger di Unity in Mac con lo stesso debugger di Unity core di Windows.

  - Sostituzione di NRefactory a favore di Roslyn per la valutazione delle espressioni.

  - Aggiunta del supporto per i puntatori: dereferenziazione, cast e aritmetica dei puntatori (sono richiesti sia Unity 2018.2+ che il nuovo runtime).

  - Aggiunta del supporto per la visualizzazione dei puntatori di matrici (come nel C++). In un'espressione per puntatori aggiungere una virgola e il numero di elementi che si vogliono visualizzare.

  - Aggiunta del supporto per i costrutti async.

  - Aggiunta del supporto per le pseudovariabili (identificatori di eccezione e oggetto).

### <a name="bug-fixes"></a>Correzioni di bug

- **Debugger:**

  - Correzione della valutazione delle espressioni con espressioni in formato non valido o non supportate.

## <a name="1700"></a>1.7.0.0

Data di rilascio: 13 novembre 2018

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Debugger:**

  - Aggiunta di altre informazioni sul client (IP, nome del computer) nella finestra di dialogo di connessione.

### <a name="bug-fixes"></a>Correzioni di bug

- **Debugger:**

  - Correzione di un deadlock nella libreria usata per comunicare con il motore di debugger di Unity, che blocca Visual Studio o Unity, in particolare al raggiungimento di "Collega a Unity" o al riavvio del gioco.

- **Integrazione:**

  - Correzione dell'attivazione del plug-in Unity quando veniva selezionato un altro editor predefinito.

  - Correzione della creazione di un modello di file Unity.

## <a name="1602"></a>1.6.0.2

Data di rilascio: 24 luglio 2018

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Eseguito il rollback della soluzione alternativa per un bug delle prestazioni di Unity che è stato risolto da Unity.

## <a name="1601"></a>1.6.0.1

Data di rilascio: 10 luglio 2018

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Correzione del supporto della colorazione del codice di Shader.

## <a name="1600"></a>1.6.0.0

Data di rilascio: 26 giugno 2018

### <a name="bug-fixes"></a>Correzioni di bug

- **Procedure guidate:**

  - Correzione di un errore ortografico per il messaggio OnApplicationFocus.

- **Generazione del progetto:**

  - Soluzione alternativa temporanea per un bug delle prestazioni Unity: memorizzazione nella cache di MonoIsland durante la generazione di progetti.

  - Non convertire più pdb portabili a mdb quando si usa il nuovo runtime di Unity.

## <a name="1502"></a>1.5.0.2

Data di rilascio: 18 aprile 2018

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione:**

  - Aggiunta del supporto per il completamento del codice Shader di base.

  - Aggiunta del supporto per attivare e disattivare i commenti nei file di Shader.

## <a name="1501"></a>1.5.0.1

Data di rilascio: 28 marzo 2018

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione:**

  - Aggiunta del supporto per modelli aggiuntivi in Esplora progetti Unity.

## <a name="1500"></a>1.5.0.0

Data di rilascio: 21 marzo 2018

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione:**

  - Aggiunta del supporto per il rilevamento e la connessione a lettori Android connessi tramite USB.

## <a name="1403"></a>1.4.0.3

Data di rilascio: 5 marzo 2018

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Generazione del progetto:**

  - Aggiunta del supporto per il nuovo generatore di progetti in Unity 2018.1.

- **Integrazione:**

  - Aggiunta del pannello opzioni per le impostazioni dedicate.

## <a name="1402"></a>1.4.0.2

Data di rilascio: 24 gennaio 2018

### <a name="bug-fixes"></a>Correzioni di bug

- **Generazione del progetto:**

  - Correzione del rilevamento della versione di Mono.

- **Integrazione:**

  - Correzione dei problemi di tempistica per l'attivazione di 2018.1 e plug-in.

  - Correzione delle notifiche quando si rilevava un nuovo giocatore.

## <a name="1401"></a>1.4.0.1

Data di rilascio: 23 gennaio 2018

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Correzione delle cartelle Espandi / Comprimi con doppio clic

## <a name="1400"></a>1.4.0.0

Data di rilascio: 13 dicembre 2017

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Generazione del progetto:**

  - Aggiunta del supporto per .NET Standard.

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Correzione della conversione automatica dei simboli di debug da pdb a mdb.

## <a name="1301"></a>1.3.0.1

Data di rilascio: 12 dicembre 2017

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Correzione della chiamata indiretta a EditorPrefs.GetBool con effetti sul controllo durante il tentativo di modifica delle dimensioni della matrice.

- **Procedure guidate:**

  - Aggiornamento del contesto roslyn prima dell'inserimento del metodo.

## <a name="1300"></a>1.3.0.0

Data di rilascio: 20 novembre 2017

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Procedure guidate:**

  - Aggiunta della procedura guidata "Implement Unity message" (Implementare il messaggio di Unity).

  - Aggiunta del supporto per la nuova API di completamento in VS per Mac 7.4.

## <a name="1200"></a>1.2.0.0

Data di rilascio: 23 ottobre 2017

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Debugger:**

  - È stato aggiunto il supporto per i file di simboli di debug portatili.

### <a name="bug-fixes"></a>Correzioni di bug

- **Generazione del progetto:**

  - È stato corretto il problema dell'aggiunta di estensioni dll in eccesso al nome del file di assembly.

  - Non forzare il flag Unity AllowAttachedDebuggingOfEditor Unity, il cui valore predefinito è ora 'true'.

## <a name="1103"></a>1.1.0.3

Data di rilascio: 23 ottobre 2017

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Generazione del progetto:**

  - Aggiunta del supporto per il profilo .NET 4.6.

## <a name="1102"></a>1.1.0.2

Data di rilascio: 8 agosto 2017

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Debugger:**

  - Avvia il collegamento per elaborare la finestra di dialogo, se non si sa a quale Unity collegarsi.

- **Generazione del progetto:**

  - Abilita sempre l'opzione di compilazione non sicura quando viene usato Unity 5.6.

## <a name="1101"></a>1.1.0.1

Data di rilascio: 20 luglio 2017

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione:**

  - Aggiunta del supporto per le risorse localizzate.

## <a name="1100"></a>1.1.0.0

Data di rilascio: 12 luglio 2017

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione:**

  - Aggiunta del supporto per la connessione ai lettori ed editor tramite la finestra Associa a processo.

- **Generazione del progetto:**

  - Riferimenti ai nomi assembly di Fixed con i file mcs.rsp.

  - Supporto aggiunto per le unità di compilazione assembly.json.

  - Fixed è definito con i livelli di API.

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Messaggio di errore shader fisso durante la compilazione.

## <a name="1001"></a>1.0.0.1

Data di rilascio: 4 maggio 2017

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Correzione della verifica dei documenti attivi con progetti regolari e ibridi.

## <a name="1000"></a>1.0.0.0

Data di rilascio: 3 maggio 2017
