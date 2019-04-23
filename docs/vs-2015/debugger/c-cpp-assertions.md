---
title: Asserzioni C / C++ | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
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
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 759376a6682287cbe41d4d1dc13666c5a540f8e9
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60050557"
---
# <a name="cc-assertions"></a>Asserzioni C/C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un'istruzione di asserzione specifica una condizione che si prevede abbia valore true in un punto del programma. Se tale condizione non è true, l'asserzione non riesce, viene interrotta l'esecuzione del programma e il [finestra di dialogo Asserzione non riuscita](../debugger/assertion-failed-dialog-box.md) viene visualizzata.  

 Visual C++ supporta le istruzioni di asserzione che si basano sui costrutti seguenti:  

- Asserzioni MFC per programmi MFC.  

- [ATLASSERT](http://msdn.microsoft.com/library/98e3e0fc-77e2-499b-a6f6-b17a21c6fbd3) per programmi che usano ATL.  

- Asserzioni di CRT per i programmi che usano la libreria di runtime C.  

- ANSI [funzione assert](http://msdn.microsoft.com/library/a9ca031a-648b-47a6-bdf1-65fc7399dd40) per altri programmi C/C++.  

  È possibile utilizzare le asserzioni per intercettare gli errori per la logica, controllare i risultati di un'operazione e testare le condizioni di errore che avrebbero dovuto essere gestite.  

## <a name="BKMK_In_this_topic"></a> In questo argomento  
 [Funzionano delle asserzioni](#BKMK_How_assertions_work)  

 [Asserzioni nelle build di Debug e rilascio](#BKMK_Assertions_in_Debug_and_Release_builds)  

 [Effetti collaterali dell'uso di asserzioni](#BKMK_Side_effects_of_using_assertions)  

 [Asserzioni di CRT](#BKMK_CRT_assertions)  

 [Asserzioni MFC](#BKMK_MFC_assertions)  

- [ASSERT_VALID e CObject:: AssertValid](#BKMK_MFC_ASSERT_VALID_and_CObject__AssertValid)  

- [Limitazioni di AssertValid](#BKMK_Limitations_of_AssertValid)  

  [Utilizzo di asserzioni](#BKMK_Using_assertions)  

- [Rilevamento di errori per la logica](#BKMK_Catching_logic_errors)  

- [Verifica i risultati](#BKMK_Checking_results_)  

- [Errori di ricerca non gestita](#BKMK_Testing_error_conditions_)  

## <a name="BKMK_How_assertions_work"></a> Funzionano delle asserzioni  
 Quando il debugger viene interrotto a causa di un'asserzione di libreria di runtime MFC o C, quindi se l'origine è disponibile, il debugger passa al punto nel file di origine in cui si è verificata l'asserzione. Viene visualizzato il messaggio di asserzione in entrambe le [finestra di Output](../ide/reference/output-window.md) e il **asserzione non riuscita** nella finestra di dialogo. È possibile copiare il messaggio dell'asserzione dal **Output** finestra da una finestra di testo se si desidera salvarlo per riferimento futuro. Il **Output** finestra può contenere anche altri messaggi di errore. Esaminare i messaggi con attenzione, perché forniscono indizi sulla causa dell'errore di asserzione.  

 Usare le asserzioni per rilevare gli errori durante lo sviluppo. Come regola, usare un'asserzione per ogni presupposto. Ad esempio, se si presuppone che un argomento non è NULL, usare un'asserzione per verificare questa ipotesi.  

 [In questo argomento](#BKMK_In_this_topic)  

## <a name="BKMK_Assertions_in_Debug_and_Release_builds"></a> Asserzioni nelle build di Debug e rilascio  
 Le istruzioni di asserzione compilare solo se `_DEBUG` è definito. In caso contrario, il compilatore considera asserzioni come istruzioni null. Di conseguenza, le istruzioni di asserzione è previsto alcun overhead o le prestazioni di costo nella versione finale del programma e consentono di evitare di usare `#ifdef` direttive.  

## <a name="BKMK_Side_effects_of_using_assertions"></a> Effetti collaterali dell'uso di asserzioni  
 Quando si aggiungono asserzioni nel codice, verificare che le asserzioni sono privi di effetti collaterali. Ad esempio, prendere in considerazione l'asserzione seguente che modifica il `nM` valore:  

```  
ASSERT(nM++ > 0); // Don't do this!  

```  

 Poiché il `ASSERT` espressione non viene valutata nella versione di rilascio del programma, `nM` possono avere valori diversi nelle versioni di Debug e rilascio. Per evitare questo problema in MFC, è possibile usare la [VERIFY](http://msdn.microsoft.com/library/3e1ab4ee-cbc7-4290-a777-c92f42ce7b96) macro anziché `ASSERT`.  `VERIFY` valuta l'espressione in tutte le versioni, ma non controlla il risultato nella versione di rilascio.  

 Prestare particolare attenzione sull'utilizzo di chiamate di funzione nelle istruzioni di asserzione, dato che la valutazione di una funzione può avere effetti collaterali imprevisti.  

```  
ASSERT ( myFnctn(0)==1 ) // unsafe if myFnctn has side effects  
VERIFY ( myFnctn(0)==1 ) // safe  
```  

 `VERIFY` le chiamate `myFnctn` nelle versioni di Debug e di versione, pertanto, è accettabile usare. Se tuttavia si utilizza `VERIFY` impone l'overhead di una chiamata di funzione non necessaria nella versione di rilascio.  

 [In questo argomento](#BKMK_In_this_topic)  

## <a name="BKMK_CRT_assertions"></a> Asserzioni di CRT  
 CRTDBG. H definisce i [macro Assert e ASSERTE](http://msdn.microsoft.com/library/e98fd2a6-7f5e-4aa8-8fe8-e93490deba36) per il controllo delle asserzioni.  

|   Macro    |                                             Risultato                                              |
|------------|-------------------------------------------------------------------------------------------------|
| `_ASSERT`  | Se l'espressione specificata restituisce FALSE, il numero di riga e il nome di file del `_ASSERT`. |
| `_ASSERTE` |      Uguale allo `_ASSERT`, oltre a una rappresentazione di stringa dell'espressione è stato dichiarato.       |

 `_ASSERTE` è più potente, perché segnala l'espressione di asserzione che è risultato per essere FALSE. Ciò potrebbe essere sufficiente per identificare il problema senza fare riferimento al codice sorgente. Tuttavia, la versione di Debug dell'applicazione conterrà una costante di stringa per ogni espressione dichiarato usando `_ASSERTE`. Se si usano molte `_ASSERTE` macro, queste espressioni stringa occupano una quantità significativa di memoria. Se questo costituisce un problema, utilizzare `_ASSERT` per risparmiare memoria.  

 Quando `_DEBUG` è definito, il `_ASSERTE` macro viene definita come segue:  

```  
#define _ASSERTE(expr) \  
   do { \  
      if (!(expr) && (1 == _CrtDbgReport( \  
         _CRT_ASSERT, __FILE__, __LINE__, #expr))) \  
         _CrtDbgBreak(); \  
   } while (0)  
```  

 Se l'espressione di asserzione restituisce FALSE, [CrtDbgReport](http://msdn.microsoft.com/library/6e581fb6-f7fb-4716-9432-f0145d639ecc) viene chiamato per segnalare l'errore di asserzione (tramite una finestra di dialogo del messaggio per impostazione predefinita). Se si sceglie **ripetere** nella finestra di dialogo messaggio `_CrtDbgReport` restituisce 1 e `_CrtDbgBreak` chiama il debugger `DebugBreak`.  

### <a name="checking-for-heap-corruption"></a>Cercare il danneggiamento dell'Heap  
 L'esempio seguente usa [CrtCheckMemory](http://msdn.microsoft.com/library/457cc72e-60fd-4177-ab5c-6ae26a420765) per verificare la presenza di danneggiamento dell'heap:  

```  
_ASSERTE(_CrtCheckMemory());  
```  

### <a name="checking-pointer-validity"></a>Controllo della validità del puntatore  
 L'esempio seguente usa [CrtIsValidPointer](http://msdn.microsoft.com/library/91c35590-ea5e-450f-a15d-ad8d62ade1fa) per verificare che sia valido per la lettura o scrittura di un determinato intervallo di memoria.  

```  
_ASSERTE(_CrtIsValidPointer( address, size, TRUE );  
```  

 L'esempio seguente usa [CrtIsValidHeapPointer](http://msdn.microsoft.com/library/caf597ce-1b05-4764-9f37-0197a982bec5) per verificare un puntatore punta alla memoria nell'heap locale (all'heap creato e gestito da questa istanza della libreria di runtime C, ovvero una DLL può avere una propria istanza della libreria, e di conseguenza il proprio heap, di fuori di heap dell'applicazione). Questa asserzione non intercetta solo null o non compresi nell'intervallo indirizzi, ma anche i puntatori alle variabili statiche, le variabili dello stack e qualsiasi altra memoria non locale.  

```  
_ASSERTE(_CrtIsValidPointer( myData );  
```  

### <a name="checking-a-memory-block"></a>Verifica un blocco di memoria  
 L'esempio seguente usa [CrtIsMemoryBlock](http://msdn.microsoft.com/library/f7cbbc60-3690-4da0-a07b-68fd7f250273) per verificare che un blocco di memoria nell'heap locale e dispone di un tipo di blocco valido.  

```  
_ASSERTE(_CrtIsMemoryBlock (myData, size, &requestNumber, &filename, &linenumber));  
```  

 [In questo argomento](#BKMK_In_this_topic)  

## <a name="BKMK_MFC_assertions"></a> Asserzioni MFC  
 MFC definisce il [ASSERT](http://msdn.microsoft.com/library/1e70902d-d58c-4e7b-9f69-2aeb6cbe476c) macro per il controllo delle asserzioni. Definisce anche il `MFC ASSERT_VALID` e `CObject::AssertValid` metodi per verificare lo stato interno di un `CObject`-oggetto derivato.  

 Se l'argomento di MFC `ASSERT` macro restituisce zero o false, la macro interrompe l'esecuzione del programma e avvisa l'utente; in caso contrario, l'esecuzione continua.  

 Quando un'asserzione non riesce, una finestra di dialogo messaggio Mostra il nome del file di origine e il numero di riga dell'asserzione. Se si sceglie di ripetizione dei tentativi nella finestra di dialogo casella, una chiamata a [AfxDebugBreak](http://msdn.microsoft.com/library/c4cd79b9-9327-4db5-a9d6-c4004a92aa30) causa l'esecuzione al debugger. A questo punto, è possibile esaminare lo stack di chiamate e utilizzare altre utilità del debugger per determinare il motivo per cui l'asserzione non riuscita. Se è stata abilitata [Just-in-time debug](../debugger/just-in-time-debugging-in-visual-studio.md)e il debugger non era già in esecuzione, la finestra di dialogo è possibile avviare il debug.  

 Nell'esempio seguente viene illustrato come utilizzare `ASSERT` per controllare il valore restituito di una funzione:  

```  
int x = SomeFunc(y);  
ASSERT(x >= 0);   //  Assertion fails if x is negative  
```  

 È possibile usare ASSERT con il [IsKindOf](http://msdn.microsoft.com/library/7c87c748-b7e0-4c6d-9694-6035e62fdfd6) funzione per fornire degli argomenti della funzione di controllo del tipo:  

```  
ASSERT( pObject1->IsKindOf( RUNTIME_CLASS( CPerson ) ) );  
```  

 Il `ASSERT` macro mancata generazione di codice nella versione di rilascio. Se è necessario valutare l'espressione nella versione di rilascio, usare il [VERIFY](http://msdn.microsoft.com/library/3e1ab4ee-cbc7-4290-a777-c92f42ce7b96) macro invece di ASSERT.  

### <a name="BKMK_MFC_ASSERT_VALID_and_CObject__AssertValid"></a> ASSERT_VALID e CObject:: AssertValid  
 Il [CObject:: AssertValid](http://msdn.microsoft.com/library/534a0744-4ab6-423d-b492-b4058b3d5157) metodo fornisce controlli di runtime dello stato interno di un oggetto. Sebbene non sia necessario eseguire l'override `AssertValid` quando si deriva la classe da `CObject`, si può rendere più affidabili la classe in questo modo. `AssertValid` deve eseguire asserzioni in tutte le variabili membro dell'oggetto per verificare che contengano i valori validi. Ad esempio, è necessario verificare che le variabili membro di puntatore non sono NULL.  

 Nell'esempio seguente viene illustrato come dichiarare un `AssertValid` funzione:  

```  
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

 Quando esegue l'override `AssertValid`, chiamare la versione della classe base `AssertValid` prima di eseguire i controlli. Utilizzare quindi la macro di ASSERZIONE per controllare i membri univoci per la classe derivata, come illustrato di seguito:  

```  
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

 Se una o più delle variabili membro memorizza gli oggetti, è possibile usare la `ASSERT_VALID` macro per verificarne la validità interna (se esegue l'override delle classi `AssertValid`).  

 Ad esempio, si consideri una classe `CMyData`, gli archivi che un [CObList](http://msdn.microsoft.com/library/80699c93-33d8-4f8b-b8cf-7b58aeab64ca) in una delle variabili membro. Il `CObList` variabile `m_DataList`, archivia una raccolta di `CPerson` oggetti. Una dichiarazione di abbreviato di `CMyData` ha un aspetto simile al seguente:  

```  
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

 Il `AssertValid` esegue l'override in `CMyData` ha un aspetto simile al seguente:  

```  
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

 `CMyData` Usa il `AssertValid` meccanismo per testare la validità degli oggetti archiviati nel proprio membro dati. Eseguire l'override `AssertValid` dei `CMyData` richiama le `ASSERT_VALID` macro per il proprio variabile membro m_pDataList.  

 Verifica della validità non termina a questo livello, poiché la classe `CObList` sovrascrive anche `AssertValid`. Questa sostituzione consente di eseguire validità aggiuntive sullo stato interno dell'elenco di test. Di conseguenza, una validità di test in un `CMyData` oggetto conduce a test di validità aggiuntive per gli stati interni della stored `CObList` oggetto elenco.  

 Con altre operazioni, è possibile aggiungere i test di validità per il `CPerson` gli oggetti archiviati anche nell'elenco. È possibile derivare una classe `CPersonList` dal `CObList` ed eseguire l'override `AssertValid`. Eseguire l'override viene chiamato `CObject::AssertValid` e quindi scorrere l'elenco, la chiamata `AssertValid` in ogni `CPerson` oggetto archiviato nell'elenco. Il `CPerson` esegue l'override di classe illustrata all'inizio di questo argomento già `AssertValid`.  

 Questo è un meccanismo efficace quando si compila per il debug. Quando si compila in seguito per la versione, il meccanismo viene disattivato automaticamente.  

### <a name="BKMK_Limitations_of_AssertValid"></a> Limitazioni di AssertValid  
 Generazione di un'asserzione indica che l'oggetto non è corretto e l'esecuzione verrà interrotta. Tuttavia, una mancanza di asserzione indica solo che è stato rilevato alcun problema, ma l'oggetto non è garantito a essere valido.  

 [In questo argomento](#BKMK_In_this_topic)  

## <a name="BKMK_Using_assertions"></a> Utilizzo di asserzioni  

### <a name="BKMK_Catching_logic_errors"></a> Rilevamento di errori per la logica  
 È possibile impostare un'asserzione a una condizione che deve essere true in base alla logica del programma. L'asserzione non ha alcun effetto a meno che non si verifica un errore per la logica.  

 Ad esempio, si supponga che è una simulazione molecole gas in un contenitore, mentre la variabile `numMols` rappresenta il numero totale delle molecole. Questo numero non può essere minore di zero, pertanto è possibile includere un'istruzione di asserzione MFC simile al seguente:  

```  
ASSERT(numMols >= 0);  

```  

 In alternativa, è possibile includere un'asserzione di CRT simile al seguente:  

```  
_ASSERT(numMols >= 0);  
```  

 Queste istruzioni non esegue alcuna operazione se il programma è in esecuzione correttamente. Se a causa un errore per la logica `numMols` per essere minore di zero, tuttavia, l'asserzione arresta l'esecuzione del programma e viene visualizzato il [finestra di dialogo non è stato possibile asserzione](../debugger/assertion-failed-dialog-box.md).  

 [In questo argomento](#BKMK_In_this_topic)  

### <a name="BKMK_Checking_results_"></a> Verifica i risultati  
 Le asserzioni risultano utili per operazioni quali i risultati non sono evidenti da un esame visivo rapido di test.  

 Ad esempio, si consideri il codice seguente, che aggiorna la variabile `iMols` basata sul contenuto dell'elenco collegato a cui punta `mols`:  

```  
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

 Il numero delle molecole conteggiati mediante `iMols` deve essere sempre minore o uguale al numero totale delle molecole, `numMols`. Esame visivo del ciclo non viene visualizzato che verrà necessariamente essere questo il caso, in modo che un'istruzione di asserzione viene utilizzata dopo il ciclo per verificare se tale condizione.  

 [In questo argomento](#BKMK_In_this_topic)  

### <a name="BKMK_Testing_error_conditions_"></a> Errori di ricerca non gestita  
 È possibile usare le asserzioni per verificare le condizioni di errore in un punto nel codice in cui gli eventuali errori devono sono stati gestiti. Nell'esempio seguente, una routine grafica restituisce un codice di errore o zero per l'esito positivo.  

```  
myErr = myGraphRoutine(a, b);  

/* Code to handle errors and  
   reset myErr if successful */  

ASSERT(!myErr); -- MFC version  
_ASSERT(!myErr); -- CRT version  
```  

 Se il codice di gestione degli errori funziona correttamente, l'errore deve essere gestito e `myErr` Reimposta su zero prima che venga raggiunto l'asserzione. Se `myErr` dispone di un altro valore, l'asserzione ha esito negativo, il programma verrà interrotto e il [finestra di dialogo non è stato possibile asserzione](../debugger/assertion-failed-dialog-box.md) viene visualizzata.  

 Le istruzioni di asserzione non sostituiscono il codice di gestione degli errori, tuttavia sono. Nell'esempio seguente viene illustrata un'istruzione di asserzione che può causare problemi nel codice della versione finale:  

```  
myErr = myGraphRoutine(a, b);  

/* No Code to handle errors */  

ASSERT(!myErr); // Don't do this!  
_ASSERT(!myErr); // Don't do this, either!  
```  

 Questo codice si basa sull'istruzione di asserzione per gestire la condizione di errore. Di conseguenza, qualsiasi codice di errore restituito da `myGraphRoutine` risulterà non gestito nel codice della versione finale.  

 [In questo argomento](#BKMK_In_this_topic)  

## <a name="see-also"></a>Vedere anche  
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Debug del codice nativo](../debugger/debugging-native-code.md)   
 [Asserzioni nel codice gestito](../debugger/assertions-in-managed-code.md)
