---
title: Log delle modifiche (Visual Studio Tools per Unity, Windows) | Microsoft Docs
description: Visualizzare il log delle modifiche Visual Studio Tools per Unity, Windows. Vedere le modifiche dalla versione 1.0.0.0 alla 4.7.0.0 e versioni successiva.
ms.custom: ''
ms.date: 9/7/2021
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: conceptual
ms.assetid: ea490b7e-fc0d-44b1-858a-a725ce20e396
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 522d016e218b19d63cacd746128150b23734aa62
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710514"
---
# <a name="change-log-visual-studio-tools-for-unity-windows"></a>Log delle modifiche (Visual Studio Tools per Unity, Windows)

Registro delle modifiche di Visual Studio Tools per Unity.

## <a name="41140"></a>4.11.4.0
Data di rilascio: 14 settembre 2021

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione:**

  - Disabilitare automaticamente l'indicizzazione degli asset per progetti Unity di grandi dimensioni.

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Correzione del rilevamento delle espressioni supportate con [`UNT0024`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0024.md) la diagnostica.

## <a name="41130"></a>4.11.3.0
Data di rilascio: 10 agosto 2021

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Riduzione del consumo di memoria durante l'elaborazione degli asset.

  - Allocazioni ottimizzate con [`USP0008`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0008.md) [`USP0009`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0009.md) [`USP0010`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0010.md) soppressori , e [`USP0011`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0011.md) .

  - Utilizzo ottimizzato dei simboli con [`UNT0002`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0002.md) [`UNT0003`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0003.md) , , , [`UNT0012`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0012.md) [`UNT0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0014.md) diagnostica.

## <a name="41120"></a>4.11.2.0
Data di rilascio: 13 luglio 2021

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Miglioramento del tempo di compilazione leggero, eseguendo solo gli strumenti di eliminazione in grado di gestire gli avvisi del compilatore CS. Tutti gli altri analizzatori verranno eseguiti tramite l'analisi della soluzione.

## <a name="41110"></a>4.11.1.0
Data di rilascio: 15 giugno 2021

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Riduzione del consumo di memoria durante l'analisi di asset yaml.

## <a name="41100"></a>4.11.0.0
Data di rilascio: 25 maggio 2021

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione:**

  - Aggiunta [`UNT0025`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0025.md) della diagnostica. Preferire gli overload Input.GetKey con l'argomento KeyCode.

  - Aggiunta di altri utilizzi non validi (campi statici e di sola lettura) alla [`UNT0013`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0013.md) diagnostica.

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Sono stati risolti i problemi relativi alle implementazioni esplicite dei metodi e [`UNT0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0006.md) alla diagnostica.

## <a name="41030"></a>4.10.3.0
Data di rilascio: 8 giugno 2021

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - [Backported] Riduzione del consumo di memoria durante l'analisi di asset yaml.

## <a name="41020"></a>4.10.2.0
Data di rilascio: 25 maggio 2021

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione:**

  - Aggiunta [`UNT0024`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0024.md) della diagnostica. Assegnare la priorità ai calcoli scalari rispetto ai calcoli vettoriali.

- **Valutazione:**

  - Aggiunta del supporto per l'uso di simboli pdb portabili per filtrare correttamente le variabili locali visibili.

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Stabilità della ricerca dei riferimenti ai cespiti.

  - Correzione dell'annuncio dell'analisi da parte del lettore con le versioni recenti di Unity.

## <a name="41010"></a>4.10.1.0
Data di rilascio: 11 maggio 2021

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Correzione dei problemi di stabilità con [`UNT0008`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0008.md) quickfix.

  - Sono stati risolti problemi di prestazioni con i thread.

## <a name="41000"></a>4.10.0.0
Data di rilascio: 13 aprile 2021

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione:**

  - Aggiunta [`UNT0019`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0019.md) della diagnostica. Chiamata indiretta non necessaria per `GameObject.gameObject` .

  - Aggiunta [`UNT0020`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0020.md) della diagnostica. `MenuItem` Attributo utilizzato nel metodo non statico.

  - Aggiunta [`UNT0021`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0021.md) della diagnostica. Il messaggio Unity deve essere protetto (consenso esplicito).

  - Aggiunta [`UNT0022`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0022.md) della diagnostica. Metodo inefficiente per impostare posizione e rotazione.

  - Aggiunta [`UNT0023`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0023.md) della diagnostica. Assegnazione di unione su oggetti Unity.

  - Aggiunta [`USP0017`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0017.md) dell'soppressore per `IDE0074` . Gli oggetti Unity non devono usare l'assegnazione coalescing.

  - Aggiunta del rilevamento di progetti C# nonflavorati che hanno come destinazione Unity.

  - Aggiunta della ricerca di riferimento all'asset unity in CodeLens.

## <a name="4910"></a>4.9.1.0
Data di rilascio: 2 marzo 2021

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Valutazione:**

  - Aggiunta `Active Scene` a variabili locali, che mostrano gli oggetti di gioco radice.

  - Aggiunta `this.gameObject` a variabili locali, dato che è ampiamente usata nei progetti Unity.

  - Aggiunta `Children` di e gruppi a tutte le `Components` `GameObject` istanze, in modo da poter visualizzare facilmente tutta la gerarchia di oggetti.

  - Aggiunta `Scene Path` a tutte le istanze di per visualizzare la posizione nella `GameObject` scena.

  - Aggiunta del supporto `JobEntityBatch` per /Lambdas quando si usano entità con generatori di origine.

  - Supporto migliorato per la visualizzazione di matrici di grandi dimensioni (usando il bucketing degli indici).
  
  - Sono stati aggiunti messaggi Unity mancanti per l'API 2019.4.

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Sono stati risolti vari problemi dell'interfaccia utente per le lingue non ENU.

  - Sono stati risolti problemi di stabilità con [`UNT0018`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0018.md) la diagnostica.
  
- **Debug:**

  - Sono stati risolti i problemi di disconnessione della macchina virtuale quando si usano `Trace` i metodi.

- **Valutazione:**

  - Correzione del filtro delle proprietà obsolete che generano eccezioni.

## <a name="4900"></a>4.9.0.0
Data di rilascio: 20 gennaio 2021

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione:**

  - Aggiunta del supporto per `raytrace shaders` `UXML` i file e `USS` .

  - Aggiunta `.vsconfig` del supporto per la generazione. Visual Studio ora rilevare i componenti mancanti e richiedere di installarli quando si usano progetti Unity.

  - Aggiornamento dell'API messaggi unity (per tutti i metodi usati come coroutine).

  - Aggiornamento del Android SDK rilevamento.

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Correzione dell'aggiornamento del processo quando si usa la finestra di dialogo di selezione dell'istanza.

  - Correzione [`UNT0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0006.md) della diagnostica, che ha dato avvisi erri per coroutine e `AssetPostprocessor.OnAssignMaterialModel` .

## <a name="4820"></a>4.8.2.0
Data di rilascio: 10 novembre 2020

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione:**

  - Diagnostica [`UNT0010`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0010.md) migliorata da applicare a tutti gli elementi che ereditano da , non solo `Component` `MonoBehaviour` .

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Correzione dell'invalidazione del messaggio CodeLens.

## <a name="4810"></a>4.8.1.0
Data di rilascio: 13 ottobre 2020

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Valutazione:**

  - Aggiunta del supporto per la conversione implicita con chiamate. In precedenza l'analizzatore applicava il controllo dei tipi strict, con la conseguente visualizzazione di `Failed to find a match for method([parameters...])` messaggi di avviso.

- **Integrazione:**

  - Aggiunta [`UNT0018`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0018.md) della diagnostica. Non è consigliabile usare `System.Reflection` funzionalità nei messaggi critici per le prestazioni, ad `Update` esempio , , o `FixedUpdate` `LateUpdate` `OnGUI` .

  - Migliorato [`USP0003`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0003.md) ed [`USP0005`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0005.md) eliminatori, con supporto per tutti i `AssetPostprocessor` metodi statici.

  - Aggiunta [`USP0016`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0016.md) dell'soppressore per `CS8618` . `C# 8.0` introduce tipi riferimento nullable e tipi riferimento non nullable. Il rilevamento dell'inizializzazione dei tipi che ereditano da `UnityEngine.Object` non è supportato e comporta errori.

  - Ora si usa lo stesso meccanismo di generazione del progetto player e asmdef per Unity 2019.x e 2020.x+.

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Correzione del completamento imprevisto per i messaggi nei commenti.

## <a name="4800"></a>4.8.0.0 
Data di rilascio: 14 settembre 2020

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Generazione del progetto lettore fisso con Unity 2019.x.

## <a name="4710"></a>4.7.1.0
Data di rilascio: 5 agosto 2020

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione:**

  - Aggiunta del supporto dello spazio dei nomi ai modelli predefiniti.
  
  - Aggiornamento dell'API messaggi unity alla versione 2019.4.

  - Aggiunta [`USP0013`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0013.md) dell'soppressore per `CA1823` . I campi privati con gli attributi o non `SerializeField` `SerializeReference` devono essere contrassegnati come non usati (FxCop).
  
  - Aggiunta [`USP0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0014.md) dell'soppressore per `CA1822` . I messaggi Unity non devono essere contrassegnati come candidati per `static` il modificatore (FxCop).

  - Aggiunta [`USP0015`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0015.md) dell'soppressore per `CA1801` . I parametri inutilizzati non devono essere rimossi dai messaggi unity (FxCop).
  
  - Aggiunta del supporto MenuItem [`USP0009`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0009.md) all'oggetto suppressor.  

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Correzione [`USP0001`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0001.md) di [`USP0002`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0002.md) e soppressori che non funzionano con parentesi aggiuntive o con argomenti del metodo.
  
  - Correzione dell'aggiornamento obbligatorio del database degli asset anche quando l'aggiornamento automatico è stato disabilitato nelle impostazioni di Unity.

## <a name="4700"></a>4.7.0.0
Data di rilascio: 23 giugno 2020

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione:**

  - Aggiunta del supporto per rendere persistenti le cartelle della soluzione quando Unity rigenera soluzioni e progetti.

  - Aggiunta [`UNT0015`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0015.md) della diagnostica. Rilevare la firma del metodo non corretta `InitializeOnLoadMethod` con l'attributo o `RuntimeInitializeOnLoadMethod` .

  - Aggiunta [`UNT0016`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0016.md) della diagnostica. `Invoke`L'uso di , o con un primo argomento come valore `InvokeRepeating` `StartCoroutine` `StopCoroutine` letterale stringa non è indipendente dai tipi.

  - Aggiunta [`UNT0017`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0017.md) della diagnostica. `SetPixels` la chiamata è lenta.

  - Aggiunta del supporto per il commento di blocco e il rientro per i file shader.

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Non reimpostare la selezione quando si filtrano i messaggi nella creazione guidata messaggi di Unity.
  
  - Usare sempre il browser predefinito all'apertura della documentazione dell'API Unity.
  
  - Sono stati corretti gli oggetti suppressor e con le regole [`USP0004`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0004.md) [`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0006.md) [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0007.md) seguenti: suppress `IDE0044` (readonly), (unused), (mai assegnato) per tutti i campi decorati con `IDE0051` `CS0649` l'attributo SerializeField. Eliminare `CS0649` (mai assegnato) per i campi pubblici di tutti i tipi che estendono `Unity.Object`.

  - Correzione del controllo dei parametri di tipo generico [`UNT0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0014.md) per diagostic.

- **Valutazione:**

  - Correzione del confronto di uguaglianza con le enumerazioni.

## <a name="4610"></a>4.6.1.0
Data di rilascio: 19 maggio 2020

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Avvisa se non è possibile creare il server di messaggistica sul lato Unity.
  
  - Eseguire correttamente gli analizzatori durante la compilazione leggera.
  
  - È stato risolto un problema a causa del quale una classe MonoBehaviour creata dall'upe non corrispondeva al nome del file.

## <a name="4600"></a>4.6.0.0
Data di rilascio: 14 aprile 2020

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione:**

  - Aggiunta del supporto per CodeLens (script e messaggi di Unity).
  
  - Aggiunta [`UNT0012`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0012.md) della diagnostica. Rilevare ed eseguire il wrapping delle chiamate alle coroutine in `StartCoroutine()` .

  - Aggiunta [`UNT0013`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0013.md) della diagnostica. Rilevare e rimuovere un attributo non valido o `SerializeField` ridondante.

  - Aggiunta [`UNT0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0014.md) della diagnostica. Rilevare `GetComponent()` chiamato con un tipo non component o non di interfaccia.
  
  - Aggiunta [`USP0009`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0009.md) dell'soppressore per `IDE0051` . Non contrassegnare i metodi con `ContextMenu` l'attributo o a cui fa riferimento un campo con `ContextMenuItem` l'attributo come inutilizzato.

  - Aggiunta [`USP0010`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0010.md) dell'soppressore per `IDE0051` . Non contrassegnare i campi con `ContextMenuItem` l'attributo come inutilizzati.
  
  - Aggiunta [`USP0011`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0011.md) dell'soppressore per `IDE0044` . Non rendere i campi con `ContextMenuItem` l'attributo di sola lettura.
  
  - [`USP0004`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0004.md)e [`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0006.md) [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0007.md) funzionano ora sia per gli attributi `SerializeReference` che per gli attributi `SerializeField` .
  
### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Inviare i comandi di avvio/arresto a Unity solo quando l'editor è in grado di comunicare.
  
  - Correzione della documentazione di Informazioni rapide con i messaggi ereditati.
  
  - Risolto l'ambito del `CreateInspectorGUI` messaggio.

  - Non creare report [`UNT0001`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0001.md) sui metodi con modificatori polimorfici.

- **Valutazione:**

  - Correzione della gestione delle using con alias.

## <a name="4510"></a>4.5.1.0

Data di rilascio: 16 marzo 2020

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione:**

  - Aggiunta [`USP0008`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0008.md) dell'soppressore per `IDE0051` . I metodi privati usati con Invoke, InvokeRepeating, StartCoroutine o StopCoroutine non devono essere contrassegnati come inutilizzati.

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Correzione della documentazione di OnDrawGizmos/OnDrawGizmosSelected.

- **Valutazione:**

  - Correzione dell'ispezione degli argomenti lambda.

## <a name="4501"></a>4.5.0.1

Data di rilascio: 19 febbraio 2020

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Correzione [`UNT0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0006.md) del controllo diagnostico per la firma del messaggio non corretta. Quando si esaminano i tipi con più livelli di ereditarietà, questa diagnostica potrebbe non riuscire con il messaggio seguente: `warning AD0001: Analyzer 'Microsoft.Unity.Analyzers.MessageSignatureAnalyzer' threw an exception of type 'System.ArgumentException' with message 'An item with the same key has already been added` .

## <a name="4500"></a>4.5.0.0

Data di rilascio: 22 gennaio 2020

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione:**

  - Aggiunta del supporto per i file HLSL.
  
  - Aggiunta [`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0006.md) dell'soppressore per `IDE0051` . I campi privati con `SerializeField` l'attributo non devono essere contrassegnati come inutilizzati.
  
  - Aggiunta [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0007.md) dell'soppressore per `CS0649` . I campi con `SerializeField` l'attributo non devono essere contrassegnati come non assegnati.  

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Correzione della generazione del progetto `GenerateTargetFrameworkMonikerAttribute` (la destinazione non è sempre stata individuata correttamente).

## <a name="4420"></a>4.4.2.0

Data di rilascio: 3 dicembre 2019

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Correzione della diagnostica con le interfacce definite dall'utente.

  - Correzione di descrizioni comando rapide con espressioni in formato non valido.

## <a name="4410"></a>4.4.1.0

Data di rilascio: 6 novembre 2019

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione:**

  - Aggiunta del supporto per i processi in background di Unity. Il debugger è in grado di connettersi automaticamente al processo principale anziché a un processo figlio.
  
  - Aggiunta di una descrizione comando rapida per i messaggi di Unity, che visualizza la documentazione associata.

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Correzione dell'analizzatore di confronto dei tag [`UNT0002`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0002.md) con espressioni binarie e di chiamata avanzate.

### <a name="deprecated-features"></a>Caratteristiche deprecate

- **Integrazione:**

  - In futuro, Visual Studio Tools per Unity supporterà solo Visual Studio 2017+.

## <a name="4400"></a>4.4.0.0

Data di rilascio: 15 ottobre 2019

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione:**

  - Aggiunta [`USP0005`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0005.md) dell'eliminazione `IDE0060` per (parametro inutilizzato) per tutti i messaggi di Unity.
  
  - Aggiunta di una descrizione comando rapida per i campi contrassegnati con `TooltipAttribute` . Questa operazione funziona anche per una semplice funzione di accesso get che usa questo campo.

## <a name="4330"></a>4.3.3.0

Data di rilascio: 23 settembre 2019

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Correzione della segnalazione di errori e avvisi per le compilazioni leggere.

## <a name="4320"></a>4.3.2.0

Data di rilascio: 16 settembre 2019

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione:**

  - È stato approfondito il modo in cui Visual Studio per i progetti Unity aggiungendo nuove funzionalità di diagnostica specifiche per Unity. Inoltre, l'IDE è stata resa più intelligente eliminando la diagnostica C# generale non applicabile ai progetti Unity. Ad esempio, l'IDE non mostrerà una correzione rapida per modificare una variabile inspector in modo da impedire la modifica della `readonly` variabile nell'editor di Unity.
    - [`UNT0001`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0001.md): i messaggi Unity vengono chiamati dal runtime anche se sono vuoti, non dichiararli per evitare uncesseray di elaborazione da parte del runtime di Unity.
    - [`UNT0002`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0002.md): il confronto tra tag che usa l'uguaglianza delle stringhe è più lento rispetto al metodo CompareTag predefinito.
    - [`UNT0003`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0003.md): l'utilizzo della forma generica di GetComponent è preferibile per l'sicurezza dei tipi.
    - [`UNT0004`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0004.md): il messaggio di aggiornamento dipende dalla frequenza dei fotogrammi e deve usare Time.deltaTime anziché Time.fixedDeltaTime.
    - [`UNT0005`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0005.md): il messaggio FixedUpdate è indipendente dalla frequenza dei fotogrammi e deve usare Time.fixedDeltaTime anziché Time.deltaTime.
    - [`UNT0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0006.md): è stata rilevata una firma del metodo non corretta per questo messaggio unity.
    - [`UNT0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0007.md): Unity esegue l'override dell'operatore di confronto Null per gli oggetti Unity che non è compatibile con la coalescing null.
    - [`UNT0008`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0008.md): Unity esegue l'override dell'operatore di confronto Null per gli oggetti Unity che non è compatibile con la propagazione null.
    - [`UNT0009`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0009.md): quando si applica l'attributo InitializeOnLoad a una classe, è necessario fornire un costruttore statico. L'attributo InitializeOnLoad garantisce che verrà chiamato all'avvio dell'editor.
    - [`UNT0010`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0010.md): MonoBehaviours deve essere creato solo usando AddComponent(). un MonoBehaviour è un componente e deve essere associato a un GameObject.
    - [`UNT0011`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0011.md): ScriptableObject deve essere creato solo usando CreateInstance(). Gli ScriptableObject devono essere creati dal motore di Unity per gestire i metodi relativi ai messaggi di Unity.
    - [`USP0001`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0001.md) per `IDE0029` : gli oggetti Unity non devono usare il coalescing null.
    - [`USP0002`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0002.md) per `IDE0031` : gli oggetti Unity non devono usare la propagazione Null.
    - [`USP0003`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0003.md) per `IDE0051` : i messaggi unity vengono richiamati dal runtime di Unity.
    - [`USP0004`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0004.md) per `IDE0044` : i campi con un attributo SerializeField non devono essere resi di sola lettura.

## <a name="4310"></a>4.3.1.0

Data di rilascio: 4 settembre 2019

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Valutazione:**

  - Aggiunta del supporto per una migliore visualizzazione dei tipi, ad esempio `List<object>` anziché `List'1[[System.Object, <corlib...>]]` .

  - Aggiunta del supporto per l'accesso ai membri puntatore, ad esempio `p->data->member` .

  - Aggiunta del supporto per le conversioni implicite negli inizializzatori di matrice, ad esempio `new byte [] {1,2,3,4}` .

## <a name="4300"></a>4.3.0.0

Data di rilascio: 13 agosto 2019

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Debugger:**

  - Aggiunta del supporto per il protocollo MDS 2.51.

- **Integrazione:**

  - È stata migliorata la finestra "Collega all'istanza di Unity" con le funzionalità di ordinamento, ricerca e aggiornamento. Il PID viene ora visualizzato anche per i lettori locali (tramite query sui socket di ascolto nel sistema per recuperare il processo proprietario).

  - Aggiunta del supporto per file con estensione asmdef.

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Correzione della gestione dei messaggi in formato non corretto durante la comunicazione con lettori di Unity.

- **Valutazione:**

  - Gestione semplificata degli spazi dei nomi nelle espressioni.

  - Correzione dell'ispezione con tipi IntPtr.
  
  - Sono stati risolti problemi di esecuzione di istruzioni con eccezioni.

  - Correzione della valutazione degli pseudo identificatori (ad esempio $exception).

  - Impedire l'arresto anomalo del sistema durante la dereferenziazione di indirizzi non validi.  

  - È stato risolto un problema relativo ai domini app scaricati.

## <a name="4201"></a>4.2.0.1

Data di rilascio: 24 luglio 2019

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione:**

  - Aggiunta di una nuova opzione per la creazione di qualsiasi tipo di file da Esplora progetti Unity.
  
  - Miglioramento della memorizzazione nella cache di diagnostica quando si usano compilazioni veloci per i progetti Unity.

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Correzione di un problema a causa del quale l'estensione del file non viene gestita da alcun editor noto.

  - Correzione del supporto per estensioni personalizzate in Esplora progetti Unity.

  - Correzione delle impostazioni di salvataggio all'esterno della finestra di dialogo principale.

  - Rimozione della dipendenza da Microsoft.VisualStudio.MPF legacy.

## <a name="4110"></a>4.1.1.0

Data di rilascio: 24 maggio 2019

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione:**

  - Aggiornamento dell'API MonoBehaviour alla versione 2019.1.

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Correzione degli avvisi e degli errori per l'output quando è abilitata la compilazione leggera.

  - Correzione delle prestazioni per la compilazione leggera.

## <a name="4100"></a>4.1.0.0

Data di rilascio: 21 maggio 2019

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione:**

  - Aggiunta del supporto per la nuova API batch per ricaricare i progetti più velocemente.

  - Disabilitazione della compilazione completa per i progetti Unity, a favore dell'uso di errori e avvisi IntelliSense. Indeed Unity crea una soluzione di Visual Studio con progetti di libreria di classi che rappresentano le operazioni eseguite internamente da Unity. Detto questo, il risultato della compilazione in Visual Studio non viene mai usato o acquisito da Unity perché la pipeline di compilazione è chiusa. La compilazione in Visual Studio utilizza inutilmente risorse. Se è necessaria una compilazione completa perché si usano strumenti o un programma di installazione che dipende da essa, è possibile disabilitare questa ottimizzazione: Strumenti/Opzioni/Tools for Unity/Disable the full build of projects (Strumenti per Unity/Disabilita compilazione completa dei progetti).

  - Visualizzazione automatica di Esplora progetti Unity quando viene caricato un progetto Unity. Esplora progetti Unity sarà ancorato accanto a Esplora soluzioni.

  - Aggiornamento del meccanismo di estrazione del nome di progetto con Unity 2019.x.

  - Aggiunta del supporto per i pacchetti Unity in Esplora progetti Unity. Sono visibili solo i pacchetti a cui viene fatto riferimento (usando il file manifest.json nella cartella `Packages`) e i pacchetti locali (incorporati nella cartella `Packages`).

- **Project Generazione:**

  - Mantenere le proprietà esterne durante l'elaborazione del file di soluzione.

- **Valutazione:**

  - Aggiunta del supporto per nomi completi di alias (solo lo spazio dei nomi globale per il momento). L'analizzatore di espressioni accetta quindi ora i tipi nel formato global::namespace.type.

  - Aggiunta del supporto per il formato `pointer[index]`, semanticamente identico al formato `*(pointer+index)` per la dereferenziazione del puntatore.

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Correzione di problemi di dipendenza con Microsoft.VisualStudio.MPF.

  - Correzione del collegamento del lettore UWP, senza alcun progetto caricato.

  - Correzione dell'aggiornamento automatico del database degli asset quando Visual Studio non è ancora associato.

  - Correzione di problemi del tema con etichette e caselle di controllo.

- **Debugger:**

  - Correzione dell'esecuzione di istruzioni con i costruttori statici.

## <a name="4005"></a>4.0.0.5

Data di rilascio: 27 febbraio 2019

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Correzione del rilevamento della versione di Visual Studio con il pacchetto di installazione.

  - Rimozione degli assembly inutilizzati dal pacchetto di installazione.

## <a name="4004"></a>4.0.0.4

Data di rilascio: 13 febbraio 2019

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione:**

  - Aggiunta del supporto per rilevare correttamente i processi Unity durante l'installazione e per consentire al motore di installazione di gestire meglio i blocchi di file.

  - Aggiornamento `ScriptableObject` dell'API.

## <a name="4003"></a>4.0.0.3

Data di rilascio: 31 gennaio 2019

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Project Generazione:**

  - I campi pubblici e serializzati non causeranno più avvisi. Sono stati eliminati automaticamente gli avvisi del compilatore `CS0649` e nei progetti Unity che hanno creato questi `IDE0051` messaggi.

- **Integrazione:**

  - Miglioramento dell'esperienza utente per visualizzare le istanze dell'editor di Unity e del lettore (le finestre sono ora ridimensionabili, usano margini uniformi e visualizzano un controllo di ridimensionamento). Aggiunta di informazioni dall'ID del processo per gli editor di Unity.

  - Aggiornamento `MonoBehaviour` dell'API.

- **Valutazione:**

  - Aggiunta del supporto per le funzioni locali.

  - Aggiunta del supporto per le pseudovariabili (identificatori di eccezione e oggetto).

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Correzione di un problema con i temi e le immagini del moniker.

  - Solo scrittura nella finestra di output durante il debug, durante l'aggiornamento automatico del database degli asset.

  - Correzione dei ritardi dell'interfaccia utente con il filtraggio della procedura guidata MonoBehaviour.

- **Debugger:**

  - Correzione per la lettura di attributi personalizzati per argomenti denominati quando si usano versioni meno recenti del protocollo.

## <a name="4002"></a>4.0.0.2

Data di rilascio: 23 gennaio 2019

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Correzione della generazione di build sperimentale.

  - Correzione della gestione degli eventi del file di progetto per ridurre al minimo la pressione sul thread dell'interfaccia utente.

  - Correzione del provider di completamento con modifiche al testo in modalità batch.

- **Debugger:**

  - Correzione della visualizzazione di messaggi di debug utente nel debugger collegato.

## <a name="4001"></a>4.0.0.1

Data di rilascio: 10 dicembre 2018

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Valutazione:**

  - Sostituzione di NRefactory a favore di Roslyn per la valutazione delle espressioni.

  - Aggiunta del supporto per i puntatori: dereferenziazione, cast e aritmetica dei puntatori (sono richiesti sia Unity 2018.2+ che il nuovo runtime).

  - Aggiunta del supporto per la visualizzazione dei puntatori di matrici (come nel C++). In un'espressione per puntatori aggiungere una virgola e il numero di elementi che si vogliono visualizzare.

  - Aggiunta del supporto per i costrutti async.

- **Integrazione:**

  - Aggiunta del supporto per l'aggiornamento automatico dei database degli asset Unity al momento del salvataggio. Questa funzionalità è abilitata per impostazione predefinita e verrà attivata una ricompilazione sul lato di Unity quando si salva uno script in Visual Studio. È possibile disabilitare questa funzionalità in Strumenti\Opzioni\Strumenti per Unity\Aggiorna il database degli asset di Unity durante il salvataggio.

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Correzione dell'attivazione del bridge quando Visual Studio non è selezionato come editor esterno preferito.

  - Correzione della valutazione delle espressioni con espressioni in formato non valido o non supportate.

## <a name="4000"></a>4.0.0.0

Data di rilascio: 4 dicembre 2018

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione:**

  - Aggiunta del supporto per Visual Studio 2019 (è necessaria almeno la versione 2018.3 di Unity per poter usare Visual Studio 2019 come editor di script esterno).

  - Adozione del servizio immagini e del catalogo di Visual Studio, con supporto completo per ridimensionamento HDPI, immagini perfette al pixel e temi.

### <a name="deprecated-features"></a>Funzionalità deprecate

- **Integrazione:**

  - Da ora in poi, Visual Studio Tools per Unity supporterà solo Unity 5.2+ (con l'integrazione di Visual Studio predefinita di Unity).

  - Da ora in poi, Visual Studio Tools per Unity supporterà solo Visual Studio 2015+.

  - Rimozione del servizio di linguaggio, dell'elenco di errori e della barra di stato legacy.

  - Rimozione della procedura guidata rapida Monobehaviour (a favore del supporto dedicato di IntelliSense).

## <a name="3903"></a>3.9.0.3

Data di rilascio: 28 novembre 2018

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Correzione di problemi di ricaricamento dei progetti e di IntelliSense durante l'aggiunta o la rimozione degli script che si trovano nel primissimo progetto.

## <a name="3902"></a>3.9.0.2

Data di rilascio: 19 novembre 2018

### <a name="bug-fixes"></a>Correzioni di bug

- **Debugger:**

  - Correzione di un deadlock nella libreria usata per comunicare con il motore di debugger di Unity, che blocca Visual Studio o Unity, in particolare al raggiungimento di "Collega a Unity" o al riavvio del gioco.

## <a name="3901"></a>3.9.0.1

Data di rilascio: 15 novembre 2018

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Correzione dell'attivazione del plug-in Unity quando veniva selezionato un altro editor predefinito.

## <a name="3900"></a>3.9.0.0

Data di rilascio: 13 novembre 2018

### <a name="bug-fixes"></a>Correzioni di bug

- **Project Generazione:**

  - Eseguito il rollback della soluzione alternativa per un bug delle prestazioni di Unity che è stato risolto da Unity.

## <a name="3807"></a>3.8.0.7

Rilascio: 20 settembre 2018

### <a name="bug-fixes"></a>Correzioni di bug

- **Debugger:**

  - (Backporting dalla versione 3.9.0.2) Correzione di un deadlock nella libreria usata per comunicare con il motore di debugger di Unity, che blocca Visual Studio o Unity, in particolare al raggiungimento del collegamento a Unity o al riavvio del gioco.

## <a name="3806"></a>3.8.0.6

Data di rilascio: 27 agosto 2018

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Correzione di ricaricamento di progetti e soluzione.

## <a name="3805"></a>3.8.0.5

Data di rilascio: 20 agosto 2018

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Correzione dell'eliminazione della sottoscrizione di monitoraggio del progetto.

## <a name="3804"></a>3.8.0.4

Data di rilascio: 14 agosto 2018

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Valutazione:**

  - Aggiunta del supporto per i valori del puntatore.

  - Aggiunta del supporto per metodi generici.

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Ricarica rapida con modifica su più progetti.

## <a name="3803"></a>3.8.0.3

Data di rilascio: 24 luglio 2018

### <a name="bug-fixes"></a>Correzioni di bug

- **Project Generazione:**

  - (Backporting dalla versione 3.9.0.0) Eseguito il rollback della soluzione alternativa per un bug delle prestazioni di Unity che è stato risolto da Unity.

## <a name="3802"></a>3.8.0.2

Data di rilascio: 7 luglio 2018

### <a name="bug-fixes"></a>Correzioni di bug

- **Project Generazione:**

  - Soluzione alternativa temporanea per un bug delle prestazioni Unity: memorizzazione nella cache di MonoIsland durante la generazione di progetti.

## <a name="3801"></a>3.8.0.1

Data di rilascio: 26 giugno 2018

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Debug:**

  - Aggiunta del supporto per i comandi UserLog e UserBreak.

  - Aggiunta del supporto di tipo-caricamento lazy (ottimizzazione della latenza del carico di rete e della risposta del debugger).

### <a name="bug-fixes"></a>Correzioni di bug

- **Valutazione:**

  - Ricerca metodo e valutazione dell'espressione dell'operatore binario migliorati.

## <a name="3800"></a>3.8.0.0

Data di rilascio: 30 maggio 2018

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Debug:**

  - Aggiunta del supporto per la visualizzazione delle variabili nei costrutti asincroni.

  - Aggiunta del supporto per l'elaborazione di tipi nidificati quando si impostano i punti di interruzione, per impedire gli avvisi con i costrutti del compilatore.

- **Integrazione:**

  - Aggiunta del supporto per le grammatiche di TextMate per Shader (il carico di lavoro C++ non è più necessario per la colorazione del codice di Shader).

### <a name="bug-fixes"></a>Correzioni di bug

- **Project Generazione:**

  - Non convertire più pdb portabili a mdb quando si usa il nuovo runtime di Unity.

## <a name="3701"></a>3.7.0.1

Data di rilascio: 7 maggio 2018

### <a name="bug-fixes"></a>Correzioni di bug

- **Programma di installazione:**

  - Correzione di un problema di dipendenza durante l'uso di build sperimentali.

## <a name="3700"></a>3.7.0.0

Data di rilascio: 7 maggio 2018

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Debug:**

  - Aggiunta del supporto per il debug orchestrato (debug di più lettori/editor con la stessa sessione di Visual Studio).

  - Aggiunta del supporto per il debug del lettore USB Android.

  - Aggiunta del supporto per il debug del lettore UWP/IL2CPP.

- **Valutazione:**

  - Aggiunta del supporto per gli identificatori esadecimali.

  - Miglioramento dell'esperienza di valutazione della finestra delle espressioni di controllo.

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Correzione dell'utilizzo delle impostazioni di eccezione.

- **Project Generazione:**

  - Esclusione delle unità di compilazione di gestione pacchetti dalla generazione.

## <a name="3605"></a>3.6.0.5

Data di rilascio: 13 marzo 2018

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Project Generazione:**

  - Aggiunta del supporto per il nuovo generatore di progetti in Unity 2018.1.

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Correzione della gestione degli stati danneggiati con progetti personalizzati.

- **Debugger:**

  - Correzione dell'impostazione dell'istruzione successiva.

## <a name="3604"></a>3.6.0.4

Data di rilascio: 5 marzo 2018

### <a name="bug-fixes"></a>Correzioni di bug

- **Project Generazione:**

  - Correzione del rilevamento della versione di Mono.

- **Integrazione:**

  - Correzione dei problemi di tempistica per l'attivazione di 2018.1 e plug-in.

## <a name="3603"></a>3.6.0.3

Data di rilascio: 23 febbraio 2018

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Project Generazione:**

  - Aggiunta del supporto per .NET Standard.

### <a name="bug-fixes"></a>Correzioni di bug

- **Project Generazione:**

  - Correzione del rilevamento del framework di destinazione Unity.

- **Debugger:**

  - Correzione dell'interruzione per eccezioni generate al di fuori del codice utente.

## <a name="3602"></a>3.6.0.2

Data di rilascio: 7 febbraio 2018

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione:**

  - Aggiornamento della superficie dell'API UnityMessage per 2017.3.

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - I progetti vengono ricaricati solo per modifiche esterne (con limitazione).

## <a name="3601"></a>3.6.0.1

Data di rilascio: 24 gennaio 2018

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Correzione della conversione automatica dei simboli di debug da pdb a mdb.

  - Correzione della chiamata indiretta a EditorPrefs.GetBool con effetti sul controllo durante il tentativo di modifica delle dimensioni della matrice.

## <a name="3600"></a>3.6.0.0

Data di rilascio: 10 gennaio 2018

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Project Generazione:**

  - Aggiunta del supporto per il modello di riferimento MonoIsland 2018.1.

- **Valutazione:**

  - Aggiunta del supporto per l'identificatore $exception.

- **Debugger:**

  - Aggiunta del supporto per gli attributi DebuggerHidden/DebuggerStepThrough con il nuovo runtime di Unity.

- **Procedure guidate:**

  - Introduzione della versione 'Latest' per le procedure guidate.

### <a name="bug-fixes"></a>Correzioni di bug

- **Project Generazione:**

  - Correzione del calcolo del GUID di progetto per i progetti di lettore.

- **Debugger:**

  - Correzione di una race condition nella gestione degli eventi di interruzione.

- **Procedure guidate:**

  - Aggiornamento del contesto roslyn prima dell'inserimento del metodo.

## <a name="3503"></a>3.5.0.3

Data di rilascio: 9 gennaio 2018

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Correzione della conversione automatica dei simboli di debug da pdb a mdb.

## <a name="3502"></a>3.5.0.2

Data di rilascio: 4 dicembre 2017

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Integrazione:**

  - I progetti Unity vengono ora ricaricati automaticamente in Visual Studio quando si aggiunge o rimuove uno script da Unity.

- **Debugger:**

  - È stata aggiunta un'opzione che consente di eseguire il debug dell'editor di Unity tramite il debugger Mono condiviso da Xamarin e Visual Studio per Mac.

  - È stato aggiunto il supporto per i file di simboli di debug portatili.

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione:**

  - Sono stati corretti problemi relativi alle dipendenze di installazione.

  - È stata corretta la mancata visualizzazione del menu della Guida dell'API di Unity.

- **Project Generazione:**

  - È stata corretta la generazione di un progetto giocatore quando si lavora a un gioco UWP con il back-end IL2CPP/.NET 4.6.

  - È stato corretto il problema dell'aggiunta di estensioni dll in eccesso al nome del file di assembly.

  - È stato corretto l'utilizzo del livello di compatibilità di un'API di un progetto specifico anziché del livello di compatibilità globale.

  - Non forzare il flag Unity AllowAttachedDebuggingOfEditor Unity, il cui valore predefinito è ora 'true'.

## <a name="3402"></a>3.4.0.2

Data di rilascio: 19 settembre 2017

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Project Generazione:**

  - Supporto aggiunto per le unità di compilazione assembly.json.

  - La copia delle assembly dell'unità per la cartella del progetto è stata arrestata.

- **Debugger:**

  - Supporto aggiunto per l'impostazione dell'istruzione successiva con il nuovo runtime dell'unità.

  - Supporto aggiunto per il tipo di decimale con il nuovo runtime dell'unità.

  - Supporto aggiunto per le conversioni implicite/esplicite.

### <a name="bug-fixes"></a>Correzioni di bug

- **Valutazione:**

  - Creazione della matrice di Fixed con dimensioni implicite.

  - Il compilatore di Fixed ha generato degli elementi con variabili locali.

- **Project Generazione:**

  - Riferimento di Fixed a Microsoft.CSharp per il livello API 4.6.

## <a name="3302"></a>3.3.0.2

Data di rilascio 15 agosto 2017

### <a name="bug-fixes"></a>Correzioni di bug

- **Project Generazione:**

  - È stata corretta la generazione della soluzione Visual Studio in Unity 5.5 e versioni precedenti.

## <a name="3300"></a>3.3.0.0

Data di rilascio: 14 agosto 2017

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Valutazione:**

  - Supporto aggiunto per la creazione di struct con il nuovo runtime dell'unità.

  - Supporto minimo aggiunto per i puntatori.

### <a name="bug-fixes"></a>Correzioni di bug

- **Valutazione:**

  - Chiamata del metodo di Fixed sulle primitive.

  - Valutazione del campo di Fixed con tipi contrassegnati con BeforeFieldInit.

  - Chiamate non supportate di Fixed con operatori binari (sottrarre).

  - Problemi di Fixed quando si aggiungono elementi all'espressione di controllo di Visual Studio.

- **Project Generazione:**

  - Riferimenti ai nomi assembly di Fixed con i file mcs.rsp.

  - Fixed è definito con i livelli di API.

## <a name="3200"></a>3.2.0.0

Data di rilascio: 10 maggio 2017

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Programma di installazione:**

  - Supporto aggiunto per la pulizia della cache MEF.

### <a name="bug-fixes"></a>Correzioni di bug

- **Editor di codice:**

  - Classificazione/completamento di Fixed con gli attributi personalizzati.

  - Sfarfallio di Fixed con messaggi di Unity.

## <a name="3100"></a>3.1.0.0

Data di rilascio: 7 aprile 2017

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Debugger:**

  - Aggiunto il supporto per il nuovo runtime di Unity, compatibile con .NET 4.6 / C# 6.

- **Project Generazione:**

  - Aggiunta del supporto per il profilo .NET 4.6.

  - Aggiunta del supporto per i file con estensione mcs.rsp.

  - Abilita sempre l'opzione di compilazione non sicura quando viene usato Unity 5.6.

  - Aggiunto il supporto per la generazione del progetto "Player" quando si usa la piattaforma Windows Store e il back-end il2cpp.

### <a name="bug-fixes"></a>Correzioni di bug

- **Editor di codice:**

  - Corretta la posizione del cursore dopo l'inserimento del metodo con completamento automatico.

- **Project Generazione:**

  - Eliminata la post-elaborazione della versione dell'assembly.

## <a name="3001"></a>3.0.0.1

Data di rilascio: 7 aprile 2017

### <a name="this-version-includes-all-new-features-and-bug-fixes-introduced-with-28x-series"></a>Questa versione include tutte le nuove funzionalità e correzioni di bug introdotte con la serie 2.8.x.

## <a name="2820---30-preview-3"></a>2.8.2.0 (3.0 anteprima) 3
Data di rilascio: 25 gennaio 2017

### <a name="bug-fixes"></a>Correzioni di bug

- **Project Generazione:**

  - Corretta la regressione dove veniva fatto riferimento ai progetti Plugins due volte, prima come DLL binario e poi come riferimento al progetto.

## <a name="2810---30-preview-2"></a>2.8.1.0 (3.0 anteprima) 2
Data di rilascio: 23 gennaio 2017

### <a name="bug-fixes"></a>Correzioni di bug

- **Editor di codice:**

  - Corretto un arresto anomalo all'avvio di una dichiarazione di attributo senza completamento parentesi graffa.

- **Debugger:**

  - Corretti i punti di interruzione delle funzioni con coroutine sotto il nuovo compilatore/runtime Unity.

  - Aggiunto un avviso in caso di punto di interruzione non associabile (quando non viene trovato alcun percorso di origine corrispondente).

- **Project Generazione:**

  - Corretta la generazione di file csproj con caratteri speciali/localizzati.

  - Corretti i riferimenti esterni ad Asset, ad esempio Libreria (come Facebook SDK).

- **Varie:**

  - Aggiunto il controllo per impedire l'esecuzione di Unity durante l'installazione o la disinstallazione.

  - Eseguito il passaggio a https per l'uso della documentazione remota di Unity.

## <a name="2800---30-preview"></a>2.8.0.0 (3.0 anteprima)
Data di rilascio: 17 novembre 2016

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Generale:**

  - Aggiunto il supporto per l'installazione di Visual Studio 2017.

  - Aggiunto il supporto per l'estensione di Visual Studio 2017.

  - Aggiunto il supporto per la localizzazione.

- **Editor di codice:**

  - Aggiunto IntelliSense C# per i messaggi di Unity.

  - Aggiunta la colorazione del codice C# per i messaggi di Unity.

- **Debugger:**

  - Aggiunto il supporto per le espressioni `is`, `as`, cast diretto, `default`, `new`.

  - Aggiunto il supporto per le espressioni string concat.

  - Aggiunto il supporto per la visualizzazione esadecimale di valori Integer.

  - Aggiunto il supporto per la creazione di nuove variabili temporanee (istruzioni).

  - Aggiunto il supporto per le conversioni implicite di primitive.

  - Aggiunti messaggi di errore più efficaci quando un tipo è previsto o non trovato.

- **Project Generazione:**

  - Rimosso il suffisso CSharp dai nomi di progetto.

  - Rimosso il riferimento a un file di destinazioni di MSBuild a livello di sistema.

- **Procedure guidate:**

  - Aggiunto il supporto per i messaggi di Unity in tipi non Behaviour come Editor o EditorWindow.

  - Eseguito il passaggio a Roslyn per inserire e formattare i messaggi di Unity.

### <a name="bug-fixes"></a>Correzioni di bug

- **Debugger:**

  - Risolto un bug con arresto anomalo di Unity durante la valutazione di tipi generici.

  - Corretta la gestione dei tipi nullable.

  - Corretta la gestione delle enumerazioni.

  - Corretta la gestione dei tipi di membro annidato.

  - Corretto l'accesso all'indicizzatore raccolta.

  - Corretto il supporto per il debug dei frame di iteratore con il nuovo compilatore C#.

- **Project Generazione:**

  - Corretto il bug che impediva la compilazione quando si usava Unity Web Player.

  - Corretto il bug che impediva la compilazione durante la compilazione di uno script con nome file con codifica Web.

## <a name="2300"></a>2.3.0.0

Data di rilascio: 14 luglio 2016

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Generale:**

  - Aggiunta un'opzione per disabilitare i log della console Unity nell'elenco errori di Visual Studio.

  - Aggiunta un'opzione per consentire la modifica delle proprietà del progetto generato.

- **Debugger:**

  - Aggiunti i visualizzatori stringa per testo, XML, HTML e JSON.

- **Procedure guidate:**

  - Aggiunti i MonoBehaviour mancanti.

### <a name="bug-fixes"></a>Correzioni di bug

- **Generale:**

  - Risolto un conflitto con ReSharper che impediva la visualizzazione di controlli all'interno delle impostazioni di Visual Studio.

  - Risolto un conflitto con Xamarin che impediva il debug in alcuni casi.

- **Debugger:**

  - Risolto un problema che causava il blocco di Visual Studio durante il debug.

  - Risolto un problema con i punti di interruzione di funzione in Visual Studio 2015.

  - Risolti diversi problemi di valutazione delle espressioni.

## <a name="2200"></a>2.2.0.0

Data di rilascio: 4 febbraio 2016

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- **Procedure guidate:**

  - Aggiunta della ricerca intelligente nella procedura guidata **Implement Monobehaviour** .

  - Le procedure guidate ora riconoscono il contesto. Ad esempio, i messaggi NetworkBehavior sono disponibili solo quando si lavora con NetworkBehavior.

  - Aggiunta del supporto per i messaggi NetworkBehavior nelle procedure guidate.

- **UI:**

  - Aggiunta di un'opzione per configurare la visibilità dei messaggi MonoBehavior.

  - Rimozione delle pagine delle proprietà di Visual Studio non rilevanti per i progetti Unity.

### <a name="bug-fixes"></a>Correzioni di bug

- **Generazione del progetto:**

  - Correzione dei riferimenti a UnityEngine e UnityEditor in Unity 4.6.

  - Correzione della generazione dei file di progetto in caso di esecuzione di Unity su OSX.

  - Correzione della gestione dei nomi di progetto contenenti caratteri cancelletto (#).

  - Limitazione dei progetti generati a C# 4.

- **Debugger:**

  - Risolto un problema relativo alla valutazione delle espressioni durante il debug all'interno di un coroutine Unity.

  - Risolto un problema che causava il blocco di Visual Studio durante il debug.

- **UI:**

  - Risolto un problema di incompatibilità con l'estensione di Visual Studio [Tabs Studio](https://tabsstudio.com/) .

- **Programma di installazione:**

  - Supporto dell'installazione a livello di computer di VSTU (installazione per tutti gli utenti) mediante la creazione di voci del Registro di sistema HKLM.

  - Risoluzione dei problemi con la disinstallazione di VSTU quando viene installata la stessa versione di VSTU per più versioni diverse di Visual Studio. Ad esempio, quando sono installati sia VSTU **2015** 2.1.0.0 che VSTU **2013** 2.1.0.0.

## <a name="2100"></a>2.1.0.0

Data di rilascio: 8 settembre 2015

### <a name="new-features"></a>Nuove funzioni e caratteristiche

- Supporto di Unity 5.2

### <a name="bug-fixes"></a>Correzioni di bug

- Visualizzazione di voci di menu in Unity < 4.2

- Non viene più visualizzato un messaggio di errore quando Visual Studio blocca i file XMLS IntelliSense.

- Gestire <\<When Changed>> punti di interruzione condizionali quando l'argomento condizionale non è un valore booleano.

- Correzione dei riferimenti agli assembly UnityEngine e UnityEditor per le app di Windows Store.

- Correzione dell'errore durante l'esecuzione di istruzioni nel debugger: Impossibile eseguire l'istruzione. Eccezione generale.

- Correzione dei punti di interruzione dei passaggi in Visual Studio 2015.

## <a name="2000"></a>2.0.0.0

Data di rilascio: 20 luglio 2015

### <a name="bug-fixes"></a>Correzioni di bug

- **Integrazione con Unity:**

  - Correzione della conversione dei simboli di debug creati con Visual Studio 2015 durante l'importazione di una DLL e dei relativi simboli di debug (PDB).

  - Vengono generati sempre file MDB durante l'importazione di una DLL e dei relativi simboli di debug (PDB), tranne quando viene fornito anche un file MDB.

  - Correzione dell'inquinamento della directory di progetto Unity con una directory obj.

  - Correzione della generazione di riferimenti a System.Xml.Link e System.Runtime.Serialization.

  - Aggiunta del supporto di più sottoscrittori agli hook delle API di generazione di file di progetto.

  - Viene sempre completata la generazione di file di progetto anche quando uno dei file da generare è bloccato.

  - Aggiunta del supporto dei caratteri jolly * nel filtro delle estensioni quando si specificano i file da includere nel progetto C#.

- **Visual Studio integrazione:**

  - Risolto un problema di compatibilità con Productivity Power Tools.

  - Correzione della generazione di MonoBehavior nelle dichiarazioni di eventi e delegati.

- **Debugger:**

  - Correzione di un blocco potenziale durante il debug.

  - Risolto un problema di mancata visualizzazione delle variabili locali in alcuni stack frame.

  - Correzione del controllo delle matrici vuote.

## <a name="1990---20-preview-2"></a>1.9.9.0 (2.0 anteprima) 2
Data di rilascio: 2 aprile 2015

### <a name="new-features"></a>Nuove funzionalità

- **Esplora progetti Unity:**

  - Ridenominazione automatica della classe quando si rinomina un file in Esplora progetti Unity (vedere la finestra di dialogo **Opzioni** ).

  - Selezione automatica dei nuovi script creati in Esplora progetti Unity.

  - Rilevamento dello script attivo in Esplora progetti Unity (vedere la finestra di dialogo **Opzioni** ).

  - Doppia sincronizzazione di Esplora soluzioni di Visual Studio (vedere la finestra di dialogo **Opzioni** ).

  - Adozione delle icone di Visual Studio in Esplora progetti Unity.

- **Debugger:**

  - Possibilità di selezionare la destinazione di debug attiva da un elenco di destinazioni salvate o usate di recente (vedere la finestra di dialogo **Opzioni** ).

  - Creazione di punti di interruzione delle funzioni in metodi MonoBehavior e loro applicazione a più classi MonoBehavior.

  - Supporto di Crea ID oggetto nel debugger.

  - Supporto del numero di passaggi del punto di interruzione nel debugger.

  - Supporto dell'interruzione in caso di eccezioni nel debugger (sperimentale. Vedere la finestra di dialogo **Opzioni** ).

  - Supporto della creazione di oggetti e matrici durante la valutazione di espressioni nel debugger.

  - Supporto dei confronti Null durante la valutazione di espressioni nel debugger.

  - Possibilità di escludere membri obsoleti nelle finestre delle espressioni di controllo del debugger.

- **Programma di installazione:**

  - Ottimizzazione della registrazione delle estensioni di Visual Studio Tools per Unity.

  - Installazione del pacchetto Visual Studio Tools per Unity per Unity 5.

- **Documentazione:** miglioramento delle prestazioni di generazione della documentazione.

- **Procedure guidate:** supporto dei nuovi metodi MonoBehavior per Unity 4.6 e Unity 5.

- **Unity:** ricerca di flag non sicuri e definizioni personalizzate nei file RSP durante la generazione dei file di progetto.

- **Interfaccia utente:** aggiunta della finestra di dialogo **Opzioni** di Visual Studio Tools per Unity in Visual Studio.

### <a name="bug-fixes"></a>Correzioni di bug

- **Esplora progetti Unity:**

  - Aggiornamento di Esplora progetti Unity dopo lo spostamento o la ridenominazione dei file in Esplora soluzioni di Visual Studio.

  - Mantenimento delle selezioni quando i file vengono rinominati in Esplora progetti Unity.

  - Disattivazione dell'espansione e della compressione automatiche quando si fa doppio clic sui file in Esplora progetti Unity.

  - Possibilità di visualizzare in Esplora progetti Unity i nuovi file selezionati.

- **Debugger:**

  - Risoluzione di un possibile problema di blocco di Visual Studio durante la valutazione di espressioni nel debugger.

  - Le chiamate dei metodi vengono sempre eseguite nel dominio corretto nel debugger.

- **Unità:**

  - Correzione del percorso di UnityVS.OpenFile con Unity 5.

  - Correzione del percorso di pdb2mdb con Unity 5.

  - Correzione di una possibile eccezione durante la generazione dei file di progetto.

  - Correzione di un possibile problema di blocco durante l'esecuzione di Unity su OSX.

  - Gestione delle eccezioni interne.

  - Invio dei log della console di Unity all'elenco degli errori di Visual Studio.

- **Documentazione:** correzione della generazione della documentazione per la nuova documentazione di Unity.

- **Progetto:** spostamento e ridenominazione dei file con estensione meta di Unity quando necessario, anche in cartelle.

- **Procedure guidate:** correzione dell'ordine dei parametri dei metodi MonoBehavior durante la generazione del codice.

- **Interfaccia utente:** supporto dei temi di Visual Studio per il menu di scelta rapida e le icone.

## <a name="1980---20-preview"></a>1.9.8.0 (2.0 anteprima)
Data di rilascio: 12 novembre 2014

### <a name="new-features"></a>Nuove funzionalità

- Supporto per Visual Studio 2015.

- Colorazione del codice per shader Unity in Visual Studio 2015.

- Miglioramento della visualizzazione dei valori durante il debug:

  - Miglioramento della visualizzazione per ArrayLists, elenchi, tabelle hash e dizionari.

  - Visualizzazione di membri non pubblici e statici come categorie in espressioni di controllo e visualizzazioni locali.

  - Miglioramento della visualizzazione di SerializedProperty di Unity per valutare solo il campo del valore valido per la proprietà.

  - Supporto di DebuggerDisplayAttribute per classi e struct.

  - Supporto di DebuggerTypeProxyAttribute.

- Inserimento dei metodi MonoBehaviour mediante le procedure guidate per rispettare le convenzioni per la scrittura di codice degli utenti.

- Implementazione del supporto per modelli di testo in fase di compilazione in progetti generati con UnityVS.

- Implementazione del supporto per risorse ResX in progetti generati con UnityVS.

- Supporto dell'apertura di shader Visual Studio da Unity.

### <a name="bug-fixes"></a>Correzioni di bug

- Pulizia dei socket prima di avviare il gioco in Unity dopo l'attivazione di Connetti ed Esegui in Visual Studio. Questa correzione risolve alcuni problemi di stabilità della connessione tra Unity e Visual Studio quando si usano le opzioni Connetti ed Esegui.

- Mancata chiamata nell'interfaccia del debugger del motore di script di Unity di metodi che tendono a bloccare Unity. Questa correzione risolve il blocco di Unity durante il collegamento del debugger.

- Correzione della visualizzazione degli stack di chiamate quando non è disponibile alcun simbolo.

- Mancata registrazione del callback di log se non è necessario.

## <a name="1920"></a>1.9.2.0

Data di rilascio: 9 ottobre 2014

### <a name="new-features"></a>Nuove funzionalità

- Miglioramento del rilevamento dei lettori di Unity.

- Quando si usa lo strumento di apertura dei file, Unity passa il numero di riga nonché il nome del file.

- Visualizzazione predefinita della documentazione di Unity online se non è disponibile documentazione locale.

### <a name="bug-fixes"></a>Correzioni di bug

- Correzione di un potenziale arresto anomalo di Unity al raggiungimento di un punto di interruzione dopo il ricaricamento di un dominio.

- Correzione delle eccezioni visualizzate nella console di Unity quando si chiudono le finestre Configurazione o Informazioni su, dopo il ricaricamento di un dominio.

- Correzione del rilevamento di Unity a 64 bit in esecuzione in locale.

- Correzione dei filtri dei metodi MonoBehaviour per ogni versione di Unity nelle procedure guidate.

- Correzione di un bug per cui tutte le risorse venivano incluse nei file di progetto se il filtro delle estensioni era vuoto.

## <a name="1910"></a>1.9.1.0

Data di rilascio: 22 settembre 2014

### <a name="new-features"></a>Nuove funzionalità

- Ottimizzazione dell'associazione dei punti di interruzione a percorsi di origine.

- Supporto per i metodi di overload nella valutazione di espressioni del debugger.

- Supporto per il boxing delle primitive e dei tipi di valore nella valutazione di espressioni del debugger.

- Supporto per la ricreazione dell'ambiente delle variabili locali C# durante il debug di metodi anonimi.

- Eliminazione e ridenominazione dei file con estensione meta durante l'eliminazione o la ridenominazione di file da Visual Studio.

### <a name="bug-fixes"></a>Correzioni di bug

- Correzione della gestione dei temi di Visual Studio. Nelle versioni precedenti le finestre di dialogo su temi neri possono apparire vuote.

- Correzione del blocco di Unity durante la connessione del debugger quando Unity è in fase di ricompilazione.

- Correzione dei punti di interruzione durante il debug di editor o lettori remoti compilati su un altro sistema.

- Correzione di un possibile arresto anomalo di Visual Studio quando viene raggiunto un punto di interruzione.

- Correzione dell'associazione dei punti di interruzione per evitare che vengano visualizzati come non caricati.

- Correzione della gestione dell'ambito delle variabili nel debugger per evitare variabili live indicate come esterne all'ambito.

- Correzione della ricerca di membri statici nella valutazione di espressioni del debugger.

- Correzione della visualizzazione dei tipi nella valutazione di espressioni del debugger in modo da mostrare proprietà e campi statici.

- Correzione della generazione della soluzione quando i nomi di progetto Unity includono caratteri speciali non accettati da Visual Studio (problema Connect #948666).

- Correzione del pacchetto Visual Studio Tools per Unity in modo da arrestare immediatamente l'invio di eventi della console dopo la deselezione dell'opzione (problema Connect #933357).

- Correzione del rilevamento dei riferimenti per rigenerare correttamente riferimenti a nuove API come UnityEngine.UI in progetti generati con UnityVS.

- Correzione del programma di installazione in modo da richiedere che Visual Studio venga chiuso prima dell'installazione, per evitare installazioni danneggiate.

- Correzione del programma di installazione in modo da installare gli assembly di riferimento di Unity come componenti autonomi appropriati, condivisi tra tutte le versioni di VSTU.

- Correzione dell'apertura di script con VSTU nelle versioni a 64 bit di Unity.

## <a name="1900"></a>1.9.0.0

Data di rilascio: 29 luglio 2014

### <a name="new-features"></a>Nuove funzionalità

- Aggiunta della possibilità di immettere una porta e un IP personalizzati di cui eseguire il debug nella finestra di collegamento del debugger di Unity.

- Aggiunta dell'opzione di configurazione che consente di impostare Unity per l'esecuzione o meno in background.

- Aggiunta dell'opzione di configurazione che consente di generare i file di progetto e della soluzione oppure solo i file di progetto.

- Destinazione di avvio: possibilità di scegliere il collegamento a Unity o il collegamento a Unity e l'esecuzione.

- Visualizzazione di matrici multidimensionali nel debugger.

- Gestione di nuove porte di debug dei lettori di Unity.

- Gestione dei riferimenti a nuovi assembly di Unity, come gli assembly GUI di Unity 4.6.

- Annullamento della costruzione delle chiusure in modo da visualizzare correttamente variabili locali durante il debug.

- Annullamento della costruzione di variabili di iteratori generati negli argomenti durante il debug.

- Mantenimento dello stato di Esplora progetti Unity dopo il ricaricamento di un progetto.

- Aggiunta di un comando per sincronizzare Esplora progetti Unity con il documento corrente.

### <a name="bug-fixes"></a>Correzioni di bug

- Correzione dei punti di interruzione condizionali le cui condizioni vengono impostate prima dell'avvio del debugger.

- Correzione dei riferimenti a UnityEngine per evitare la generazione di avvisi.

- Correzione dell'analisi delle versioni per versioni beta di Unity.

- Correzione di un problema che comportava la mancata visualizzazione delle variabili nella finestra delle variabili locali al raggiungimento di un punto di interruzione o durante l'esecuzione di istruzioni.

- Correzione delle descrizioni comando delle variabili in Visual Studio 2013.

- Correzione della generazione della documentazione di IntelliSense per Unity 4.5.

- Correzione della comunicazione tra Unity e Visual Studio dopo il ricaricamento di un dominio (riproduzione/arresto in Unity).

- Correzione della gestione di parti dei temi di Visual Studio.

> [!IMPORTANT]
> Poiché C# è il linguaggio predominante nell'ecosistema Unity (le nuove risorse di esempio sono in C#, la documentazione di Unity sarà relativa a C# per impostazione predefinita), è stato rimosso il supporto tecnico di base per UnityScript e Boo in modo da concentrarsi meglio sull'esperienza in C#. Di conseguenza, le soluzioni VSTU sono ora solo in C# e vengono caricate molto più rapidamente.

## <a name="1820"></a>1.8.2.0

Data di rilascio: 7 gennaio 2014

### <a name="new-features"></a>Nuove funzionalità

- Risoluzione di un problema nel livello di rete del motore di script di Unity in Mavericks per l'individuazione remota degli editor.

- Gestione di nuove porte per individuare lettori remoti di Unity.

- Riferimento all'assembly UnityEngine specifico della destinazione di compilazione corrente.

- Aggiunta di un'impostazione che consente di filtrare i file da includere nei progetti generati.

- Aggiunta di un'impostazione che consente di disabilitare l'invio dei log della console all'elenco degli errori di Visual Studio. Questa impostazione è utile quando si usa PlayMaker o Console Pro, in quanto potrebbe essere registrato un solo callback in Unity per la ricezione dei log della console.

- Aggiunta di un'impostazione che consente di disabilitare la generazione di simboli di debug MDB. Questa impostazione è utile se si genera personalmente il file MDB.

### <a name="bug-fixes"></a>Correzioni di bug

- Correzione di una regressione per cui file aperti in Visual Studio da Unity >= 4.2 perdevano IntelliSense.

- Correzione delle finestre di dialogo di Visual Studio per la gestione dei temi personalizzati.

- Correzione della chiusura del menu di scelta rapida dell'ambiente di programmazione di Unity.

- Risoluzione di un problema di arresto anomalo in Unity quando l'assembly generato specifico della versione non è sincronizzato.

## <a name="1810"></a>1.8.1.0

Data di rilascio: 21 novembre 2013

### <a name="new-features"></a>Nuove funzionalità

- Modifica delle procedure guidate MonoBehaviour con le API di Unity 4.3.

- Le procedure guidate MonoBehaviour filtrano le API di Unity a seconda della versione usata.

- Aggiunta di un riferimento a System.Xml.Linq ai progetti per Unity > 4.1.

- Miglioramento delle chiamate a Debug.Log in modo da non includere l'inizio dell'analisi dello stack nel messaggio.

### <a name="bug-fixes"></a>Correzioni di bug

- Correzione di un bug per cui si generava un'interferenza con la gestione predefinita di file JavaScript in Visual Studio.

- Definitiva correzione di un pixel bianco visualizzato in Visual Studio.

- Correzione dell'eliminazione dell'assembly UnityVS.VersionSpecific se è contrassegnato come di sola lettura da un server SCM.

- Correzione delle eccezioni durante la creazione di socket nel pacchetto UnityVS.

- Correzione di un arresto anomalo in Visual Studio durante il caricamento di immagini predefinite da assembly di Visual Studio.

- Correzione di un bug nella generazione di UnityVS.VersionSpecific per le compilazioni di origine di Unity.

- Correzione di un possibile blocco durante l'apertura di un socket nel pacchetto Unity.

- Correzione della gestione dei progetti di Unity il cui nome contiene un trattino (-).

- Correzione dell'apertura di script da Unity in modo da non confondere l'ordine ALT+TAB per Unity 4.2 e versioni successive.

## <a name="1800"></a>1.8.0.0

Data di rilascio: 24 settembre 2013

### <a name="new-features"></a>Nuove funzionalità

- Drastico miglioramento della velocità di connessione del debugger.

- Gestione automatica della navigazione a file e righe in Unity 4.2 e versioni successive.

- Punti di interruzione condizionali.

- Il generatore di file di progetto gestisce ora modelli T4.

- Aggiornamento delle procedure guidate MonoBehavior con nuove API.

- Documentazione di IntelliSense in C# per tipi Unity.

- Valutazione di espressioni aritmetiche e logiche.

- Migliore individuazione degli editor remoti per l'anteprima di debug remoto.

### <a name="bug-fixes"></a>Correzioni di bug

- Correzione di un bug che determinava la perdita di un thread in Visual Studio dopo la disconnessione del debugger.

- Correzione di un pixel bianco visualizzato in Visual Studio.

- Correzione della gestione dei clic sull'icona della barra di stato.

- Correzione della generazione di riferimenti con assembly nelle cartelle dei plug-in.

- Correzione della creazione di socket dal pacchetto UnityVS in caso di eccezioni.

- Correzione del rilevamento di nuove versioni di UnityVS.

- Correzione della richiesta della gestione licenze alla scadenza della licenza.

- Correzione di un bug che poteva rendere vuoto l'elenco dei processi nella finestra di Visual Studio per il collegamento del debugger al processo.

- Correzione della modifica dei valori booleani nella visualizzazione locale.

## <a name="1220"></a>1.2.2.0

Data di rilascio: 9 luglio 2013

### <a name="bug-fixes"></a>Correzioni di bug

- Gestione dei nomi completi nell'analizzatore di espressioni.

- Correzione di un blocco correlato alla gestione delle eccezioni per cui il motore di script di Unity invia dati di stack frame non corretti.

- Correzione del processo di compilazione per destinazioni Web.

- Correzione di un possibile errore che si verificava se Visual Studio era avviato e un file eliminato era incluso nell'elenco dei file da aprire all'avvio.

- Correzione di UnityVS.OpenFile in modo da gestire file non di script, come gli shader compilati.

- Viene ora fatto riferimento a Boo.Lang e UnityScript.Lang da tutti i progetti C#.

- Correzione della generazione di riferimenti nei progetti se il progetto contiene caratteri speciali.

- Risoluzione di un problema di Visual Studio per cui le chiamate dei metodi a progetti eliminati attivavano più MessageBox NullReferenceException.

- Correzione della gestione degli assembly di Unity 4.2 Beta.

## <a name="1210"></a>1.2.1.0

Data di rilascio: 9 aprile 2013

### <a name="bug-fixes"></a>Correzioni di bug

- Correzione della distribuzione locale degli assembly di Unity per il completamento del codice in caso di un errore di I/O (come file di sola lettura o file bloccati da Visual Studio).

- Correzione di una regressione quando l'apertura di uno script da Unity non individuava il file se questo era già aperto in Visual Studio.

- Correzione di un problema di prestazioni della nuova gestione delle eccezioni.

- Correzione dell'associazione dei punti di interruzione in alcune DLL esterne.

## <a name="1200"></a>1.2.0.0

Data di rilascio: 25 marzo 2013

### <a name="new-features"></a>Nuove funzionalità

- Drastico miglioramento della velocità di connessione del debugger.

- Ottimizzazione di Gestione progetti per Unity per progetti di grandi dimensioni.

- Applicazione delle impostazioni di Visual Studio per l'interruzione (o la non interruzione) in corrispondenza di eccezioni gestite e non gestite.

- Applicazione dell'impostazione di Visual Studio per la chiamata di ToString in variabili locali.

- Aggiunta del nuovo menu Debug -> Associa debugger Unity, che consente di eseguire il debug di lettori di Unity.

- Mantenimento dei progetti personalizzati aggiunti alla soluzione UnityVS al momento della generazione dei file della soluzione.

- Aggiunta dei nuovi tasti di scelta rapida CTRL+ALT+M -> CTRL+H per visualizzare la documentazione di Unity per la funzione o il membro di Unity in corrispondenza del punto di inserimento.

- Considerazione dei file di risposta del compilatore (RSP) durante la compilazione da Visual Studio.

- Annullamento della costruzione dei tipi generati dal compilatore per mostrare le variabili durante il debug dei metodi del generatore.

- Semplificazione del debug remoto attraverso l'eliminazione della necessità di configurare una cartella condivisa in Unity. È ora sufficiente avere accesso al progetto di Unity da Windows.

- Installare un profilo Unity personalizzato come profilo di destinazione .NET standard. In questo modo, vengono corretti tutti i falsi positivi eventualmente indicati da ReSharper.

- Risoluzione di un bug del motore di script di Unity, in modo che il debugger non generi un'interruzione in corrispondenza di thread registrati non correttamente.

- Rielaborazione dello strumento di apertura dei file per evitare una race condition in Visual Studio per cui si dichiarava in grado di aprire i file ma si arrestava in modo anomalo alla richiesta di apertura dei file.

- UnityVS richiede ora di aggiornare la compilazione quando durante la compilazione del progetto in Visual Studio e non più al momento del salvataggio dei file.

### <a name="bug-fixes"></a>Correzioni di bug

- Correzione del profilo .NET personalizzato

- Correzione dell'integrazione dei temi, che corregge i problemi relativi al tema scuro di Visual Studio 2012.

- Correzione del collegamento di comportamento rapido in Visual Studio 2012.

- Correzione di un problema di esecuzione di istruzioni che poteva verificarsi durante il debug quando un thread non principale raggiungeva un punto di interruzione.

- Correzione del completamento degli alias dei tipi da parte di UnityScript e Boo, tra cui int.

- Correzione dell'eccezione durante la scrittura di una nuova stringa UnityScript o Boo.

- Correzione delle eccezioni nei menu di Unity quando una soluzione non veniva caricata.

- Correzione del bug UVS-48 per cui la digitazione di virgolette doppie produceva talvolta un errore e interrompeva la funzione (completamento del codice, evidenziazione della sintassi e così via).

- Corretto il bug UVS-46 per cui veniva generato un file di script aperto duplicato (UnityScript) quando si faceva clic sull'elenco errori di Visual Studio.

- Corretto il bug UVS-42 per cui il logo di connettività di Unity sulla barra di stato non gestiva gli eventi del mouse in Visual Studio 2012.

- Corretto il bug UVS-44 per cui CTRL+MAIUSC+Q non era disponibile in Visual Studio 2012 per metodi MonoBehaviour rapidi.

- Corretto il bug UVS-40 per cui elementi selezionati in Esplora progetti Unity non erano leggibili in caso di inattività della finestra nel tema scuro di Visual Studio 2012.

- Corretto il bug UVS-39 per cui si verificava un problema di suddivisione in token di stringhe con caratteri di escape.

- Corretto il bug UVS-35 per cui veniva richiamato ToString negli oggetti durante il controllo delle variabili.

- Corretto il bug UVS-27 relativo all'incoerenza della finestra Vai al simbolo con il tema scuro in Visual Studio 2012.

- Corretto il bug UVS-11 relativo alla presenza di variabili locali in coroutine.

## <a name="1100---beta-release"></a>1.1.0.0 - Versione beta
Data di rilascio: 9 marzo 2013

## <a name="10130"></a>1.0.13.0
Data di rilascio: 21 gennaio 2013

### <a name="bug-fixes"></a>Correzioni di bug

- Correzione di un blocco di Visual Studio che poteva verificarsi se la destinazione oggetto del debug inviava eventi di thread non validi. Questo bug si verificava in genere durante il debug di un'istanza remota di Unity su OSX.

- Correzione di un blocco di Visual Studio che poteva verificarsi se un'eccezione arrestava il debugger.

- Correzione degli helper MonoBehavior quando un oggetto MonoBehavior C# è incluso in uno spazio dei nomi.

- Correzione delle descrizioni comando del debugger per UnityScript in Visual Studio 2012.

- Correzione della generazione di progetti in caso di modifica delle sole costanti di debug da Unity.

- Correzione della navigazione tramite tastiera in Esplora progetti Unity.

- Correzione della colorazione di UnityScript per stringhe con caratteri di escape.

- Correzione dello strumento di apertura dei file in modo da indovinare meglio il nome del progetto se usato esternamente a Unity. Questo comportamento è necessario quando l'utente usa uno strumento di apertura dei file di terze parti in Unity che delega a UnityVS.

- Correzione della gestione di messaggi lunghi inviati da Unity a UnityVS. Prima di questa correzione, i messaggi lunghi potevano provocare l'arresto anomalo della parte di messaggistica di UnityVS. Di conseguenza, talvolta UnityVS non era in grado di aprire un file da Unity.

## <a name="10120"></a>1.0.12.0
Data di rilascio: 3 gennaio 2013

### <a name="bug-fixes"></a>Correzioni di bug

- Correzione di un blocco di Visual Studio che poteva verificarsi durante l'eliminazione di un punto di interruzione.

- Correzione di un bug per cui non era possibile raggiungere alcuni punti di interruzione dopo la ricompilazione di script di gioco da parte di Unity.

- Correzione del debugger in modo da notificare correttamente a Visual Studio la mancata associazione dei punti di interruzione.

- Correzione di un problema di registrazione che poteva impedire al debugger di Visual Studio di eseguire il debug di programmi nativi.

- Correzione di un'eccezione che poteva verificarsi durante la valutazione di espressioni UnityScript e Boo.

- Correzione di una regressione in cui la modifica del livello API .NET in Unity non attiva un aggiornamento dei file di progetto.

- Correzione di un problema di un'API per cui il codice utente non poteva fare parte del gestore dei callback di log.

## <a name="10110"></a>1.0.11.0
Data di rilascio: 28 novembre 2012

### <a name="new-features"></a>Nuove funzionalità

- Supporto ufficiale di Unity 4.

- Modifica di script da Gestione progetti per Unity.

- Integrazione nella finestra Passa a di Visual Studio.

- Analisi del messaggio della console di informazioni, per cui facendo clic nell'elenco degli errori si viene indirizzati al primo stack frame con simboli.

- Aggiunta di un'API per consentire all'utente di partecipare alla generazione del progetto.

- Aggiunta di un'API per consentire all'utente di partecipare a LogCallback.

### <a name="bug-fixes"></a>Correzioni di bug

- Correzione di una regressione nello sfondo di Esplora progetti Unity in Visual Studio 2012.

- Correzione della generazione del progetto per gli utenti del profilo .NET completo.

- Correzione della generazione di progetti per gli utenti della destinazione Web.

- Correzione della generazione di progetti in modo da includere i simboli di compilazione DEBUG e TRACE come avviene in Unity.

- Correzione dell'arresto anomalo durante l'uso di caratteri speciali nella finestra Vai al simbolo.

- Correzione dell'arresto anomalo quando non è possibile inserire l'icona nella barra di stato di Visual Studio.

## <a name="10100"></a>1.0.10.0
Data di rilascio: 9 ottobre 2012

### <a name="bug-fixes"></a>Correzioni di bug

- Correzione dello sfondo di Esplora progetti Unity in Visual Studio 2010.

- Correzione di un blocco di Visual Studio che poteva verificarsi se UnityVS tentava di collegare il debugger a un'istanza di Unity la cui interfaccia del debugger aveva subito un arresto anomalo in precedenza.

- Correzione di un blocco di Visual Studio che poteva verificarsi quando era impostato un punto di interruzione e veniva eseguito un ricaricamento di AppDomain.

- Correzione del modo in cui gli assembly vengono recuperati da Unity per evitare il blocco dei file e la confusione del processo di compilazione di Unity.

## <a name="1090"></a>1.0.9.0

Data di rilascio: 3 ottobre 2012

### <a name="bug-fixes"></a>Correzioni di bug

- Correzione della generazione di progetti quando il progetto di Unity include risorse JavaScript effettive.

- Correzione di un errore di gestione nella valutazione di espressioni.

- Correzione dell'impostazione di nuovi valori in campi di tipi di valore.

- Correzione di possibili effetti collaterali quando si posiziona il puntatore su espressioni nell'editor di codice.

- Correzione del modo in cui i tipi vengono cercati negli assembly caricati per la valutazione di espressioni.

- Corretto il bug UVS-21 per cui la valutazione dell'assegnazione su oggetti Unity non aveva effetto.

- Corretto il bug UVS-21 che generava un puntatore non valido durante la valutazione della chiamata di un metodo nell'API Math di Unity.

## <a name="1080"></a>1.0.8.0

Data di rilascio: 26 settembre 2012

### <a name="bug-fixes"></a>Correzioni di bug

- Correzione del modo in cui lo strumento di apertura dei file acquisiva il percorso del progetto in modo da garantire che sia in grado di aprire sia Visual Studio sia gli script.

- Correzione di un bug relativo ai punti di interruzione creati durante l'esecuzione della sessione di debug, che poteva provocare il blocco di Visual Studio.

- Correzione del modo in cui UnityVS viene registrato in Visual Studio 2010.

## <a name="1070"></a>1.0.7.0

Data di rilascio: 14 settembre 2012

### <a name="new-features"></a>Nuove funzionalità

- Supporto di Visual Studio 2012.

### <a name="bug-fixes"></a>Correzioni di bug

- Correzione della generazione di file di progetto degli editor e dei plug-in in modo che corrisponda al comportamento di Unity.

- Correzione della traduzione di simboli PDB in Unity 4.

> [!IMPORTANT]
> A causa del supporto di Visual Studio 2012, è stato necessario rinominare alcuni file e spostarne altri. Il pacchetto UnityVS per importare Unity si chiama ora UnityVS 2010 o UnityVS 2012, rispettivamente per Visual Studio 2010 e Visual Studio 2012. Per questa versione è anche necessario che i file di progetto di UnityVS vengano rigenerati.

## <a name="1060---internal-build"></a>1.0.6.0 - Build interna
Data di rilascio: 12 settembre 2012

## <a name="1050"></a>1.0.5.0

Data di rilascio: 10 settembre 2012

### <a name="bug-fixes"></a>Correzioni di bug

- Correzione della generazione dei file di progetto quando gli script o gli shader contengono un carattere XML non valido.

- Correzione del rilevamento di istanze di Unity quando Unity è connesso al server delle risorse. Questo problema generava errori di apertura dei file da Unity e relativi alla connessione automatica del debugger di Visual Studio.

## <a name="1040"></a>1.0.4.0

Data di rilascio: 5 settembre 2012

### <a name="new-features"></a>Nuove funzionalità

- Conversione automatica dei simboli di debug in Unity.

    Se nella cartella Asset è presente un assembly DLL .NET con il file PDB associato, è sufficiente importare l'assembly perché UnityVS converta il file PDB in un file di simboli di debug riconosciuto dal motore di script di Unity e perché sia possibile passare agli assembly .NET da UnityVS.

### <a name="bug-fixes"></a>Correzioni di bug

- Correzione dell'arresto anomalo di UnityVS durante il debug, causato da eccezioni generate da metodi o proprietà all'interno di Unity.

## <a name="1030"></a>1.0.3.0

Data di rilascio: 4 settembre 2012

### <a name="new-features"></a>Nuove funzionalità

- Nuova opzione di configurazione che consente di disabilitare l'utilizzo di UnityVS per aprire file da Unity.

### <a name="bug-fixes"></a>Correzioni di bug

- Correzione della generazione di riferimenti a UnityEditor per progetti non di editor.

- Correzione della definizione del simbolo UNITY_EDITOR per progetti non di editor.

- Correzione di un arresto anomalo casuale di Visual Studio provocato dalla barra di stato personalizzata.

## <a name="1020"></a>1.0.2.0

Data di rilascio: 30 agosto 2012

### <a name="bug-fixes"></a>Correzioni di bug

- Correzione del conflitto con il debugger PythonTools.

- Correzione dei riferimenti a Mono.Cecil.

- Correzione di un bug relativo al modo in cui gli assembly di script vengono recuperato da Unity con Unity 4 b7.

## <a name="1010"></a>1.0.1.0

Data di rilascio: 28 agosto 2012

### <a name="new-features"></a>Nuove funzionalità

- Supporto di anteprima per Unity 4.0 Beta.

### <a name="bug-fixes"></a>Correzioni di bug

- Correzione del controllo delle proprietà che generano eccezioni.

- Correzione dell'ordine decrescente verso gli oggetti base durante il controllo degli oggetti.

- Correzione dell'elenco a discesa vuoto per il punto di inserimento nella procedura guidata MonoBehavior.

- Correzione del completamento per le DLL all'interno della cartella Asset per UnityScript e Boo.

## <a name="1000---initial-release"></a>1.0.0.0 - Versione iniziale
Data di rilascio: 22 agosto 2012
