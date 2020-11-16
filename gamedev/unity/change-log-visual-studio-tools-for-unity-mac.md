---
title: Registro modifiche (Visual Studio Tools per Unity, Mac) | Microsoft Docs
description: Visualizzare il log delle modifiche per Visual Studio Tools per Unity, Mac. Vedere le modifiche della versione 1.0.0.0 con 2.7.0.0 e oltre.
ms.custom: ''
ms.date: 5/19/2020
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: conceptual
ms.assetid: 33a6ac54-d997-4308-b5a0-af7387460849
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 72e1897e8eb7f7072ba22189c6414ba2585a6711
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/05/2020
ms.locfileid: "94341728"
---
# <a name="change-log-visual-studio-tools-for-unity-mac"></a>Registro modifiche (Visual Studio Tools per Unity, Mac)

Registro delle modifiche di Visual Studio Tools per Unity.

## <a name="2710"></a>2.7.1.0
Rilasciata il 5 agosto 2020

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione**

  - API messaggi Unity aggiornato a 2019,4.

  - Aggiunto un [`USP0013`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0013.md) silenziatore per `CA1823` . I campi privati con `SerializeField` gli `SerializeReference` attributi o non devono essere contrassegnati come inutilizzati (FxCop).
  
  - Aggiunto un [`USP0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0014.md) silenziatore per `CA1822` . I messaggi Unity non devono essere contrassegnati come candidati per il `static` modificatore (FxCop).

  - Aggiunto un [`USP0015`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0015.md) silenziatore per `CA1801` . I parametri inutilizzati non devono essere rimossi da messaggi Unity (FxCop).
  
  - Aggiunta `MenuItem` del supporto per l' [`USP0009`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0009.md) eliminazione.  

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione**

  - Corretti [`USP0001`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0001.md) ed [`USP0002`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0002.md) eliminati che non funzionano con le parentesi aggiuntive o con argomenti di metodo.
  
  - Correzione dell'aggiornamento obbligatorio del database asset anche quando l'aggiornamento automatico è stato disabilitato nelle impostazioni di Unity.

## <a name="2700"></a>2.7.0.0
Rilasciata il 23 giugno 2020

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione**

  - Aggiunto il supporto per mantenere le cartelle della soluzione quando Unity rigenera la soluzione e i progetti.

  - Aggiunta della [`UNT0015`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0015.md) diagnostica. Rilevare la firma di un metodo non corretto con l' `InitializeOnLoadMethod` `RuntimeInitializeOnLoadMethod` attributo o.

  - Aggiunta della [`UNT0016`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0016.md) diagnostica. `Invoke`L'uso `InvokeRepeating` di, `StartCoroutine` o `StopCoroutine` con un primo argomento che è un valore letterale stringa non è indipendente dai tipi.

  - Aggiunta della [`UNT0017`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0017.md) diagnostica. `SetPixels` la chiamata è lenta.

### <a name="bug-fixes"></a>Correzioni di bug

- **Debugger**

  - Correzione della creazione di punti di interruzione durante l'esecuzione del gioco nel runtime di mono precedente (tentativo di associare il punto di interruzione non appena viene creato). 
  
- **Integrazione**

  - Non reimpostare la selezione quando si filtrano i messaggi nella creazione guidata messaggio di Unity.
  
  - Corretti [`USP0004`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0004.md) [`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0006.md) ed [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0007.md) eliminati con le regole seguenti: `IDE0044` non visualizzare (ReadOnly), `IDE0051` (non usato), `CS0649` (mai assegnato) per tutti i campi decorati con l'attributo SerializeField. Eliminare `CS0649` (mai assegnato) per i campi pubblici di tutti i tipi che estendono `Unity.Object`.

  - Correzione del controllo dei parametri di tipo generico per [`UNT0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0014.md) .

- **Valutazione**

  - Correzione del confronto di uguaglianza con le enumerazioni.

## <a name="2610"></a>2.6.1.0
Rilasciato il 19 maggio 2020

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione**

  - Avvisa se non è possibile creare il server di messaggistica sul lato Unity.

  - Esecuzione corretta degli analizzatori durante la compilazione Lightweight.

  - Documentazione dell'API fissa con le installazioni dell'hub Unity.
  
  - Arresto anomalo del visualizzatore del debugger.

## <a name="2600"></a>2.6.0.0
Rilasciata il 14 aprile 2020

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione**

  - Aggiunta della [`UNT0012`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0012.md) diagnostica. Rilevare ed eseguire il wrapping delle chiamate alle coroutine in `StartCoroutine()` .

  - Aggiunta della [`UNT0013`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0013.md) diagnostica. Rilevare e rimuovere l'attributo non valido o ridondante `SerializeField` .

  - Aggiunta della [`UNT0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0014.md) diagnostica. Rilevamento `GetComponent()` chiamato con tipo non componente o non di interfaccia.

  - Aggiunto un [`USP0009`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0009.md) silenziatore per `IDE0051` . Non contrassegnare i metodi con l' `ContextMenu` attributo o a cui fa riferimento un campo con l' `ContextMenuItem` attributo come inutilizzato.

  - Aggiunto un [`USP0010`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0010.md) silenziatore per `IDE0051` . Non contrassegnare i campi con l' `ContextMenuItem` attributo come inutilizzato.

  - Aggiunto un [`USP0011`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0011.md) silenziatore per `IDE0044` . Non rendere i campi con l'attributo di sola `ContextMenuItem` lettura.

  - [`USP0004`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0004.md)[`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0006.md)e [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0007.md) ora funzionano per `SerializeReference` `SerializeField` gli attributi e.

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione**

  - Inviare i comandi Start/Stop a Unity solo quando l'editor è in grado di comunicare.

  - Correzione della documentazione di informazioni rapide con i messaggi ereditati.

  - Ambito del messaggio fisso per il `CreateInspectorGUI` messaggio.

  - Non creare report [`UNT0001`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0001.md) sui metodi con modificatori polimorfici.

- **Valutazione**

  - Correzione della gestione di using con alias.
  
  - Correzione della gestione dei valori null.  

## <a name="2520"></a>2.5.2.0

Rilasciata il 23 marzo 2020

### <a name="bug-fixes"></a>Correzioni di bug

- **Debugger**

  - Correzione della registrazione dei thread al momento della connessione.

## <a name="2510"></a>2.5.1.0

Rilasciata il 3 marzo 2020

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione**

  - Aggiunto un [`USP0008`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0008.md) silenziatore per `IDE0051` . I metodi privati utilizzati con Invoke, InvokeRepeating, StartCoroutine o StopCoroutine non devono essere contrassegnati come inutilizzati.

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione**

  - Correzione della documentazione di funzione ondrawgizmos/funzione ondrawgizmosselected.

- **Valutazione**

  - Controllo dell'argomento lambda fisso.

## <a name="2501"></a>2.5.0.1

Rilasciata il 19 febbraio 2020

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione**

  - Correzione [`UNT0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0006.md) del controllo diagnostico per la firma del messaggio non corretta. Quando si esaminano i tipi con più livelli di ereditarietà, la diagnostica potrebbe non riuscire con il messaggio seguente: `warning AD0001: Analyzer 'Microsoft.Unity.Analyzers.MessageSignatureAnalyzer' threw an exception of type 'System.ArgumentException' with message 'An item with the same key has already been added` .

## <a name="2500"></a>2.5.0.0

Rilasciata il 22 gennaio 2020

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione**

  - Aggiunta del supporto per i file HLSL.
  
  - Passare a un'interfaccia utente della finestra di dialogo nuova cartella.
  
  - Passare a una nuova griglia delle proprietà accessibile per le impostazioni.

  - Aggiunto un [`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0006.md) silenziatore per `IDE0051` . I campi privati con l' `SerializeField` attributo non devono essere contrassegnati come inutilizzati.

  - Aggiunto un [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0007.md) silenziatore per `CS0649` . I campi con l' `SerializeField` attributo non devono essere contrassegnati come non assegnati.  

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione**

  - Generazione del progetto fissa (la `GenerateTargetFrameworkMonikerAttribute` destinazione non è sempre stata individuata correttamente).

- **Valutazione**

  - Correzione della valutazione di una stringa (senza usare le chiamate a ToString ())

## <a name="2420"></a>2.4.2.0

Rilasciata il 3 dicembre 2019

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione**

  - Correzione della diagnostica con le interfacce definite dall'utente.

  - Correzione delle descrizioni rapide con espressioni in formato non valido.
  
## <a name="2410"></a>2.4.1.0

Rilasciata il 6 novembre 2019

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione**

  - Aggiunta del supporto per i processi in background di Unity. Il debugger è in grado di connettersi automaticamente al processo principale invece che a un processo figlio.

  - Aggiunta di una descrizione comando rapida per i messaggi Unity, che visualizza la documentazione associata.

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione**

  - Correzione dell'analizzatore del confronto dei tag `UNT0002` con espressioni di chiamata e binarie avanzate.

### <a name="deprecated-features"></a>Caratteristiche deprecate

- **Integrazione**

  - In futuro, Visual Studio Tools per Unity supporterà solo Visual Studio 2017 +.

## <a name="2400"></a>2.4.0.0

Rilasciata il 15 ottobre 2019

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione**

  - Aggiunto il [`USP0005`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0005.md) silenziatore per il `IDE0060` parametro (non usato) per tutti i messaggi Unity.

  - Aggiunta di una descrizione comando rapida per i campi contrassegnati con `TooltipAttribute` . Questa operazione funzionerà anche per una semplice funzione di accesso get usando questo campo.

## <a name="2330"></a>2.3.3.0

Rilasciata il 23 settembre 2019

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione**

  - È stato aggiunto un nuovo silenziatore per IDE0060, per impedire che l'IDE visualizzi una correzione rapida per rimuovere i parametri non usati.
    - `USP0005` per `IDE0060` : i messaggi Unity vengono richiamati dal runtime di Unity.

## <a name="2320"></a>2.3.2.0

Rilasciata il 16 settembre 2019

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione**

  - È stata approfondita la comprensione di Visual Studio per i progetti Unity con l'aggiunta di una nuova diagnostica specifica di Unity. Inoltre, l'IDE è stata resa più intelligente eliminando la diagnostica C# generale non applicabile ai progetti Unity. Ad esempio, l'IDE non visualizzerà una correzione rapida per modificare una variabile di controllo in modo `readonly` da impedire la modifica della variabile nell'editor di Unity.
    - `UNT0001`: I messaggi Unity vengono chiamati dal runtime anche se sono vuoti, non dichiararli per evitare l'elaborazione del uncesseray da parte del runtime di Unity.
    - `UNT0002`: Il confronto dei tag con l'uguaglianza delle stringhe è più lento del metodo CompareTag incorporato.
    - `UNT0003`: L'utilizzo della forma generica di getComponent è preferibile per l'indipendenza dai tipi.
    - `UNT0004`: Il messaggio di aggiornamento è dipendente dalla frequenza dei frame e deve usare Time. deltaTime anziché time. fixedDeltaTime.
    - `UNT0005`: Il messaggio FixedUpdate è indipendente dalla frequenza dei frame e deve usare Time. fixedDeltaTime anziché time. deltaTime.
    - `UNT0006`: È stata rilevata una firma del metodo non corretta per questo messaggio Unity.
    - `UNT0007`: Unity esegue l'override dell'operatore di confronto null per gli oggetti Unity che non è compatibile con l'Unione di valori null.
    - `UNT0008`: Unity esegue l'override dell'operatore di confronto null per gli oggetti Unity che non è compatibile con la propagazione Null.
    - `UNT0009`: Quando si applica l'attributo InitializeOnLoad a una classe, è necessario fornire un costruttore statico. L'attributo InitializeOnLoad garantisce che verrà chiamato all'avvio dell'editor.
    - `UNT0010`: I comportamenti monocomportamentali devono essere creati solo utilizzando AddComponent (). un MonoBehaviour è un componente e deve essere associato a un GameObject.
    - `UNT0011`: ScriptableObject deve essere creato solo con CreateInstance (). Gli ScriptableObject devono essere creati dal motore di Unity per gestire i metodi relativi ai messaggi di Unity.
    - `USP0001` per `IDE0029` : gli oggetti Unity non devono usare la coalesone null.
    - `USP0002` per `IDE0031` : gli oggetti Unity non devono utilizzare la propagazione Null.
    - `USP0003` per `IDE0051` : i messaggi Unity vengono richiamati dal runtime di Unity.
    - `USP0004` per `IDE0044` : i campi con un attributo SerializeField non devono essere resi di sola lettura.

## <a name="2310"></a>2.3.1.0

Rilasciata il 4 settembre 2019

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Valutazione**

  - Aggiunta del supporto per la visualizzazione dei tipi migliore, ovvero `List<object>` anziché `List'1[[System.Object, <corlib...>]]` .

  - Aggiunta del supporto per l'accesso ai membri del puntatore, ad esempio `p->data->member` .

  - Aggiunto il supporto per le conversioni implicite negli inizializzatori di matrice, ad esempio `new byte [] {1,2,3,4}` .

  - Aggiunta del supporto per l'editor esadecimale quando si esaminano le matrici di byte e le stringhe.

## <a name="2300"></a>2.3.0.0

Rilasciata il 13 agosto 2019

### <a name="bug-fixes"></a>Correzioni di bug

- **Valutazione**

  - Correzione dei problemi di esecuzione delle eccezioni.

  - Correzione della valutazione di pseudo-identificatori (ad esempio $exception).

  - Impedisci arresto anomalo quando si dereferenziano indirizzi non validi.  

  - Correzione del problema relativo agli AppDomain scaricati.

## <a name="2200"></a>2.2.0.0

Data di rilascio: 25 luglio 2019

### <a name="bug-fixes"></a>Correzioni di bug

- **Valutazione**

  - Correzione dell'ispezione con tipi IntPtr.

- **Debugger**

  - Correzione della gestione dei punti di intercettazione e dei punti di interruzione delle funzioni.

## <a name="2130"></a>2.1.3.0

Data di rilascio: 9 luglio 2019

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Debugger**

  - Aggiunta del supporto per intercettare sottoclassi di eccezioni.

  - Aggiunta del supporto per il protocollo MDS 2.51.

- **Integrazione**

  - Aggiunta del supporto per file con estensione asmdef.

  - Passaggio alla modalità di ridenominazione quando si aggiunge un file da un modello (per simulare il comportamento dell'editor Unity).

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione**

  - Correzione della gestione dei messaggi in formato non corretto durante la comunicazione con lettori di Unity.

- **Valutazione**

  - Gestione semplificata degli spazi dei nomi nelle espressioni.

## <a name="2120"></a>2.1.2.0

Data di rilascio: 2 luglio 2019

### <a name="bug-fixes"></a>Correzioni di bug

- **Valutazione**

  - Correzione della segnalazione degli errori con espressioni non analizzabili.

## <a name="2110"></a>2.1.1.0

Data di rilascio: 27 giugno 2019

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione**

  - Aggiornamento dell'API MonoBehaviour alla versione 2019.1.

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione**

  - Correzione delle prestazioni di Esplora progetti Unity.

  - Correzione degli avvisi e degli errori per l'output quando è abilitata la compilazione leggera.

  - Correzione delle prestazioni per la compilazione leggera.

## <a name="2100"></a>2.1.0.0

Data di rilascio: 20 giugno 2019

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione**

  - Disabilitazione della compilazione completa per i progetti Unity, a favore dell'uso di errori e avvisi IntelliSense. Indeed Unity crea una soluzione di Visual Studio con progetti di libreria di classi che rappresentano le operazioni eseguite internamente da Unity. Detto questo, il risultato della compilazione in Visual Studio non viene mai usato o acquisito da Unity perché la pipeline di compilazione è chiusa. La compilazione in Visual Studio utilizza inutilmente risorse. Se gli strumenti o la configurazione usati richiedono una configurazione completa perché ne sono dipendenti, è possibile disabilitare questa ottimizzazione: Strumenti/Opzioni/Strumenti per Unity/Disabilita la compilazione completa dei progetti.
  
  - Aggiunta del supporto per i pacchetti Unity in Esplora progetti Unity. Sono visibili solo i pacchetti a cui viene fatto riferimento (usando il file manifest.json nella cartella `Packages`) e i pacchetti locali (incorporati nella cartella `Packages`).

## <a name="2021"></a>2.0.2.1

Data di rilascio: 30 maggio 2019

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione**

  - Aggiunta dell'icona personalizzata per le destinazioni di esecuzione di Unity.

## <a name="2020"></a>2.0.2.0

Data di rilascio: 2 aprile 2019

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione**

  - Aggiunta del supporto per l'aggiornamento automatico dei database degli asset Unity al momento del salvataggio. Questa funzionalità è abilitata per impostazione predefinita e verrà attivata una ricompilazione sul lato di Unity quando si salva uno script in Visual Studio. È possibile disabilitare questa funzionalità in Strumenti\Opzioni\Strumenti per Unity\Aggiorna il database degli asset di Unity durante il salvataggio.

  - Aggiunta del supporto per l'impostazione dell'installazione preferita di Unity per la documentazione offline.

  - Aggiunta del menu di scelta rapida per il nuovo editor.

### <a name="bug-fixes"></a>Correzioni di bug

- **Debugger**

  - Correzione del filtraggio degli assembly e dell'ispezione dei frame con frame vuoti.

## <a name="2011"></a>2.0.1.1
 
 Data di rilascio: 26 marzo 2019

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione**

  - Mono impostato temporaneamente come debugger predefinito e unico debugger utilizzabile per questa specifica versione.

## <a name="2006"></a>2.0.0.6

Data di rilascio: 26 marzo 2019

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione**

  - Aggiunta del supporto per "Collega a Unity e gioca".

## <a name="2005"></a>2.0.0.5

Data di rilascio: 20 marzo 2019

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Generazione del progetto:**

  - Mantenere le proprietà esterne durante l'elaborazione del file di soluzione.
  
- **Valutazione**

  - Aggiunta del supporto per nomi completi di alias (solo lo spazio dei nomi globale per il momento). L'analizzatore di espressioni accetta quindi ora i tipi nel formato global::namespace.type.

  - Aggiunta del supporto per il formato `pointer[index]`, semanticamente identico al formato `*(pointer+index)` per la dereferenziazione del puntatore.

## <a name="2004"></a>2.0.0.4

Data di rilascio: 5 marzo 2019

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione**

  - Aggiornamento dell' `ScriptableObject` API.

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione**

  - Rimozione di spazi dei nomi dai modelli.

## <a name="2003"></a>2.0.0.3
 
 Data di rilascio: 5 marzo 2019

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Generazione del progetto:**

  - I campi pubblici e serializzati non causeranno più avvisi. Sono stati eliminati automaticamente gli avvisi del `CS0649` `IDE0051` compilatore e nei progetti Unity che hanno creato questi messaggi.

- **Integrazione**

  - Richiesta di collegamento a un'istanza specifica se sono in esecuzione più processi Unity.

- **Valutazione**

  - Aggiunta del supporto per le funzioni locali.

### <a name="bug-fixes"></a>Correzioni di bug

- **Debugger**

  - Correzione per la lettura di attributi personalizzati per argomenti denominati quando si usano versioni meno recenti del protocollo.

## <a name="2002"></a>2.0.0.2

Data di rilascio: 4 febbraio 2019

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione**

  - Aggiornamento dell'API MonoBehaviour.

### <a name="bug-fixes"></a>Correzioni di bug

- **Debugger**

  - Correzione dell'impostazione di valori primitivi nel debugger.

## <a name="2001"></a>2.0.0.1

Data di rilascio: 4 dicembre 2018

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione**

  - Correzione del contenimento del pacchetto di installazione.

## <a name="2000"></a>2.0.0.0
 Data di rilascio: 4 dicembre 2018

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Debugger**

  - Sostituzione del debugger di Unity in Mac con lo stesso debugger di Unity core di Windows.

  - Sostituzione di NRefactory a favore di Roslyn per la valutazione delle espressioni.

  - Aggiunta del supporto per i puntatori: dereferenziazione, cast e aritmetica dei puntatori (sono richiesti sia Unity 2018.2+ che il nuovo runtime).

  - Aggiunta del supporto per la visualizzazione dei puntatori di matrici (come nel C++). In un'espressione per puntatori aggiungere una virgola e il numero di elementi che si vogliono visualizzare.

  - Aggiunta del supporto per i costrutti async.

  - Aggiunta del supporto per le pseudovariabili (identificatori di eccezione e oggetto).

### <a name="bug-fixes"></a>Correzioni di bug

- **Debugger**

  - Correzione della valutazione delle espressioni con espressioni in formato non valido o non supportate.

## <a name="1700"></a>1.7.0.0

Data di rilascio: 13 novembre 2018

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Debugger**

  - Aggiunta di altre informazioni sul client (IP, nome del computer) nella finestra di dialogo di connessione.

### <a name="bug-fixes"></a>Correzioni di bug

- **Debugger**

  - Correzione di un deadlock nella libreria usata per comunicare con il motore di debugger di Unity, che blocca Visual Studio o Unity, in particolare al raggiungimento di "Collega a Unity" o al riavvio del gioco.

- **Integrazione**

  - Correzione dell'attivazione del plug-in Unity quando veniva selezionato un altro editor predefinito.

  - Correzione della creazione di un modello di file Unity.

## <a name="1602"></a>1.6.0.2

Data di rilascio: 24 luglio 2018

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione**

  - Eseguito il rollback della soluzione alternativa per un bug delle prestazioni di Unity che è stato risolto da Unity.

## <a name="1601"></a>1.6.0.1

Data di rilascio: 10 luglio 2018

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione**

  - Correzione del supporto della colorazione del codice di Shader.

## <a name="1600"></a>1.6.0.0

Data di rilascio: 26 giugno 2018

### <a name="bug-fixes"></a>Correzioni di bug

- **Procedure guidate**

  - Correzione di un errore ortografico per il messaggio OnApplicationFocus.

- **Generazione del progetto:**

  - Soluzione alternativa temporanea per un bug delle prestazioni Unity: memorizzazione nella cache di MonoIsland durante la generazione di progetti.

  - Non convertire più pdb portabili a mdb quando si usa il nuovo runtime di Unity.

## <a name="1502"></a>1.5.0.2

Data di rilascio: 18 aprile 2018

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione**

  - Aggiunta del supporto per il completamento del codice Shader di base.

  - Aggiunta del supporto per attivare e disattivare i commenti nei file di Shader.

## <a name="1501"></a>1.5.0.1

Data di rilascio: 28 marzo 2018

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione**

  - Aggiunta del supporto per modelli aggiuntivi in Esplora progetti Unity.

## <a name="1500"></a>1.5.0.0

Data di rilascio: 21 marzo 2018

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione**

  - Aggiunta del supporto per il rilevamento e la connessione a lettori Android connessi tramite USB.

## <a name="1403"></a>1.4.0.3

Data di rilascio: 5 marzo 2018

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Generazione del progetto:**

  - Aggiunta del supporto per il nuovo generatore di progetti in Unity 2018.1.

- **Integrazione**

  - Aggiunta del pannello opzioni per le impostazioni dedicate.

## <a name="1402"></a>1.4.0.2

Data di rilascio: 24 gennaio 2018

### <a name="bug-fixes"></a>Correzioni di bug

- **Generazione del progetto:**

  - Correzione del rilevamento della versione di Mono.

- **Integrazione**

  - Correzione dei problemi di tempistica per l'attivazione di 2018.1 e plug-in.

  - Correzione delle notifiche quando si rilevava un nuovo giocatore.

## <a name="1401"></a>1.4.0.1

Data di rilascio: 23 gennaio 2018

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione**

  - Correzione delle cartelle Espandi / Comprimi con doppio clic

## <a name="1400"></a>1.4.0.0

Data di rilascio: 13 dicembre 2017

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Generazione del progetto:**

  - Aggiunta del supporto per .NET Standard.

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione**

  - Correzione della conversione automatica dei simboli di debug da pdb a mdb.

## <a name="1301"></a>1.3.0.1

Data di rilascio: 12 dicembre 2017

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione**

  - Correzione della chiamata indiretta a EditorPrefs.GetBool con effetti sul controllo durante il tentativo di modifica delle dimensioni della matrice.

- **Procedure guidate**

  - Aggiornamento del contesto roslyn prima dell'inserimento del metodo.

## <a name="1300"></a>1.3.0.0

Data di rilascio: 20 novembre 2017

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Procedure guidate**

  - Aggiunta della procedura guidata "Implement Unity message" (Implementare il messaggio di Unity).

  - Aggiunta del supporto per la nuova API di completamento in VS per Mac 7.4.

## <a name="1200"></a>1.2.0.0

Data di rilascio: 23 ottobre 2017

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Debugger**

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

- **Debugger**

  - Avvia il collegamento per elaborare la finestra di dialogo, se non si sa a quale Unity collegarsi.

- **Generazione del progetto:**

  - Abilita sempre l'opzione di compilazione non sicura quando viene usato Unity 5.6.

## <a name="1101"></a>1.1.0.1

Data di rilascio: 20 luglio 2017

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione**

  - Aggiunta del supporto per le risorse localizzate.

## <a name="1100"></a>1.1.0.0

Data di rilascio: 12 luglio 2017

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione**

  - Aggiunta del supporto per la connessione ai lettori ed editor tramite la finestra Associa a processo.

- **Generazione del progetto:**

  - Riferimenti ai nomi assembly di Fixed con i file mcs.rsp.

  - Supporto aggiunto per le unità di compilazione assembly.json.

  - Fixed è definito con i livelli di API.

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione**

  - Messaggio di errore shader fisso durante la compilazione.

## <a name="1001"></a>1.0.0.1

Data di rilascio: 4 maggio 2017

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione**

  - Correzione della verifica dei documenti attivi con progetti regolari e ibridi.

## <a name="1000"></a>1.0.0.0

Data di rilascio: 3 maggio 2017