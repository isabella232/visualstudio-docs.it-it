---
title: C/C++ asserzioni | Microsoft Docs
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
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: f7ac27b46252582b3982082a2a9a90a09223574f
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/25/2019
ms.locfileid: "72911610"
---
# <a name="cc-assertions"></a>Asserzioni C/C++
Un'istruzione di asserzione specifica una condizione che si prevede venga soddisfatta in un punto del programma. Se tale condizione non è true, l'asserzione ha esito negativo, l'esecuzione del programma viene interrotta e viene visualizzata la finestra di [dialogo asserzione non riuscita](../debugger/assertion-failed-dialog-box.md) .

Visual Studio supporta C++ le istruzioni di asserzione basate sui costrutti seguenti:

- Asserzioni MFC per i programmi MFC.

- [ATLASSERT](/cpp/atl/reference/debugging-and-error-reporting-macros#atlassert) per i programmi che utilizzano ATL.

- Asserzioni CRT per i programmi che usano la libreria di runtime del linguaggio C.

- La [funzione ANSI Assert](/cpp/c-runtime-library/reference/assert-macro-assert-wassert) per altri C/C++ programmi.

  È possibile utilizzare le asserzioni per rilevare gli errori logici, controllare i risultati di un'operazione e verificare le condizioni di errore che devono essere gestite.

## <a name="BKMK_In_this_topic"></a> In questo argomento
[Funzionamento delle asserzioni](#BKMK_How_assertions_work)

[Asserzioni nelle build di debug e di rilascio](#BKMK_Assertions_in_Debug_and_Release_builds)

[Effetti collaterali dell'utilizzo delle asserzioni](#BKMK_Side_effects_of_using_assertions)

[Asserzioni CRT](#BKMK_CRT_assertions)

[Asserzioni MFC](#BKMK_MFC_assertions)

- [MFC ASSERT_VALID e CObject:: AssertValid](#BKMK_MFC_ASSERT_VALID_and_CObject__AssertValid)

- [Limitazioni di AssertValid](#BKMK_Limitations_of_AssertValid)

  [Utilizzo di asserzioni](#BKMK_Using_assertions)

- [Rilevamento di errori di logica](#BKMK_Catching_logic_errors)

- [Verifica dei risultati](#BKMK_Checking_results_)

- [Individuazione degli errori non gestiti](#BKMK_Testing_error_conditions_)

## <a name="BKMK_How_assertions_work"></a>Funzionamento delle asserzioni
Quando il debugger si interrompe a causa di un'asserzione della libreria di runtime C o MFC, se l'origine è disponibile, il debugger passa al punto nel file di origine in cui si è verificata l'asserzione. Il messaggio di asserzione viene visualizzato sia nella [finestra di output](../ide/reference/output-window.md) che nella finestra di dialogo **asserzione non riuscita** . È possibile copiare il messaggio di asserzione dalla finestra di **output** in una finestra di testo se si desidera salvarlo per riferimento futuro. La finestra di **output** può contenere anche altri messaggi di errore. Esaminare attentamente questi messaggi perché forniscono indizi sulla causa dell'errore di asserzione.

Usare le asserzioni per rilevare gli errori durante lo sviluppo. Come regola, usare un'asserzione per ogni presupposto. Se ad esempio si presuppone che un argomento non sia NULL, utilizzare un'asserzione per verificare tale presupposto.

[In questo argomento](#BKMK_In_this_topic)

## <a name="BKMK_Assertions_in_Debug_and_Release_builds"></a>Asserzioni nelle build di debug e di rilascio
Le istruzioni di asserzione vengono compilate solo se `_DEBUG` è definito. In caso contrario, il compilatore considera le asserzioni come istruzioni null. Di conseguenza, le istruzioni di asserzione non comportano costi di overhead o prestazioni nel programma di rilascio finale e consentono di evitare l'uso di direttive `#ifdef`.

## <a name="BKMK_Side_effects_of_using_assertions"></a>Effetti collaterali dell'utilizzo delle asserzioni
Quando si aggiungono asserzioni al codice, assicurarsi che le asserzioni non abbiano effetti collaterali. Si consideri, ad esempio, la seguente asserzione che modifica il valore `nM`:

```cpp
ASSERT(nM++ > 0); // Don't do this!
```

Poiché l'espressione `ASSERT` non viene valutata nella versione di rilascio del programma, `nM` avrà valori diversi nelle versioni di debug e di rilascio. Per evitare questo problema in MFC, è possibile utilizzare la macro [Verify](/cpp/mfc/reference/diagnostic-services#verify) anziché `ASSERT`. `VERIFY` valuta l'espressione in tutte le versioni, ma non controlla il risultato nella versione di rilascio.

Prestare particolare attenzione all'utilizzo delle chiamate di funzione nelle istruzioni di asserzione, perché la valutazione di una funzione può avere effetti collaterali imprevisti.

```cpp
ASSERT ( myFnctn(0)==1 ) // unsafe if myFnctn has side effects
VERIFY ( myFnctn(0)==1 ) // safe
```

`VERIFY` chiama `myFnctn` nelle versioni di debug e di rilascio, quindi è accettabile usare. Tuttavia, l'utilizzo di `VERIFY` impone l'overhead di una chiamata di funzione non necessaria nella versione di rilascio.

[In questo argomento](#BKMK_In_this_topic)

## <a name="BKMK_CRT_assertions"></a>Asserzioni CRT
CRTDBG. Il file di intestazione H definisce le [macro _ASSERT e _ASSERTE](/cpp/c-runtime-library/reference/assert-asserte-assert-expr-macros) per il controllo dell'asserzione.

| Macro | Risultato |
|------------| - |
| `_ASSERT` | Se l'espressione specificata restituisce FALSE, il nome del file e il numero di riga del `_ASSERT`. |
| `_ASSERTE` | Uguale a `_ASSERT`, oltre a una rappresentazione di stringa dell'espressione dichiarata. |

`_ASSERTE` è più potente perché segnala l'espressione dichiarata che si è rivelata falsa. Questo può essere sufficiente per identificare il problema senza fare riferimento al codice sorgente. Tuttavia, la versione di debug dell'applicazione conterrà una costante di stringa per ogni espressione dichiarata utilizzando `_ASSERTE`. Se si usano molte macro `_ASSERTE`, queste espressioni di stringa hanno una quantità significativa di memoria. Se si verifica un problema, usare `_ASSERT` per salvare la memoria.

Quando viene definito `_DEBUG`, la macro `_ASSERTE` viene definita nel modo seguente:

```cpp
#define _ASSERTE(expr) \
    do { \
        if (!(expr) && (1 == _CrtDbgReport( \
            _CRT_ASSERT, __FILE__, __LINE__, #expr))) \
            _CrtDbgBreak(); \
    } while (0)
```

Se l'espressione dichiarata restituisce FALSE, viene chiamato [_CrtDbgReport](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw) per segnalare l'errore di asserzione (tramite una finestra di dialogo di messaggio per impostazione predefinita). Se si sceglie **Riprova** nella finestra di dialogo messaggio, `_CrtDbgReport` restituisce 1 e `_CrtDbgBreak` chiama il debugger tramite `DebugBreak`.

### <a name="checking-for-heap-corruption"></a>Verifica del danneggiamento dell'heap
Nell'esempio seguente viene usato [_CrtCheckMemory](/cpp/c-runtime-library/reference/crtcheckmemory) per verificare il danneggiamento dell'heap:

```cpp
_ASSERTE(_CrtCheckMemory());
```

### <a name="checking-pointer-validity"></a>Verifica della validità del puntatore
Nell'esempio seguente viene usato [_CrtIsValidPointer](/cpp/c-runtime-library/reference/crtisvalidpointer) per verificare che un intervallo di memoria specificato sia valido per la lettura o la scrittura.

```cpp
_ASSERTE(_CrtIsValidPointer( address, size, TRUE );
```

Nell'esempio seguente viene usato [_CrtIsValidHeapPointer](/cpp/c-runtime-library/reference/crtisvalidheappointer) per verificare che un puntatore punti alla memoria nell'heap locale (l'heap creato e gestito da questa istanza della libreria di runtime C): una dll può avere una propria istanza della libreria e quindi il proprio heap, al di fuori dell'heap dell'applicazione. Questa asserzione rileva non solo gli indirizzi null o fuori limite, ma anche i puntatori a variabili statiche, variabili dello stack e qualsiasi altra memoria non locale.

```cpp
_ASSERTE(_CrtIsValidPointer( myData );
```

### <a name="checking-a-memory-block"></a>Controllo di un blocco di memoria
Nell'esempio seguente viene usato [_CrtIsMemoryBlock](/cpp/c-runtime-library/reference/crtismemoryblock) per verificare che un blocco di memoria si trovi nell'heap locale e che abbia un tipo di blocco valido.

```cpp
_ASSERTE(_CrtIsMemoryBlock (myData, size, &requestNumber, &filename, &linenumber));
```

[In questo argomento](#BKMK_In_this_topic)

## <a name="BKMK_MFC_assertions"></a>Asserzioni MFC
MFC definisce la macro [Assert](https://msdn.microsoft.com/Library/1e70902d-d58c-4e7b-9f69-2aeb6cbe476c) per il controllo dell'asserzione. Definisce inoltre i metodi `MFC ASSERT_VALID` e `CObject::AssertValid` per verificare lo stato interno di un oggetto derivato da `CObject`.

Se l'argomento della macro MFC `ASSERT` restituisce zero o false, la macro interrompe l'esecuzione del programma e avvisa l'utente. in caso contrario, l'esecuzione continua.

Quando un'asserzione ha esito negativo, viene visualizzata una finestra di dialogo di messaggio con il nome del file di origine e il numero di riga dell'asserzione. Se si sceglie Riprova nella finestra di dialogo, una chiamata a [AfxDebugBreak](/cpp/mfc/reference/diagnostic-services#afxdebugbreak) fa sì che l'esecuzione venga interrotta nel debugger. A questo punto, è possibile esaminare lo stack di chiamate e usare altre funzionalità del debugger per determinare il motivo per cui l'asserzione non è riuscita. Se è stato abilitato il [debug](../debugger/just-in-time-debugging-in-visual-studio.md)JIT e il debugger non è ancora in esecuzione, la finestra di dialogo può avviare il debugger.

Nell'esempio seguente viene illustrato come utilizzare `ASSERT` per verificare il valore restituito di una funzione:

```cpp
int x = SomeFunc(y);
ASSERT(x >= 0);   //  Assertion fails if x is negative
```

È possibile usare ASSERT con la funzione [IsKindOf](/cpp/mfc/reference/cobject-class#iskindof) per fornire il controllo del tipo degli argomenti della funzione:

```cpp
ASSERT( pObject1->IsKindOf( RUNTIME_CLASS( CPerson ) ) );
```

La macro `ASSERT` non produce codice nella versione di rilascio. Se è necessario valutare l'espressione nella versione di rilascio, usare la macro [Verify](https://msdn.microsoft.com/library/s8c29sw2.aspx#verify) anziché ASSERT.

### <a name="BKMK_MFC_ASSERT_VALID_and_CObject__AssertValid"></a>MFC ASSERT_VALID e CObject:: AssertValid
Il metodo [CObject:: AssertValid](/cpp/mfc/reference/cobject-class#assertvalid) fornisce controlli run-time dello stato interno di un oggetto. Sebbene non sia necessario eseguire l'override di `AssertValid` quando si deriva la classe da `CObject`, è possibile rendere la classe più affidabile eseguendo questa operazione. `AssertValid` deve eseguire asserzioni in tutte le variabili membro dell'oggetto per verificare che contengano valori validi. Ad esempio, deve verificare che le variabili membro del puntatore non siano NULL.

Nell'esempio seguente viene illustrato come dichiarare una funzione `AssertValid`:

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

Quando si esegue l'override di `AssertValid`, chiamare la versione della classe base di `AssertValid` prima di eseguire controlli personalizzati. Usare quindi la macro ASSERT per verificare i membri univoci della classe derivata, come illustrato di seguito:

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

Se una delle variabili membro Archivia oggetti, è possibile usare la macro `ASSERT_VALID` per verificarne la validità interna, se le relative classi eseguono l'override di `AssertValid`.

Si consideri, ad esempio, una classe `CMyData`, che archivia un [CObList](/cpp/mfc/reference/coblist-class) in una delle variabili membro. La variabile `CObList`, `m_DataList`, archivia una raccolta di oggetti di `CPerson`. Una dichiarazione abbreviata di `CMyData` ha un aspetto simile al seguente:

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

L'override `AssertValid` in `CMyData` ha un aspetto simile al seguente:

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

`CMyData` utilizza il meccanismo `AssertValid` per verificare la validità degli oggetti archiviati nel relativo membro dati. L'override `AssertValid` di `CMyData` richiama la macro `ASSERT_VALID` per la propria variabile membro m_pDataList.

Il test di validità non si arresta a questo livello perché anche la classe `CObList` esegue l'override di `AssertValid`. Questo override esegue un test di validità aggiuntivo sullo stato interno dell'elenco. Pertanto, un test di validità su un oggetto `CMyData` comporta test di validità aggiuntivi per gli Stati interni dell'oggetto elenco `CObList` archiviato.

Con altre operazioni, è possibile aggiungere i test di validità per gli oggetti `CPerson` archiviati nell'elenco. È possibile derivare una classe `CPersonList` da `CObList` ed eseguire l'override di `AssertValid`. Nell'override, chiamare `CObject::AssertValid` e quindi scorrere l'elenco, chiamando `AssertValid` in ogni oggetto `CPerson` archiviato nell'elenco. La classe `CPerson` illustrata all'inizio di questo argomento ha già eseguito l'override di `AssertValid`.

Si tratta di un meccanismo potente quando si compila per il debug. Quando successivamente si compila per la versione, il meccanismo viene disattivato automaticamente.

### <a name="BKMK_Limitations_of_AssertValid"></a>Limitazioni di AssertValid
Un'asserzione attivata indica che l'oggetto è decisamente errato e l'esecuzione viene arrestata. Tuttavia, una mancanza di asserzione indica solo che non è stato trovato alcun problema, ma non è garantito che l'oggetto sia valido.

[In questo argomento](#BKMK_In_this_topic)

## <a name="BKMK_Using_assertions"></a>Utilizzo di asserzioni

### <a name="BKMK_Catching_logic_errors"></a>Rilevamento di errori di logica
È possibile impostare un'asserzione su una condizione che deve essere true in base alla logica del programma. L'asserzione non ha alcun effetto a meno che non si verifichi un errore di logica.

Si supponga, ad esempio, di simulare le molecole di gas in un contenitore e che la variabile `numMols` rappresenti il numero totale di molecole. Questo numero non può essere minore di zero, quindi è possibile includere un'istruzione di asserzione MFC come la seguente:

```cpp
ASSERT(numMols >= 0);
```

In alternativa, è possibile includere un'asserzione CRT come la seguente:

```cpp
_ASSERT(numMols >= 0);
```

Queste istruzioni non eseguono alcuna operazione se il programma funziona correttamente. Se un errore logico causa la disattivazione di `numMols`, tuttavia, l'asserzione interrompe l'esecuzione del programma e visualizza la finestra di [dialogo asserzione non riuscita](../debugger/assertion-failed-dialog-box.md).

[In questo argomento](#BKMK_In_this_topic)

### <a name="BKMK_Checking_results_"></a>Verifica dei risultati
Le asserzioni sono utili per le operazioni di test i cui risultati non sono evidenti da un'ispezione visiva rapida.

Si consideri, ad esempio, il codice seguente, che aggiorna la variabile `iMols` in base al contenuto dell'elenco collegato a cui punta `mols`:

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

Il numero di molecole conteggiate da `iMols` deve essere sempre minore o uguale al numero totale di molecole, `numMols`. L'ispezione visiva del ciclo non indica che questo sarà necessariamente il caso, pertanto viene utilizzata un'istruzione di asserzione dopo il ciclo per verificare la condizione.

[In questo argomento](#BKMK_In_this_topic)

### <a name="BKMK_Testing_error_conditions_"></a>Individuazione degli errori non gestiti
È possibile usare le asserzioni per testare le condizioni di errore in un punto del codice in cui devono essere gestiti gli errori. Nell'esempio seguente una routine grafica restituisce un codice di errore o zero in caso di esito positivo.

```cpp
myErr = myGraphRoutine(a, b);

/* Code to handle errors and
   reset myErr if successful */

ASSERT(!myErr); -- MFC version
_ASSERT(!myErr); -- CRT version
```

Se il codice di gestione degli errori funziona correttamente, l'errore deve essere gestito e `myErr` viene reimpostato su zero prima che venga raggiunta l'asserzione. Se `myErr` ha un altro valore, l'asserzione ha esito negativo, il programma si interrompe e viene visualizzata la finestra di [dialogo asserzione non riuscita](../debugger/assertion-failed-dialog-box.md) .

Tuttavia, le istruzioni di asserzione non costituiscono un sostituto per il codice di gestione degli errori. Nell'esempio seguente viene illustrata un'istruzione di asserzione che può causare problemi nel codice finale della versione:

```cpp
myErr = myGraphRoutine(a, b);

/* No Code to handle errors */

ASSERT(!myErr); // Don't do this!
_ASSERT(!myErr); // Don't do this, either!
```

Questo codice si basa sull'istruzione Assertion per gestire la condizione di errore. Di conseguenza, qualsiasi codice di errore restituito da `myGraphRoutine` non verrà gestito nel codice della versione finale.

[In questo argomento](#BKMK_In_this_topic)

## <a name="see-also"></a>Vedere anche

- [Sicurezza del debugger](../debugger/debugger-security.md)
- [Debug del codice nativo](../debugger/debugging-native-code.md)
- [Asserzioni nel codice gestito](../debugger/assertions-in-managed-code.md)