---
title: Tecniche di debug MFC | Microsoft Docs
description: 'Informazioni sulle tecniche per il debug di programmi MFC, tra cui: punti di interruzione codificati, traccia, rilevamento di perdite di memoria, dump della memoria degli oggetti e riduzione delle dimensioni del programma.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- AfxEnableMemoryTracking
- CMemoryState
- delayFreeMemDF
- checkAlwaysMemDF
- vs.debug.mfc
- vs.debug.objects.dump
- vs.debug.memory.dump
- allocMemDF
- afxMemDF
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [MFC]
ms.assetid: b154fc31-5e90-4734-8cbd-58dd9fe1f750
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 458ffde8a2289608f1de0cd88689c4c718d4e300
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122090642"
---
# <a name="mfc-debugging-techniques"></a>Tecniche di debug MFC
Se si effettua il debug di un programma MFC, possono essere utili le seguenti tecniche di debug.

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> In questo argomento
[AfxDebugBreak](#BKMK_AfxDebugBreak)

[Macro TRACE](#BKMK_The_TRACE_macro)

[Rilevamento di perdite di memoria in MFC](#BKMK_Memory_leak_detection_in_MFC)

- [Rilevamento delle allocazioni di memoria](#BKMK_Tracking_memory_allocations)

- [Abilitazione della diagnostica della memoria](#BKMK_Enabling_memory_diagnostics)

- [Creazione di snapshot di memoria](#BKMK_Taking_memory_snapshots)

- [Visualizzazione delle statistiche di memoria](#BKMK_Viewing_memory_statistics)

- [Creazione di dump di oggetti](#BKMK_Taking_object_dumps)

  - [Interpretazione dei dump della memoria](#BKMK_Interpreting_memory_dumps)

  - [Personalizzazione di dump di oggetti](#BKMK_Customizing_object_dumps)

  - [Riduzione delle dimensioni di una build di debug di MFC](#BKMK_Reducing_the_size_of_an_MFC_Debug_build)

  - [Compilazione di un'app MFC con informazioni di debug per i moduli selezionati](#BKMK_Building_an_MFC_app_with_debug_information_for_selected_modules)

## <a name="afxdebugbreak"></a><a name="BKMK_AfxDebugBreak"></a> AfxDebugBreak
MFC offre una speciale funzione [AfxDebugBreak](/cpp/mfc/reference/diagnostic-services#afxdebugbreak) per programmare i punti di interruzione nel codice sorgente:

```cpp
AfxDebugBreak( );
```

Su piattaforme Intel `AfxDebugBreak` genera il seguente codice, che interrompe il codice sorgente anziché il codice kernel:

```cpp
_asm int 3
```

Su altre piattaforme, `AfxDebugBreak` richiama semplicemente `DebugBreak`.

Accertarsi di rimuovere le istruzioni `AfxDebugBreak` quando si crea una build di rilascio o si utilizza `#ifdef _DEBUG` per racchiuderle.

[Contenuto dell'argomento](#BKMK_In_this_topic)

## <a name="the-trace-macro"></a><a name="BKMK_The_TRACE_macro"></a> Utilizzo della macro TRACE
Per visualizzare i messaggi generati dal programma nella [finestra di output](../ide/reference/output-window.md)del debugger è possibile usare la macro [ATLTRACE](/previous-versions/6xkxyz08(v=vs.140)) oppure la macro [TRACE](/previous-versions/6w95a4ha(v=vs.140)) MFC. Analogamente alle [asserzioni](../debugger/c-cpp-assertions.md)le macro di traccia sono attive solo nella versione di debug del programma e vengono annullate quando ne viene effettuata la compilazione nella versione di rilascio.

Gli esempi che seguono illustrano alcuni metodi di utilizzo della macro **TRACE** . Analogamente a `printf`la macro **TRACE** è in grado di gestire svariati argomenti.

```cpp
int x = 1;
int y = 16;
float z = 32.0;
TRACE( "This is a TRACE statement\n" );

TRACE( "The value of x is %d\n", x );

TRACE( "x = %d and y = %d\n", x, y );

TRACE( "x = %d and y = %x and z = %f\n", x, y, z );
```

La macro TRACE gestisce in modo appropriato sia i parametri char \* che wchar_t \* parametri. Negli esempi seguenti viene illustrato l'utilizzo della macro TRACE, insieme ai diversi tipi di parametri di stringa.

```cpp
TRACE( "This is a test of the TRACE macro that uses an ANSI string: %s %d\n", "The number is:", 2);

TRACE( L"This is a test of the TRACE macro that uses a UNICODE string: %s %d\n", L"The number is:", 2);

TRACE( _T("This is a test of the TRACE macro that uses a TCHAR string: %s %d\n"), _T("The number is:"), 2);
```

Per altre informazioni sulla macro **TRACE** , vedere [Servizi diagnostici](/cpp/mfc/reference/diagnostic-services).

[Contenuto dell'argomento](#BKMK_In_this_topic)

## <a name="detecting-memory-leaks-in-mfc"></a><a name="BKMK_Memory_leak_detection_in_MFC"></a> Rilevamento di perdite di memoria in MFC
MFC offre classi e funzioni per il rilevamento della memoria allocata ma mai disallocata.

### <a name="tracking-memory-allocations"></a><a name="BKMK_Tracking_memory_allocations"></a> Gestione delle allocazioni di memoria
In MFC è possibile usare la macro [DEBUG_NEW](/previous-versions/tz7sxz99(v=vs.140)) anziché l'operatore **new** per un supporto nella ricerca di perdite di memoria. Nella versione di debug del programma, `DEBUG_NEW` tiene traccia del nome file e del numero di riga di ciascun oggetto da esso allocato. Quando si compila una versione di rilascio del programma, `DEBUG_NEW` si traduce in una semplice operazione **new** senza informazioni relative a nome file e numero di riga. La velocità non viene pertanto in alcun modo compromessa nella versione di rilascio del programma.

Se non si desidera riscrivere l'intero programma in modo da utilizzare `DEBUG_NEW` anziché **new**, sarà possibile definire questa macro nei file sorgente:

```cpp
#define new DEBUG_NEW
```

Quando si esegue un [dump di oggetti](#BKMK_Taking_object_dumps), ciascun oggetto allocato con `DEBUG_NEW` indicherà il file e il numero di riga in cui è stato allocato, consentendo di risalire all'origine delle perdite di memoria.

La versione di debug del framework MFC utilizza `DEBUG_NEW` automaticamente, a differenza del codice. Se si desidera godere dei vantaggi di `DEBUG_NEW`, sarà necessario utilizzare `DEBUG_NEW` esplicitamente oppure **#define new** come illustrato in precedenza.

[Contenuto dell'argomento](#BKMK_In_this_topic)

### <a name="enabling-memory-diagnostics"></a><a name="BKMK_Enabling_memory_diagnostics"></a> Abilitazione della diagnostica di memoria
Per poter utilizzare le utilità di diagnostica della memoria è necessario attivare la traccia diagnostica.

**Per abilitare o disabilitare la diagnostica della memoria**

- Chiamare la funzione globale [AfxEnableMemoryTracking](/previous-versions/hzsxb6e8(v=vs.140)) per abilitare o disabilitare l'allocatore di memoria diagnostico. Dal momento che la diagnostica della memoria si trova per impostazione predefinita nella libreria di debug, in genere si ricorre a questa funzione per disattivare tale diagnostica temporaneamente, aumentando la velocità di esecuzione del programma e riducendo l'output di diagnostica.

  **Per selezionare caratteristiche specifiche di diagnostica della memoria con afxMemDF**

- Se si desidera godere di un maggior controllo sulle caratteristiche di diagnostica della memoria, sarà possibile attivare e disattivare selettivamente singole caratteristiche di diagnostica della memoria impostando il valore della variabile globale MFC [afxMemDF](/previous-versions/ahe4a83t(v=vs.140)). A questa variabile è possibile assegnare i seguenti valori, come specificato dal tipo enumerato **afxMemDF**.

  |Valore|Descrizione|
  |-----------|-----------------|
  |**allocMemDF**|Attiva l'allocatore di memoria diagnostica (impostazione predefinita).|
  |**delayFreeMemDF**|Liberare memoria quando si chiama `delete` o `free` solo dopo la chiusura del programma. In questo modo il programma allocherà la maggior quantità possibile di memoria.|
  |**checkAlwaysMemDF**|Chiama [AfxCheckMemory](/cpp/mfc/reference/diagnostic-services#afxcheckmemory) ogni volta che viene allocata o liberata memoria.|

  È inoltre possibile usare combinazioni di questi valori eseguendo un'operazione OR logica, come illustrato di seguito:

  ```C++
  afxMemDF = allocMemDF | delayFreeMemDF | checkAlwaysMemDF;
  ```

  [Contenuto dell'argomento](#BKMK_In_this_topic)

### <a name="taking-memory-snapshots"></a><a name="BKMK_Taking_memory_snapshots"></a> Creazione di snapshot di memoria

1. Creare un oggetto [CMemoryState](/previous-versions/visualstudio/visual-studio-2010/2ads32e2(v=vs.100)) e chiamare la funzione membro [CMemoryState::Checkpoint](/cpp/mfc/reference/cmemorystate-structure#checkpoint) . Verrà creato il primo snapshot della memoria.

2. Dopo che il programma ha eseguito le operazioni di allocazione e disallocazione di memoria, creare un altro oggetto `CMemoryState` e chiamare `Checkpoint` per tale oggetto. Verrà creato un secondo snapshot dell'utilizzo della memoria.

3. Creare un terzo oggetto `CMemoryState` e chiamarne la funzione membro [CMemoryState::Difference](/cpp/mfc/reference/cmemorystate-structure#difference) , fornendo come argomenti i due oggetti `CMemoryState` precedenti. Se esiste una differenza tra i due stati della memoria, la funzione `Difference` restituirà un valore diverso da zero, indicando così che alcuni blocchi di memoria non sono stati disallocati.

    Il codice sarà del tipo riportato in questo esempio:

    ```cpp
    // Declare the variables needed
    #ifdef _DEBUG
        CMemoryState oldMemState, newMemState, diffMemState;
        oldMemState.Checkpoint();
    #endif

        // Do your memory allocations and deallocations.
        CString s("This is a frame variable");
        // The next object is a heap object.
        CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );

    #ifdef _DEBUG
        newMemState.Checkpoint();
        if( diffMemState.Difference( oldMemState, newMemState ) )
        {
            TRACE( "Memory leaked!\n" );
        }
    #endif
    ```

    Si noti che le istruzioni di controllo della memoria sono racchiuse tra **#ifdef _DEBUG/#endif** in modo che siano compilate solo nelle versioni di debug del programma.

    Determinata l'esistenza di una perdita di memoria, sarà possibile usare un'altra funzione membro, [CMemoryState::DumpStatistics](/cpp/mfc/reference/cmemorystate-structure#dumpstatistics) , che consentirà di individuare la perdita.

    [Contenuto dell'argomento](#BKMK_In_this_topic)

### <a name="viewing-memory-statistics"></a><a name="BKMK_Viewing_memory_statistics"></a> Visualizzazione delle statistiche di memoria
La funzione [CMemoryState::Difference](/cpp/mfc/reference/cmemorystate-structure#difference) esamina due oggetti stato di memoria e rileva eventuali oggetti non deallocati dall'heap tra gli stati iniziale e finale. Dopo aver creato snapshot di memoria e averli confrontati usando `CMemoryState::Difference`, è possibile chiamare [CMemoryState::DumpStatistics](/cpp/mfc/reference/cmemorystate-structure#dumpstatistics) per ottenere informazioni sugli oggetti non deallocati.

Si consideri l'esempio seguente:

```cpp
if( diffMemState.Difference( oldMemState, newMemState ) )
{
    TRACE( "Memory leaked!\n" );
    diffMemState.DumpStatistics();
}
```

Un dump campione sarà del seguente tipo:

```cpp
0 bytes in 0 Free Blocks
22 bytes in 1 Object Blocks
45 bytes in 4 Non-Object Blocks
Largest number used: 67 bytes
Total allocations: 67 bytes
```

I blocchi liberi rappresentano blocchi la cui deallocazione viene ritardata se `afxMemDF` è stato impostato su `delayFreeMemDF`.

I blocchi di oggetti ordinari, indicati alla seconda riga, rimangono allocati sull'heap.

I blocchi non di oggetti includono matrici e strutture allocate con `new`. In questo caso quattro blocchi non di oggetti sono stati allocati sull'heap ma non disallocati.

`Largest number used` indica la quantità massima di memoria utilizzata dal programma in qualsiasi momento.

`Total allocations` indica la quantità totale di memoria utilizzata dal programma.

[Contenuto dell'argomento](#BKMK_In_this_topic)

### <a name="taking-object-dumps"></a><a name="BKMK_Taking_object_dumps"></a> Eseguire dump di oggetti
In un programma MFC è possibile usare [CMemoryState::D umpAllObjectsSince](/cpp/mfc/reference/cmemorystate-structure#dumpallobjectssince) per eseguire il dump di una descrizione di tutti gli oggetti sull'heap che non sono stati deallocati. `DumpAllObjectsSince` esegue il dump di tutti gli oggetti allocati dall'ultima [CMemoryState::Checkpoint](/cpp/mfc/reference/cmemorystate-structure#checkpoint). Se non ha avuto luogo alcuna chiamata `Checkpoint` , `DumpAllObjectsSince` effettuerà il dump di tutti gli oggetti e non oggetti attualmente in memoria.

> [!NOTE]
> Prima di poter utilizzare il dump di oggetti MFC, è necessario [abilitare la traccia di diagnostica](#BKMK_Enabling_memory_diagnostics).

> [!NOTE]
> MFC effettua automaticamente il dump di tutti gli oggetti persi alla chiusura del programma, pertanto non è necessario creare codice per il dump degli oggetti in tale posizione.

Nel codice che segue si verifica la presenza di eventuali perdite di memoria confrontando due stati della memoria e si effettua il dump di tutti gli oggetti eventualmente persi.

```cpp
if( diffMemState.Difference( oldMemState, newMemState ) )
{
    TRACE( "Memory leaked!\n" );
    diffMemState.DumpAllObjectsSince();
}
```

Il contenuto del dump sarà del seguente tipo:

```cmd
Dumping objects ->

{5} strcore.cpp(80) : non-object block at $00A7521A, 9 bytes long
{4} strcore.cpp(80) : non-object block at $00A751F8, 5 bytes long
{3} strcore.cpp(80) : non-object block at $00A751D6, 6 bytes long
{2} a CPerson at $51A4

Last Name: Smith
First Name: Alan
Phone #: 581-0215

{1} strcore.cpp(80) : non-object block at $00A7516E, 25 bytes long
```

I numeri tra parentesi graffe all'inizio della maggior parte delle righe specificano l'ordine in cui gli oggetti sono stati allocati. L'ultimo oggetto allocato presenta il numero più alto e si trova all'inizio del dump.

Per ottenere la quantità massima di informazioni da un dump di oggetti, è possibile eseguire l'override della funzione membro `Dump` di qualsiasi oggetto derivato da `CObject`per personalizzare il dump di oggetti.

È possibile definire un punto di interruzione su una particolare allocazione di memoria impostando la variabile globale `_afxBreakAlloc` sul numero indicato tra le parentesi graffe. Se si esegue nuovamente il programma il debugger interromperà l'esecuzione quando avrà luogo tale allocazione. Sarà quindi possibile esaminare lo stack di chiamate per sapere come il programma è giunto a tale punto.

La libreria di run-time del linguaggio C dispone di una funzione simile, [_CrtSetBreakAlloc](/cpp/c-runtime-library/reference/crtsetbreakalloc), che è possibile usare per le allocazioni di run-time del linguaggio C.

[Contenuto dell'argomento](#BKMK_In_this_topic)

#### <a name="interpreting-memory-dumps"></a><a name="BKMK_Interpreting_memory_dumps"></a> Interpretazione dei dump di memoria
Considerare questo dump di oggetti in maggior dettaglio:

```cmd
{5} strcore.cpp(80) : non-object block at $00A7521A, 9 bytes long
{4} strcore.cpp(80) : non-object block at $00A751F8, 5 bytes long
{3} strcore.cpp(80) : non-object block at $00A751D6, 6 bytes long
{2} a CPerson at $51A4

Last Name: Smith
First Name: Alan
Phone #: 581-0215

{1} strcore.cpp(80) : non-object block at $00A7516E, 25 bytes long
```

Nel programma che ha generato questo dump erano presenti solo due allocazioni esplicite, una sullo stack e una sull'heap:

```cpp
// Do your memory allocations and deallocations.
CString s("This is a frame variable");
// The next object is a heap object.
CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );
```

Il costruttore `CPerson` accetta tre argomenti che rappresentano puntatori a `char`, utilizzati per inizializzare variabili membro `CString` . Nel dump della memoria è possibile individuare l'oggetto `CPerson` nonché tre blocchi non di oggetti (3, 4 e 5). Questi blocchi contengono i caratteri delle variabili membro `CString` e non verranno eliminati quando sarà chiamato il distruttore dell'oggetto `CPerson` .

Il blocco il numero 2 è l'oggetto `CPerson` stesso. `$51A4` rappresenta l'indirizzo del blocco ed è seguito dal contenuto dell'oggetto, restituito come output da `CPerson`::`Dump` quando è stato chiamato da [DumpAllObjectsSince](/cpp/mfc/reference/cmemorystate-structure#dumpallobjectssince).

È chiaro che il blocco numero 1 è associato alla variabile di frame `CString` , in quanto presenta una sequenza di numero e dimensione che corrisponde al numero di caratteri della variabile di frame `CString` . Le variabili allocate sul frame vengono automaticamente disallocate quando il frame esce dall'ambito consentito.

**Variabili di frame**

In generale gli oggetti degli heap associati a variabili di frame non devono destare preoccupazioni, poiché vengono automaticamente disallocati quando le variabili di frame escono dall'ambito consentito. Per far sì che i dump di diagnostica della memoria non siano eccessivamente ingombranti, è opportuno inserire le chiamate a `Checkpoint` in modo che restino all'esterno dell'ambito delle variabili di frame. Inserire, ad esempio, il precedente codice di allocazione tra parentesi indicanti l'ambito, come illustrato di seguito:

```cpp
oldMemState.Checkpoint();
{
    // Do your memory allocations and deallocations ...
    CString s("This is a frame variable");
    // The next object is a heap object.
    CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );
}
newMemState.Checkpoint();
```

Dopo l'inserimento delle parentesi di ambito, il dump della memoria di questo esempio sarà il seguente:

```cmd
Dumping objects ->

{5} strcore.cpp(80) : non-object block at $00A7521A, 9 bytes long
{4} strcore.cpp(80) : non-object block at $00A751F8, 5 bytes long
{3} strcore.cpp(80) : non-object block at $00A751D6, 6 bytes long
{2} a CPerson at $51A4

Last Name: Smith
First Name: Alan
Phone #: 581-0215
```

**Allocazioni di non oggetti**

Si noti che alcune allocazioni sono di oggetti (ad esempio `CPerson`) mentre altre sono allocazioni di non oggetti. Queste ultime sono allocazioni di oggetti non derivati da `CObject` o allocazioni di tipi C primitivi, ad esempio `char`, `int` o `long`. Se la classe derivata da <strong>CObject-</strong>alloca ulteriore spazio, ad esempio per buffer interni, questi oggetti presenteranno allocazioni di oggetti e di non oggetti.

**Prevenzione di perdite di memoria**

Si noti che nel codice precedente il blocco di memoria associato alla variabile di frame `CString` è stato disallocato automaticamente e non appare quindi come una perdita di memoria. La disallocazione automatica associata alle regole di ambito gestisce la maggior parte delle perdite di memoria associati alle variabili di frame.

Per gli oggetti allocati sull'heap, tuttavia, è necessario eliminare esplicitamente l'oggetto per impedire una perdita di memoria. Per eliminare l'ultima perdita di memoria dell'esempio precedente, eliminare l'oggetto `CPerson` allocato sull'heap, come segue:

```cpp
{
    // Do your memory allocations and deallocations.
    CString s("This is a frame variable");
    // The next object is a heap object.
    CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );
    delete p;
}
```

[Contenuto dell'argomento](#BKMK_In_this_topic)

#### <a name="customizing-object-dumps"></a><a name="BKMK_Customizing_object_dumps"></a> Personalizzazione dei dump di oggetti
Quando si deriva una classe da [CObject](/cpp/mfc/reference/cobject-class), è possibile eseguire l'override della funzione membro `Dump` per fornire ulteriori informazioni quando si usa [DumpAllObjectsSince](/cpp/mfc/reference/cmemorystate-structure#dumpallobjectssince) per eseguire il dump di oggetti nella [finestra Output](../ide/reference/output-window.md).

La funzione `Dump` scrive una rappresentazione testuale delle variabili membro dell'oggetto in un contesto di dump ([CDumpContext](/cpp/mfc/reference/cdumpcontext-class)). Il contesto di dump è analogo a un flusso I/O. È possibile usare l'operatore append ( **<<** ) per inviare dati a `CDumpContext` un oggetto .

Quando si esegue l'override della funzione `Dump` , è opportuno chiamare dapprima la versione della classe base di `Dump` per effettuare il dump del contenuto dell'oggetto classe base, generando poi una descrizione testuale e un valore per ciascuna variabile membro della classe derivata.

La dichiarazione della funzione `Dump` sarà del seguente tipo:

```cpp
class CPerson : public CObject
{
public:
#ifdef _DEBUG
    virtual void Dump( CDumpContext& dc ) const;
#endif

    CString m_firstName;
    CString m_lastName;
    // And so on...
};
```

Dal momento che il dump di oggetti ha senso solo quando si effettua il debug del programma, la dichiarazione della funzione `Dump` è racchiusa all'interno di un blocco **#ifdef _DEBUG / #endif** .

Nell'esempio che segue la funzione `Dump` chiama dapprima la funzione `Dump` della relativa classe base e poi scrive nel flusso diagnostico una breve descrizione di ciascuna variabile membro, insieme al valore del membro.

```cpp
#ifdef _DEBUG
void CPerson::Dump( CDumpContext& dc ) const
{
    // Call the base class function first.
    CObject::Dump( dc );

    // Now do the stuff for our specific class.
    dc << "last name: " << m_lastName << "\n"
        << "first name: " << m_firstName << "\n";
}
#endif
```

È necessario fornire un argomento `CDumpContext` per specificare la posizione in cui verrà generato l'output del dump. La versione di debug di MFC offre un oggetto `CDumpContext` predefinito denominato `afxDump` che invia l'output al debugger.

```cpp
CPerson* pMyPerson = new CPerson;
// Set some fields of the CPerson object.
//...
// Now dump the contents.
#ifdef _DEBUG
pMyPerson->Dump( afxDump );
#endif
```

[Contenuto dell'argomento](#BKMK_In_this_topic)

## <a name="reducing-the-size-of-an-mfc-debug-build"></a><a name="BKMK_Reducing_the_size_of_an_MFC_Debug_build"></a> Riduzione delle dimensioni di una build di debug MFC
Le informazioni di debug di un'applicazione MFC di grandi dimensioni possono richiedere notevole spazio su disco. Per ridurre le dimensioni, è possibile usare una di queste procedure:

1. Ricompilare le librerie MFC usando l'opzione [/Z7, /Zi, /ZI (Formato informazioni](/cpp/build/reference/z7-zi-zi-debug-information-format) di debug) anziché **/Z7**. Queste opzioni compilano un singolo file di database di programma (PDB) che contiene informazioni di debug per l'intera libreria, riducendo la ridondanza e risparmiando spazio.

2. Ricompilare le librerie MFC senza informazioni di debug (nessuna [opzione /Z7, /Zi, /ZI (Formato informazioni di](/cpp/build/reference/z7-zi-zi-debug-information-format) debug). In questo caso la mancanza delle informazioni di debug impedirà di utilizzare la maggior parte delle utilità del debugger nel codice delle librerie MFC, ma dal momento che le librerie MFC sono già state sottoposte a un debug completo, questo non dovrebbe rappresentare un problema.

3. Compilare l'applicazione con informazioni di debug solo per i moduli selezionati, come descritto di seguito.

    [Contenuto dell'argomento](#BKMK_In_this_topic)

### <a name="building-an-mfc-app-with-debug-information-for-selected-modules"></a><a name="BKMK_Building_an_MFC_app_with_debug_information_for_selected_modules"></a> Compilazione di un'app MFC con informazioni di debug per i moduli selezionati
La compilazione di moduli selezionati con le librerie di debug MFC consente di eseguire i moduli un'istruzione alla volta e di utilizzare altre utilità di debug. Questa procedura usa sia le configurazioni di debug che di versione del progetto, rendendo quindi necessarie le modifiche descritte nei passaggi seguenti e rendendo necessaria una "ricompilazione di tutti" quando è necessaria una build di versione completa.

1. In Esplora soluzioni selezionare il progetto.

2. Scegliere **Pagine delle proprietà** dal menu **Visualizza**.

3. Creare innanzitutto una nuova configurazione di progetto.

   1. Nella finestra **\<Project> di dialogo Pagine** delle proprietà fare clic sul pulsante **Gestione configurazione** proprietà.

   2. Nella [finestra di dialogo Gestione configurazione](/previous-versions/visualstudio/visual-studio-2010/t1hy4dhz(v=vs.100))individuare il progetto all'interno della griglia. Nella colonna **Configurazione** selezionare **\<New...>** .

   3. Nella [finestra di dialogo Nuova configurazione progetto](/previous-versions/visualstudio/visual-studio-2010/0eh8w4cf(v=vs.100))digitare, all'interno della casella **Nome configurazione progetto** , il nome da assegnare alla nuova configurazione, ad esempio "Debug parziale".

   4. Scegliere **Release** dall'elenco **Copia impostazioni da**.

   5. Fare **clic su OK** per chiudere la finestra di dialogo Nuova **Project** configurazione.

   6. Chiudere la finestra di dialogo **Gestione configurazione** .

4. Impostare ora le opzioni desiderate per l'intero progetto.

   1. Nella finestra di dialogo **Pagine delle proprietà** , sotto la cartella **Proprietà di configurazione** , selezionare la categoria **Generale** .

   2. Nella griglia delle impostazioni del progetto espandere **Impostazioni predefinite progetto** (se necessario).

   3. In **Impostazioni predefinite progetto** trovare **Uso di MFC**. L'impostazione corrente verrà visualizzata nella colonna di destra della griglia. Fare clic sull'impostazione corrente e modificarla in **Usa MFC in una libreria statica**.

   4. Nel riquadro di sinistra della finestra di dialogo **Pagine delle proprietà** aprire la cartella **C/C++** e selezionare **Preprocessore**. Nella griglia delle proprietà cercare **Definizioni preprocessore** e sostituire "NDEBUG" con "_DEBUG".

   5. Nel riquadro di sinistra della finestra di dialogo **Pagine delle proprietà** aprire la cartella **Linker** e selezionare la categoria **Input** . Nella griglia delle proprietà cercare **Dipendenze aggiuntive**. Nell'impostazione **Dipendenze aggiuntive** digitare "NAFXCWD.LIB" e "LIBCMT."

   6. Scegliere **OK** per salvare le nuove opzioni di compilazione e chiudere la finestra di dialogo **Pagine delle proprietà** .

5. Scegliere **Ricompila** dal menu **Compila**. Verranno così rimosse tutte le informazioni di debug dai moduli, ma non verrà apportata alcuna modifica alla libreria MFC.

6. A questo punto è necessario aggiungere nuovamente le informazioni di debug ai moduli selezionati nell'applicazione. Tenere presente che è possibile impostare punti di interruzione ed eseguire altre funzioni di debug solo nei moduli che sono stati compilati con informazioni di debug. Per ciascun file di progetto in cui si desidera includere informazioni di debug, eseguire i seguenti passaggi:

   1. In Esplora soluzioni aprire la cartella **File di origine** sotto il progetto.

   2. Selezionare il file per il quale si desidera impostare informazioni di debug.

   3. Scegliere **Pagine delle proprietà** dal menu **Visualizza**.

   4. Nella finestra di dialogo **Pagine delle proprietà** , sotto la cartella **Impostazioni di configurazione** , aprire la cartella **C/C++** , quindi selezionare la categoria **Generale** .

   5. Nella griglia delle proprietà cercare **Formato informazioni di debug.**

   6. Fare clic sulle impostazioni **Formato informazioni di debug** e selezionare l'opzione desiderata (in genere **/ZI**) per le informazioni di debug.

   7. Se si usa un'applicazione generata mediante una creazione guidata di applicazioni o si fa uso di intestazioni precompilate, sarà necessario disattivare tali intestazioni o compilarle nuovamente prima di compilare gli altri moduli. In caso contrario, verranno generati l'avviso C4650 e il messaggio di errore C2855. È possibile disattivare le intestazioni precompilate modificando l'impostazione **\<Project>** **Crea/Usa** intestazioni precompilate nella finestra di dialogo Proprietà **(** cartella Proprietà di configurazione, sottocartella **C/C++,** categoria Intestazioni precompilate). 

7. Scegliere **Compila** dal menu **Compila** per compilare nuovamente i file di progetto non aggiornati.

   In alternativa alla tecnica descritta in questo argomento è possibile usare un makefile esterno per definire singole opzioni per ciascun file. In tal caso, per collegarsi alle librerie di debug MFC, sarà necessario definire il flag [_DEBUG](/cpp/c-runtime-library/debug) per ciascun modulo. Per utilizzare le librerie di rilascio MFC, è necessario definire NDEBUG. Per altre informazioni sulla scrittura di makefile esterni, vedere [Riferimenti a NMAKE](/cpp/build/running-nmake).

   [Contenuto dell'argomento](#BKMK_In_this_topic)

## <a name="see-also"></a>Vedi anche
[Debug del codice nativo](../debugger/debugging-native-code.md)