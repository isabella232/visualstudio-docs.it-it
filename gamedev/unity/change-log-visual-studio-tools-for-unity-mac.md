---
title: Registro modifiche (Visual Studio Tools per Unity, Mac) | Microsoft Docs
description: Visualizzare il log delle modifiche Visual Studio Tools per Unity, Mac. Vedere le modifiche dalla versione 1.0.0.0 alla 2.7.0.0 e versioni successiva.
ms.custom: ''
ms.date: 6/3/2021
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: conceptual
ms.assetid: 33a6ac54-d997-4308-b5a0-af7387460849
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 5ab2a8e5e3a4ef49999c2e986353f15684508a53306284e5832ea4d71a57fc0e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121440004"
---
# <a name="change-log-visual-studio-tools-for-unity-mac"></a>Registro modifiche (Visual Studio Tools per Unity, Mac)

Registro delle modifiche di Visual Studio Tools per Unity.

## <a name="21020"></a>2.10.2.0
Data di rilascio: 2 giugno 2021

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione:**

  - Aggiunta [`UNT0024`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0024.md) della diagnostica. Assegnare la priorità ai calcoli scalari rispetto ai calcoli vettoriali.

- **Valutazione:**

  - Aggiunta del supporto per l'uso di simboli pdb portabili per filtrare correttamente le variabili locali visibili.

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Correzione dell'annuncio da parte del lettore dell'analisi con le versioni recenti di Unity.

## <a name="21010"></a>2.10.1.0
Data di rilascio: 11 maggio 2021

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Correzione dei problemi di stabilità con [`UNT0008`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0008.md) quickfix.

  - Sono stati risolti problemi di prestazioni con i thread.

  - Correzione del filtro degli avvisi e degli errori eliminati nell'elenco errori.

  - Correzione del filtro dei processi in background di Unity.

## <a name="21000"></a>2.10.0.0
Data di rilascio: 13 aprile 2021

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione:**

  - Aggiunta [`UNT0019`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0019.md) della diagnostica. Chiamata indiretta non necessaria per `GameObject.gameObject` .

  - Aggiunta [`UNT0020`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0020.md) della diagnostica. `MenuItem` Attributo utilizzato nel metodo non statico.

  - Aggiunta [`UNT0021`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0021.md) della diagnostica. Il messaggio unity deve essere protetto (consenso esplicito).

  - Aggiunta [`UNT0022`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0022.md) della diagnostica. Metodo inefficiente per impostare posizione e rotazione.

  - Aggiunta [`UNT0023`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0023.md) della diagnostica. Assegnazione di unione su oggetti Unity.

  - Aggiunta [`USP0017`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0017.md) dell'suppressor per `IDE0074` . Gli oggetti Unity non devono usare l'assegnazione di unione.

## <a name="2940"></a>2.9.4.0
Data di rilascio: 6 aprile 2021

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Risolvere i problemi relativi all'enumerazione dei test

## <a name="2930"></a>2.9.3.0
Data di rilascio: 30 marzo 2021

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Risolvere i problemi relativi a Test Runner 

## <a name="2920"></a>2.9.2.0
Data di rilascio: 2 marzo 2021

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Correzione dell'evidenziazione della ricerca nella finestra di dialogo dei messaggi di Unity.

  - Sono stati risolti problemi di stabilità con la visualizzazione albero del progetto Unity.

- **Debug:**

  - Correzione della gestione dei punti di interruzione condizionali.

## <a name="2910"></a>2.9.1.0
Data di rilascio: 9 febbraio 2021

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione:**

  - Aggiunta del supporto per l'esecuzione e il debug di test Unity dall'IDE

- **Valutazione:**

  - Aggiunto `Active Scene` alle variabili locali, che mostra gli oggetti del gioco radice.

  - Aggiunto `this.gameObject` alle variabili locali, dato che è ampiamente usato nei progetti Unity.

  - Aggiunta `Children` di gruppi e a tutte le `Components` `GameObject` istanze, in modo da poter visualizzare facilmente tutta la gerarchia di oggetti.

  - Aggiunta `Scene Path` a tutte le istanze di per visualizzare la posizione nella `GameObject` scena.

  - Aggiunta del supporto `JobEntityBatch` per /Lambdas quando si usano entità con generatori di origine.

  - Supporto migliorato per la visualizzazione di matrici di grandi dimensioni (tramite bucket di indici).

  - Aggiunta dei messaggi Unity mancanti per l'API 2019.4.

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Correzione dei problemi di stabilità con la finestra di dialogo dei messaggi di Unity

  - Sono stati risolti vari problemi dell'interfaccia utente per le lingue non ENU.

  - Sono stati risolti problemi di stabilità con [`UNT0018`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0018.md) la diagnostica.

- **Debug:**

  - Correzione dei problemi di disconnessione della macchina virtuale quando si usano `Trace` i metodi.

- **Valutazione:**

  - Correzione del filtro delle proprietà obsolete che generano eccezioni.

## <a name="2900"></a>2.9.0.0
Data di rilascio: 20 gennaio 2021

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione:**

  - Aggiunta del supporto per `raytrace shaders` i file , e `UXML` `USS` .

  - Aggiornamento dell'API dei messaggi Unity (per tutti i metodi usati come coroutine).

  - Aggiornamento del Android SDK rilevamento delle modifiche.

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Correzione [`UNT0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0006.md) della diagnostica e visualizzazione di avvisi non corretti per coroutine e `AssetPostprocessor.OnAssignMaterialModel` .

## <a name="2840"></a>2.8.4.0
Data di rilascio: 15 dicembre 2020

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Risolto un problema di affidabilità alla chiusura della creazione guidata di eventi Unity.

## <a name="2830"></a>2.8.3.0
Data di rilascio: 10 novembre 2020

### <a name="bug-fixes"></a>Correzioni di bug

- **Debugger:**

  - Correzione del collegamento a Unity anche se nella soluzione non è presente alcun progetto VSTU.

## <a name="2820"></a>2.8.2.0
Data di rilascio: 27 ottobre 2020

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione:**

  - Miglioramento [`UNT0010`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0010.md) della diagnostica da applicare a tutti gli elementi che ereditano `Component` da , non solo `MonoBehaviour` .

## <a name="2810"></a>2.8.1.0
Data di rilascio: 13 ottobre 2020

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Valutazione:**

  - Aggiunta del supporto per la conversione implicita con chiamate. In precedenza l'analizzatore applicava un controllo rigoroso dei tipi, con la conseguente visualizzazione `Failed to find a match for method([parameters...])` di messaggi di avviso.

- **Integrazione:**

  - Aggiunta [`UNT0018`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0018.md) della diagnostica. È consigliabile non `System.Reflection` usare funzionalità nei messaggi critici per le prestazioni, ad `Update` esempio , , o `FixedUpdate` `LateUpdate` `OnGUI` .

  - Migliorato [`USP0003`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0003.md) e [`USP0005`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0005.md) soppressori, con supporto per tutti `AssetPostprocessor` i metodi statici.

  - Aggiunta [`USP0016`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0016.md) dell'suppressor per `CS8618` . `C# 8.0` introduce tipi riferimento nullable e tipi riferimento non nullable. Il rilevamento dell'inizializzazione dei tipi che ereditano `UnityEngine.Object` da non è supportato e comporta errori.

  - Usare ora lo stesso meccanismo di generazione del progetto player e asmdef per Unity 2019.x e 2020.x+.
  
  - Esperienza utente migliorata durante la generazione di messaggi Unity con una procedura guidata.

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Correzione del completamento imprevisto per i messaggi nei commenti.

## <a name="2800"></a>2.8.0.0 
Data di rilascio: 14 settembre 2020

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Correzione della generazione del progetto lettore con Unity 2019.x.

## <a name="2710"></a>2.7.1.0
Data di rilascio: 5 agosto 2020

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione:**

  - Aggiornamento dell'API dei messaggi Unity alla versione 2019.4.

  - Aggiunta [`USP0013`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0013.md) dell'suppressor per `CA1823` . I campi privati con `SerializeField` gli attributi o non devono essere `SerializeReference` contrassegnati come inutilizzati (FxCop).
  
  - Aggiunta [`USP0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0014.md) dell'suppressor per `CA1822` . I messaggi Unity non devono essere contrassegnati come candidati per `static` il modificatore (FxCop).

  - Aggiunta [`USP0015`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0015.md) dell'suppressor per `CA1801` . I parametri inutilizzati non devono essere rimossi dai messaggi Unity (FxCop).
  
  - Aggiunta `MenuItem` del supporto [`USP0009`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0009.md) all'suppressor.  

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Correzione [`USP0001`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0001.md) degli [`USP0002`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0002.md) suppressor e che non funzionano con parentesi aggiuntive o con argomenti del metodo.
  
  - Correzione dell'aggiornamento obbligatorio del database degli asset anche quando l'aggiornamento automatico è stato disabilitato nelle impostazioni di Unity.

## <a name="2700"></a>2.7.0.0
Data di rilascio: 23 giugno 2020

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione:**

  - Aggiunta del supporto per rendere persistenti le cartelle della soluzione quando Unity rigenera la soluzione e i progetti.

  - Aggiunta [`UNT0015`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0015.md) della diagnostica. Rilevare la firma del metodo non corretta `InitializeOnLoadMethod` con `RuntimeInitializeOnLoadMethod` l'attributo o .

  - Aggiunta [`UNT0016`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0016.md) della diagnostica. `Invoke`L'uso di , o con un primo argomento come valore `InvokeRepeating` `StartCoroutine` `StopCoroutine` letterale stringa non è indipendente dai tipi.

  - Aggiunta [`UNT0017`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0017.md) della diagnostica. `SetPixels` la chiamata è lenta.

### <a name="bug-fixes"></a>Correzioni di bug

- **Debugger:**

  - Correzione della creazione di punti di interruzione mentre il gioco è in esecuzione nel runtime di Mono precedente (tentativo di associare il punto di interruzione non appena viene creato). 
  
- **Integrazione:**

  - Non reimpostare la selezione quando si filtrano i messaggi nella creazione guidata di messaggi unity.
  
  - Correzione di e degli elementi suppressor con le [`USP0004`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0004.md) [`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0006.md) regole [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0007.md) seguenti: suppress (readonly), (non usato), (mai assegnato) per tutti i campi decorati con `IDE0044` `IDE0051` `CS0649` l'attributo SerializeField. Eliminare `CS0649` (mai assegnato) per i campi pubblici di tutti i tipi che estendono `Unity.Object`.

  - Correzione del controllo dei parametri di tipo generico per [`UNT0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0014.md) .

- **Valutazione:**

  - Correzione del confronto di uguaglianza con le enumerazioni.

## <a name="2610"></a>2.6.1.0
Data di rilascio: 19 maggio 2020

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Avvisa se non è possibile creare il server di messaggistica sul lato Unity.

  - Eseguire correttamente gli analizzatori durante la compilazione leggera.

  - Correzione della documentazione dell'API con le installazioni di Unity Hub.
  
  - Correzione degli arresti anomali del visualizzatore del debugger.

## <a name="2600"></a>2.6.0.0
Data di rilascio: 14 aprile 2020

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione:**

  - Aggiunta [`UNT0012`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0012.md) della diagnostica. Rilevare ed eseguire il wrapping delle chiamate alle coroutine in `StartCoroutine()` .

  - Aggiunta [`UNT0013`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0013.md) della diagnostica. Rilevare e rimuovere un attributo non valido o `SerializeField` ridondante.

  - Aggiunta [`UNT0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0014.md) della diagnostica. Rilevamento `GetComponent()` chiamato con un tipo non componente o non di interfaccia.

  - Aggiunta [`USP0009`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0009.md) dell'suppressor per `IDE0051` . Non contrassegnare i metodi con l'attributo o a cui fa riferimento `ContextMenu` un campo con `ContextMenuItem` l'attributo come inutilizzato.

  - Aggiunta [`USP0010`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0010.md) dell'suppressor per `IDE0051` . Non contrassegnare i campi con `ContextMenuItem` l'attributo come inutilizzati.

  - Aggiunta [`USP0011`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0011.md) dell'suppressor per `IDE0044` . Non impostare campi con `ContextMenuItem` l'attributo come di sola lettura.

  - [`USP0004`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0004.md)e [`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0006.md) [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0007.md) ora funzionano per entrambi gli attributi `SerializeReference` `SerializeField` e .

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Inviare comandi di avvio/arresto a Unity solo quando l'editor è in grado di comunicare.

  - Correzione della documentazione di Informazioni rapide con messaggi ereditati.

  - Correzione dell'ambito del `CreateInspectorGUI` messaggio.

  - Non creare report [`UNT0001`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0001.md) sui metodi con modificatori polimorfici.

- **Valutazione:**

  - Correzione della gestione delle using con alias.
  
  - Correzione della gestione dei valori Null.  

## <a name="2520"></a>2.5.2.0

Data di rilascio: 23 marzo 2020

### <a name="bug-fixes"></a>Correzioni di bug

- **Debugger:**

  - Correzione della registrazione dei thread al momento del collegamento.

## <a name="2510"></a>2.5.1.0

Data di rilascio: 3 marzo 2020

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione:**

  - Aggiunta [`USP0008`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0008.md) dell'soppressore per `IDE0051` . I metodi privati usati con Invoke, InvokeRepeating, StartCoroutine o StopCoroutine non devono essere contrassegnati come inutilizzati.

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Correzione della documentazione di OnDrawGizmos/OnDrawGizmosSelected.

- **Valutazione:**

  - Correzione dell'ispezione degli argomenti lambda.

## <a name="2501"></a>2.5.0.1

Data di rilascio: 19 febbraio 2020

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Correzione del [`UNT0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0006.md) controllo diagnostico per la firma del messaggio non corretta. Quando si esaminano i tipi con più livelli di ereditarietà, questa diagnostica potrebbe non riuscire con il messaggio seguente: `warning AD0001: Analyzer 'Microsoft.Unity.Analyzers.MessageSignatureAnalyzer' threw an exception of type 'System.ArgumentException' with message 'An item with the same key has already been added` .

## <a name="2500"></a>2.5.0.0

Data di rilascio: 22 gennaio 2020

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione:**

  - Aggiunta del supporto per i file HLSL.
  
  - È stata passata a una nuova interfaccia utente della finestra di dialogo della cartella.
  
  - Passa a una nuova griglia delle proprietà accessibili per le impostazioni.

  - Aggiunta [`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0006.md) dell'soppressore per `IDE0051` . I campi privati con `SerializeField` l'attributo non devono essere contrassegnati come inutilizzati.

  - Aggiunta [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0007.md) dell'soppressore per `CS0649` . I campi con `SerializeField` l'attributo non devono essere contrassegnati come non assegnati.  

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Correzione della generazione del progetto `GenerateTargetFrameworkMonikerAttribute` (la destinazione non è sempre stata individuata correttamente).

- **Valutazione:**

  - Correzione della valutazione delle stringhe (senza chiamate ToString() )

## <a name="2420"></a>2.4.2.0

Data di rilascio: 3 dicembre 2019

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Correzione della diagnostica con le interfacce definite dall'utente.

  - Correzione di descrizioni comando rapide con espressioni in formato non valido.
  
## <a name="2410"></a>2.4.1.0

Data di rilascio: 6 novembre 2019

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione:**

  - Aggiunta del supporto per i processi in background di Unity. Il debugger è in grado di connettersi automaticamente al processo principale anziché a un processo figlio.

  - Aggiunta di una descrizione comando rapida per i messaggi di Unity, che visualizza la documentazione associata.

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Correzione dell'analizzatore di confronto dei tag `UNT0002` con espressioni binarie e di chiamata avanzate.

### <a name="deprecated-features"></a>Caratteristiche deprecate

- **Integrazione:**

  - In futuro, Visual Studio Tools per Unity supporterà solo Visual Studio 2017+.

## <a name="2400"></a>2.4.0.0

Data di rilascio: 15 ottobre 2019

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione:**

  - Aggiunta [`USP0005`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0005.md) dell'eliminazione `IDE0060` per (parametro inutilizzato) per tutti i messaggi unity.

  - Aggiunta di una descrizione comando rapida per i campi contrassegnati con `TooltipAttribute` . Questa operazione funziona anche per una semplice funzione di accesso get che usa questo campo.

## <a name="2330"></a>2.3.3.0

Data di rilascio: 23 settembre 2019

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione:**

  - Aggiunta di un nuovo soppressore per IDE0060, per impedire all'IDE di visualizzare una correzione rapida per rimuovere i parametri inutilizzati.
    - `USP0005` per `IDE0060` : i messaggi unity vengono richiamati dal runtime di Unity.

## <a name="2320"></a>2.3.2.0

Data di rilascio: 16 settembre 2019

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione:**

  - È stato approfondito il modo in cui Visual Studio per i progetti Unity aggiungendo nuove funzionalità di diagnostica specifiche per Unity. Inoltre, l'IDE è stata resa più intelligente eliminando la diagnostica C# generale non applicabile ai progetti Unity. Ad esempio, l'IDE non mostrerà una correzione rapida per modificare una variabile inspector in modo da impedire la modifica della `readonly` variabile nell'editor di Unity.
    - `UNT0001`: i messaggi Unity vengono chiamati dal runtime anche se sono vuoti, non dichiararli per evitare l'elaborazione non richiesta dal runtime di Unity.
    - `UNT0002`: il confronto tra tag che usa l'uguaglianza delle stringhe è più lento rispetto al metodo CompareTag predefinito.
    - `UNT0003`: l'utilizzo della forma generica di GetComponent è preferibile per l'sicurezza dei tipi.
    - `UNT0004`: il messaggio di aggiornamento dipende dalla frequenza dei fotogrammi e deve usare Time.deltaTime anziché Time.fixedDeltaTime.
    - `UNT0005`: il messaggio FixedUpdate è indipendente dalla frequenza dei fotogrammi e deve usare Time.fixedDeltaTime anziché Time.deltaTime.
    - `UNT0006`: è stata rilevata una firma del metodo non corretta per questo messaggio unity.
    - `UNT0007`: Unity esegue l'override dell'operatore di confronto Null per gli oggetti Unity che non è compatibile con la coalescing null.
    - `UNT0008`: Unity esegue l'override dell'operatore di confronto Null per gli oggetti Unity che non è compatibile con la propagazione null.
    - `UNT0009`: quando si applica l'attributo InitializeOnLoad a una classe, è necessario fornire un costruttore statico. L'attributo InitializeOnLoad garantisce che verrà chiamato all'avvio dell'editor.
    - `UNT0010`: MonoBehaviours deve essere creato solo usando AddComponent(). un MonoBehaviour è un componente e deve essere associato a un GameObject.
    - `UNT0011`: ScriptableObject deve essere creato solo usando CreateInstance(). Gli ScriptableObject devono essere creati dal motore di Unity per gestire i metodi relativi ai messaggi di Unity.
    - `USP0001` per `IDE0029` : gli oggetti Unity non devono usare il coalescing null.
    - `USP0002` per `IDE0031` : gli oggetti Unity non devono usare la propagazione Null.
    - `USP0003` per `IDE0051` : i messaggi unity vengono richiamati dal runtime di Unity.
    - `USP0004` per `IDE0044` : i campi con un attributo SerializeField non devono essere resi di sola lettura.

## <a name="2310"></a>2.3.1.0

Data di rilascio: 4 settembre 2019

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Valutazione:**

  - Aggiunta del supporto per una migliore visualizzazione dei tipi, ad esempio `List<object>` anziché `List'1[[System.Object, <corlib...>]]` .

  - Aggiunta del supporto per l'accesso ai membri puntatore, ad esempio `p->data->member` .

  - Aggiunta del supporto per le conversioni implicite negli inizializzatori di matrice, ad esempio `new byte [] {1,2,3,4}` .

  - Aggiunta del supporto per l'editor esadecimale durante il controllo di stringhe e matrici di byte.

## <a name="2300"></a>2.3.0.0

Data di rilascio: 13 agosto 2019

### <a name="bug-fixes"></a>Correzioni di bug

- **Valutazione:**

  - Correzione dei problemi di esecuzione delle istruzioni con le eccezioni.

  - Correzione della valutazione di pseudoi identificatori (ad esempio $exception).

  - Impedire l'arresto anomalo del sistema durante la dereferenziazione di indirizzi non validi.  

  - Correzione del problema relativo ai domini applicazione non caricati.

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

- **Project Generazione:**

  - Mantenere le proprietà esterne durante l'elaborazione del file di soluzione.
  
- **Valutazione:**

  - Aggiunta del supporto per nomi completi di alias (solo lo spazio dei nomi globale per il momento). L'analizzatore di espressioni accetta quindi ora i tipi nel formato global::namespace.type.

  - Aggiunta del supporto per il formato `pointer[index]`, semanticamente identico al formato `*(pointer+index)` per la dereferenziazione del puntatore.

## <a name="2004"></a>2.0.0.4

Data di rilascio: 5 marzo 2019

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione:**

  - Aggiornamento `ScriptableObject` dell'API.

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Rimozione di spazi dei nomi dai modelli.

## <a name="2003"></a>2.0.0.3
 
 Data di rilascio: 5 marzo 2019

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Project Generazione:**

  - I campi pubblici e serializzati non causeranno più avvisi. Sono stati eliminati automaticamente gli avvisi del compilatore `CS0649` e nei progetti Unity che hanno creato questi `IDE0051` messaggi.

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

- **Project Generazione:**

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

- **Project Generazione:**

  - Aggiunta del supporto per il nuovo generatore di progetti in Unity 2018.1.

- **Integrazione:**

  - Aggiunta del pannello opzioni per le impostazioni dedicate.

## <a name="1402"></a>1.4.0.2

Data di rilascio: 24 gennaio 2018

### <a name="bug-fixes"></a>Correzioni di bug

- **Project Generazione:**

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

- **Project Generazione:**

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

- **Project Generazione:**

  - È stato corretto il problema dell'aggiunta di estensioni dll in eccesso al nome del file di assembly.

  - Non forzare il flag Unity AllowAttachedDebuggingOfEditor Unity, il cui valore predefinito è ora 'true'.

## <a name="1103"></a>1.1.0.3

Data di rilascio: 23 ottobre 2017

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Project Generazione:**

  - Aggiunta del supporto per il profilo .NET 4.6.

## <a name="1102"></a>1.1.0.2

Data di rilascio: 8 agosto 2017

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Debugger:**

  - Avvia il collegamento per elaborare la finestra di dialogo, se non si sa a quale Unity collegarsi.

- **Project Generazione:**

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

- **Project Generazione:**

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
