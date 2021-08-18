---
title: Asserzioni C/C++ | Microsoft Docs
description: Informazioni sul funzionamento delle asserzioni C/C++ Visual Studio debug. Un'asserzione specifica una condizione che si prevede sia true in un punto del programma.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [MFC], assertions
- results, checking
- result checking
- Call Stack window, assertion failures
- debugging [C++], assertions
- VERIFY macro
- assertions, side effects
- assertions
- ASSERT macro
- errors [C++], catching with assertions
- testing, error conditions with assertion statements
- _DEBUG macro
- Assertion Failed dialog box
- failures, finding locations
ms.assetid: 2d7b0121-71aa-414b-bbb6-ede1093d0bfc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- cplusplus
ms.openlocfilehash: 2ed7f138b41cc71cd4964bb50e3358e020905355
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122129766"
---
# <a name="cc-assertions"></a>Asserzioni C/C++

Un'istruzione di asserzione specifica una condizione che si prevede sia true in un punto del programma. Se tale condizione non è vera, l'asserzione ha esito negativo, l'esecuzione del programma viene interrotta e viene visualizzata la finestra di dialogo Asserzione [non](../debugger/assertion-failed-dialog-box.md) riuscita.

Visual Studio supporta istruzioni di asserzione C++ basate sui costrutti seguenti:

- Asserzioni MFC per i programmi MFC.

- [ATLASSERT per](/cpp/atl/reference/debugging-and-error-reporting-macros#atlassert) i programmi che usano ATL.

- Asserzioni CRT per i programmi che usano la libreria di runtime C.

- Funzione [asserzione](/cpp/c-runtime-library/reference/assert-macro-assert-wassert) ANSI per altri programmi C/C++.

  È possibile usare le asserzioni per rilevare gli errori logici, controllare i risultati di un'operazione e testare le condizioni di errore che devono essere state gestite.

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> In questo argomento

[Funzionamento delle asserzioni](#BKMK_How_assertions_work)

[Asserzioni nelle build di debug e di rilascio](#BKMK_Assertions_in_Debug_and_Release_builds)

[Effetti collaterali dell'uso delle asserzioni](#BKMK_Side_effects_of_using_assertions)

[Asserzioni CRT](#BKMK_CRT_assertions)

[Asserzioni MFC](#BKMK_MFC_assertions)

- [Mfc ASSERT_VALID e CObject::AssertValid](#BKMK_MFC_ASSERT_VALID_and_CObject__AssertValid)

- [Limitazioni di AssertValid](#BKMK_Limitations_of_AssertValid)

  [Uso di asserzioni](#BKMK_Using_assertions)

- [Intercettazione di errori logici](#BKMK_Catching_logic_errors)

- [Controllo dei risultati](#BKMK_Checking_results_)

- [Ricerca di errori non gestiti](#BKMK_Testing_error_conditions_)

## <a name="how-assertions-work"></a><a name="BKMK_How_assertions_work"></a> Funzionamento delle asserzioni

Quando il debugger si arresta a causa di un'asserzione della libreria di runtime MFC o C, se l'origine è disponibile, il debugger passa al punto nel file di origine in cui si è verificata l'asserzione. Il messaggio di asserzione viene visualizzato sia nella finestra [Output che](../ide/reference/output-window.md) nella finestra **di dialogo Asserzione** non riuscita. È possibile copiare il messaggio di asserzione dalla **finestra Output** in una finestra di testo se si vuole salvarlo per riferimento futuro. La **finestra Output** può contenere anche altri messaggi di errore. Esaminare attentamente questi messaggi, perché forniscono indicazioni sulla causa dell'errore di asserzione.

Usare le asserzioni per rilevare gli errori durante lo sviluppo. Di norma, usare un'asserzione per ogni presupposto. Ad esempio, se si presuppone che un argomento non sia NULL, usare un'asserzione per testare tale presupposto.

[Contenuto dell'argomento](#BKMK_In_this_topic)

## <a name="assertions-in-debug-and-release-builds"></a><a name="BKMK_Assertions_in_Debug_and_Release_builds"></a> Asserzioni nelle build di debug e di rilascio

Le istruzioni di asserzione vengono compilate solo `_DEBUG` se è definito. In caso contrario, il compilatore considera le asserzioni come istruzioni Null. Pertanto, le istruzioni di asserzione non impongono costi generali o di prestazioni nel programma di versione finale e consentono di evitare l'uso `#ifdef` di direttive .

## <a name="side-effects-of-using-assertions"></a><a name="BKMK_Side_effects_of_using_assertions"></a> Effetti collaterali dell'uso di asserzioni

Quando si aggiungono asserzioni al codice, assicurarsi che le asserzioni non abbia effetti collaterali. Si consideri ad esempio l'asserzione seguente che modifica il `nM` valore:

```cpp
ASSERT(nM++ > 0); // Don't do this!
```

Poiché `ASSERT` l'espressione non viene valutata nella versione di rilascio del programma, `nM` avrà valori diversi nelle versioni di debug e versione. Per evitare questo problema in MFC, è possibile usare la macro [VERIFY](/cpp/mfc/reference/diagnostic-services#verify) anziché `ASSERT` . `VERIFY` valuta l'espressione in tutte le versioni, ma non controlla il risultato nella versione di versione.

Prestare particolare attenzione all'uso delle chiamate di funzione nelle istruzioni di asserzione, perché la valutazione di una funzione può avere effetti collaterali imprevisti.

```cpp
ASSERT ( myFnctn(0)==1 ) // unsafe if myFnctn has side effects
VERIFY ( myFnctn(0)==1 ) // safe
```

`VERIFY` chiama sia nelle versioni di debug che in versione `myFnctn` di rilascio, quindi è accettabile usarlo. Tuttavia, `VERIFY` l'uso di impone l'overhead di una chiamata di funzione non necessaria nella versione di versione.

[Contenuto dell'argomento](#BKMK_In_this_topic)

## <a name="crt-assertions"></a><a name="BKMK_CRT_assertions"></a> Asserzioni CRT

The CRTDBG. Il file di intestazione H definisce le [macro _ASSERT e _ASSERTE per](/cpp/c-runtime-library/reference/assert-asserte-assert-expr-macros) il controllo delle asserzioni.

| Macro | Risultato |
|------------| - |
| `_ASSERT` | Se l'espressione specificata restituisce FALSE, il nome file e il numero di riga di `_ASSERT` . |
| `_ASSERTE` | Uguale a `_ASSERT` , più una rappresentazione di stringa dell'espressione che è stata asserta. |

`_ASSERTE` è più potente perché segnala l'espressione asserta che ha restituito FALSE. Questo potrebbe essere sufficiente per identificare il problema senza fare riferimento al codice sorgente. Tuttavia, la versione debug dell'applicazione conterrà una costante stringa per ogni espressione asserta tramite `_ASSERTE` . Se si usano molte `_ASSERTE` macro, queste espressioni stringa utilizzano una quantità significativa di memoria. Se si verifica un problema, usare per `_ASSERT` salvare la memoria.

Quando `_DEBUG` è definita, la `_ASSERTE` macro viene definita nel modo seguente:

```cpp
#define _ASSERTE(expr) \
    do { \
        if (!(expr) && (1 == _CrtDbgReport( \
            _CRT_ASSERT, __FILE__, __LINE__, #expr))) \
            _CrtDbgBreak(); \
    } while (0)
```

Se l'espressione asserzionata restituisce [FALSE,](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw) _CrtDbgReport viene chiamato per segnalare l'errore di asserzione (per impostazione predefinita viene utilizzata una finestra di dialogo di messaggio). Se si sceglie **Riprova** nella finestra di dialogo del messaggio, `_CrtDbgReport` restituisce 1 e chiama il debugger tramite `_CrtDbgBreak` `DebugBreak` .

Se è necessario disabilitare temporaneamente tutte le asserzioni, usare [_CtrSetReportMode](/cpp/c-runtime-library/reference/crtsetreportmode).

### <a name="checking-for-heap-corruption"></a>Controllo del danneggiamento dell'heap

L'esempio seguente usa [_CrtCheckMemory](/cpp/c-runtime-library/reference/crtcheckmemory) per verificare il danneggiamento dell'heap:

```cpp
_ASSERTE(_CrtCheckMemory());
```

### <a name="checking-pointer-validity"></a>Controllo della validità del puntatore

L'esempio seguente usa [_CrtIsValidPointer](/cpp/c-runtime-library/reference/crtisvalidpointer) per verificare che un determinato intervallo di memoria sia valido per la lettura o la scrittura.

```cpp
_ASSERTE(_CrtIsValidPointer( address, size, TRUE );
```

L'esempio seguente usa [_CrtIsValidHeapPointer](/cpp/c-runtime-library/reference/crtisvalidheappointer) per verificare che un puntatore punti alla memoria nell'heap locale (l'heap creato e gestito da questa istanza della libreria di runtime C). Una DLL può avere una propria istanza della libreria e quindi il proprio heap, all'esterno dell'heap dell'applicazione. Questa asserzione rileva non solo gli indirizzi null o non delimitati, ma anche i puntatori a variabili statiche, variabili dello stack e qualsiasi altra memoria non locale.

```cpp
_ASSERTE(_CrtIsValidPointer( myData );
```

### <a name="checking-a-memory-block"></a>Controllo di un blocco di memoria

L'esempio seguente [usa _CrtIsMemoryBlock](/cpp/c-runtime-library/reference/crtismemoryblock) per verificare che un blocco di memoria si trova nell'heap locale e abbia un tipo di blocco valido.

```cpp
_ASSERTE(_CrtIsMemoryBlock (myData, size, &requestNumber, &filename, &linenumber));
```

[Contenuto dell'argomento](#BKMK_In_this_topic)

## <a name="mfc-assertions"></a><a name="BKMK_MFC_assertions"></a> Asserzioni MFC

MFC definisce la macro [ASSERT per](/previous-versions/ew16s3zc(v=vs.140)) il controllo delle asserzioni. Definisce anche i metodi `MFC ASSERT_VALID` e per controllare lo stato interno di un oggetto `CObject::AssertValid` `CObject` derivato da .

Se l'argomento della macro MFC restituisce zero o false, la macro interrompe l'esecuzione del programma e avvisa l'utente; in caso `ASSERT` contrario, l'esecuzione continua.

Quando un'asserzione ha esito negativo, viene visualizzata una finestra di dialogo di messaggio con il nome del file di origine e il numero di riga dell'asserzione. Se si sceglie Riprova nella finestra di dialogo, una chiamata ad [AfxDebugBreak](/cpp/mfc/reference/diagnostic-services#afxdebugbreak) causa l'interruzione dell'esecuzione nel debugger. A questo punto, è possibile esaminare lo stack di chiamate e usare altre funzionalità del debugger per determinare il motivo per cui l'asserzione ha avuto esito negativo. Se è stato abilitato il debug [JIT](../debugger/just-in-time-debugging-in-visual-studio.md)e il debugger non era già in esecuzione, la finestra di dialogo può avviare il debugger.

L'esempio seguente illustra come usare `ASSERT` per controllare il valore restituito di una funzione:

```cpp
int x = SomeFunc(y);
ASSERT(x >= 0);   //  Assertion fails if x is negative
```

È possibile usare ASSERT con la [funzione IsKindOf](/cpp/mfc/reference/cobject-class#iskindof) per fornire il controllo dei tipi degli argomenti della funzione:

```cpp
ASSERT( pObject1->IsKindOf( RUNTIME_CLASS( CPerson ) ) );
```

La `ASSERT` macro non produce codice nella versione di rilascio. Se è necessario valutare l'espressione nella versione di rilascio, usare la macro [VERIFY](/cpp/mfc/reference/diagnostic-services#verify) anziché ASSERT.

### <a name="mfc-assert_valid-and-cobjectassertvalid"></a><a name="BKMK_MFC_ASSERT_VALID_and_CObject__AssertValid"></a> Mfc ASSERT_VALID e CObject::AssertValid

Il [metodo CObject::AssertValid](/cpp/mfc/reference/cobject-class#assertvalid) fornisce controlli in fase di esecuzione dello stato interno di un oggetto. Anche se non è necessario eseguire l'override quando si deriva la classe da , è possibile rendere la classe più affidabile `AssertValid` `CObject` in questo modo. `AssertValid` deve eseguire asserzioni su tutte le variabili membro dell'oggetto per verificare che contengano valori validi. Ad esempio, deve verificare che le variabili membro puntatore non siano NULL.

L'esempio seguente illustra come dichiarare una `AssertValid` funzione:

```cpp
class CPerson : public CObject
{
protected:
    CString m_strName;
    float   m_salary;
public:
#ifdef _DEBUG
    // Override
    virtual void AssertValid() const;
#endif
    // ...
};
```

Quando si esegue l'override di , chiamare la versione della classe `AssertValid` base di prima di eseguire controlli `AssertValid` personalizzati. Usare quindi la macro ASSERT per controllare i membri univoci per la classe derivata, come illustrato di seguito:

```cpp
#ifdef _DEBUG
void CPerson::AssertValid() const
{
    // Call inherited AssertValid first.
    CObject::AssertValid();

    // Check CPerson members...
    // Must have a name.
    ASSERT( !m_strName.IsEmpty());
    // Must have an income.
    ASSERT( m_salary > 0 );
}
#endif
```

Se una delle variabili membro archivia oggetti, è possibile usare la macro per verificarne la validità interna (se le classi eseguono `ASSERT_VALID` l'override di `AssertValid` ).

Si consideri ad esempio una classe `CMyData` , che archivia un [CObList](/cpp/mfc/reference/coblist-class) in una delle relative variabili membro. La `CObList` variabile , archivia una raccolta di oggetti `m_DataList` `CPerson` . Una dichiarazione abbreviata di `CMyData` è simile alla seguente:

```cpp
class CMyData : public CObject
{
    // Constructor and other members ...
    protected:
        CObList* m_pDataList;
    // Other declarations ...
    public:
#ifdef _DEBUG
        // Override:
        virtual void AssertValid( ) const;
#endif
    // And so on ...
};
```

`AssertValid`L'override in è simile al `CMyData` seguente:

```cpp
#ifdef _DEBUG
void CMyData::AssertValid( ) const
{
    // Call inherited AssertValid.
    CObject::AssertValid( );
    // Check validity of CMyData members.
    ASSERT_VALID( m_pDataList );
    // ...
}
#endif
```

`CMyData` usa il `AssertValid` meccanismo per testare la validità degli oggetti archiviati nel relativo membro dati. L'override `AssertValid` di richiama la macro per la propria m_pDataList `CMyData` `ASSERT_VALID` membro.

Il test di validità non si arresta a questo livello perché la classe `CObList` esegue anche l'override di `AssertValid` . Questo override esegue test di validità aggiuntivi sullo stato interno dell'elenco. Di conseguenza, un test di validità su un oggetto comporta test di validità aggiuntivi per `CMyData` gli stati interni dell'oggetto `CObList` elenco archiviato.

Con altre operazioni, è possibile aggiungere test di validità anche per `CPerson` gli oggetti archiviati nell'elenco. È possibile derivare una classe `CPersonList` da ed `CObList` eseguire l'override di `AssertValid` . Nell'override chiamare e `CObject::AssertValid` quindi scorrere l'elenco, chiamando su ogni `AssertValid` oggetto archiviato `CPerson` nell'elenco. La `CPerson` classe illustrata all'inizio di questo argomento esegue già l'override di `AssertValid` .

Si tratta di un meccanismo potente quando si esegue la compilazione per il debug. Quando successivamente si esegue la compilazione per il rilascio, il meccanismo viene disattivato automaticamente.

### <a name="limitations-of-assertvalid"></a><a name="BKMK_Limitations_of_AssertValid"></a> Limitazioni di AssertValid
Un'asserzione attivata indica che l'oggetto è sicuramente non valido e l'esecuzione verrà interrotta. Tuttavia, una mancanza di asserzione indica solo che non è stato trovato alcun problema, ma non è garantito che l'oggetto sia valido.

[Contenuto dell'argomento](#BKMK_In_this_topic)

## <a name="using-assertions"></a><a name="BKMK_Using_assertions"></a> Uso di asserzioni

### <a name="catching-logic-errors"></a><a name="BKMK_Catching_logic_errors"></a> Rilevamento degli errori logici

È possibile impostare un'asserzione su una condizione che deve essere true in base alla logica del programma. L'asserzione non ha alcun effetto a meno che non si verifichi un errore logico.

Si supponga, ad esempio, di simulare i gas in un contenitore e che la variabile `numMols` rappresenti il numero totale di erre. Questo numero non può essere minore di zero, pertanto è possibile includere un'istruzione di asserzione MFC simile alla seguente:

```cpp
ASSERT(numMols >= 0);
```

Oppure è possibile includere un'asserzione CRT simile alla seguente:

```cpp
_ASSERT(numMols >= 0);
```

Queste istruzioni non e fanno nulla se il programma funziona correttamente. Se tuttavia un errore logico causa un errore di logica minore di zero, l'asserzione interrompe l'esecuzione del programma e visualizza la finestra di `numMols` dialogo Asserzione [non riuscita](../debugger/assertion-failed-dialog-box.md).

[Contenuto dell'argomento](#BKMK_In_this_topic)

### <a name="checking-results"></a><a name="BKMK_Checking_results_"></a> Controllo dei risultati

Le asserzioni sono utili per le operazioni di test i cui risultati non sono evidenti da un rapido controllo visivo.

Si consideri ad esempio il codice seguente, che aggiorna la variabile in base al contenuto `iMols` dell'elenco collegato a cui punta `mols` :

```cpp
/* This code assumes that type has overloaded the != operator
 with const char *
It also assumes that H2O is somewhere in that linked list.
Otherwise we'll get an access violation... */
while (mols->type != "H2O")
{
    iMols += mols->num;
    mols = mols->next;
}
ASSERT(iMols<=numMols); // MFC version
_ASSERT(iMols<=numMols); // CRT version
```

Il numero di evase conteggiate da deve essere sempre minore o `iMols` uguale al numero totale di erre, `numMols` . L'ispezione visiva del ciclo non mostra che questo sarà necessariamente il caso, quindi viene usata un'istruzione di asserzione dopo il ciclo per testare tale condizione.

[Contenuto dell'argomento](#BKMK_In_this_topic)

### <a name="finding-unhandled-errors"></a><a name="BKMK_Testing_error_conditions_"></a> Ricerca di errori non gestiti

È possibile usare le asserzioni per verificare le condizioni di errore in un punto del codice in cui devono essere gestiti eventuali errori. Nell'esempio seguente una routine grafica restituisce un codice di errore o zero per l'esito positivo.

```cpp
myErr = myGraphRoutine(a, b);

/* Code to handle errors and
   reset myErr if successful */

ASSERT(!myErr); -- MFC version
_ASSERT(!myErr); -- CRT version
```

Se il codice di gestione degli errori funziona correttamente, l'errore deve essere gestito e reimpostato su zero prima che venga `myErr` raggiunta l'asserzione. Se `myErr` ha un altro valore, l'asserzione ha esito negativo, il programma si interrompe e viene visualizzata la finestra di dialogo [Asserzione non](../debugger/assertion-failed-dialog-box.md) riuscita.

Le istruzioni di asserzione, tuttavia, non sostituiscono il codice di gestione degli errori. L'esempio seguente illustra un'istruzione di asserzione che può causare problemi nel codice della versione finale:

```cpp
myErr = myGraphRoutine(a, b);

/* No Code to handle errors */

ASSERT(!myErr); // Don't do this!
_ASSERT(!myErr); // Don't do this, either!
```

Questo codice si basa sull'istruzione di asserzione per gestire la condizione di errore. Di conseguenza, qualsiasi codice di errore restituito da `myGraphRoutine` non verrà gestito nel codice di versione finale.

[Contenuto dell'argomento](#BKMK_In_this_topic)

## <a name="see-also"></a>Vedi anche

- [Sicurezza del debugger](../debugger/debugger-security.md)
- [Debug del codice nativo](../debugger/debugging-native-code.md)
- [Asserzioni nel codice gestito](../debugger/assertions-in-managed-code.md)