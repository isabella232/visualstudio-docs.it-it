---
title: Dettagli heap di debug CRT | Microsoft Docs
description: L'heap di debug offre strumenti potenti per risolvere i problemi di allocazione della memoria. Informazioni sugli strumenti e su come sono utili per problemi quali perdite e sovraccarichi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debug heap, accessing
- heap functions
- _CRTDBG_CHECK_ALWAYS_DF macro
- _CrtMemDumpStatistics function
- debugging [C++], debug heap
- _CRT_BLOCK macro
- DBGINT.H file
- _CrtMemDumpAllObjectsSince function
- _crtBreakAlloc global variable
- _CrtMemState function
- _CLIENT_BLOCK macro
- _FREE_BLOCK block
- _CrtMemBlockHeader function
- heap state reporting functions
- _CRTDBG_ALLOC_MEM_DF macro
- _CrtSetBreakAlloc function
- memory blocks, allocation types on debug heap
- debugging [C++], CRT debug support
- debug heap, tracking heap allocation requests
- memory allocation, debug heap
- _NORMAL_BLOCK block
- crtBreakAlloc global variable
- _CrtDoForAllClientObjects function
- new operator, using debug heap from C++
- _CrtSetDumpClient function
- debugging [CRT], heap-related problems
- debug heap, solving memory allocation problems
- _CrtMemCheckpoint function
- debug builds, linking to debug heap
- _IGNORE_BLOCK block
- _crtDbgFlag function
- client blocks, specifying subtypes
- memory leaks, tracking
- _CrtSetDbgFlag function
- nBlockUse method
- memory leaks, CRT debug library functions
- _CRTDBG_DELAY_FREE_MEM_DF macro
- allocation request numbers
- _CRTDBG_LEAK_CHECK_DF macro
- debug heap
- memory, debugging
- _CrtReportBlockType function
- _CrtDumpMemoryLeaks function
- _CrtCheckMemory function
- debug heap, CRT
- memory blocks, free
- _BLOCK_TYPE macro
- debug heap, memory blocks
- heap allocation, debug
- debugging memory leaks
- _BLOCK_SUBTYPE macro
- debug heap, using from C++
- _CrtMemDifference function
- heap allocation, tracking requests
- debugging [Visual Studio], debug heap
- delete operator, using debug heap from C++
- blocks, types of on the debug heap
- _CRTDBG_CHECK_CRT_DF macro
- debug heap, reporting functions
ms.assetid: bf78ace6-28e4-4a04-97c6-39e0cdd00ba4
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 2714de8b6c93931832fdf5e00e1f22462e2d6e58
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630834"
---
# <a name="crt-debug-heap-details"></a>Informazioni dettagliate sull'heap di debug CRT
In questo argomento vengono fornite informazioni dettagliate sull'heap di debug CRT.

## <a name="contents"></a><a name="BKMK_Contents"></a> Contenuto
[Trovare sovraccarichi del buffer con heap di debug](#BKMK_Find_buffer_overruns_with_debug_heap)

[Tipi di blocchi sull'heap di debug](#BKMK_Types_of_blocks_on_the_debug_heap)

[Verificare l'integrità dell'heap e le perdite di memoria](#BKMK_Check_for_heap_integrity_and_memory_leaks)

[Configurare l'heap di debug](#BKMK_Configure_the_debug_heap)

[new, delete e _CLIENT_BLOCKs nell'heap di debug C++](#BKMK_new__delete__and__CLIENT_BLOCKs_in_the_C___debug_heap)

[Funzioni di creazione di report sullo stato dell'heap](#BKMK_Heap_State_Reporting_Functions)

[Tenere traccia delle richieste di allocazione heap](#BKMK_Track_Heap_Allocation_Requests)

## <a name="find-buffer-overruns-with-debug-heap"></a><a name="BKMK_Find_buffer_overruns_with_debug_heap"></a> Individuare i sovraccarichi del buffer con l'heap di debug
Due dei problemi più comuni e difficili da gestire che si presentano ai programmatori sono la sovrascrittura della fine di un buffer allocato e la perdita di memoria, ovvero la mancata liberazione delle allocazioni non più necessarie. L'heap di debug offre strumenti estremamente efficaci per la risoluzione dei problemi di allocazione di memoria di questo tipo.

Le versioni di debug delle funzioni degli heap chiamano le versioni standard o di base utilizzate nelle build di rilascio. Quando si richiede un blocco di memoria, il gestore dello heap di debug alloca dall'heap di base un blocco di memoria un poco più grande di quanto richiesto e restituisce un puntatore alla porzione utilizzata di tale blocco. Si supponga ad esempio che l'applicazione contenga la chiamata: `malloc( 10 )`. In una build di [versione, malloc](/cpp/c-runtime-library/reference/malloc) chiama la routine di allocazione dell'heap di base che richiede un'allocazione di 10 byte. In una build di debug, tuttavia, chiama _malloc_dbg , che chiama quindi la routine di allocazione heap di base che richiede un'allocazione di 10 byte più circa `malloc` 36 byte di memoria aggiuntiva. [](/cpp/c-runtime-library/reference/malloc-dbg) Tutti i blocchi di memoria generati nell'heap di debug sono connessi in un unico elenco collegato, ordinato in base al momento dell'allocazione.

La memoria aggiuntiva allocata dalle routine dello heap di debug viene utilizzata per l'archiviazione delle informazioni sulla gestione, per i puntatori che collegano tra loro i blocchi di memoria di debug e per piccoli buffer prima e dopo i dati che hanno la funzione di rilevare eventuali sovrascritture della regione allocata.

Attualmente la struttura dell'intestazione del blocco utilizzata per memorizzare le informazioni relative alla gestione dell'heap di debug viene dichiarata come segue nel file di intestazione DBGINT.H:

```cpp
typedef struct _CrtMemBlockHeader
{
// Pointer to the block allocated just before this one:
    struct _CrtMemBlockHeader *pBlockHeaderNext;
// Pointer to the block allocated just after this one:
    struct _CrtMemBlockHeader *pBlockHeaderPrev;
    char *szFileName;    // File name
    int nLine;           // Line number
    size_t nDataSize;    // Size of user block
    int nBlockUse;       // Type of block
    long lRequest;       // Allocation number
// Buffer just before (lower than) the user's memory:
    unsigned char gap[nNoMansLandSize];
} _CrtMemBlockHeader;

/* In an actual memory block in the debug heap,
 * this structure is followed by:
 *   unsigned char data[nDataSize];
 *   unsigned char anotherGap[nNoMansLandSize];
 */
```

I buffer `NoMansLand`presenti da entrambi i lati dell'area del blocco destinata ai dati dell'utente hanno attualmente una dimensione di 4 byte e sono riempiti con un valore byte noto utilizzato dalle routine dello heap di debug per verificare che i limiti del blocco di memoria dell'utente non siano stati sovrascritti. L'heap di debug riempie inoltre i nuovi blocchi di memoria con un valore noto. Se, come illustrato di seguito, si sceglie di mantenere nell'elenco collegato dello heap i blocchi liberati, anche questi blocchi liberati verranno riempiti con un valore noto. Attualmente i valori byte utilizzati sono i seguenti:

NoMansLand (0xFD) I buffer "NoMansLand" su entrambi i lati della memoria usata da un'applicazione sono attualmente riempiti con 0xFD.

Blocchi liberati (0xDD) I blocchi liberati mantenuti inutilizzati nell'elenco collegato dell'heap di debug quando è impostato il flag sono attualmente riempiti `_CRTDBG_DELAY_FREE_MEM_DF` con 0xDD.

Nuovi oggetti (0xCD) I nuovi oggetti vengono riempiti con 0xCD quando vengono allocati.

![Torna all'inizio](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [Contenuto](#BKMK_Contents)

## <a name="types-of-blocks-on-the-debug-heap"></a><a name="BKMK_Types_of_blocks_on_the_debug_heap"></a> Tipi di blocchi nell'heap di debug
Ciascun blocco di memoria dell'heap di debug viene assegnato a uno di cinque tipi di allocazione. Questi tipi vengono registrati e visualizzati nei report in modo diverso per il rilevamento di perdite e i report sullo stato. È possibile specificare il tipo di un blocco allocandolo mediante una chiamata diretta a una delle funzioni di allocazione dello heap di debug quale [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg). I cinque tipi di blocchi di memoria dell'heap di debug (impostati nel membro **nBlockUse** della struttura **_CrtMemBlockHeader**) sono i seguenti:

**_NORMAL_BLOCK** Una chiamata a [malloc](/cpp/c-runtime-library/reference/malloc) o [calloc](/cpp/c-runtime-library/reference/calloc) crea un blocco Normal. Se si ha intenzione di utilizzare solo blocchi normali e non sono necessari blocchi client, è possibile definire [_CRTDBG_MAP_ALLOC](/cpp/c-runtime-library/crtdbg-map-alloc), in modo che tutte le chiamate di allocazione dello heap vengano associate agli equivalenti di debug delle build di debug. Sarà così possibile archiviare le informazioni di nome file e numero di riga relative a ciascuna chiamata di allocazione nella corrispondente intestazione di blocco.

`_CRT_BLOCK` I blocchi di memoria allocati internamente da numerose funzioni della libreria di runtime sono contrassegnati come blocchi CRT, in modo da poter essere gestiti separatamente. Di conseguenza non avranno necessariamente alcun effetto sul rilevamento delle perdite e su altre operazioni. Le allocazioni non devono mai allocare, riallocare o liberare blocchi di tipo CRT.

`_CLIENT_BLOCK` Un'applicazione può tenere traccia con modalità speciali di un dato gruppo di allocazioni a scopo di debug effettuando tali allocazioni con questo tipo di blocco di memoria, usando chiamate esplicite alle funzioni dell'heap di debug. In MFC, ad esempio, tutti gli oggetti **CObjects** vengono allocati come blocchi client, mentre è possibile che altre applicazioni inseriscano oggetti di memoria differenti in blocchi client. È inoltre possibile specificare sottotipi dei blocchi client per consentire una registrazione più differenziata. Per specificare sottotipi di blocchi client, spostare il numero verso sinistra di 16 bit ed effettuare un'operazione `OR` su di esso con `_CLIENT_BLOCK`. Ad esempio:

```cpp
#define MYSUBTYPE 4
freedbg(pbData, _CLIENT_BLOCK|(MYSUBTYPE<<16));
```

È possibile installare una funzione hook fornita dal client per il dump degli oggetti memorizzati in blocchi Client mediante [_CrtSetDumpClient](/cpp/c-runtime-library/reference/crtsetdumpclient). Tale funzione verrà quindi chiamata ogni volta che una funzione di debug esegue il dump di un blocco Client. È inoltre possibile usare [_CrtDoForAllClientObjects](/cpp/c-runtime-library/reference/crtdoforallclientobjects) per chiamare una data funzione fornita dall'applicazione per ciascun blocco Client dell'heap di debug.

**_FREE_BLOCK** In genere, i blocchi liberati vengono rimossi dall'elenco. Per controllare che non vengano eseguite operazioni di scrittura nella memoria liberata o per simulare condizioni di memoria ridotta, è possibile scegliere di mantenere i blocchi liberati nell'elenco collegato, contrassegnati come liberi e riempiendoli con un valore byte noto (attualmente 0xDD).

**_IGNORE_BLOCK** È possibile disattivare le operazioni dell'heap di debug per un periodo di tempo. Durante questo periodo i blocchi di memoria vengono mantenuti nell'elenco, ma vengono contrassegnati come blocchi da ignorare.

Per determinare il tipo e il sottotipo di un dato blocco, usare la funzione [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype) e le macro **_BLOCK_TYPE** e **_BLOCK_SUBTYPE**. Le macro vengono definite (in Crtdbg.h) come segue:

```cpp
#define _BLOCK_TYPE(block)          (block & 0xFFFF)
#define _BLOCK_SUBTYPE(block)       (block >> 16 & 0xFFFF)
```

![Torna all'inizio](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [Contenuto](#BKMK_Contents)

## <a name="check-for-heap-integrity-and-memory-leaks"></a><a name="BKMK_Check_for_heap_integrity_and_memory_leaks"></a> Verificare l'integrità dell'heap e le perdite di memoria
È necessario accedere a diverse funzionalità dell'heap di debug dall'interno del codice. Nella seguente sezione vengono descritte alcune funzionalità e le relative modalità di utilizzo.

`_CrtCheckMemory` È possibile usare una chiamata a [_CrtCheckMemory](/cpp/c-runtime-library/reference/crtcheckmemory), ad esempio, per controllare l'integrità dell'heap in qualsiasi punto. Questa funzione esamina ciascun blocco di memoria nell'heap, verifica che le informazioni dell'intestazione del blocco di memoria siano valide e conferma che i buffer non sono stati modificati.

`_CrtSetDbgFlag` È possibile definire nei dettagli le modalità con cui l'heap di debug tiene traccia delle allocazioni ricorrendo a un flag interno, [_crtDbgFlag](/cpp/c-runtime-library/crtdbgflag), che può essere letto e impostato mediante la funzione [_CrtSetDbgFlag](/cpp/c-runtime-library/reference/crtsetdbgflag). Modificando questo flag, è possibile comunicare all'heap di debug di verificare la presenza di eventuali perdite di memoria al termine del programma e di segnalare le perdite rilevate. Analogamente, è possibile specificare che i blocchi di memoria liberati non siano rimossi dall'elenco collegato, per simulare situazioni di poca memoria. Al controllo dell'heap questi blocchi liberati vengono esaminati nella loro interezza per verificare che non siano stati compromessi.

Il flag **_crtDbgFlag** contiene i seguenti campi di bit:

|Campo di bit|Predefinito<br /><br /> Valore|Descrizione|
|---------------|-----------------------|-----------------|
|**_CRTDBG_ALLOC_MEM_DF**|On|Attiva l'allocazione di debug. Quando questo bit è off, le allocazioni rimangono concatenate ma vengono assegnate al tipo di blocco **_IGNORE_BLOCK**.|
|**_CRTDBG_DELAY_FREE_MEM_DF**|Off|Impedisce l'effettiva liberazione della memoria, ad esempio per simulare condizioni di poca memoria. Quando questo bit è on, i blocchi liberati vengono mantenuti nell'elenco collegato dell'heap di debug, ma vengono contrassegnati come **_FREE_BLOCK** e riempiti con uno speciale valore byte.|
|**_CRTDBG_CHECK_ALWAYS_DF**|Off|Causa la chiamata a **_CrtCheckMemory** a ogni allocazione e disallocazione. Ciò rallenta l'esecuzione, ma rileva velocemente gli errori.|
|**_CRTDBG_CHECK_CRT_DF**|Off|Fa sì che i blocchi contrassegnati come tipo **_CRT_BLOCK** vengano inclusi nelle operazioni di rilevamento di perdite e differenze tra stati. Quando questo bit è off, la memoria utilizzata internamente dalla libreria di runtime viene ignorata durante queste operazioni.|
|**_CRTDBG_LEAK_CHECK_DF**|Off|Fa sì che il controllo delle perdite di memoria venga eseguito al termine del programma mediante una chiamata a **_CrtDumpMemoryLeaks**. Se l'applicazione non ha liberato tutta la memoria allocata, verrà generato un report di errore.|

![Torna all'inizio](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [Contenuto](#BKMK_Contents)

## <a name="configure-the-debug-heap"></a><a name="BKMK_Configure_the_debug_heap"></a> Configurare l'heap di debug
Tutte le chiamate alle funzioni dell'heap, quali `malloc`, `free`, `calloc`, `realloc`, `new` e `delete` vengono risolte nelle versioni di debug di tali funzioni che operano nell'heap di debug. Quando si libera un blocco di memoria, l'heap di debug controlla automaticamente l'integrità dei buffer presenti da entrambi i lati dell'area allocata e genera un messaggio di errore se si è verificata una sovrascrittura.

**Per utilizzare l'heap di debug**

- Collegare la build di debug dell'applicazione a una versione di debug della libreria di runtime del linguaggio C.

  **Per modificare uno più campi di bit _crtDbgFlag e creare un nuovo stato per il flag**

1. Chiamare `_CrtSetDbgFlag` con il parametro `newFlag` impostato su `_CRTDBG_REPORT_FLAG` (per ottenere lo stato corrente di `_crtDbgFlag`) e archiviare il valore restituito in una variabile temporanea.

2. Attivare i bit con -ing (simbolo di &#124; bit per bit) la variabile temporanea con le maschera di bit corrispondenti (rappresentate nel codice dell'applicazione da costanti `OR` manifesto).

3. Disattivare gli altri bit da -ing (simbolo di & bit) la variabile con `AND` `NOT` un (simbolo ~ bit per bit) delle maschera di bit appropriate.

4. Chiamare `_CrtSetDbgFlag` con il parametro `newFlag` impostato sul valore archiviato nella variabile temporanea per creare il nuovo stato di `_crtDbgFlag`.

   Le righe di codice riportate di seguito, ad esempio, attivano il rilevamento automatico delle perdite di memoria e disattivano il controllo dei blocchi di tipo `_CRT_BLOCK`:

```cpp
// Get current flag
int tmpFlag = _CrtSetDbgFlag( _CRTDBG_REPORT_FLAG );

// Turn on leak-checking bit.
tmpFlag |= _CRTDBG_LEAK_CHECK_DF;

// Turn off CRT block checking bit.
tmpFlag &= ~_CRTDBG_CHECK_CRT_DF;

// Set flag to the new value.
_CrtSetDbgFlag( tmpFlag );
```

![Torna all'inizio](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [Contenuto](#BKMK_Contents)

## <a name="new-delete-and-_client_blocks-in-the-c-debug-heap"></a><a name="BKMK_new__delete__and__CLIENT_BLOCKs_in_the_C___debug_heap"></a> BLOCCHI NUOVI, DELETE e \_ CLIENT \_ nell'heap di debug C++
Le versioni di debug della libreria di runtime C contengono le versioni di debug degli operatori C++ `new` e `delete`. Se si utilizza il tipo di allocazione `_CLIENT_BLOCK`, è necessario chiamare la versione di debug dell'operatore `new` in modo diretto oppure creare macro che sostituiscano l'operatore `new` nella modalità di debug, come illustrato nell'esempio che segue:

```cpp
/* MyDbgNew.h
 Defines global operator new to allocate from
 client blocks
*/

#ifdef _DEBUG
   #define DEBUG_CLIENTBLOCK   new( _CLIENT_BLOCK, __FILE__, __LINE__)
#else
   #define DEBUG_CLIENTBLOCK
#endif // _DEBUG

/* MyApp.cpp
        Use a default workspace for a Console Application to
 *      build a Debug version of this code
*/

#include "crtdbg.h"
#include "mydbgnew.h"

#ifdef _DEBUG
#define new DEBUG_CLIENTBLOCK
#endif

int main( )   {
    char *p1;
    p1 =  new char[40];
    _CrtMemDumpAllObjectsSince( NULL );
}
```

La versione di debug dell'operatore `delete` può essere utilizzata con tutti i tipi di blocco e non è necessario apportare alcuna modifica al programma quando si compila una versione di rilascio.

![Torna all'inizio](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [Contenuto](#BKMK_Contents)

## <a name="heap-state-reporting-functions"></a><a name="BKMK_Heap_State_Reporting_Functions"></a> Funzioni per la creazione di report sullo stato dell'heap
 **_CrtMemState**

 Per generare uno snapshot di riepilogo dello stato dell'heap in un dato momento, utilizzare la struttura _CrtMemState definita in CRTDBG.H:

```cpp
typedef struct _CrtMemState
{
    // Pointer to the most recently allocated block:
    struct _CrtMemBlockHeader * pBlockHeader;
    // A counter for each of the 5 types of block:
    size_t lCounts[_MAX_BLOCKS];
    // Total bytes allocated in each block type:
    size_t lSizes[_MAX_BLOCKS];
    // The most bytes allocated at a time up to now:
    size_t lHighWaterCount;
    // The total bytes allocated at present:
    size_t lTotalCount;
} _CrtMemState;
```

Questa struttura salva un puntatore al primo blocco (quello allocato più di recente) dell'elenco collegato dell'heap di debug. Quindi, registrare in due matrici il numero di blocchi di memoria presenti nell'elenco per ciascun tipo (_NORMAL_BLOCK`_CLIENT_BLOCK`, _FREE_BLOCK e così via), nonché il numero dei byte allocati in ciascun tipo di blocco. Riporta infine il massimo numero di byte allocato come singola entità nello heap fino a tal punto.

**Altre funzioni CRT per la creazione di report**

Le funzioni elencate di seguito indicano lo stato e il contenuto dell'heap e utilizzano tali informazioni per il rilevamento di perdite di memoria e altri problemi.

|Funzione|Descrizione|
|--------------|-----------------|
|[_CrtMemCheckpoint](/cpp/c-runtime-library/reference/crtmemcheckpoint)|Salva uno snapshot dell'heap in una struttura **_CrtMemState** fornita dall'applicazione.|
|[_CrtMemDifference](/cpp/c-runtime-library/reference/crtmemdifference)|Confronta due strutture dello stato della memoria, salva le differenze tra di esse in una terza struttura di stato e restituisce TRUE se i due stati sono differenti.|
|[_CrtMemDumpStatistics](/cpp/c-runtime-library/reference/crtmemdumpstatistics)|Esegue il dump di una data struttura **_CrtMemState**. La struttura può contenere uno snapshot dello stato dell'heap di debug in un dato momento o le differenze tra i due snapshot.|
|[_CrtMemDumpAllObjectsSince](/cpp/c-runtime-library/reference/crtmemdumpallobjectssince)|Esegue il dump di informazioni su tutti gli oggetti allocati dopo la generazione di un dato snapshot dell'heap o dall'inizio dell'esecuzione. Ogni volta che esegue il dump di un blocco **_CLIENT_BLOCK**, chiama una funzione hook fornita dall'applicazione, qualora ne sia stata installata una mediante **_CrtSetDumpClient**.|
|[_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks)|Determina se si sono verificate perdite di memoria dall'inizio dell'esecuzione del programma e, in caso positivo, esegue il dump di tutti gli oggetti allocati. Ogni volta che **_CrtDumpMemoryLeaks** esegue il dump di un blocco **_CLIENT_BLOCK**, chiama una funzione hook fornita dall'applicazione, qualora ne sia stata installata una mediante **_CrtSetDumpClient**.|

![Torna all'inizio](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [Contenuto](#BKMK_Contents)

## <a name="track-heap-allocation-requests"></a><a name="BKMK_Track_Heap_Allocation_Requests"></a> Rilevare le richieste di allocazione dell'heap
Sebbene conoscere il nome del file sorgente e il numero di riga in cui viene eseguita un'asserzione o una macro per la creazione di report sia spesso molto utile per individuare la causa di un problema, non è sempre così per le funzioni di allocazione heap. Sebbene le macro possano essere inserite in numerosi punti appropriati nell'albero logico di un'applicazione, un'allocazione è spesso inclusa in una speciale routine che viene richiamata in momenti diversi da più posizioni differenti. La difficoltà non risiede in genere nel sapere quale riga di codice ha eseguito un'allocazione errata, ma piuttosto nel capire quale delle migliaia di allocazioni eseguite da tale riga di codice è responsabile del problema e perché.

**Numeri univoci di richiesta di allocazione e _crtBreakAlloc**

Il metodo più semplice per identificare la specifica chiamata di allocazione heap che ha avuto esito negativo consiste nell'utilizzare il numero univoco di richiesta di allocazione associato a ciascun blocco dell'heap di debug. Quando le informazioni relative a un blocco vengono restituite da una delle funzioni dump, questo numero di richiesta di allocazione è racchiuso tra parentesi, ad esempio "{36}".

Quando si conosce il numero di richiesta di allocazione di un blocco allocato in modo errato, è possibile passare questo numero a [_CrtSetBreakAlloc](/cpp/c-runtime-library/reference/crtsetbreakalloc) per creare un punto di interruzione. L'esecuzione si interromperà appena prima dell'allocazione del blocco e sarà possibile risalire i passi del codice in senso contrario all'esecuzione per determinare la routine responsabile della chiamata errata. Per evitare di dover ripetere la compilazione, è possibile eseguire la stessa operazione nel debugger impostando **_crtBreakAlloc** sul numero di richiesta di allocazione in questione.

**Creazione di versioni di debug delle routine di allocazione**

Una tecnica un po' più complicata consiste nel creare versioni di debug delle routine di allocazione, paragonabili alle versioni **_dbg** delle [funzioni di allocazione heap](../debugger/debug-versions-of-heap-allocation-functions.md). Sarà quindi possibile passare gli argomenti relativi a file sorgente e numero di riga attraverso le routine di allocazione heap sottostanti per sapere immediatamente dove ha avuto origine un'allocazione errata.

Si supponga ad esempio che l'applicazione contenga una routine di utilizzo comune simile alla seguente:

```cpp
int addNewRecord(struct RecStruct * prevRecord,
                 int recType, int recAccess)
{
    // ...code omitted through actual allocation...
    if ((newRec = malloc(recSize)) == NULL)
    // ... rest of routine omitted too ...
}
```

In un file di intestazione sarebbe possibile aggiungere codice del seguente tipo:

```cpp
#ifdef _DEBUG
#define  addNewRecord(p, t, a) \
            addNewRecord(p, t, a, __FILE__, __LINE__)
#endif
```

Si provvederebbe quindi a modificare l'allocazione nella routine di creazione record come segue:

```cpp
int addNewRecord(struct RecStruct *prevRecord,
                int recType, int recAccess
#ifdef _DEBUG
               , const char *srcFile, int srcLine
#endif
    )
{
    /* ... code omitted through actual allocation ... */
    if ((newRec = _malloc_dbg(recSize, _NORMAL_BLOCK,
            srcFile, scrLine)) == NULL)
    /* ... rest of routine omitted too ... */
}
```

Il nome del file di origine e il numero di riga in cui è stata effettuata la chiamata a `addNewRecord` verranno memorizzati in ciascun blocco allocato nell'heap di debug e verranno indicati quando il blocco verrà esaminato.

![Torna all'inizio](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [Contenuto](#BKMK_Contents)

## <a name="see-also"></a>Vedi anche
[Debug del codice nativo](../debugger/debugging-native-code.md)
