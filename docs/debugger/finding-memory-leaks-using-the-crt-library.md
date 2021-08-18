---
title: Trovare perdite di memoria con la libreria CRT | Microsoft Docs
description: Informazioni su come il debugger C/C++ e la libreria di runtime C (CRT) possono aiutare a individuare perdite di memoria. Le tecniche includono i report sulle perdite di memoria e il confronto degli snapshot di memoria.
ms.custom: SEO-VS-2020
ms.date: 10/04/2018
ms.topic: how-to
dev_langs:
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 6f248d29640f6d8e3cb629d083f6589ec1e173f3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122030893"
---
# <a name="find-memory-leaks-with-the-crt-library"></a>Individuare le perdite di memoria con la libreria CRT

Le perdite di memoria sono tra i bug più sottili e difficili da rilevare nelle app C/C++. Le perdite di memoria sono causate dall'errore di deallocare correttamente la memoria allocata in precedenza. Una piccola perdita di memoria potrebbe non essere notata all'inizio, ma nel corso del tempo può causare sintomi che vanno da prestazioni scarse a arresto anomalo quando l'app esaurirà la memoria. Un'app in perdita che usa tutta la memoria disponibile può causare l'arresto anomalo di altre app, creando confusione su quale app è responsabile. Anche perdite di memoria innocue potrebbero indicare altri problemi che devono essere corretti.

Il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] debugger e la libreria di runtime C (CRT) consentono di rilevare e identificare le perdite di memoria.

## <a name="enable-memory-leak-detection"></a>Abilitare il rilevamento delle perdite di memoria

Gli strumenti principali per rilevare le perdite di memoria sono il debugger C/C++ e le funzioni heap di debug della libreria di runtime C (CRT).

Per abilitare tutte le funzioni heap di debug, includere le istruzioni seguenti nel programma C++, nell'ordine seguente:

```cpp
#define _CRTDBG_MAP_ALLOC
#include <stdlib.h>
#include <crtdbg.h>
```

L'istruzione `#define` esegue il mapping di una versione di base delle funzioni di heap CRT alla corrispondente versione di debug. Se si osempre `#define` l'istruzione , il dump della perdita di memoria sarà [meno dettagliato.](#interpret-the-memory-leak-report)

L'inclusione *di crtdbg.h* esegue il mapping delle funzioni e alle relative versioni di debug, _malloc_dbg e _free_dbg , che tiene traccia dell'allocazione e della `malloc` `free` deallocazione della memoria. [](/cpp/c-runtime-library/reference/malloc-dbg) [](/cpp/c-runtime-library/reference/free-dbg) Questa operazione di mapping viene eseguita solo nelle build di debug che presentano `_DEBUG`. Le build di rilascio usano le normali funzioni `malloc` e `free` .

Dopo aver abilitato le funzioni dell'heap di debug usando le istruzioni precedenti, effettuare una chiamata a [_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks) prima di un punto di uscita dell'app per visualizzare un report di perdita di memoria alla chiusura dell'app.

```cpp
_CrtDumpMemoryLeaks();
```

Se l'app ha diverse exit, non è necessario posizionarsi manualmente `_CrtDumpMemoryLeaks` in ogni punto di uscita. Per generare una chiamata automatica a in ogni punto di uscita, eseguire una chiamata a all'inizio dell'app con i campi `_CrtDumpMemoryLeaks` di bit illustrati di `_CrtSetDbgFlag` seguito:

```cpp
_CrtSetDbgFlag ( _CRTDBG_ALLOC_MEM_DF | _CRTDBG_LEAK_CHECK_DF );
```

Per impostazione predefinita, `_CrtDumpMemoryLeaks` genera il report delle perdite di memoria nel riquadro **Debug** della finestra **Output** . Se si usa una libreria, è possibile che l'output venga indirizzato in un'altra posizione.

È possibile usare per reindirizzare il report a un'altra posizione `_CrtSetReportMode` o tornare alla finestra **Output,** come illustrato di seguito:

```cpp
_CrtSetReportMode( _CRT_WARN, _CRTDBG_MODE_DEBUG );
```

## <a name="interpret-the-memory-leak-report"></a>Interpretare il report di perdita di memoria

Se l'app non definisce , _CrtDumpMemoryLeaks un report di perdita `_CRTDBG_MAP_ALLOC` di memoria simile al seguente: [](/cpp/c-runtime-library/reference/crtdumpmemoryleaks)

```cmd
Detected memory leaks!
Dumping objects ->
{18} normal block at 0x00780E80, 64 bytes long.
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD
Object dump complete.
```

Se l'app definisce `_CRTDBG_MAP_ALLOC` , il report di perdita di memoria è simile al seguente:

```cmd
Detected memory leaks!
Dumping objects ->
c:\users\username\documents\projects\leaktest\leaktest.cpp(20) : {18}
normal block at 0x00780E80, 64 bytes long.
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD
Object dump complete.
```

Il secondo report mostra il nome file e il numero di riga in cui viene allocata per la prima volta la memoria persa.

Se si definisce o meno `_CRTDBG_MAP_ALLOC` , viene visualizzato il report di perdita di memoria:

- Numero di allocazione di memoria, `18` nell'esempio
- Tipo di blocco, `normal` nell'esempio.
- Posizione della memoria esadecimale, `0x00780E80` nell'esempio.
- Dimensioni del blocco, `64 bytes` nell'esempio.
- I primi 16 byte di dati nel blocco, in formato esadecimale.

I tipi di blocchi di memoria *sono normali,* *client* o *CRT.* Un *blocco normale* è dato da memoria ordinaria allocata dal programma. Un *blocco client* è un tipo speciale di blocco di memoria usato dai programmi MFC per oggetti che richiedono un distruttore. L'operazione MFC `new` crea un blocco normale o un blocco client, a seconda dell'oggetto creato.

Un *blocco CRT* è allocato dalla libreria CRT per il proprio uso. La libreria CRT gestisce la deallocazione per questi blocchi, quindi i blocchi CRT non verranno visualizzati nel report di perdita di memoria a meno che non si siano verificati seri problemi con la libreria CRT.

Esistono altri due tipi di blocchi di memoria che non compaiono mai nei report delle perdite di memoria. Un *blocco libero* è la memoria rilasciata, quindi per definizione non viene persa. Un *blocco ignore* è la memoria contrassegnata in modo esplicito per l'esclusione dal report di perdita di memoria.

Le tecniche precedenti identificano le perdite di memoria per la memoria allocata usando la funzione CRT `malloc` standard. Se il programma alloca memoria usando l'operatore C++, tuttavia, è possibile visualizzare solo il nome file e il numero di riga in cui vengono chiamate nel report di perdita `new` `operator new` di `_malloc_dbg` memoria. Per creare un report di perdita di memoria più utile, è possibile scrivere una macro simile alla seguente per segnalare la riga che ha effettuato l'allocazione:

```cpp
#ifdef _DEBUG
    #define DBG_NEW new ( _NORMAL_BLOCK , __FILE__ , __LINE__ )
    // Replace _NORMAL_BLOCK with _CLIENT_BLOCK if you want the
    // allocations to be of _CLIENT_BLOCK type
#else
    #define DBG_NEW new
#endif
```

È ora possibile sostituire `new` l'operatore usando la `DBG_NEW` macro nel codice. Nelle build di debug usa un overload di `DBG_NEW` globale che accetta parametri aggiuntivi per il tipo di `operator new` blocco, il file e il numero di riga. Overload di chiamate `new` `_malloc_dbg` per registrare le informazioni aggiuntive. I report sulle perdite di memoria mostrano il nome file e il numero di riga in cui sono stati allocati gli oggetti persi. Le build di versione usano comunque il valore predefinito `new` . Ecco un esempio della tecnica:

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

Quando si esegue questo codice nel debugger Visual Studio, la chiamata a genera un report nella finestra `_CrtDumpMemoryLeaks` **Output** simile al seguente:

```Output
Detected memory leaks!
Dumping objects ->
c:\users\username\documents\projects\debug_new\debug_new.cpp(20) : {75}
 normal block at 0x0098B8C8, 4 bytes long.
 Data: <    > CD CD CD CD
Object dump complete.
```

Questo output segnala che l'allocazione persa era alla riga 20 *di debug_new.cpp*.

>[!NOTE]
>Non è consigliabile creare una macro del preprocessore denominata `new` o qualsiasi altra parola chiave del linguaggio.

## <a name="set-breakpoints-on-a-memory-allocation-number"></a>Impostare punti di interruzione su un numero di allocazione di memoria

Il numero di allocazione della memoria indica quando è stato allocato un blocco di memoria di cui è stata registrata la perdita. Un blocco con un numero di allocazione di memoria di 18, ad esempio, è il 18° blocco di memoria allocato durante l'esecuzione dell'app. Il report CRT conta tutte le allocazioni di blocchi di memoria durante l'esecuzione, incluse le allocazioni dalla libreria CRT e da altre librerie, ad esempio MFC. Di conseguenza, il blocco di allocazione di memoria numero 18 probabilmente non è il 18° blocco di memoria allocato dal codice.

È possibile usare il numero di allocazione per impostare un punto di interruzione sull'allocazione di memoria.

**Per impostare un punto di interruzione di allocazione di memoria usando il finestra Espressioni di controllo:**

1. Impostare un punto di interruzione vicino all'inizio dell'app e avviare il debug.

1. Quando l'app viene sospesa  in corrispondenza del punto di interruzione, aprire una finestra Espressioni di controllo selezionando Debug   >  **Windows**  >  **Watch 1** (o Watch **2,** **Watch 3** o Watch **4).**

1. Nella finestra **Espressioni di** controllo digitare `_crtBreakAlloc` nella **colonna** Nome .

   Se si usa la versione dll multithreading della libreria CRT (opzione /MD), aggiungere l'operatore context: `{,,ucrtbased.dll}_crtBreakAlloc`
   
   Assicurarsi che i simboli di debug siano caricati. In `_crtBreakAlloc` caso contrario, verrà segnalato *come non identificato.*

1. Premere **INVIO**.

   Il debugger valuterà la chiamata e ne visualizzerà il risultato nella colonna **Valore** . Questo valore sarà **-1** se non sono stati impostati punti di interruzione sulle allocazioni di memoria.

1. Nella colonna **Valore** sostituire il valore con il numero di allocazione della memoria in cui si vuole interrompere il debugger.

Dopo aver impostato un punto di interruzione su un numero di allocazione di memoria, continuare con il debug. Assicurarsi di eseguire nelle stesse condizioni, in modo che il numero di allocazione di memoria non cambi. Quando il programma si interrompe in corrispondenza dell'allocazione di memoria specificata, usare la finestra **Stack** di chiamate e altre finestre del debugger per determinare le condizioni in cui è stata allocata la memoria. È quindi possibile continuare l'esecuzione per osservare cosa accade all'oggetto e determinare il motivo per cui non è deallocato correttamente.

Anche l'impostazione di un punto di interruzione dei dati sull'oggetto può essere utile. Per altre informazioni, vedere [Uso dei punti di interruzione.](../debugger/using-breakpoints.md)

È anche possibile impostare i punti di interruzione dell'allocazione di memoria nel codice. Tra cui:

```cpp
_crtBreakAlloc = 18;
```

 oppure:

```cpp
_CrtSetBreakAlloc(18);
```

## <a name="compare-memory-states"></a>Confrontare gli stati di memoria

Un'altra tecnica per l'individuazione delle perdite di memoria comporta l'esecuzione di snapshot dello stato della memoria dell'applicazione in corrispondenza di punti chiave. Per creare uno snapshot dello stato della memoria in un determinato punto dell'applicazione, creare una `_CrtMemState` struttura e passarla alla `_CrtMemCheckpoint` funzione .

```cpp
_CrtMemState s1;
_CrtMemCheckpoint( &s1 );
```

La `_CrtMemCheckpoint` funzione riempie la struttura con uno snapshot dello stato di memoria corrente.

Per eseguire l'output del `_CrtMemState` contenuto di una struttura , passare la struttura alla funzione `_ CrtMemDumpStatistics` :

```cpp
_CrtMemDumpStatistics( &s1 );
```

`_ CrtMemDumpStatistics` restituisce un dump dello stato della memoria simile al seguente:

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

`_CrtMemDifference` confronta gli stati di memoria `s1` e restituisce un risultato in ( ) che rappresenta la differenza tra e `s2` `s3` `s1` `s2` .

Una tecnica per trovare perdite di memoria inizia inserendo chiamate all'inizio e alla fine dell'app e quindi `_CrtMemCheckpoint` usando per confrontare i `_CrtMemDifference` risultati. Se viene visualizzata una perdita di memoria, è possibile aggiungere altre chiamate per dividere il programma usando una ricerca binaria, fino a quando non si isola `_CrtMemDifference` `_CrtMemCheckpoint` l'origine della perdita.

## <a name="false-positives"></a>Falsi positivi

 `_CrtDumpMemoryLeaks` può fornire false indicazioni di perdite di memoria se una libreria contrassegna le allocazioni interne come blocchi normali anziché blocchi CRT o blocchi client. In questo caso, `_CrtDumpMemoryLeaks` non è in grado di indicare la differenza tra allocazioni utente e allocazioni interne della libreria. Se i distruttori globali relativi alle allocazioni della libreria vengono eseguiti dopo il punto in cui viene chiamato `_CrtDumpMemoryLeaks`, ogni allocazione interna della libreria viene segnalata come perdita di memoria. Le versioni della libreria di modelli standard precedenti Visual Studio .NET possono causare `_CrtDumpMemoryLeaks` la segnalazione di tali falsi positivi.

## <a name="see-also"></a>Vedi anche

- [Informazioni dettagliate sull'heap di debug CRT](../debugger/crt-debug-heap-details.md)
- [Sicurezza del debugger](../debugger/debugger-security.md)
- [Debug di codice nativo](../debugger/debugging-native-code.md)
