---
title: Individuare le perdite di memoria con la libreria CRT | Microsoft Docs
ms.date: 10/04/2018
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4ae879d8ed03653959ae926cc372300db9b71b9f
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2020
ms.locfileid: "84182651"
---
# <a name="find-memory-leaks-with-the-crt-library"></a>Individuare le perdite di memoria con la libreria CRT

Le perdite di memoria sono tra i bug più complessi e difficili da rilevare nelle applicazioni C/C++. Le perdite di memoria derivano dall'errore di deallocare correttamente la memoria allocata in precedenza. Una piccola perdita di memoria potrebbe non essere nota prima, ma nel corso del tempo può causare sintomi che variano da prestazioni ridotte a interruzioni anomale quando l'app esaurisce la memoria. Un'app che si sta perdendo che usa tutta la memoria disponibile può causare l'arresto anomalo di altre app, creando confusione in merito a quale app è responsabile. Anche le perdite di memoria innocue potrebbero indicare altri problemi che devono essere corretti.

Il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] debugger e la libreria di runtime C (CRT) consentono di rilevare e identificare le perdite di memoria.

## <a name="enable-memory-leak-detection"></a>Abilita rilevamento delle perdite di memoria

Gli strumenti principali per rilevare le perdite di memoria sono il debugger C/C++ e le funzioni dell'heap di debug della libreria di runtime C (CRT).

Per abilitare tutte le funzioni dell'heap di debug, includere le istruzioni seguenti nel programma C++, nell'ordine seguente:

```cpp
#define _CRTDBG_MAP_ALLOC
#include <stdlib.h>
#include <crtdbg.h>
```

L'istruzione `#define` esegue il mapping di una versione di base delle funzioni di heap CRT alla corrispondente versione di debug. Se si omette l' `#define` istruzione, il dump della perdita di memoria sarà [meno dettagliato](#interpret-the-memory-leak-report).

Includendo *Crtdbg. h* viene eseguito il mapping delle `malloc` `free` funzioni e alle relative versioni di debug, [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg) e [_free_dbg](/cpp/c-runtime-library/reference/free-dbg), che tengono traccia dell'allocazione e della deallocazione della memoria. Questa operazione di mapping viene eseguita solo nelle build di debug che presentano `_DEBUG`. Le build di rilascio usano le normali funzioni `malloc` e `free` .

Dopo aver abilitato le funzioni dell'heap di debug usando le istruzioni precedenti, inserire una chiamata a [_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks) prima di un punto di uscita dell'app per visualizzare un report delle perdite di memoria quando l'app viene chiusa.

```cpp
_CrtDumpMemoryLeaks();
```

Se l'app ha diverse uscite, non è necessario inserire manualmente `_CrtDumpMemoryLeaks` a ogni punto di uscita. Per eseguire una chiamata automatica a `_CrtDumpMemoryLeaks` a ogni punto di uscita, inserire una chiamata a all' `_CrtSetDbgFlag` inizio dell'applicazione con i campi di bit indicati di seguito:

```cpp
_CrtSetDbgFlag ( _CRTDBG_ALLOC_MEM_DF | _CRTDBG_LEAK_CHECK_DF );
```

Per impostazione predefinita, `_CrtDumpMemoryLeaks` genera il report delle perdite di memoria nel riquadro **Debug** della finestra **Output** . Se si usa una libreria, è possibile che l'output venga indirizzato in un'altra posizione.

È possibile usare `_CrtSetReportMode` per reindirizzare il report in un'altra posizione o tornare alla finestra di **output** , come illustrato di seguito:

```cpp
_CrtSetReportMode( _CRT_WARN, _CRTDBG_MODE_DEBUG );
```

## <a name="interpret-the-memory-leak-report"></a>Interpretare il report sulle perdite di memoria

Se l'app non `_CRTDBG_MAP_ALLOC` viene definita, [_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks) Visualizza un report delle perdite di memoria simile al seguente:

```cmd
Detected memory leaks!
Dumping objects ->
{18} normal block at 0x00780E80, 64 bytes long.
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD
Object dump complete.
```

Se l'app definisce `_CRTDBG_MAP_ALLOC` , il report sulle perdite di memoria ha un aspetto simile al seguente:

```cmd
Detected memory leaks!
Dumping objects ->
c:\users\username\documents\projects\leaktest\leaktest.cpp(20) : {18}
normal block at 0x00780E80, 64 bytes long.
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD
Object dump complete.
```

Il secondo report Mostra il nome file e il numero di riga in cui la memoria persa è stata allocata per la prima volta.

Indipendentemente dal fatto che venga definito `_CRTDBG_MAP_ALLOC` , il report sulle perdite di memoria Visualizza:

- Numero di allocazione della memoria, `18` riportato nell'esempio
- Tipo di blocco, `normal` nell'esempio.
- Posizione di memoria esadecimale, `0x00780E80` nell'esempio.
- Dimensioni del blocco, `64 bytes` nell'esempio.
- I primi 16 byte di dati nel blocco, in formato esadecimale.

I tipi di blocchi di memoria sono *Normal*, *client*o *CRT*. Un *blocco normale* è dato da memoria ordinaria allocata dal programma. Un *blocco client* è un tipo speciale di blocco di memoria usato dai programmi MFC per oggetti che richiedono un distruttore. L'operazione MFC `new` crea un blocco normale o un blocco client, a seconda dell'oggetto creato.

Un *blocco CRT* è allocato dalla libreria CRT per il proprio uso. La libreria CRT gestisce la deallocazione per questi blocchi, quindi i blocchi CRT non vengono visualizzati nel report delle perdite di memoria, a meno che non vi siano gravi problemi con la libreria CRT.

Esistono altri due tipi di blocchi di memoria che non compaiono mai nei report delle perdite di memoria. Un *blocco libero* è una memoria che è stata rilasciata, quindi per definizione non si verificano perdite. Un *blocco ignore* è la memoria contrassegnata in modo esplicito per escludere dal report delle perdite di memoria.

Le tecniche precedenti identificano le perdite di memoria per la memoria allocata tramite la funzione CRT standard `malloc` . Se il programma alloca memoria usando l'operatore C++ `new` , tuttavia, è possibile visualizzare solo il nome file e il numero di riga in cui le `operator new` chiamate `_malloc_dbg` sono presenti nel report delle perdite di memoria. Per creare un report più utile sulle perdite di memoria, è possibile scrivere una macro simile alla seguente per segnalare la riga che ha eseguito l'allocazione:

```cpp
#ifdef _DEBUG
    #define DBG_NEW new ( _NORMAL_BLOCK , __FILE__ , __LINE__ )
    // Replace _NORMAL_BLOCK with _CLIENT_BLOCK if you want the
    // allocations to be of _CLIENT_BLOCK type
#else
    #define DBG_NEW new
#endif
```

A questo punto è possibile sostituire l' `new` operatore usando la `DBG_NEW` macro nel codice. Nelle build di debug `DBG_NEW` Usa un overload di Global `operator new` che accetta parametri aggiuntivi per il tipo di blocco, il file e il numero di riga. Overload delle `new` chiamate `_malloc_dbg` per registrare le informazioni aggiuntive. I report sulle perdite di memoria mostrano il nome file e il numero di riga in cui sono stati allocati gli oggetti persi. Le compilazioni di versione usano ancora il valore predefinito `new` . Ecco un esempio della tecnica:

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

Quando si esegue questo codice nel debugger di Visual Studio, la chiamata a `_CrtDumpMemoryLeaks` genera un report nella finestra di **output** simile alla seguente:

```Output
Detected memory leaks!
Dumping objects ->
c:\users\username\documents\projects\debug_new\debug_new.cpp(20) : {75}
 normal block at 0x0098B8C8, 4 bytes long.
 Data: <    > CD CD CD CD
Object dump complete.
```

Questo output segnala che l'allocazione persa si trovava alla riga 20 di *DEBUG_NEW. cpp*.

>[!NOTE]
>Non è consigliabile creare una macro del preprocessore denominata `new` o qualsiasi altra parola chiave del linguaggio.

## <a name="set-breakpoints-on-a-memory-allocation-number"></a>Imposta punti di interruzione su un numero di allocazione di memoria

Il numero di allocazione della memoria indica quando è stato allocato un blocco di memoria di cui è stata registrata la perdita. Un blocco con un numero di allocazione della memoria pari a 18, ad esempio, è il diciottesimo blocco di memoria allocato durante l'esecuzione dell'app. Il report CRT tiene conto di tutte le allocazioni di blocchi di memoria durante l'esecuzione, incluse le allocazioni della libreria CRT e di altre librerie come MFC. Pertanto, il numero di blocchi di allocazione di memoria 18 probabilmente non è il diciottesimo blocco di memoria allocato dal codice.

È possibile usare il numero di allocazione per impostare un punto di interruzione sull'allocazione di memoria.

**Per impostare un punto di interruzione dell'allocazione della memoria utilizzando la finestra Espressioni di controllo:**

1. Impostare un punto di interruzione in prossimità dell'inizio dell'app e avviare il debug.

1. Quando l'app viene sospesa in corrispondenza del punto di interruzione, aprire una finestra **espressioni di controllo** selezionando **debug**  >  **Windows**  >  **Watch 1** (o espressione di controllo **2**, espressione di controllo **3**o espressione di **controllo 4**).

1. Nella finestra **espressioni di controllo** Digitare `_crtBreakAlloc` nella colonna **nome** .

   Se si usa la versione DLL multithread della libreria CRT (opzione/MD), aggiungere l'operatore di contesto:`{,,ucrtbased.dll}_crtBreakAlloc`
   
   Assicurarsi che i simboli di debug siano caricati. In caso contrario `_crtBreakAlloc` , verrà segnalato come non *identificato*.

1. Premere **INVIO**.

   Il debugger valuterà la chiamata e ne visualizzerà il risultato nella colonna **Valore** . Questo valore sarà **-1** se non sono stati impostati punti di interruzione per le allocazioni di memoria.

1. Nella colonna **valore** sostituire il valore con il numero di allocazione di memoria in cui si desidera che il debugger si interrompa.

Dopo aver impostato un punto di interruzione su un numero di allocazione della memoria, continuare a eseguire il debug. Assicurarsi di eseguire le stesse condizioni, in modo che il numero di allocazione della memoria non venga modificato. Quando il programma si interrompe in corrispondenza dell'allocazione di memoria specificata, utilizzare la finestra **stack di chiamate** e altre finestre del debugger per determinare le condizioni in cui è stata allocata la memoria. Quindi, è possibile continuare l'esecuzione per osservare ciò che accade all'oggetto e determinare perché non è correttamente deallocato.

Anche l'impostazione di un punto di interruzione dei dati sull'oggetto può essere utile. Per ulteriori informazioni, vedere [utilizzo](../debugger/using-breakpoints.md)di punti di interruzione.

È anche possibile impostare i punti di interruzione dell'allocazione di memoria nel codice. Tra cui:

```cpp
_crtBreakAlloc = 18;
```

 oppure:

```cpp
_CrtSetBreakAlloc(18);
```

## <a name="compare-memory-states"></a>Confrontare gli Stati della memoria

Un'altra tecnica per l'individuazione delle perdite di memoria comporta l'esecuzione di snapshot dello stato della memoria dell'applicazione in corrispondenza di punti chiave. Per eseguire uno snapshot dello stato della memoria in un determinato punto dell'applicazione, creare una `_CrtMemState` struttura e passarla alla `_CrtMemCheckpoint` funzione.

```cpp
_CrtMemState s1;
_CrtMemCheckpoint( &s1 );
```

La `_CrtMemCheckpoint` funzione compila la struttura con uno snapshot dello stato corrente della memoria.

Per restituire il contenuto di una `_CrtMemState` struttura, passare la struttura alla `_ CrtMemDumpStatistics` funzione:

```cpp
_CrtMemDumpStatistics( &s1 );
```

`_ CrtMemDumpStatistics`Restituisce un dump dello stato di memoria simile al seguente:

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

`_CrtMemDifference`Confronta gli Stati di memoria `s1` e `s2` e restituisce un risultato in ( `s3` ) che rappresenta la differenza tra `s1` e `s2` .

Una tecnica per individuare le perdite di memoria inizia inserendo le `_CrtMemCheckpoint` chiamate all'inizio e alla fine dell'applicazione, quindi usando `_CrtMemDifference` per confrontare i risultati. Se `_CrtMemDifference` Mostra una perdita di memoria, è possibile aggiungere altre `_CrtMemCheckpoint` chiamate per dividere il programma usando una ricerca binaria, fino a quando non si è isolata l'origine della perdita.

## <a name="false-positives"></a>Falsi positivi

 `_CrtDumpMemoryLeaks`può fornire false indicazioni di perdite di memoria se una libreria contrassegna le allocazioni interne come blocchi normali anziché come blocchi CRT o client. In questo caso, `_CrtDumpMemoryLeaks` non è in grado di indicare la differenza tra allocazioni utente e allocazioni interne della libreria. Se i distruttori globali relativi alle allocazioni della libreria vengono eseguiti dopo il punto in cui viene chiamato `_CrtDumpMemoryLeaks`, ogni allocazione interna della libreria viene segnalata come perdita di memoria. Le versioni della libreria di modelli standard precedenti a Visual Studio .NET possono causare la `_CrtDumpMemoryLeaks` segnalazione di falsi positivi.

## <a name="see-also"></a>Vedere anche

- [Dettagli heap di debug CRT](../debugger/crt-debug-heap-details.md)
- [Sicurezza del debugger](../debugger/debugger-security.md)
- [Debug del codice nativo](../debugger/debugging-native-code.md)
