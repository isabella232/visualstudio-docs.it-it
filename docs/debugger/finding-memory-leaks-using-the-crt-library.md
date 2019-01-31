---
title: Individuare le perdite di memoria con la libreria CRT | Microsoft Docs
ms.date: 10/04/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- breakpoints, on memory allocation
- _CrtMemState
- _CrtMemCheckpoint
- memory leaks
- _CrtMemDifference
- memory leaks, detecting and isolating
- _CrtDumpMemoryLeaks
- _CrtSetBreakAlloc
- _crtBreakAlloc
- _CrtSetReportMode
- memory, debugging
- _CrtMemDumpStatistics
- debugging memory leaks
- _CRTDBG_MAP_ALLOC
- _CrtSetDbgFlag
ms.assetid: cf6dc7a6-cd12-4283-b1b6-ea53915f7ed1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e3045f9e420ad8d70b9f02172c18f46e4e412c37
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54946311"
---
# <a name="find-memory-leaks-with-the-crt-library"></a>Individuare le perdite di memoria con la libreria CRT

Perdite di memoria sono tra i bug più gravi e difficili da rilevare nelle applicazioni C/C++. Risultato in caso di errore di deallocare correttamente la memoria allocata in precedenza le perdite di memoria. Una piccola perdita di memoria potrebbe non essere notata inizialmente, ma nel tempo può causare problemi come compreso tra una riduzione delle prestazioni e agli arresti anomali durante l'esecuzione dell'app memoria insufficiente. Un'app di individuazione che utilizzi tutta la memoria disponibile possono causare altre App in modo anomalo, creando confusione sul quale app è responsabile. Anche le perdite di memoria potrebbero indicare altri problemi che devono essere corretti.  

 Il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] debugger e libreria Run-time C (CRT) consente di rilevare e identificare le perdite di memoria.  

## <a name="enable-memory-leak-detection"></a>Abilitare il rilevamento di perdite di memoria  

I principali strumenti per il rilevamento di perdite di memoria sono il debugger di C/C++ e la libreria Run-time C (CRT) funzioni heap di debug.  

Per abilitare tutte le funzioni di heap di debug, includere le istruzioni seguenti nel programma C++, nell'ordine seguente:  

```cpp
#define _CRTDBG_MAP_ALLOC  
#include <stdlib.h>  
#include <crtdbg.h>  
```  

L'istruzione `#define` esegue il mapping di una versione di base delle funzioni di heap CRT alla corrispondente versione di debug. Se si omette il `#define` istruzione, il dump delle perdite di memoria saranno [meno dettagliati](#interpret-the-memory-leak-report).  

Tra cui *CRTDBG. h* esegue il mapping di `malloc` e `free` funzioni alle corrispondenti versioni di debug, [malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg) e [free_dbg](/cpp/c-runtime-library/reference/free-dbg), quali tenere traccia della memoria allocazione e deallocazione. Questa operazione di mapping viene eseguita solo nelle build di debug che presentano `_DEBUG`. Le build di rilascio usano le normali funzioni `malloc` e `free` .  

Dopo aver abilitato le funzioni heap di debug usando le istruzioni precedenti, inserire una chiamata a [CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks) prima di un punto di uscita di app per visualizzare un report delle perdite di memoria quando l'app viene chiusa.  

```cpp
_CrtDumpMemoryLeaks();  
```  

Se l'app presenta più uscite, non è necessario inserire manualmente `_CrtDumpMemoryLeaks` a ogni punto di uscita. A causa di una chiamata automatica a `_CrtDumpMemoryLeaks` a ogni punto di uscita, inserire una chiamata a `_CrtSetDbgFlag` all'inizio della tua app con i campi di bit illustrato di seguito:

```cpp
_CrtSetDbgFlag ( _CRTDBG_ALLOC_MEM_DF | _CRTDBG_LEAK_CHECK_DF );  
```  

Per impostazione predefinita, `_CrtDumpMemoryLeaks` genera il report delle perdite di memoria nel riquadro **Debug** della finestra **Output** . Se si usa una libreria, è possibile che l'output venga indirizzato in un'altra posizione. 

È possibile usare `_CrtSetReportMode` per reindirizzare il report in un altro percorso o eseguire il backup per il **Output** finestra come illustrato di seguito:  

```cpp
_CrtSetReportMode( _CRT_ERROR, _CRTDBG_MODE_DEBUG );  
```  

## <a name="interpret-the-memory-leak-report"></a>Interpretazione del report delle perdite di memoria  

Se l'app non definisce `_CRTDBG_MAP_ALLOC`, [CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks) consente di visualizzare un report delle perdite di memoria è simile a:  

```cmd
Detected memory leaks!  
Dumping objects ->  
{18} normal block at 0x00780E80, 64 bytes long.  
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD  
Object dump complete.  
```  

Se l'app definisce `_CRTDBG_MAP_ALLOC`, il report delle perdite di memoria è simile a:  

```cmd
Detected memory leaks!  
Dumping objects ->  
c:\users\username\documents\projects\leaktest\leaktest.cpp(20) : {18}   
normal block at 0x00780E80, 64 bytes long.  
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD  
Object dump complete.  
```  

Il secondo report mostra il numero di riga e nome file in cui la memoria persa era stata allocata.  

Se definiscono `_CRTDBG_MAP_ALLOC`, consente di visualizzare il report delle perdite di memoria:  

- Il numero di allocazione della memoria, ovvero `18` nell'esempio  
- Il tipo di blocco, `normal` nell'esempio.  
- Posizione esadecimale della memoria, `0x00780E80` nell'esempio.  
- Le dimensioni del blocco, `64 bytes` nell'esempio.  
- I primi 16 byte di dati nel blocco, in formato esadecimale.  

Tipi di blocchi di memoria vengono *normali*, *client*, o *CRT*. Un *blocco normale* è dato da memoria ordinaria allocata dal programma. Un *blocco client* è un tipo speciale di blocco di memoria usato dai programmi MFC per oggetti che richiedono un distruttore. L'operazione MFC `new` crea un blocco normale o un blocco client, a seconda dell'oggetto creato. 

Un *blocco CRT* è allocato dalla libreria CRT per il proprio uso. La libreria CRT gestisce la deallocazione di questi blocchi, blocchi CRT non sarà più visualizzato nel report delle perdite di memoria, a meno che non sono presenti gravi problemi con la libreria CRT.  

Esistono altri due tipi di blocchi di memoria che non compaiono mai nei report delle perdite di memoria. Oggetto *blocco libero* indica la memoria che è stata rilasciata, pertanto per definizione, non viene persa. Un' *blocco da ignorare* indica la memoria che è stata esplicitamente contrassegnata per essere esclusa dal report delle perdite di memoria.  

Tecniche precedenti identificano le perdite di memoria per la memoria allocata tramite la libreria CRT standard `malloc` (funzione). Se la memoria usando C++ viene allocata `new` operatore, tuttavia, ne verrà visualizzato solo il numero di riga e nome file in cui `operator new` chiamate `_malloc_dbg` nel report delle perdite di memoria. Per creare un report delle perdite di memoria più utile, è possibile scrivere una macro simile al seguente per segnalare la riga che ha effettuato l'allocazione: 

```cpp  
#ifdef _DEBUG
    #define DBG_NEW new ( _NORMAL_BLOCK , __FILE__ , __LINE__ )
    // Replace _NORMAL_BLOCK with _CLIENT_BLOCK if you want the
    // allocations to be of _CLIENT_BLOCK type
#else
    #define DBG_NEW new
#endif
```  

A questo punto è possibile sostituire il `new` operatore usando la `DBG_NEW` macro nel codice. Nelle build di debug `DBG_NEW` Usa un overload dell'oggetto globale `operator new` che accetta parametri aggiuntivi per il tipo di blocco, file e numero di riga. Eseguire l'overload del `new` chiamate `_malloc_dbg` per registrare le informazioni aggiuntive. I report delle perdite di memoria mostrano il numero di riga e nome file in cui sono stati allocati gli oggetti persi. Build di rilascio si avvale ancora il valore predefinito `new`. Di seguito è riportato un esempio della tecnica:  

```cpp  
// debug_new.cpp
// compile by using: cl /EHsc /W4 /D_DEBUG /MDd debug_new.cpp
#define _CRTDBG_MAP_ALLOC
#include <cstdlib>
#include <crtdbg.h>

#ifdef _DEBUG
    #define DBG_NEW new ( _NORMAL_BLOCK , __FILE__ , __LINE__ )
    // Replace _NORMAL_BLOCK with _CLIENT_BLOCK if you want the
    // allocations to be of _CLIENT_BLOCK type
#else
    #define DBG_NEW new
#endif

struct Pod {
    int x;
};

void main() {
    Pod* pPod = DBG_NEW Pod;
    pPod = DBG_NEW Pod; // Oops, leaked the original pPod!
    delete pPod;

    _CrtDumpMemoryLeaks();
}
```  

Quando si esegue questo codice in Visual Studio del debugger, la chiamata a `_CrtDumpMemoryLeaks` genera un report nel **Output** finestra simile a:  

```Output  
Detected memory leaks!
Dumping objects ->
c:\users\username\documents\projects\debug_new\debug_new.cpp(20) : {75}
 normal block at 0x0098B8C8, 4 bytes long.
 Data: <    > CD CD CD CD 
Object dump complete.
```  

Questo output di report che è stato l'allocazione persa nella riga 20 dello *debug_new.cpp*.  

>[!NOTE]
>Non si consiglia di creare una macro del preprocessore denominata `new`, o qualsiasi altra lingua (parola chiave). 

## <a name="set-breakpoints-on-a-memory-allocation-number"></a>Impostare punti di interruzione su un numero di allocazione di memoria  

Il numero di allocazione della memoria indica quando è stato allocato un blocco di memoria di cui è stata registrata la perdita. Un blocco con un numero di allocazione della memoria pari a 18, ad esempio, è il 18 blocco di memoria allocato durante l'esecuzione dell'app. Il report CRT TIENE conto tutte le allocazioni di blocchi di memoria durante l'esecuzione, incluse le allocazioni della libreria CRT e altre librerie come MFC. Pertanto, 18 numero di blocchi di allocazione di memoria probabilmente non è disponibile il 18 blocco di memoria allocato dal codice. 

È possibile usare il numero di allocazione per impostare un punto di interruzione sull'allocazione di memoria.  

**Per impostare un punto di interruzione dell'allocazione di memoria usando la finestra Espressioni di controllo:**  

1. Impostare un punto di interruzione in prossimità dell'inizio dell'app e avviare il debug.  
   
1. Quando l'app viene sospesa nel punto di interruzione, aprire una **Watch** finestra selezionando **Debug** > **Windows** > **Watch1** (o **guardare 2**, **guarda 3**, o **guarda 4**).  
   
1. Nel **Watch** finestra, digitare `_crtBreakAlloc` nel **nome** colonna.  
   
   Se si usa la versione DLL multithread della libreria CRT (opzione /MD), aggiungere l'operatore di contesto: `{,,ucrtbased.dll}_crtBreakAlloc`  
   
1. Premere **INVIO**.  
   
   Il debugger valuterà la chiamata e ne visualizzerà il risultato nella colonna **Valore** . Questo valore sarà **-1** se non è stato impostato alcun punto di interruzione su allocazioni di memoria.  
   
1. Nel **valore** colonne, sostituire il valore con il numero di allocazione della memoria in cui si desidera che l'interruzione del debugger.  

Dopo aver impostato un punto di interruzione su un numero di allocazione della memoria, continuare a eseguire il debug. Assicurarsi che venga eseguito con le stesse condizioni, in modo da non modifica il numero di allocazione della memoria. Quando il programma si interrompe all'allocazione di memoria specificata, usare il **Stack di chiamate** finestra e altre finestre del debugger per determinare le condizioni in cui è stata allocata la memoria. Quindi, è possibile continuare l'esecuzione per osservare ciò che accade all'oggetto e determinare il motivo per cui è in modo corretto non viene deallocata.  

Anche l'impostazione di un punto di interruzione dei dati sull'oggetto può essere utile. Per altre informazioni, vedere [Uso di punti di interruzione](../debugger/using-breakpoints.md).  

È anche possibile impostare i punti di interruzione dell'allocazione di memoria nel codice. Tra cui:  

```cpp
_crtBreakAlloc = 18;  
```  

 oppure:  

```cpp
_CrtSetBreakAlloc(18);  
```  

## <a name="compare-memory-states"></a>Confrontare gli stati della memoria  
 Un'altra tecnica per l'individuazione delle perdite di memoria comporta l'esecuzione di snapshot dello stato della memoria dell'applicazione in corrispondenza di punti chiave. Per eseguire uno snapshot dello stato della memoria in un determinato punto dell'applicazione, creare un `_CrtMemState` strutturare e passarlo al `_CrtMemCheckpoint` (funzione). 

```cpp
_CrtMemState s1;  
_CrtMemCheckpoint( &s1 );  
```  

Il `_CrtMemCheckpoint` funzione inserisce nella struttura uno snapshot dello stato corrente della memoria.  

Per generare il contenuto di un `_CrtMemState` strutturare, passare la struttura per il `_ CrtMemDumpStatistics` funzione:  

```cpp
_CrtMemDumpStatistics( &s1 );  
```  

`_ CrtMemDumpStatistics` Genera un dump dello stato di memoria è simile a:  

```cmd
0 bytes in 0 Free Blocks.  
0 bytes in 0 Normal Blocks.  
3071 bytes in 16 CRT Blocks.  
0 bytes in 0 Ignore Blocks.  
0 bytes in 0 Client Blocks.  
Largest number used: 3071 bytes.  
Total allocations: 3764 bytes.  
```  

Per verificare se si è verificata una perdita di memoria in una sezione di codice, è possibile eseguire snapshot dello stato della memoria prima e dopo la sezione, quindi usare `_ CrtMemDifference` per confrontare i due stati:  

```cpp
_CrtMemCheckpoint( &s1 );  
// memory allocations take place here  
_CrtMemCheckpoint( &s2 );  

if ( _CrtMemDifference( &s3, &s1, &s2) )  
   _CrtMemDumpStatistics( &s3 );  
```  

`_CrtMemDifference` Confronta gli stati di memoria `s1` e `s2` e restituisce un risultato in (`s3`) che rappresenta la differenza tra `s1` e `s2`.  

Inizia una tecnica per individuare le perdite di memoria, inserendo `_CrtMemCheckpoint` chiamate all'inizio e alla fine dell'app, quindi utilizzando `_CrtMemDifference` per confrontare i risultati. Se `_CrtMemDifference` Mostra una perdita di memoria, è possibile aggiungerne altri `_CrtMemCheckpoint` chiamate per dividere il programma usando una ricerca binaria, fino a quando non si è stabilito che l'origine della perdita.  

## <a name="false-positives"></a>Falsi positivi  
 `_CrtDumpMemoryLeaks` Se una libreria contrassegna allocazioni interne come blocchi normali anziché blocchi CRT o blocchi client, possibile fornire false indicazioni di perdite di memoria. In questo caso, `_CrtDumpMemoryLeaks` non è in grado di indicare la differenza tra allocazioni utente e allocazioni interne della libreria. Se i distruttori globali relativi alle allocazioni della libreria vengono eseguiti dopo il punto in cui viene chiamato `_CrtDumpMemoryLeaks`, ogni allocazione interna della libreria viene segnalata come perdita di memoria. Le versioni della libreria di modelli Standard precedenti a Visual Studio .NET può causare `_CrtDumpMemoryLeaks` segnalare dei falsi positivi.  

## <a name="see-also"></a>Vedere anche  
 [Informazioni dettagliate sull'heap di debug CRT](../debugger/crt-debug-heap-details.md)   
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Debug del codice nativo](../debugger/debugging-native-code.md)
