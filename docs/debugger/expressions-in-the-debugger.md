---
title: Espressioni nel debugger | Microsoft Docs
description: Informazioni sulle espressioni del linguaggio non supportate dagli analizzatori di espressioni nel debugger Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 08/24/2021
ms.topic: conceptual
f1_keywords:
- vs.debug.expressions
helpviewer_keywords:
- expressions [debugger]
- debugging [Visual Studio], expressions
- expression evaluation, debugger evaluator
- native expression evaluation
- expression evaluators
- debugger, evaluating expressions
- debugging [Visual Studio], expression evaluation
- debugging [Visual Studio], variable evaluation
ms.assetid: 70f9b531-44c7-4d77-980d-5eddbf2bff41
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 7db52fff8d2e952c0f0d591845d0c644e8212e3f
ms.sourcegitcommit: aef3e3f99e022675d339b7fe381cb37202be5be2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2021
ms.locfileid: "122785949"
---
# <a name="expressions-in-the-visual-studio-debugger"></a>Espressioni nel debugger Visual Studio
Il debugger di Visual Studio include analizzatori di espressioni che vengono usati quando si immette un'espressione nella finestra di dialogo **Controllo immediato** , nella finestra **Espressioni di controllo** o **Immediato** . Gli analizzatori di espressioni vengono inoltre usati nella finestra **Punti di interruzione** e in molte altre posizioni all'interno del debugger.

Nelle sezioni seguenti vengono descritte le limitazioni della valutazione delle espressioni per i linguaggi supportati da Visual Studio.

## <a name="f-expressions-are-not-supported"></a>Le espressioni F# non sono supportate
Le espressioni F# non sono riconosciute. Se si esegue il debug del codice F#, è necessario tradurre le espressioni nella sintassi C# prima di immetterle in una finestra o finestra di dialogo del debugger. Quando si traducono espressioni da F# a C#, tenere presente che C# usa l'operatore `==` per verificare l'uguaglianza, mentre F# usa il segno `=`singolo.

## <a name="c-expressions"></a>Espressioni C++
Per informazioni sull'uso degli operatori di contesto con le espressioni in C++, vedere [Context Operator (C++)](../debugger/context-operator-cpp.md).

### <a name="unsupported-expressions-in-c"></a>Espressioni non supportate in C#

#### <a name="constructors-destructors-and-conversions"></a>Costruttori, distruttori e conversioni
Non è possibile chiamare un costruttore o distruttore per un oggetto, né in modo esplicito, né in modo implicito. La seguente espressione, ad esempio, chiama in modo esplicito un costruttore e genera un messaggio di errore:

```C++
my_date( 2, 3, 1985 )
```

Se la destinazione della conversione è una classe, non è possibile chiamare una funzione di conversione. Tale conversione comporta la costruzione di un oggetto. Se, ad esempio, `myFraction` è un'istanza di `CFraction`che definisce l'operatore della funzione di conversione `FixedPoint`, la seguente espressione genera un errore:

```C++
(FixedPoint)myFraction
```

Non è possibile chiamare gli operatori new o delete. Non è ad esempio supportata l'espressione seguente:

```C++
new Date(2,3,1985)
```

#### <a name="preprocessor-macros"></a>Macro del preprocessore
Le macro del preprocessore non sono supportate nel debugger. Ad esempio, se una costante `VALUE` viene dichiarata come `#define VALUE 3`, non è possibile usare `VALUE` nella finestra **Espressioni di controllo** . Per evitare questa limitazione, sostituire `#define`con enumerazioni e funzioni quando possibile.

### <a name="using-namespace-declarations"></a>uso delle dichiarazioni dello spazio dei nomi
Non è possibile usare le dichiarazioni `using namespace` .  Per accedere a una variabile o a un nome di tipo all'esterno di spazio dei nomi corrente, è necessario usare il nome completo.

### <a name="anonymous-namespaces"></a>Spazi dei nomi anonimi
Gli spazi dei nomi anonimi non sono supportati. In presenza del codice seguente, non è possibile aggiungere `test` alla finestra Espressioni di controllo:

```C++
namespace mars
{
    namespace
    {
        int test = 0;
    }
}
int main()
{
    // Adding a watch on test does not work.
    mars::test++;
    return 0;
}

```

### <a name="using-debugger-intrinsic-functions-to-maintain-state"></a><a name="BKMK_Using_debugger_intrinisic_functions_to_maintain_state"></a> Uso di funzioni intrinseche del debugger per mantenere lo stato
Le funzioni intrinseche del debugger consentono di chiamare alcune funzioni C/C++ nelle espressioni senza modificare lo stato dell'applicazione.

Funzioni intrinseche del debugger:

- Garantite come sicure: l'esecuzione di una funzione intrinseca del debugger non danneggia il processo sottoposto a debug.

- Consentite in tutte le espressioni, anche negli scenari in cui gli effetti collaterali e la valutazione delle funzioni non sono consentiti.

- Supportate negli scenari in cui le chiamate a funzioni regolari non sono possibili, ad esempio il debug di un minidump.

  Le funzioni intrinseche del debugger rendono più pratica la valutazione delle espressioni. Ad esempio, è molto più facile scrivere `strncmp(str, "asd")` in una condizione del punto di interruzione piuttosto che `str[0] == 'a' && str[1] == 's' && str[2] == 'd'`. )

|Area|Funzioni intrinseche|
|----------|-------------------------|
|**Lunghezza delle stringhe**|[strlen, wcslen](/cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l), [strnlen, wcsnlen](/cpp/c-runtime-library/reference/strnlen-strnlen-s)|
|**Confronto di stringhe**|[strcmp, wcscmp](/cpp/c-runtime-library/reference/strcmp-wcscmp-mbscmp), [stricmp, wcsicmp](/cpp/c-runtime-library/reference/stricmp-wcsicmp), [_stricmp, _strcmpi, _wcsicmp, _wcscmpi](/cpp/c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l), [strncmp, wcsncmp](/cpp/c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l), [strnicmp, wcsnicmp](/cpp/c-runtime-library/reference/strnicmp-wcsnicmp), [_strnicmp, _wcsnicmp](/cpp/c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l)|
|**Ricerca di stringhe**|[strchr, wcschr](/cpp/c-runtime-library/reference/strchr-wcschr-mbschr-mbschr-l), [memchr, wmemchr](/cpp/c-runtime-library/reference/memchr-wmemchr), [strstr, wcsstr](/cpp/c-runtime-library/reference/strstr-wcsstr-mbsstr-mbsstr-l)|
|**Win32**|[CoDecodeProxy,](/windows/win32/api/combaseapi/nf-combaseapi-codecodeproxy) [DecodePointer,](/previous-versions/bb432242(v=vs.85)) [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror), [TlsGetValue](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsgetvalue)|
|**Windows 8**|[RoInspectCapturedStackBackTrace,](/windows/win32/api/roerrorapi/nf-roerrorapi-roinspectcapturedstackbacktrace) [WindowsCompareStringOrdinal,](/windows/win32/api/winstring/nf-winstring-windowscomparestringordinal) [WindowsGetStringLen,](/windows/win32/api/winstring/nf-winstring-windowsgetstringlen) [WindowsGetStringRawBuffer](/windows/win32/api/winstring/nf-winstring-windowsgetstringrawbuffer)<br /><br /> Queste funzioni richiedono che il processo sottoposto a debug sia eseguito in Windows 8. Il debug dei file dump generati da un dispositivo Windows 8 richiede inoltre che nel computer Visual Studio sia eseguito Windows 8. Tuttavia, se si esegue il debug di un dispositivo Windows 8 in modalità remota, nel computer Visual Studio può essere eseguito Windows 7.<br />`WindowsGetStringLen`e `WindowsGetStringRawBuffer` vengono usati solo dal motore di esecuzione (edizione Enterprise) a livello di origine.|
|**Varie**|**__log2:** restituisce il logasto in base 2 di un intero specificato, arrotondato all'intero inferiore più vicino.<br /><br />**__findNonNull:** esegue la ricerca in una matrice di puntatori, restituisce l'indice del primo elemento non Null.<br />- Parametri: (1) Puntatore al primo elemento nella matrice (void *), (2) Dimensione della matrice (unsigned int). <br /> - Valori restituiti: (1) indice in base 0 del primo elemento non Null nella matrice o -1 se non viene trovato. <br /> <br /> **DecodeHString** - Funzione helper per formattare il valore di HSTRING. Espulsa il valore HSTRING dallo stack, inserisce i byte di una struttura StringInfo che il edizione Enterprise può usare per indicare dove si trova la stringa. Viene usato solo internamente dal edizione Enterprise; non è disponibile per la chiamata diretta da parte dell'utente.<br /><br />**DecodeWinRTRestrictedException:** decodifica un'eccezione con restrizioni WinRT per ottenere la descrizione con restrizioni.<br />- Parametri: (1) caratteri di una stringa con terminazione Null che rappresenta la stringa di riferimento con restrizioni.<br />- Valore restituito: caratteri di una stringa con terminazione Null contenente il messaggio di errore effettivo da visualizzare.<br /><br />**DynamicCast:** implementa dynamic_cast.<br />- Parametri: (1) Puntatore all'oggetto di cui eseguire il cast.<br />- Elementi di dati: un oggetto CDynamicCastData deve essere associato come elemento di dati all'istruzione ExecuteIntrinsic() corrispondente. L'elemento dati codifica il tipo da e verso il quale si sta eseguendo il cast, nonché se si sta valutando o meno un'espressione natvis (necessaria per la diagnostica per interrompere la ricorsione infinita).<br />- Valore restituito: (1) Puntatore all'oggetto, cast al tipo corretto o NULL se l'oggetto di cui eseguire il cast non è un'istanza del tipo corretto.<br /><br />**DynamicMemberLookup** : funzione helper per ottenere dinamicamente il valore di un membro di classe<br /><br />**GetEnvBlockLength:** funzione helper per ottenere la lunghezza di un blocco di ambiente, in caratteri.  Usato per $env.<br /><br />**Stdext_HashMap_Int_OperatorBracket_idx** - Operator[] per stdext::hash_map.  Presuppone la funzione hash predefinita con una chiave 'int'.  Restituisce il valore. L'operatore intrinseco [] supporta solo il recupero di elementi esistenti dalla tabella hash. Non supporta l'inserimento di nuovi elementi nella tabella, perché ciò potrebbe comportare complessità indesiderate, ad esempio l'allocazione di memoria.  È tuttavia possibile usare operator[] per modificare il valore associato a una chiave già presente nella tabella.<br />- Parametri dello stack: (1) Indirizzo dell'oggetto stdext::hash_map, (2) Chiave nella tabella (int), (3) struttura HashMapPdb che specifica gli offset di campo dei membri necessari all'implementazione della funzione per eseguire la ricerca.  Questa operazione è necessaria perché l'accesso diretto ai simboli non è disponibile sul lato remoto.<br />- Valori restituiti: (1) Se la chiave è nella tabella, l'indirizzo del valore che corrisponde alla chiave.  In caso contrario, NULL.<br /><br />**Std_UnorderedMap_Int_OperatorBracket_idx** - std::unordered_map funziona allo stesso modo di stdext::hash_map, ad eccezione del fatto che la funzione hash è diversa.<br /><br />**ConcurrencyArray_OperatorBracket_idx** // Concurrency::array<>::operator[index<>] e operator(index<>)<br /><br />**ConcurrencyArray_OperatorBracket_int** // Concurrency::array<>::operator(int, int, ...)<br /><br />**ConcurrencyArray_OperatorBracket_tidx** // Concurrency::array<>::operator[tiled_index<>] e operator(tiled_index<>)<br /><br />**ConcurrencyArrayView_OperatorBracket_idx** // Concurrency::array_view<>::operator[index<>] e operator(index<>)<br /><br />**ConcurrencyArrayView_OperatorBracket_int** // Concurrency::array_view<>::operator(int, int, ...)<br /><br />**ConcurrencyArrayView_OperatorBracket_tidx** // Concurrency::array_view<>::operator[tiled_index<>] e operator(tiled_index<>)<br /><br />**TreeTraverse_Init:** inizializza un nuovo attraversamento della struttura ad albero. <br />- Parametri dello stack: (1) Indirizzo del nodo radice, (2) Suggerimento per la profondità massima da usare.  Gli elementi con una profondità superiore a questo vengono spostati in una coda per un'elaborazione successiva.<br />- Parametri di subroutine: (1) validità del nodo (facoltativo).<br />- Valori restituiti: (1) Sequenza opaca di byte che codifica lo stato dell'attraversamento dell'albero.<br /><br />**TreeTraverse_Next:** recupera i nodi da un attraversamento dell'albero in sospeso.<br />- Parametri dello stack: (1) Matrice di byte opaca che rappresenta lo stato dell'attraversamento dell'albero, (2) Numero di nodi da recuperare.<br />- Parametri delle subroutine (devono corrispondere alla chiamata a TreeTraverse_Init()): (1) figlio sinistro, (2) figlio destro, (3) validità del nodo (facoltativo).<br />- Valori restituiti: (1) Numero di nodi recuperati (Nota: inserito dopo i nodi stessi, in modo che possa essere estratto per primo). Se è stato recuperato un numero di nodi inferiore a quello richiesto, significa che la fine dell'albero. (2) Per ogni nodo recuperato, l'indirizzo del nodo. (3) Sequenza opaca di byte che codifica il nuovo stato dell'attraversamento dell'albero<br /><br />**TreeTraverse_Skip:** ignora i nodi in un attraversamento dell'albero in sospeso.<br />- Parametri dello stack: (1) Matrice di byte opaca che rappresenta lo stato dell'attraversamento dell'albero, (2) Numero di nodi da ignorare.<br />- Parametri subroutine (devono corrispondere alle chiamate successive a Next() sullo stesso enumeratore): (1) figlio sinistro, (2) figlio destro, (3) validità del nodo (facoltativo).<br />- Valori restituiti: (1) Numero di elementi effettivamente ignorati (potrebbe essere inferiore a quello richiesto), (2) Sequenza opaca di byte che codifica il nuovo stato dell'attraversamento dell'albero|

## <a name="ccli---unsupported-expressions"></a>C++/CLI - Espressioni non supportate

- I cast che coinvolgono puntatori o i cast definiti dall'utente non sono supportati.

- Il confronto e l'assegnazione di oggetti non sono supportati.

- Gli operatori di overload di e le funzioni in overload non sono supportati.

- Le conversioni boxing e unboxing non sono supportate.

- L'operatore`Sizeof` non è supportato.

## <a name="c---unsupported-expressions"></a>C# - Espressioni non supportate

### <a name="dynamic-objects"></a>Oggetti dinamici
Nelle espressioni del debugger è possibile usare variabili tipizzate staticamente come dinamiche. Quando gli oggetti che <xref:System.Dynamic.IDynamicMetaObjectProvider> implementano vengono valutati nel finestra Espressioni di controllo, viene aggiunto un nodo Di visualizzazione dinamica. Il nodo Visualizzazione dinamica mostra i membri dell'oggetto, ma non consente la modifica dei valori dei membri.

Le funzionalità seguenti degli oggetti dinamici non sono supportate:

- Gli operatori composti `+=`, `-=`, `%=`, `/=`e `*=`

- Molti cast, inclusi cast numerici e cast dell'argomento di tipo

- Chiamate al metodo con più di due argomenti

- Metodi Get di proprietà con più di due argomenti

- Metodi set di proprietà con argomenti

- Assegnazione a un indicizzatore

- Operatori booleani `&&` e `||`

### <a name="anonymous-methods"></a>Metodi anonimi
La creazione di nuovi metodi anonimi non è supportata.

## <a name="visual-basic---unsupported-expressions"></a>Visual Basic - Espressioni non supportate

### <a name="dynamic-objects"></a>Oggetti dinamici
Nelle espressioni del debugger è possibile usare variabili tipizzate staticamente come dinamiche. Quando gli oggetti che implementano <xref:System.Dynamic.IDynamicMetaObjectProvider> vengono valutati nella finestra Espressioni di controllo, viene aggiunto un nodo Visualizzazione dinamica. Il nodo Visualizzazione dinamica mostra i membri dell'oggetto, ma non consente la modifica dei valori dei membri.

Le funzionalità seguenti degli oggetti dinamici non sono supportate:

- Gli operatori composti `+=`, `-=`, `%=`, `/=`e `*=`

- Molti cast, inclusi cast numerici e cast dell'argomento di tipo

- Chiamate al metodo con più di due argomenti

- Metodi Get di proprietà con più di due argomenti

- Metodi set di proprietà con argomenti

- Assegnazione a un indicizzatore

- Operatori booleani `&&` e `||`

### <a name="local-constants"></a>Costanti locali
Le costanti locali non sono supportate.

### <a name="import-aliases"></a>Alias di importazione
Gli alias di importazione non sono supportati.

### <a name="variable-declarations"></a>Dichiarazione di variabili
Non è possibile dichiarare nuove variabili esplicite nelle finestre del debugger. È invece possibile assegnare un valore a una variabile implicita nella finestra **Controllo immediato** . Queste variabili implicite hanno un ambito limitato alla sessione di debug e non sono accessibili all'esterno del debugger. L'istruzione `o = 5` , ad esempio, crea in modo implicito una nuova variabile `o` alla quale assegna il valore 5. Tali variabili implicite sono di tipo **Object** , a meno che il tipo non possa essere dedotto dal debugger.

### <a name="unsupported-keywords"></a>Parole chiave non supportate

- `AddressOf`

- `End`

- `Error`

- `Exit`

- `Goto`

- `On Error`

- `Resume`

- `Return`

- `Select/Case`

- `Stop`

- `SyncLock`

- `Throw`

- `Try/Catch/Finally`

- `With`

- Parole chiave a livello di spazio dei nomi o di modulo, ad esempio `End Sub` o `Module`.

## <a name="see-also"></a>Vedi anche
- [Identificatori di formato in C++](../debugger/format-specifiers-in-cpp.md)
- [Operatore context (C++)](../debugger/context-operator-cpp.md)
- [Identificatori di formato in C #](../debugger/format-specifiers-in-csharp.md)
- [Pseudo variabili](../debugger/pseudovariables.md)