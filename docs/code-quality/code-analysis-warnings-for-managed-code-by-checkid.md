---
title: Panoramica delle regole di qualità del codice
ms.date: 09/01/2020
ms.topic: reference
f1_keywords:
- CA1000
- CA1001
- CA1002
- CA1003
- CA1005
- CA1008
- CA1010
- CA1012
- CS1014
- CA1016
- CA1017
- CA1018
- CA1019
- CA1021
- CA1024
- CA1027
- CA1028
- CA1029
- CA1030
- CA1031
- CA1032
- CA1033
- CA1034
- CA1036
- CA1040
- CA1041
- CA1043
- CA1044
- CA1045
- CA1046
- CA1047
- CA1050
- CA1051
- CA1052
- CA1053
- CA1054
- CA1055
- CA1056
- CA1058
- CA1060
- CA1061
- CA1062
- CA1063
- CA1064
- CA1065
- CA1066
- CA1067
- CA1068
- CA1069
- CA1070
- CA1200
- CA1303
- CA1304
- CA1305
- CA1307
- CA1308
- CA1309
- CA1310
- CA1401
- CA1416
- CA1417
- CA1501
- CA1502
- CA1505
- CA1506
- CA1507
- CA1508
- CA1509
- CA1700
- CA1707
- CA1708
- CA1710
- CA1711
- CA1712
- CA1713
- CA1714
- CA1715
- CA1716
- CA1717
- CA1720
- CA1721
- CA1724
- CA1725
- CA1801
- CA1802
- CA1805
- CA1806
- CA1810
- CA1812
- CA1813
- CA1814
- CA1815
- CA1816
- CA1819
- CA1820
- CA1821
- CA1822
- CA1823
- CA1824
- CA1825
- CA1826
- CA1827
- CA1828
- CA1829
- CA1830
- CA1831
- CA1832
- CA1833
- CA1834
- CA1835
- CA1836
- CA1837
- CA1838
- CA2000
- CA2002
- CA2007
- CA2008
- CA2009
- CA2011
- CA2012
- CA2013
- CA2014
- CA2015
- CA2016
- CA2100
- CA2101
- CA2109
- CA2119
- CA2153
- CA2200
- CA2201
- CA2207
- CA2208
- CA2211
- CA2213
- CA2214
- CA2215
- CA2216
- CA2217
- CA2219
- CA2225
- CA2226
- CA2227
- CA2229
- CA2231
- CA2234
- CA2235
- CA2237
- CA2241
- CA2242
- CA2243
- CA2245
- CA2246
- CA2247
- CA2248
- CA2249
- CA2300
- CA2301
- CA2302
- CA2305
- CA2310
- CA2311
- CA2312
- CA2315
- CA2321
- CA2322
- CA2326
- CA2327
- CA2328
- CA2329
- CA2330
- CA2350
- CA2351
- CA2352
- CA2353
- CA2354
- CA2355
- CA2356
- CA2361
- CA2362
- CA3001
- CA3002
- CA3003
- CA3004
- CA3005
- CA3006
- CA3007
- CA3008
- CA3009
- CA3010
- CA3011
- CA3012
- CA3061
- CA3075
- CA3076
- CA3077
- CA5347
- CA5350
- CA5351
- CA5359
- CA5360
- CA5361
- CA5362
- CA5363
- CA5364
- CA5365
- CA5366
- CA5367
- CA5368
- CA5369
- CA5370
- CA5371
- CA5372
- CA5373
- CA5374
- CA5375
- CA5376
- CA5377
- CA5378
- CA5379
- CA5380
- CA5381
- CA5382
- CA5383
- CA5384
- CA5385
- CA5386
- CA5387
- CA5388
- CA5389
- CA5390
- CA5391
- CA5392
- CA5393
- CA5394
- CA5395
- CA5397
- CA5398
- CA5399
- CA5400
- CA5401
- CA5402
- CA5403
- IL3000
- IL3001
ms.assetid: 5cb221f6-dc59-4abf-9bfa-adbd6f907f96
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 24f7dbcdd324620f2076f5fab8247c9ba99a72cb
ms.sourcegitcommit: a18c7e9b367c2f92f6e54c3eaef442775d457667
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/15/2020
ms.locfileid: "90094226"
---
# <a name="code-quality-analysis-rules-by-rule-id"></a>Regole di analisi della qualità del codice in base all'ID regola

La tabella seguente elenca le regole di analisi della qualità del codice in base all'identificatore della regola.

| ID regola | Avviso | Descrizione |
|---------| - | - |
| CA1000 | [CA1000: Non dichiarare membri statici su tipi generici](../code-quality/ca1000.md) | Quando viene chiamato un membro statico di un tipo generico, è necessario specificare l'argomento di tipo. Quando viene chiamato un membro di istanza generica che non supporta l'inferenza, è necessario specificare l'argomento tipo relativo al membro. In questi due casi, la sintassi necessaria per specificare l'argomento di tipo è diversa e può generare confusione. |
| CA1001 | [CA1001: I tipi proprietari di campi Disposable devono essere Disposable](../code-quality/ca1001.md) | Una classe dichiara e implementa un campo di istanza di tipo System.IDisposable e la classe non implementa IDisposable. Una classe che dichiara un campo IDisposable è indirettamente proprietaria di una risorsa non gestita e deve implementare l'interfaccia IDisposable. |
| CA1002 | [CA1002: Non esporre elenchi generici](../code-quality/ca1002.md) | System. Collections. Generic. list< (of \<(T> ) >) è una raccolta generica progettata per le prestazioni, non per l'ereditarietà. List, pertanto, non contiene membri virtuali. Devono invece essere esposte le raccolte generiche che sono state progettate per l'ereditarietà. |
| CA1003 | [CA1003: Usare istanze di gestori eventi generici](../code-quality/ca1003.md) |Un tipo contiene un delegato che restituisce void, la cui firma contiene due parametri (il primo è un oggetto e il secondo è un tipo assegnabile a EventArgs) e l'assembly che lo contiene è destinato a Microsoft .NET Framework 2.0. |
| CA1005 | [CA1005: Evitare un uso eccessivo di parametri nei tipi generici](../code-quality/ca1005.md) | Quanto più è alto il numero di parametri di tipo contenuti, maggiore è la difficoltà di sapere e ricordare cosa rappresenta ciascun parametro. È in genere ovvio con un parametro di tipo, come nell'elenco \<T> , e in alcuni casi con due parametri di tipo, come in Dictionary \<TKey, TValue> . Tuttavia, se il numero dei parametri di tipo è superiore a due, il livello di difficoltà sarà troppo elevato per la maggior parte degli utenti. |
| CA1008 | [CA1008: Le enumerazioni devono avere valore zero](../code-quality/ca1008.md) | Il valore predefinito di un'enumerazione non inizializzata, come altri tipi di valore, è zero. Un'enumerazione senza attributi flag definisce un membro utilizzando il valore zero in modo che il valore predefinito sia un valore valido dell'enumerazione. Se un'enumerazione a cui è applicato l'attributo FlagsAttribute definisce un membro con valore zero, il relativo nome deve essere "None" per indicare che nell'enumerazione non è stato impostato alcun valore. |
| CA1010 | [CA1010: Le raccolte devono implementare un'interfaccia generica](../code-quality/ca1010.md) | Per ampliare la possibilità di utilizzo di una raccolta, implementare una delle interfacce di raccolta generiche. La raccolta può quindi essere utilizzata per popolare tipi di raccolte generiche. |
| CA1012 | [CA1012: I tipi astratti non devono includere costruttori](../code-quality/ca1012.md) | I costruttori sui tipi astratti possono essere chiamati solo da tipi derivati. Poiché i costruttori pubblici creano istanze di un tipo e non è possibile creare istanze di un tipo astratto, per una buona progettazione non bisognerebbe creare un tipo astratto con costruttore pubblico. |
| CA1014 | [CA1014: Contrassegnare gli assembly con CLSCompliantAttribute](../code-quality/ca1014.md) | In Common Language Specification (CLS) vengono definite limitazioni di denominazione, tipi di dati e regole che gli assembly devono rispettare per poter essere utilizzati tra diversi linguaggi di programmazione. In una progettazione corretta tutti gli assembly devono indicare in modo esplicito la conformità CLS utilizzando <xref:System.CLSCompliantAttribute>. Se questo attributo non è presente in un assembly, tale assembly non è conforme. |
| CA1016 | [CA1016: Contrassegnare gli assembly con AssemblyVersionAttribute](../code-quality/ca1016.md) | .NET usa il numero di versione per identificare in modo univoco un assembly e per eseguire il binding ai tipi in assembly con nome sicuro. Il numero di versione viene utilizzato insieme ai criteri di versione ed editore. Per impostazione predefinita, le applicazioni vengono eseguite solo con la versione di assembly con cui sono state compilate. |
| CA1017 | [CA1017: Contrassegnare gli assembly con ComVisibleAttribute](../code-quality/ca1017.md) |ComVisibleAttribute determina il modo in cui i client COM accedono al codice gestito. In una buona progettazione gli assembly devono indicare in modo esplicito la visibilità COM. È possibile impostare la visibilità COM per l'intero assembly e quindi eseguirne l'override per singoli tipi e membri dei tipi. Se questo attributo non è presente, il contenuto dell'assembly è visibile ai client COM. |
| CA1018 | [CA1018: Contrassegnare gli attributi con AttributeUsageAttribute](../code-quality/ca1018.md) | Quando si definisce un attributo personalizzato, contrassegnarlo tramite AttributeUsageAttribute per indicare la posizione nel codice sorgente in cui applicare l'attributo personalizzato. Il significato e l'utilizzo previsto di un attributo ne determinano le posizioni valide nel codice. |
| CA1019 | [CA1019: Definire le funzioni di accesso per gli argomenti degli attributi](../code-quality/ca1019.md) | Gli attributi possono definire argomenti obbligatori che devono essere specificati quando si applica l'attributo a una destinazione. Sono inoltre noti come argomenti posizionali poiché vengono forniti ai costruttori di attributo come parametri posizionali. Per ogni argomento obbligatorio, l'attributo deve fornire anche una proprietà in sola lettura corrispondente in modo che il valore dell'argomento possa essere recuperato in fase di esecuzione. Gli attributi possono inoltre definire argomenti facoltativi, noti anche come argomenti denominati. Questi argomenti sono forniti ai costruttori degli attributi in base al nome e devono disporre di una proprietà in lettura e scrittura corrispondente. |
| CA1021 | [CA1021: Evitare parametri out](../code-quality/ca1021.md) | Il passaggio di tipi per riferimento (mediante out o ref) richiede esperienza nell'utilizzo dei puntatori, nonché la conoscenza delle differenze tra tipi di valore e tipi di riferimento e dei metodi di gestione con più valori restituiti. Inoltre, la differenza tra parametri out e ref non è sempre nota. |
| CA1024 | [CA1024: Usare proprietà dove appropriato](../code-quality/ca1024.md) | Un metodo pubblico o protetto presenta un nome che inizia con "Get", non accetta parametri e restituisce un valore diverso da una matrice. Il metodo presenta tutte le caratteristiche per diventare una proprietà. |
| CA1027 |[CA1027: Contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca1027.md) | Un'enumerazione è un tipo di valore che definisce un insieme di costanti denominate correlate. Applicare FlagsAttribute a un'enumerazione quando le relative costanti denominate possono essere combinate in modo significativo. |
| CA1028 | [CA1028: Le risorse di archiviazione dell'enumerazione devono essere Int32](../code-quality/ca1028.md) | Un'enumerazione è un tipo di valore che definisce un insieme di costanti denominate correlate. Per impostazione predefinita, il tipo di dati System.Int32 viene utilizzato per archiviare il valore costante. Benché sia possibile modificare il tipo sottostante, questa operazione non è necessaria né consigliata nella maggior parte degli scenari. |
| CA1030 | [CA1030: Usare eventi dove appropriato](../code-quality/ca1030.md) |Questa regola rileva i metodi che presentano nomi comunemente utilizzati per gli eventi. Se un metodo viene chiamato in risposta a una modifica dello stato chiaramente definita, il metodo deve essere richiamato da un gestore eventi. Gli oggetti che chiamano il metodo devono generare eventi anziché chiamare direttamente il metodo. |
| CA1031 | [CA1031: Non rilevare tipi di eccezione generali](../code-quality/ca1031.md) | Le eccezioni generali non devono essere rilevate. Rilevare un'eccezione più specifica oppure generare nuovamente l'eccezione generale come ultima istruzione nel blocco catch. |
| CA1032 |[CA1032: Implementare costruttori di eccezioni standard](../code-quality/ca1032.md) | Se non viene fornito l'insieme completo di costruttori può risultare difficile gestire correttamente le eccezioni. |
| CA1033 | [CA1033: I metodi di interfaccia devono essere richiamabili dai tipi figlio](../code-quality/ca1033.md) | Un tipo visibile esternamente non sealed fornisce un'implementazione di metodo esplicita di un'interfaccia pubblica e non fornisce un metodo visibile esternamente alternativo con lo stesso nome. |
| CA1034 | [CA1034: I tipi annidati non devono essere visibili](../code-quality/ca1034.md) | Un tipo annidato è un tipo dichiarato nell'ambito di un altro tipo. I tipi annidati sono utili per incapsulare dettagli di implementazione privati del tipo contenitore. I tipi annidati utilizzati per questo scopo non devono essere visibili esternamente. |
| CA1036 | [CA1036: Eseguire l'override di metodi su tipi confrontabili](../code-quality/ca1036.md) |Un tipo pubblico o protetto implementa l'interfaccia System.IComparable. Non esegue l'override di Object.Equals né l'overload dell'operatore specifico del linguaggio per uguaglianza, ineguaglianza, minore di o maggiore di. |
| CA1040 |[CA1040: Evitare l'uso di interfacce vuote](../code-quality/ca1040.md) | Le interfacce definiscono membri che forniscono un comportamento o un contratto di utilizzo. La funzionalità descritta dall'interfaccia può essere adottata da qualsiasi tipo, indipendentemente dal punto in cui il tipo è visualizzato nella gerarchia di ereditarietà. Un tipo implementa un'interfaccia fornendo implementazioni per i membri dell'interfaccia. Un'interfaccia vuota non definisce alcun membro. Di conseguenza, non definisce un contratto implementabile. |
| CA1041 | [CA1041: Specificare una proprietà ObsoleteAttribute.Message](../code-quality/ca1041.md) | Un tipo o un membro viene contrassegnato utilizzando un attributo System.ObsoleteAttribute per cui non è stata specificata la proprietà ObsoleteAttribute.Message. Quando viene compilato un membro o un tipo contrassegnato utilizzando ObsoleteAttribute, viene visualizzata la proprietà Message dell'attributo. In questo modo vengono fornite le informazioni utente sul tipo o sul membro obsoleto. |
| CA1043 | [CA1043: Usare un argomento di tipo stringa o integrale per gli indicizzatori](../code-quality/ca1043.md) | Gli indicizzatori, ovvero le proprietà indicizzate, devono utilizzare tipi integrali o stringa per l'indice. Questi tipi vengono in genere utilizzati per l'indicizzazione di strutture di dati e aumentano l'utilizzabilità della libreria. L'utilizzo del tipo Object deve essere limitato ai casi in cui non sia possibile specificare in fase di progettazione il tipo integrale o stringa. |
| CA1044 | [CA1044: Le proprietà non devono essere in sola scrittura](../code-quality/ca1044.md) | Sebbene la presenza di proprietà di sola lettura sia accettabile e spesso necessaria, le linee guida di progettazione proibiscono l'utilizzo di proprietà di sola scrittura. Ciò è dovuto al fatto che consentire a un utente di impostare un valore e quindi impedirgli di visualizzarlo, non offre alcuna sicurezza. Inoltre, senza accesso in lettura, lo stato degli oggetti condivisi non può essere visualizzato, il che ne limita l'utilità. |
| CA1045 |[CA1045: Non passare i tipi per riferimento](../code-quality/ca1045.md) | Il passaggio di tipi per riferimento (mediante out o ref) richiede esperienza nell'utilizzo dei puntatori, nonché la conoscenza delle differenze tra tipi di valore e tipi di riferimento e dei metodi di gestione con più valori restituiti. Gli architetti di librerie che progettano per i destinatari generali non dovrebbero prevedere agli utenti di usare i `out` `ref` parametri o. |
| CA1046 | [CA1046: Non eseguire l'overload dell'operatore "uguale a" per i tipi di riferimento](../code-quality/ca1046.md) | Per i tipi di riferimento, l'implementazione predefinita dell'operatore di uguaglianza è quasi sempre corretta. Per impostazione predefinita, i due riferimenti sono uguali solo se puntano allo stesso oggetto. |
| CA1047 |[CA1047: Non dichiarare membri protected nei tipi sealed](../code-quality/ca1047.md) | I tipi dichiarano membri protetti in modo che i tipi che ereditano possano accedere al membro o eseguirne l'override. Per definizione, non è possibile ereditare tipi sealed, pertanto non è possibile chiamare metodi protetti su tipi sealed. |
| CA1050 | [CA1050: Dichiarare i tipi negli spazi dei nomi](../code-quality/ca1050.md) | I tipi vengono dichiarati in spazi dei nomi per impedire conflitti di denominazione e per organizzare i tipi correlati in una gerarchia di oggetti. |
| CA1051 | [CA1051: Non dichiarare campi di istanza visibili](../code-quality/ca1051.md) | L'utilizzo principale di un campo deve essere come dettaglio di implementazione. I campi devono essere privati o interni e devono essere esposti tramite proprietà. |
| CA1052 | [CA1052: I tipi che contengono membri statici devono essere sealed](../code-quality/ca1052.md) | Un tipo pubblico o protetto contiene solo membri statici e non è dichiarato utilizzando il modificatore (NotInheritable) (Riferimenti per C#) sealed. Un tipo non adatto a essere ereditato deve essere contrassegnato utilizzando il modificatore sealed per impedire che venga utilizzato come tipo di base. |
| CA1053 |[CA1053: I tipi che contengono membri statici non devono avere costruttori](../code-quality/ca1053.md) | Un tipo pubblico o annidato dichiara solo membri statici e presenta un costruttore predefinito pubblico o protetto. Il costruttore non è necessario perché la chiamata a membri statici non richiede un'istanza del tipo. A scopo di sicurezza e protezione, l'overload dei valori di stringa deve chiamare l'overload URI tramite l'argomento stringa. |
| CA1054 | [CA1054: I parametri URI non devono essere stringhe](../code-quality/ca1054.md) | Se un metodo accetta una rappresentazione in forma di stringa di un URI, è necessario fornire un overload corrispondente che accetti un'istanza della classe URI che fornisce questi servizi in modo sicuro e protetto. |
| CA1055 | [CA1055: I valori restituiti URI non devono essere stringhe](../code-quality/ca1055.md) | Questa regola presuppone che il metodo restituisca un URI. Una rappresentazione in forma di stringa di un URI è soggetta a errori di analisi e codifica e può creare vulnerabilità nella sicurezza. La classe System.Uri fornisce questi servizi in modo sicuro e protetto. |
| CA1056 | [CA1056: Le proprietà URI non devono essere stringhe](../code-quality/ca1056.md) | Questa regola presuppone che la proprietà rappresenti un URI (Uniform Resource Identifier). Una rappresentazione in forma di stringa di un URI è soggetta a errori di analisi e codifica e può creare vulnerabilità nella sicurezza. La classe System.Uri fornisce questi servizi in modo sicuro e protetto. |
| CA1058 | [CA1058: I tipi non devono estendere tipi di base specifici](../code-quality/ca1058.md) | Un tipo visibile esternamente estende tipi di base specifici. Utilizzare una delle alternative seguenti: |
| CA1060 | [CA1060: spostare i P/Invoke nella classe NativeMethods](../code-quality/ca1060.md) | I metodi di chiamata al sistema operativo, ad esempio quelli contrassegnati utilizzando l'attributo System.Runtime.InteropServices.DllImportAttribute, o i metodi definiti mediante la parola chiave Declare in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] accedono a codice non gestito. Questi metodi devono appartenere alla classe NativeMethods, SafeNativeMethods o UnsafeNativeMethods. |
| CA1061 |[CA1061: Non nascondere i metodi di una classe base](../code-quality/ca1061.md) | Un metodo di un tipo di base è nascosto da un metodo denominato in modo identico in un tipo derivato, quando la firma del parametro del metodo derivato differisce solo per i tipi che presentano una derivazione più debole rispetto ai tipi corrispondenti nella firma del parametro del metodo di base. |
| CA1062 | [CA1062: Convalidare gli argomenti di metodi pubblici](../code-quality/ca1062.md) | È necessario che tutti gli argomenti di riferimento passati a metodi visibili esternamente vengano sottoposti a verifica per accertarsi che non corrispondano a valori Null. |
| CA1063 | [CA1063: Implementare IDisposable correttamente](../code-quality/ca1063.md) | È necessario che tutti i tipi IDisposable implementino correttamente il modello Dispose. |
| CA1064 | [CA1064: Le eccezioni devono essere pubbliche](../code-quality/ca1064.md) | Un'eccezione interna è visibile solo nel relativo ambito interno. Se l'eccezione si verifica al di fuori dell'ambito interno, può essere rilevata solo tramite l'eccezione di base. Se l'eccezione interna viene ereditata da <xref:System.Exception> , <xref:System.SystemException> o <xref:System.ApplicationException> , il codice esterno non disporrà di informazioni sufficienti per sapere cosa fare con l'eccezione. |
| CA1065 | [CA1065: Non generare eccezioni in posizioni non previste](../code-quality/ca1065.md) | Un metodo che normalmente non genera eccezioni genera un'eccezione. |
| Ca1066 | [CA1066: Implementare IEquatable quando si esegue l'override di Equals](../code-quality/ca1066.md) | Un tipo di valore esegue l'override del <xref:System.Object.Equals%2A> metodo, ma non implementa <xref:System.IEquatable%601> . |
| CA1067 | [CA1067: Esegue l'override di Equals quando si implementa IEquatable](../code-quality/ca1067.md) | Un tipo implementa <xref:System.IEquatable%601> , ma non esegue l'override del <xref:System.Object.Equals%2A> metodo. |
| CA1068 | [CA1068: I parametri CancellationToken devono essere indicati per ultimi](../code-quality/ca1068.md) | Un metodo ha un parametro CancellationToken che non è l'ultimo parametro. |
| Ca1069 | [CA1069: Le enumerazioni non devono contenere valori duplicati](../code-quality/ca1069.md) | Un'enumerazione dispone di più membri a cui viene assegnato in modo esplicito lo stesso valore costante. |
| Ca1070 | [CA1070: Non dichiarare i campi evento come virtuali](../code-quality/ca1070.md) | Un [evento di tipo campo](/dotnet/csharp/language-reference/language-specification/classes#field-like-events) è stato dichiarato come virtuale. |
| Ca1200 | [CA1200: Evitare l'uso di tag cref con un prefisso](../code-quality/ca1200.md) | L'attributo [cref](/dotnet/csharp/programming-guide/xmldoc/cref-attribute) in un tag di documentazione XML significa "riferimento al codice". Specifica che il testo all'interno del tag è un elemento di codice, ad esempio un tipo, un metodo o una proprietà. Evitare di usare `cref` i tag con i prefissi, perché impedisce al compilatore di verificare i riferimenti. Impedisce inoltre a Visual Studio Integrated Development Environment (IDE) di trovare e aggiornare questi riferimenti ai simboli durante i refactoring. |
| CA1303 | [CA1303: Non passare valori letterali come parametri localizzati](../code-quality/ca1303.md) | Un metodo visibile esternamente passa un valore letterale stringa come parametro a un metodo o un costruttore .NET e tale stringa deve essere localizzabile. |
| CA1304 | [CA1304: Specificare CultureInfo](../code-quality/ca1304.md) | Un metodo o un costruttore chiama un membro che presenta un overload che accetta un parametro System.Globalization.CultureInfo e tale metodo o costruttore non chiama l'overload che accetta il parametro CultureInfo. Quando non viene fornito un oggetto CultureInfo o System.IFormatProvider, il valore predefinito fornito dal membro di overload potrebbe non avere l'effetto desiderato in tutte le impostazioni locali. |
| CA1305 | [CA1305: Specificare IFormatProvider](../code-quality/ca1305.md) | Un metodo o un costruttore chiama uno o più membri con overload che accettano un parametro System.IFormatProvider e tale metodo o costruttore non chiama l'overload che accetta il parametro IFormatProvider. Quando non viene fornito un oggetto System.Globalization.CultureInfo o IFormatProvider, il valore predefinito fornito dal membro di overload potrebbe non avere l'effetto desiderato in tutte le impostazioni locali. |
| CA1307 | [CA1307: Specificare StringComparison per la chiarezza](../code-quality/ca1307.md) | Un'operazione di confronto tra stringhe utilizza un overload del metodo che non imposta un parametro StringComparison. |
| CA1308 |[CA1308: Normalizzare le stringhe in lettere maiuscole](../code-quality/ca1308.md) | Le stringhe devono essere normalizzate in maiuscolo. Un piccolo gruppo di caratteri non è in grado di completare un round trip in caso di conversione in lettere minuscole. |
| CA1309 | [CA1309: Usare StringComparison ordinale](../code-quality/ca1309.md) | In un'operazione di confronto tra stringhe di tipo non linguistico il parametro StringComparison non viene impostato su Ordinal o OrdinalIgnoreCase. L'impostazione esplicita del parametro su StringComparison.Ordinal o StringComparison.OrdinalIgnoreCase consente spesso di rendere il codice più veloce, corretto e affidabile. |
| Ca1310 | [CA1310: Specificare StringComparison per la correttezza](../code-quality/ca1310.md) | Un'operazione di confronto tra stringhe usa un overload del metodo che non imposta un parametro StringComparison e usa il confronto di stringhe specifico delle impostazioni cultura per impostazione predefinita. |
| CA1401 | [CA1401: i P/Invoke non devono essere visibili](../code-quality/ca1401.md) | Un metodo pubblico o protetto in un tipo pubblico presenta l'attributo System.Runtime.InteropServices.DllImportAttribute (implementato anche dalla parola chiave Declare in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Questi metodi non devono essere esposti. |
| CA1416 | [CA1416: convalida della compatibilità della piattaforma](../code-quality/ca1416.md) | L'uso di API dipendenti dalla piattaforma su un componente rende il codice non più funzionante in tutte le piattaforme. |
| Ca1417 | [Ca1417: non usare `OutAttribute` nei parametri di stringa per P/Invoke](../code-quality/ca1417.md) | I parametri stringa passati per valore con `OutAttribute` possono destabilizzare il runtime se la stringa è una stringa interna. |
| CA1501 | [CA1501: Evitare ereditarietà eccessiva](../code-quality/ca1501.md) | Un tipo si trova oltre il quarto livello di annidamento nella gerarchia di ereditarietà. Le gerarchie di tipi eccessivamente annidate possono comportare difficoltà di comprensione e gestione. |
| CA1502 | [CA1502: Evitare complessità eccessiva](../code-quality/ca1502.md) | Questa regola misura il numero di percorsi linearmente indipendenti tramite il metodo, determinato dal numero e dalla complessità di rami condizionali. |
| CA1505 | [CA1505: Evitare codice non gestibile](../code-quality/ca1505.md) | Un tipo o metodo presenta un valore di indice di gestibilità basso. Un indice di manutenibilità basso indica che un tipo o un metodo è probabilmente difficile da gestire e sarebbe un buon candidato per la riprogettazione. |
| CA1506 | [CA1506: Evitare un numero eccessivo di accoppiamenti tra classi](../code-quality/ca1506.md) | Questa regola misura l'accoppiamento tra classi contando il numero di riferimenti al tipo univoci contenuti in un tipo o metodo. |
| Ca1507 | [CA1507: Usare nameof invece della stringa](../code-quality/ca1507.md) | Un valore letterale stringa viene usato come argomento in cui è `nameof` possibile usare un'espressione. |
| Ca1508 | [CA1508: Evitare codice di condizione non utilizzato](../code-quality/ca1508.md) | Un metodo ha codice condizionale che restituisce sempre `true` o `false` in fase di esecuzione. In questo modo viene creato codice non attivo nel `false` ramo della condizione. |
| Ca1509 | [CA1509: Voce non valida nel file di configurazione della metrica del codice](../code-quality/ca1509.md) | Le regole della metrica del codice, ad esempio [CA1501](ca1501.md), [CA1502](ca1502.md), [CA1505](ca1505.md) e [CA1506](ca1506.md), hanno fornito un file di configurazione denominato `CodeMetricsConfig.txt` con una voce non valida. |
| CA1700 | [CA1700: Non denominare 'Reserved' i valori di enumerazione](../code-quality/ca1700.md) | Questa regola presuppone che un membro di enumerazione con un nome che contiene la parola "reserved" non sia attualmente utilizzato, ma sia un segnaposto che dovrà essere rinominato o rimosso in una versione futura. La ridenominazione o rimozione di un membro è ritenuta una modifica sostanziale. |
| CA1707 | [CA1707: Gli identificatori non devono contenere caratteri di sottolineatura](../code-quality/ca1707.md) | Per convenzione i nomi degli identificatori non contengono il carattere di sottolineatura (_). In base a questa regola vengono controllati spazi dei nomi, tipi, membri e parametri. |
| CA1708 | [CA1708: Gli identificatori non si devono differenziare solo in base alle maiuscole e minuscole](../code-quality/ca1708.md) | Gli identificatori per spazi dei nomi, tipi, membri e parametri non possono differire solo in base a maiuscole e minuscole poiché ai linguaggi destinati a Common Language Runtime non è richiesta la distinzione tra maiuscole e minuscole. |
| CA1710 | [CA1710: Gli identificatori devono contenere il suffisso corretto](../code-quality/ca1710.md) |Per convenzione, i nomi dei tipi che estendono determinati tipi di base o implementano determinate interfacce o dei tipi derivati da questi tipi contengono un suffisso associato al tipo di base o all'interfaccia. |
| CA1711 | [CA1711: Gli identificatori non devono contenere un suffisso non corretto](../code-quality/ca1711.md) | Per convenzione, solo i nomi dei tipi che estendono determinati tipi di base o che implementano determinate interfacce o dei tipi derivati da questi tipi devono terminare con suffissi specifici riservati. Gli altri nomi di tipi non devono utilizzare questi suffissi riservati. |
| CA1712 | [CA1712: Non usare nomi di tipo come prefisso nei valori di enumerazione](../code-quality/ca1712.md) | I nomi dei membri di enumerazione non hanno come prefisso il nome del tipo poiché si prevede che le informazioni sul tipo vengano fornite dagli strumenti di sviluppo. |
| CA1713 | [CA1713: Non usare il prefisso Before o After negli eventi](../code-quality/ca1713.md) | Il nome di un evento inizia con "Before" o "After". Per denominare eventi correlati generati in una sequenza specifica, utilizzare i tempi verbali presente o passato per indicare la posizione relativa nella sequenza di azioni. |
| CA1714 | [CA1714: Le enumerazioni con Flags devono avere nomi plurali](../code-quality/ca1714.md) | Un'enumerazione pubblica dispone dell'attributo System.FlagsAttribute e il nome non termina per "s". Ai tipi contrassegnati utilizzando FlagsAttribute sono assegnati nomi plurali perché tale attributo indica che è possibile specificare più valori. |
| CA1715 | [CA1715: Gli identificatori devono contenere il prefisso corretto](../code-quality/ca1715.md) | Il nome di un'interfaccia visibile esternamente non inizia con una "I" maiuscola. Il nome di un parametro di tipo generico su un tipo o metodo visibile esternamente non inizia con una "T" maiuscola. |
| CA1716 | [CA1716: Gli identificatori non devono corrispondere a parole chiave](../code-quality/ca1716.md) | Un nome di spazio dei nomi o di tipo corrisponde a una parola chiave riservata in un linguaggio di programmazione. Gli identificatori di spazi dei nomi e tipi non devono corrispondere a parole chiave definite dai linguaggi con destinazione Common Language Runtime. |
| CA1717 | [CA1717: Solo le enumerazioni con FlagsAttribute devono avere nomi plurali](../code-quality/ca1717.md) | In base alle convenzioni di denominazione, un nome plurale in un'enumerazione indica che è possibile specificare più valori di enumerazione contemporaneamente. |
| CA1720 |[CA1720: Gli identificatori non devono contenere nomi di tipo](../code-quality/ca1720.md) | Il nome di un parametro in un membro visibile esternamente contiene un nome di tipo di dati oppure il nome di un membro visibile esternamente contiene un nome di tipo di dati specifico del linguaggio. |
| CA1721 | [CA1721: I nomi delle proprietà non devono corrispondere ai metodi get](../code-quality/ca1721.md) |Il nome di un membro pubblico o protetto inizia con "Get" e corrisponde in altro modo al nome di una proprietà pubblica o protetta. I metodi "Get" e le proprietà devono avere nomi indicano chiaramente la distinzione tra le funzioni. |
| CA1724 | [CA1724: I nomi dei tipi non devono corrispondere agli spazi dei nomi](../code-quality/ca1724.md) | I nomi dei tipi non devono corrispondere ai nomi degli spazi dei nomi .NET. La violazione di questa regola può ridurre l'utilizzabilità della libreria. |
| CA1725 | [CA1725: I nomi dei parametri devono corrispondere alla dichiarazione di base](../code-quality/ca1725.md) | Una denominazione coerente dei parametri in una gerarchia di override aumenta la funzionalità degli override di metodo. Un nome di parametro in un metodo derivato diverso dal nome nella dichiarazione di base può provocare confusione sulla natura del metodo, ovvero se si tratta di un override del metodo di base o di un nuovo overload del metodo. |
| CA1801 | [CA1801: Controllare i parametri non usati](../code-quality/ca1801.md) | Una firma di metodo include un parametro non utilizzato nel corpo del metodo. |
| CA1802 |[CA1802: Utilizza valori letterali dove appropriato](../code-quality/ca1802.md) |Un campo viene dichiarato static e read-only (Shared e ReadOnly in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) e viene inizializzato utilizzando un valore calcolabile in fase di compilazione. Poiché il valore assegnato al campo di destinazione è calcolabile in fase di compilazione, modificare la dichiarazione in un campo const (const in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ) in modo che il valore venga calcolato in fase di compilazione anziché in fase di esecuzione. |
| CA1805 | [CA1805: Non eseguire inutilmente l'inizializzazione](../code-quality/ca1805.md) | Il Runtime .NET Inizializza tutti i campi dei tipi di riferimento sui rispettivi valori predefiniti prima di eseguire il costruttore. Nella maggior parte dei casi, l'inizializzazione esplicita di un campo sul valore predefinito è ridondante, che aumenta i costi di manutenzione e può influire negativamente sulle prestazioni, ad esempio con una maggiore dimensione dell'assembly. |
| CA1806 | [CA1806: Non ignorare i risultati dei metodi](../code-quality/ca1806.md) | Un nuovo oggetto viene creato, ma non viene mai utilizzato oppure viene chiamato un metodo che crea e restituisce una nuova stringa e la nuova stringa non viene mai utilizzata oppure un metodo COM o P/Invoke restituisce un HRESULT o un codice di errore che non viene mai utilizzato. |
| CA1810 | [CA1810: Inizializzare i campi statici del tipo di riferimento inline](../code-quality/ca1810.md) | Quando un tipo dichiara un costruttore statico esplicito, tramite il compilatore JIT (Just-In-Time) viene aggiunto un controllo a ogni metodo statico del tipo e a ogni costruttore di istanza del tipo per assicurare che il costruttore statico sia stato precedentemente chiamato. I controlli dei costruttori statici possono ridurre le prestazioni. |
| CA1812 | [CA1812: Evitare classi interne prive di istanze](../code-quality/ca1812.md) | Un'istanza di un tipo a livello di assembly non viene creata dal codice nell'assembly. |
| CA1813 | [CA1813: Evitare attributi unsealed](../code-quality/ca1813.md) | .NET fornisce metodi per il recupero di attributi personalizzati. Per impostazione predefinita, questi metodi eseguono ricerche nella gerarchia di ereditarietà dell'attributo. L'utilizzo di attributi sealed elimina la ricerca nella gerarchia di ereditarietà e può migliorare le prestazioni. |
| CA1814 | [CA1814: Preferire matrici di matrici rispetto a matrici multidimensionali](../code-quality/ca1814.md) | Una matrice di matrici è una matrice i cui elementi sono costituiti da matrici. Poiché le matrici che costituiscono gli elementi possono presentare dimensioni diverse, la quantità di spazio inutilizzato sarà inferiore per alcuni insiemi di dati. |
| CA1815 | [CA1815: Eseguire l'override di Equals e dell'operatore "uguale a" sui tipi di valore](../code-quality/ca1815.md) | Per i tipi di valore, l'implementazione ereditata di Equals utilizza la libreria Reflection e confronta il contenuto di tutti i campi. La libreria Reflection è onerosa dal punto di vista del calcolo, inoltre il confronto di ogni campo per determinarne l'uguaglianza potrebbe essere superfluo. Se si prevede che gli utenti confrontino o ordinino le istanze oppure le utilizzino come chiavi di tabelle hash, il tipo di valore deve implementare Equals. |
| CA1816 | [CA1816: Chiamare GC.SuppressFinalize correttamente](../code-quality/ca1816.md) | Un metodo che costituisce un'implementazione di Dispose non chiama GC.SuppressFinalize oppure un metodo che non costituisce un'implementazione di Dispose chiama GC.SuppressFinalize oppure un metodo chiama GC.SuppressFinalize e passa un elemento diverso da this (Me in Visual Basic). |
| CA1819 | [CA1819: Le proprietà non devono restituire matrici](../code-quality/ca1819.md) | Le matrici restituite dalle proprietà non sono protette in scrittura, anche se la proprietà è in sola lettura. Affinché la matrice sia protetta da eventuali alterazioni, la proprietà deve restituire una copia della matrice. In genere, gli utenti non comprendono le implicazioni negative sulle prestazioni derivanti dalla chiamata di tale proprietà. |
| CA1820 | [CA1820: Testare le stringhe vuote usando la lunghezza di stringa](../code-quality/ca1820.md) | Il confronto tra stringhe mediante la proprietà String.Length o il metodo String.IsNullOrEmpty è notevolmente più veloce rispetto all'utilizzo di Equals. |
| CA1821 | [CA1821: Rimuovere i finalizzatori vuoti](../code-quality/ca1821.md) | Quando possibile, evitare di utilizzare i finalizzatori per non sovraccaricare ulteriormente le prestazioni durante il rilevamento della durata dell'oggetto. Un finalizzatore vuoto provoca un sovraccarico aggiuntivo e non fornisce alcun vantaggio. |
| CA1822 |[CA1822: Contrassegna i membri come statici](../code-quality/ca1822.md) | I membri che non accedono ai dati di istanza o non chiamano metodi di istanza possono essere contrassegnati come static (Shared in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Tramite il compilatore verranno quindi inviati siti di chiamata non virtuali a tali membri. Si potrà così ottenere un sensibile miglioramento delle prestazioni per codici sensibili alle prestazioni. |
| CA1823 | [CA1823: Evitare campi privati non usati](../code-quality/ca1823.md) | Sono stati rilevati campi privati che non sembrano essere utilizzati all'interno dell'assembly. |
| CA1824 |[CA1824: Contrassegnare gli assembly con NeutralResourcesLanguageAttribute](../code-quality/ca1824.md) | L'attributo NeutralResourcesLanguage informa Gestione risorse della lingua utilizzata per visualizzare le risorse di impostazioni cultura non associate ad alcun paese per un assembly. Tale approccio migliora le prestazioni delle ricerche per la prima risorsa caricata e riduce il working set. |
| Ca1825 |[CA1825: Evitare allocazioni di matrici di lunghezza zero](../code-quality/ca1825.md) | L'inizializzazione di una matrice di lunghezza zero comporta l'allocazione di memoria non necessaria. Usare invece l'istanza di matrice vuota allocata in modo statico chiamando <xref:System.Array.Empty%2A?displayProperty=nameWithType> . L'allocazione di memoria è condivisa tra tutte le chiamate di questo metodo. |
| Ca1826 |[CA1826: Usare la proprietà anziché il metodo Enumerable LINQ](../code-quality/ca1826.md) | <xref:System.Linq.Enumerable> Il metodo LINQ è stato usato in un tipo che supporta una proprietà equivalente e più efficiente. |
| Ca1827 |[CA1827: Non usare Count/LongCount se è possibile usare Any](../code-quality/ca1827.md) | <xref:System.Linq.Enumerable.Count%2A><xref:System.Linq.Enumerable.LongCount%2A>è stato usato il metodo o dove il <xref:System.Linq.Enumerable.Any%2A> metodo risulta più efficiente. |
| Ca1828 |[CA1828: Non usare CountAsync/LongCountAsync se è possibile usare AnyAsync](../code-quality/ca1828.md) | <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.CountAsync%2A><xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.LongCountAsync%2A>è stato usato il metodo o dove il <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.AnyAsync%2A> metodo risulta più efficiente. |
| Ca1829 |[CA1829: Usare la proprietà Length/Count invece del metodo Enumerable.Count](../code-quality/ca1829.md) | <xref:System.Linq.Enumerable.Count%2A> Il metodo LINQ è stato usato in un tipo che supporta una proprietà equivalente, più efficiente `Length` o `Count` . |
| Ca1830 |[CA1830: Preferire gli overload di metodi Append e Insert fortemente tipizzati su StringBuilder](../code-quality/ca1830.md) | <xref:System.Text.StringBuilder.Append%2A> e <xref:System.Text.StringBuilder.Insert%2A> forniscono overload per più tipi oltre <xref:System.String> .  Quando possibile, preferire gli overload fortemente tipizzati sull'utilizzo di ToString () e dell'overload basato su stringa. |
| Ca1831 |[CA1831: Usare AsSpan invece di indicizzatori basati su Range per la stringa quando appropriato](../code-quality/ca1831.md) | Quando si usa un indicizzatore di intervallo in una stringa e si assegna in modo implicito il valore al &lt; tipo char ReadOnlySpan &gt; , <xref:System.String.Substring%2A?#System_String_Substring_System_Int32_System_Int32_> viene usato il metodo anziché <xref:System.Span%601.Slice%2A?#System_Span_1_Slice_System_Int32_System_Int32_> , che produce una copia della parte richiesta della stringa. |
| Ca1832 |[CA1832: Usare AsSpan o AsMemory invece di indicizzatori basati su Range per ottenere la parte ReadOnlySpan o ReadOnlyMemory di una matrice](../code-quality/ca1832.md) | Quando si usa un indicizzatore di intervallo in una matrice e si assegna in modo implicito il valore a un <xref:System.ReadOnlySpan%601> <xref:System.ReadOnlyMemory%601> tipo o, <xref:System.Runtime.CompilerServices.RuntimeHelpers.GetSubArray%2A> viene usato il metodo anziché <xref:System.Span%601.Slice%2A?#System_Span_1_Slice_System_Int32_System_Int32_> , che produce una copia della parte richiesta della matrice. |
| Ca1833 |[CA1833: Usare AsSpan o AsMemory invece di indicizzatori basati su Range per ottenere la parte Span o Memory di una matrice](../code-quality/ca1833.md) | Quando si usa un indicizzatore di intervallo in una matrice e si assegna in modo implicito il valore a un <xref:System.Span%601> <xref:System.Memory%601> tipo o, <xref:System.Runtime.CompilerServices.RuntimeHelpers.GetSubArray%2A> viene usato il metodo anziché <xref:System.Span%601.Slice%2A?#System_Span_1_Slice_System_Int32_System_Int32_> , che produce una copia della parte richiesta della matrice. |
| Ca1834 |[CA1834: Usare StringBuilder.Append(char) per le stringhe di caratteri singoli](../code-quality/ca1834.md) | <xref:System.Text.StringBuilder> ha un `Append` Overload che accetta `char` come argomento. Preferire la chiamata dell' `char` Overload per motivi di prestazioni. |
| Ca1835 |[Ca1835: preferisce gli overload basati su Memory'per ' ReadAsync ' è WriteAsync '](../code-quality/ca1835.md) | ' Stream ' ha un overload ' ReadAsync ' che accetta un' &lt; byte &gt; di memoria ' come primo argomento e un overload ' WriteAsync ' che accetta un'ReadOnlyMemory &lt; byte &gt; ' come primo argomento. Preferisci chiamare gli overload basati sulla memoria, che sono più efficienti. |
| Ca1836 |[Ca1836: preferenza `IsEmpty` rispetto a `Count` quando disponibile](../code-quality/ca1836.md) | Preferisci `IsEmpty` la proprietà che è più efficiente di `Count` , `Length` <xref:System.Linq.Enumerable.Count%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> o <xref:System.Linq.Enumerable.LongCount%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> per determinare se l'oggetto contiene o meno elementi. |
| Ca1837 | [Ca1837: usare `Environment.ProcessId` anziché `Process.GetCurrentProcess().Id`](../code-quality/ca1837.md) | `Environment.ProcessId` è più semplice e veloce di `Process.GetCurrentProcess().Id` . |
| Ca1838 | [Ca1838: evitare `StringBuilder` i parametri per P/Invoke](../code-quality/ca1838.md) | Il marshalling di ' StringBuilder ' Crea sempre una copia del buffer nativa, ottenendo più allocazioni per un'operazione di marshalling. |
| CA2000 | [CA2000: Eliminare gli oggetti prima che siano esterni all'ambito](../code-quality/ca2000.md) | Poiché è possibile che si verifichi un evento eccezionale che impedisca l'esecuzione del finalizzatore di un oggetto, è opportuno eliminare in modo esplicito l'oggetto prima che tutti i riferimenti a tale oggetto siano esterni all'ambito. |
| CA2002 |[CA2002: Non bloccare oggetti con identità debole](../code-quality/ca2002.md) |Un oggetto presenta un'identità debole quando è possibile accedere ad esso direttamente attraverso i confini dei domini applicazione. Un thread che tenta di acquisire un blocco su un oggetto con identità debole può essere bloccato da un secondo thread in un altro dominio applicazione con un blocco sullo stesso oggetto. |
| Ca2007 | [CA2007: Non attendere direttamente un'attività](ca2007.md) | Un metodo asincrono [attende](/dotnet/csharp/language-reference/keywords/await) direttamente un oggetto <xref:System.Threading.Tasks.Task> . Quando un metodo asincrono attende direttamente un oggetto <xref:System.Threading.Tasks.Task> , la continuazione viene eseguita nello stesso thread che ha creato l'attività. Questo comportamento può essere oneroso in termini di prestazioni e può causare un deadlock sul thread UI. Prendere <xref:System.Threading.Tasks.Task.ConfigureAwait(System.Boolean)?displayProperty=nameWithType> in considerazione la chiamata a per segnalare l'intenzione di continuare. |
| Ca2008 | [CA2008: Non creare attività senza passare un elemento TaskScheduler](ca2008.md) | Un'operazione di creazione o di continuazione di un'attività utilizza un overload del metodo che non specifica un <xref:System.Threading.Tasks.TaskScheduler> parametro. |
| Ca2009 | [CA2009: Non chiamare ToImmutableCollection su un valore ImmutableCollection](ca2009.md) | `ToImmutable` il metodo è stato chiamato inutilmente su una raccolta non modificabile dallo <xref:System.Collections.Immutable> spazio dei nomi. |
| Ca2011 | [CA2011: Non assegnare la proprietà all'interno del relativo setter](ca2011.md) | Una proprietà è stata assegnata per errore a un valore all'interno della relativa [funzione di accesso set](/dotnet/csharp/programming-guide/classes-and-structs/using-properties#the-set-accessor). |
| Ca2012 | [CA2012: Usare correttamente gli elementi ValueTask](ca2012.md) | ValueTasks restituiti dalle chiamate ai membri devono essere direttamente in attesa.  Il tentativo di utilizzare un ValueTask più volte o di accedere direttamente a un risultato prima che sia noto come completato può causare un'eccezione o un danneggiamento.  Ignorare un ValueTask di questo tipo è probabilmente un'indicazione di un bug funzionale e potrebbe influire negativamente sulle prestazioni. |
| Ca2013 | [CA2013: Non usare ReferenceEquals con tipi valore](ca2013.md) | Quando si confrontano i valori usando <xref:System.Object.ReferenceEquals%2A?displayProperty=fullName> , se objA e objB sono tipi di valore, vengono sottoposte a Boxing prima di essere passati al <xref:System.Object.ReferenceEquals%2A> metodo. Ciò significa che, anche se objA e objB rappresentano la stessa istanza di un tipo di valore, il <xref:System.Object.ReferenceEquals%2A> metodo restituisce comunque false. |
| Ca2014 | [Ca2014: non usare stackalloc nei cicli.](ca2014.md) | Lo spazio dello stack allocato da un stackalloc viene rilasciato solo alla fine della chiamata del metodo corrente.  L'uso in un ciclo può comportare una crescita non vincolata dello stack e le condizioni di overflow dello stack. |
| Ca2015 | [Ca2015: non definire finalizzatori per i tipi derivati da MemoryManager &lt; T&gt;](ca2015.md) | L'aggiunta di un finalizzatore a un tipo derivato da <xref:System.Buffers.MemoryManager%601> può consentire la liberazione della memoria mentre è ancora in uso da un oggetto <xref:System.Span%601> . |
| Ca2016 | [CA2016: Inoltrare il parametro CancellationToken ai metodi che ne accettano uno](ca2016.md) | Inoltrare il `CancellationToken` parametro ai metodi che ne accettano uno per assicurarsi che le notifiche di annullamento dell'operazione vengano propagate correttamente oppure passare in `CancellationToken.None` modo esplicito per indicare che il token non viene propagato intenzionalmente. |
| CA2100 | [CA2100: Controllare la vulnerabilità della sicurezza nelle query SQL](../code-quality/ca2100.md) | Un metodo imposta la proprietà System.Data.IDbCommand.CommandText usando una stringa compilata da un argomento stringa nel metodo. La regola presuppone che l'argomento stringa contenga l'input dell'utente. Una stringa di comando SQL compilata da un input dell'utente è vulnerabile agli attacchi intrusivi nel codice SQL, |
| CA2101 |[CA2101: specificare il marshalling per gli argomenti di stringa P/Invoke](../code-quality/ca2101.md) | Un membro di platform invoke consente i chiamanti parzialmente attendibili, presenta un parametro di stringa e non effettua il marshalling della stringa. Questo può comportare una potenziale vulnerabilità di sicurezza. |
| CA2109 | [CA2109: Controllare i gestori di eventi visibili](../code-quality/ca2109.md) | È stato rilevato un metodo di gestione eventi pubblico o protetto. I metodi di gestione eventi non devono essere esposti se non assolutamente necessario. |
| CA2119 | [CA2119: Impostare come sealed i metodi che soddisfano interfacce private](../code-quality/ca2119.md) | Un tipo pubblico ereditabile fornisce un'implementazione di metodo sottoponibile a override di un'interfaccia interna (Friend in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Per correggere una violazione di questa regola, impedire che venga eseguito l'override del metodo esternamente all'assembly. |
| CA2153 |[CA2153: evitare la gestione delle eccezioni di stato danneggiate](../code-quality/ca2153.md) | Le eccezioni di stato danneggiate (CSEs) indicano che nel processo è presente un danneggiamento della memoria. Se si prova a intercettare tali eccezioni, invece di lasciare che il processo venga arrestato in modo anomalo, può portare a vulnerabilità di sicurezza nel caso in cui un utente malintenzionato riesca a inserire un exploit nell'area della memoria danneggiata. |
| CA2200 | [CA2200: Eseguire il rethrow per mantenere i dettagli dello stack](../code-quality/ca2200.md) | Viene generata di nuovo un'eccezione, specificata in modo esplicito nell'istruzione throw. Se un'eccezione viene generata di nuovo tramite la specifica nell'istruzione throw, l'elenco di chiamate ai metodi tra il metodo originale che ha generato l'eccezione e il metodo corrente viene perso. |
| CA2201 | [CA2201: Non generare tipi di eccezione riservati](../code-quality/ca2201.md) | Tale circostanza complica il rilevamento e il debug dell'errore originale. |
| CA2207 | [CA2207: Inizializzare i campi statici dei tipi di valore inline](../code-quality/ca2207.md) | Un tipo di valore dichiara un costruttore statico esplicito. Per correggere una violazione di questa regola, inizializzare tutti i dati statici quando vengono dichiarati e rimuovere il costruttore statico. |
| CA2208 |[CA2208: Creare istanze di eccezioni di argomento correttamente](../code-quality/ca2208.md) | Viene effettuata una chiamata al costruttore predefinito (senza parametri) di un tipo di eccezione che corrisponde a o deriva da ArgumentException oppure viene passato un argomento stringa non corretto a un costruttore con parametri di un tipo di eccezione che corrisponde a o deriva da ArgumentException. |
| CA2211 |[CA2211: I campi non costanti non devono essere visibili](../code-quality/ca2211.md) | I campi statici che non sono costanti né in sola lettura non sono thread-safe. L'accesso a tali campi deve essere controllato attentamente e richiede tecniche di programmazione avanzate per la sincronizzazione dell'accesso all'oggetto classe. |
| CA2213 | [CA2213: I campi eliminabili devono essere eliminati](../code-quality/ca2213.md) | Un tipo che implementa System.IDisposable dichiara i campi di tipi che implementano anch'essi IDisposable. Il metodo Dispose del campo non viene chiamato dal metodo Dispose del tipo dichiarante. |
| CA2214 | [CA2214: Non chiamare metodi sottoponibili a override nei costruttori](../code-quality/ca2214.md) | Quando un costruttore chiama un metodo virtuale, è possibile che il costruttore per l'istanza che richiama il metodo non sia stato eseguito. |
| CA2215 | [CA2215: I metodi Dispose devono chiamare Dispose della classe di base](../code-quality/ca2215.md) | Se un tipo eredita da un tipo eliminabile, deve chiamare il metodo Dispose del tipo di base dal proprio metodo Dispose. |
| CA2216 |[CA2216: I tipi eliminabili devono dichiarare un finalizzatore](../code-quality/ca2216.md) | Un tipo che implementa System.IDisposable e include campi che suggeriscono l'utilizzo di risorse non gestite non implementa un finalizzatore, come descritto da Object.Finalize. |
| CA2217 | [CA2217: Non contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca2217.md) |Un'enumerazione visibile esternamente è contrassegnata utilizzando FlagsAttribute e presenta uno o più valori che non sono potenze di due o una combinazione degli altri valori definiti nell'enumerazione. |
| CA2219 | [CA2219: Non generare eccezioni in clausole di eccezione](../code-quality/ca2219.md) | Quando un'eccezione viene generata in una clausola finally o in una clausola fault, la nuova eccezione nasconde l'eccezione attiva. Quando un'eccezione viene generata in una clausola filter, il runtime rileva l'eccezione automaticamente. Tale circostanza complica il rilevamento e il debug dell'errore originale. |
| CA2225 | [CA2225: Gli overload degli operatori hanno alternative con nome](../code-quality/ca2225.md) |È stato rilevato un overload di operatore e il metodo alternativo denominato previsto non è stato trovato. Il membro alternativo denominato fornisce accesso alla stessa funzionalità dell'operatore e viene fornito per gli sviluppatori che programmano in linguaggi che non supportano operatori di overload. |
| CA2226 | [CA2226: Gli operatori devono avere overload simmetrici](../code-quality/ca2226.md) | Un tipo implementa l'operatore di uguaglianza o di disuguaglianza e non implementa l'operatore opposto. |
| CA2227 |[CA2227: Le proprietà di raccolte devono essere in sola lettura](../code-quality/ca2227.md) |Una proprietà di raccolta scrivibile consente a un utente di sostituire la raccolta con una raccolta diversa. Una proprietà di sola lettura interrompe la sostituzione della raccolta ma consente ancora l'impostazione dei singoli membri. |
| CA2229 | [CA2229: Implementare costruttori di serializzazione](../code-quality/ca2229.md) | Per correggere una violazione di questa regola, implementare il costruttore di serializzazione. Per una classe sealed, rendere il costruttore privato; in caso contrario renderlo protetto. |
| CA2231 | [CA2231: Eseguire l'overload dell'operatore "uguale a" all'override di ValueType.Equals](../code-quality/ca2231.md) | Un tipo di valore esegue l'override di Object.Equals, ma non implementa l'operatore di uguaglianza. |
| CA2234 | [CA2234: Passare oggetti System.Uri invece di stringhe](../code-quality/ca2234.md) | Viene effettuata una chiamata a un metodo che dispone di un parametro di stringa il cui nome contiene "uri", "URI", "urn", "URN", "url" o "URL". Il tipo dichiarante del metodo contiene un overload del metodo corrispondente con un parametro System.Uri. |
| CA2235 | [CA2235: Contrassegnare tutti i campi non serializzabili](../code-quality/ca2235.md) | Un campo di istanza di un tipo non serializzabile viene dichiarato in un tipo serializzabile. |
| CA2237 | [CA2237: Contrassegnare i tipi ISerializable con SerializableAttribute](../code-quality/ca2237.md) | Affinché i tipi vengano riconosciuti come serializzabili in Common Language Runtime, è necessario che siano contrassegnati utilizzando l'attributo SerializableAttribute anche quando utilizzano una routine di serializzazione personalizzata tramite l'implementazione dell'interfaccia ISerializable. |
| CA2241 | [CA2241: Specificare argomenti corretti ai metodi di formattazione](../code-quality/ca2241.md) | L'argomento format passato a System.String.Format non contiene un elemento di formato corrispondente a ogni argomento dell'oggetto o viceversa. |
| CA2242 |[CA2242: Testare i valori NaN in modo corretto](../code-quality/ca2242.md) | Questa espressione consente di testare un valore rispetto a Single.Nan o Double.Nan. Utilizzare Single.IsNan(Single) o Double.IsNan(Double) per testare il valore. |
| CA2243 |[CA2243: I valori letterali stringa di attributo devono essere analizzati correttamente](../code-quality/ca2243.md) | Il parametro del valore letterale stringa di un attributo non esegue l'analisi corretta di un URL, un GUID o una versione. |
| CA2244 | [CA2244: Non duplicare inizializzazioni di elementi indicizzati](../code-quality/ca2244.md) | Un inizializzatore di oggetto ha più di un inizializzatore di elemento indicizzato con lo stesso indice costante. Tutti tranne l'ultimo inizializzatore sono ridondanti. |
| CA2245 | [CA2245: Non assegnare una proprietà a se stessa](../code-quality/ca2245.md) | Una proprietà è stata assegnata per errore a se stessa. |
| CA2246 | [CA2246: Non assegnare un simbolo e il relativo membro nella stessa istruzione](../code-quality/ca2246.md) | Non è consigliabile assegnare un simbolo e il relativo membro, ovvero un campo o una proprietà, nella stessa istruzione. Non è chiaro se l'accesso ai membri fosse destinato a usare il valore precedente del simbolo prima dell'assegnazione o del nuovo valore dall'assegnazione in questa istruzione. |
| CA2247 | [CA2247: l'argomento passato al Costruttore TaskCompletionSource deve essere TaskCreationOptions enum anziché TaskContinuationOptions enum.](../code-quality/ca2247.md) | TaskCompletionSource dispone di costruttori che accettano TaskCreationOptions che controllano l'attività sottostante e i costruttori che accettano lo stato dell'oggetto archiviato nell'attività.  Se si passa accidentalmente un TaskContinuationOptions anziché un TaskCreationOptions, la chiamata tratta le opzioni come stato. |
| CA2248 | [CA2248: Specificare l'argomento enum corretto per Enum.HasFlag](../code-quality/ca2248.md) | Il tipo enum passato come argomento alla chiamata al `HasFlag` metodo è diverso dal tipo enum chiamante. |
| CA2249 | [CA2249: Provare a usare String.Contains invece di String.IndexOf](../code-quality/ca2249.md) | Le chiamate a in `string.IndexOf` cui viene usato il risultato per verificare la presenza o l'assenza di una sottostringa possono essere sostituite da `string.Contains` . |
| Ca2300 | [CA2300: Non usare il deserializzatore non sicuro BinaryFormatter](../code-quality/ca2300.md) | I deserializzatori non sicuri sono vulnerabili durante la deserializzazione di dati non attendibili. Un utente malintenzionato potrebbe modificare i dati serializzati per includere tipi imprevisti per inserire oggetti con effetti collaterali dannosi. |
| CA2301 | [CA2301: Non chiamare BinaryFormatter.Deserialize senza aver prima impostato BinaryFormatter.Binder](../code-quality/ca2301.md) | I deserializzatori non sicuri sono vulnerabili durante la deserializzazione di dati non attendibili. Un utente malintenzionato potrebbe modificare i dati serializzati per includere tipi imprevisti per inserire oggetti con effetti collaterali dannosi. |
| CA2302 | [CA2302: Assicurarsi che BinaryFormatter.Binder sia impostato prima di chiamare BinaryFormatter.Deserialize](../code-quality/ca2302.md) | I deserializzatori non sicuri sono vulnerabili durante la deserializzazione di dati non attendibili. Un utente malintenzionato potrebbe modificare i dati serializzati per includere tipi imprevisti per inserire oggetti con effetti collaterali dannosi. |
| CA2305 | [CA2305: Non usare il deserializzatore non sicuro LosFormatter](../code-quality/ca2305.md) | I deserializzatori non sicuri sono vulnerabili durante la deserializzazione di dati non attendibili. Un utente malintenzionato potrebbe modificare i dati serializzati per includere tipi imprevisti per inserire oggetti con effetti collaterali dannosi. |
| CA2310 | [CA2310: Non usare il deserializzatore non sicuro NetDataContractSerializer](../code-quality/ca2310.md) | I deserializzatori non sicuri sono vulnerabili durante la deserializzazione di dati non attendibili. Un utente malintenzionato potrebbe modificare i dati serializzati per includere tipi imprevisti per inserire oggetti con effetti collaterali dannosi. |
| CA2311 | [CA2311: Non eseguire la deserializzazione senza aver prima impostato NetDataContractSerializer.Binder](../code-quality/ca2311.md) | I deserializzatori non sicuri sono vulnerabili durante la deserializzazione di dati non attendibili. Un utente malintenzionato potrebbe modificare i dati serializzati per includere tipi imprevisti per inserire oggetti con effetti collaterali dannosi. |
| CA2312 | [CA2312: Assicurarsi di impostare NetDataContractSerializer.Binder prima della deserializzazione](../code-quality/ca2312.md) | I deserializzatori non sicuri sono vulnerabili durante la deserializzazione di dati non attendibili. Un utente malintenzionato potrebbe modificare i dati serializzati per includere tipi imprevisti per inserire oggetti con effetti collaterali dannosi. |
| CA2315 | [CA2315: Non usare il deserializzatore non sicuro ObjectStateFormatter](../code-quality/ca2315.md) | I deserializzatori non sicuri sono vulnerabili durante la deserializzazione di dati non attendibili. Un utente malintenzionato potrebbe modificare i dati serializzati per includere tipi imprevisti per inserire oggetti con effetti collaterali dannosi. |
| CA2321 | [CA2321: Non eseguire la deserializzazione con JavaScriptSerializer usando un oggetto SimpleTypeResolver](../code-quality/ca2321.md) | I deserializzatori non sicuri sono vulnerabili durante la deserializzazione di dati non attendibili. Un utente malintenzionato potrebbe modificare i dati serializzati per includere tipi imprevisti per inserire oggetti con effetti collaterali dannosi. |
| CA2322 | [CA2322: Verificare che l'oggetto JavaScriptSerializer non sia inizializzato con SimpleTypeResolver prima di eseguire la deserializzazione](../code-quality/ca2322.md) | I deserializzatori non sicuri sono vulnerabili durante la deserializzazione di dati non attendibili. Un utente malintenzionato potrebbe modificare i dati serializzati per includere tipi imprevisti per inserire oggetti con effetti collaterali dannosi. |
| CA2326 | [CA2326: Non usare valori di TypeNameHandling diversi da None](../code-quality/ca2326.md) | I deserializzatori non sicuri sono vulnerabili durante la deserializzazione di dati non attendibili. Un utente malintenzionato potrebbe modificare i dati serializzati per includere tipi imprevisti per inserire oggetti con effetti collaterali dannosi. |
| CA2327 | [CA2327: Non usare oggetti JsonSerializerSettings non sicuri](../code-quality/ca2327.md) | I deserializzatori non sicuri sono vulnerabili durante la deserializzazione di dati non attendibili. Un utente malintenzionato potrebbe modificare i dati serializzati per includere tipi imprevisti per inserire oggetti con effetti collaterali dannosi. |
| CA2328 | [CA2328: Assicurarsi che gli oggetti JsonSerializerSettings siano sicuri](../code-quality/ca2328.md) | I deserializzatori non sicuri sono vulnerabili durante la deserializzazione di dati non attendibili. Un utente malintenzionato potrebbe modificare i dati serializzati per includere tipi imprevisti per inserire oggetti con effetti collaterali dannosi. |
| CA2329 | [CA2329: Non eseguire la deserializzazione con JsonSerializer usando una configurazione non sicura](../code-quality/ca2329.md) | I deserializzatori non sicuri sono vulnerabili durante la deserializzazione di dati non attendibili. Un utente malintenzionato potrebbe modificare i dati serializzati per includere tipi imprevisti per inserire oggetti con effetti collaterali dannosi. |
| CA2330 | [CA2330: Assicurarsi che JsonSerializer abbia una configurazione sicura durante la deserializzazione](../code-quality/ca2330.md) | I deserializzatori non sicuri sono vulnerabili durante la deserializzazione di dati non attendibili. Un utente malintenzionato potrebbe modificare i dati serializzati per includere tipi imprevisti per inserire oggetti con effetti collaterali dannosi. |
| CA2350 | [CA2350: Verificare che l'input di DataTable.ReadXml() sia attendibile](ca2350.md) | Quando si deserializza un oggetto <xref:System.Data.DataTable> con un input non attendibile, un utente malintenzionato può creare input dannosi per eseguire un attacco Denial of Service. Potrebbero esserci vulnerabilità di esecuzione del codice remoto sconosciute. |
| CA2351 | [CA2351: Verificare che l'input di DataSet.ReadXml() sia attendibile](ca2351.md) | Quando si deserializza un oggetto <xref:System.Data.DataSet> con un input non attendibile, un utente malintenzionato può creare input dannosi per eseguire un attacco Denial of Service. Potrebbero esserci vulnerabilità di esecuzione del codice remoto sconosciute. |
| CA2352 | [CA2352: Un elemento DataSet o DataTable non sicuro nel tipo serializzabile può essere vulnerabile agli attacchi di esecuzione di codice remoto](ca2352.md) | Una classe o uno struct contrassegnato con <xref:System.SerializableAttribute> contiene una <xref:System.Data.DataSet> proprietà o un campo o <xref:System.Data.DataTable> e non dispone di un oggetto <xref:System.CodeDom.Compiler.GeneratedCodeAttribute> . |
| CA2353 | [CA2353: Elemento DataSet o DataTable non sicuro in un tipo serializzabile](ca2353.md) | Una classe o uno struct contrassegnato con un attributo di serializzazione XML o un attributo di contratto dati contiene un campo o una <xref:System.Data.DataSet> <xref:System.Data.DataTable> Proprietà. |
| CA2354 | [CA2354: Un elemento DataSet o DataTable non sicuro nel grafico di oggetti deserializzato può essere vulnerabile agli attacchi di esecuzione di codice remoto](ca2354.md) | La deserializzazione con un <xref:System.Runtime.Serialization.IFormatter?displayProperty=nameWithType> oggetto serializzato e l'oggetto grafico del tipo con cast possono includere un oggetto <xref:System.Data.DataSet> o <xref:System.Data.DataTable> . |
| CA2355 | [CA2355: Elemento DataSet o DataTable non sicuro nel grafico di oggetti deserializzato](ca2355.md) | Deserializzazione quando l'oggetto grafico del tipo sottoposto a cast o specificato può includere <xref:System.Data.DataSet> o <xref:System.Data.DataTable> . |
| CA2356 | [CA2356: DataSet o DataTable non sicuro nell'oggetto grafico deserializzato Web](ca2356.md) | Un metodo con un oggetto <xref:System.Web.Services.WebMethodAttribute?displayProperty=nameWithType> o <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> ha un parametro che può fare riferimento a <xref:System.Data.DataSet> o <xref:System.Data.DataTable> . |
| CA2361 | [CA2361: Assicurarsi che la classe generata automaticamente che contiene DataSet.ReadXml() non venga usata con dati non attendibili](ca2361.md) | Quando si deserializza un oggetto <xref:System.Data.DataSet> con un input non attendibile, un utente malintenzionato può creare input dannosi per eseguire un attacco Denial of Service. Potrebbero esserci vulnerabilità di esecuzione del codice remoto sconosciute. |
| CA2362 | [CA2362: L'oggetto DataSet o DataTable non sicuro nel tipo serializzabile generato automaticamente può essere vulnerabile ad attacchi di tipo esecuzione di codice remoto](ca2362.md) | Quando si deserializza un input non attendibile con <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> e l'oggetto grafico deserializzato contiene <xref:System.Data.DataSet> o <xref:System.Data.DataTable> , un utente malintenzionato può creare un payload dannoso per eseguire un attacco di esecuzione del codice remoto. |
| CA3001 | [CA3001: Esaminare il codice per verificare la presenza di vulnerabilità di tipo SQL injection](../code-quality/ca3001.md) | Quando si utilizzano comandi SQL e input non attendibili, tenere presenti gli attacchi SQL injection. Un attacco SQL injection può eseguire comandi SQL dannosi, compromettendo la sicurezza e l'integrità dell'applicazione. |
| CA3002 | [CA3002: Esaminare il codice per verificare la presenza di vulnerabilità di tipo XSS](../code-quality/ca3002.md) | Quando si utilizza un input non attendibile da richieste Web, tenere presente gli attacchi XSS (cross-site scripting). Un attacco XSS inserisce input non attendibile nell'output HTML non elaborato, consentendo all'autore dell'attacco di eseguire script dannosi o modificare il contenuto nella pagina Web. |
| Ca3003 | [CA3003: Esaminare il codice per verificare la presenza di vulnerabilità di tipo file path injection](../code-quality/ca3003.md) | Quando si utilizza un input non attendibile da richieste Web, tenere presente l'utilizzo dell'input controllato dall'utente quando si specificano i percorsi dei file. |
| Ca3004 | [CA3004: Esaminare il codice per verificare la presenza di vulnerabilità di tipo diffusione di informazioni](../code-quality/ca3004.md) | La divulgazione delle informazioni sulle eccezioni consente agli utenti malintenzionati di comprendere le caratteristiche interne dell'applicazione, che possono aiutare gli utenti malintenzionati a trovare altre vulnerabilità da sfruttare. |
| CA3006 | [CA3006: Esaminare il codice per verificare la presenza di vulnerabilità di tipo process command injection](../code-quality/ca3006.md) | Quando si lavora con un input non attendibile, tenere presente gli attacchi di inserimento dei comandi. Un attacco injection comando può eseguire comandi dannosi sul sistema operativo sottostante, compromettendo la sicurezza e l'integrità del server. |
| CA3007 | [CA3007: Esaminare il codice per verificare la presenza di vulnerabilità di tipo reindirizzamento aperto](../code-quality/ca3007.md) | Quando si lavora con un input non attendibile, tenere presenti le vulnerabilità di reindirizzamento aperte. Un utente malintenzionato può sfruttare una vulnerabilità di reindirizzamento aperto per usare il sito Web per dare l'impressione di un URL legittimo, ma reindirizzare un visitatore ignaro a un phishing o ad altre pagine Web dannose. |
| CA3008 | [CA3008: Esaminare il codice per verificare la presenza di vulnerabilità di tipo XPath injection](../code-quality/ca3008.md) | Quando si lavora con un input non attendibile, tenere presenti gli attacchi XPath injection. La costruzione di query XPath tramite input non attendibile può consentire a un utente malintenzionato di manipolare in modo dannoso la query per restituire un risultato imprevisto ed eventualmente divulgare il contenuto dell'XML sottoposto a query. |
| CA3009 | [CA3009: Esaminare il codice per verificare la presenza di vulnerabilità di tipo XML injection](../code-quality/ca3009.md) | Quando si lavora con un input non attendibile, tenere presente gli attacchi intrusivi in XML. |
| CA3010 | [CA3010: Esaminare il codice per verificare la presenza di vulnerabilità di tipo XAML injection](../code-quality/ca3010.md) | Quando si lavora con un input non attendibile, tenere presente gli attacchi di inserimento di XAML. XAML è un linguaggio di markup che rappresenta direttamente la creazione di istanze di oggetti e la relativa esecuzione. Ciò significa che gli elementi creati in XAML possono interagire con le risorse di sistema, ad esempio l'accesso alla rete e file system i/o. |
| CA3011 | [CA3011: Esaminare il codice per verificare la presenza di vulnerabilità di tipo DLL injection](../code-quality/ca3011.md) | Quando si utilizza un input non attendibile, tenere presente il caricamento di codice non attendibile. Se l'applicazione Web carica codice non attendibile, un utente malintenzionato potrebbe essere in grado di inserire dll dannose nel processo ed eseguire codice dannoso. |
| CA3012 | [CA3012: Esaminare il codice per verificare la presenza di vulnerabilità di tipo regex injection](../code-quality/ca3012.md) | Quando si lavora con un input non attendibile, tenere presente gli attacchi di attacchi Regex. Un utente malintenzionato può utilizzare l'inserimento Regex per modificare in modo dannoso un'espressione regolare, per fare in modo che l'espressione regolare corrisponda a risultati imprevisti oppure per fare in modo che la regex utilizzi una CPU eccessiva con conseguente attacco Denial of Service. |
| CA3061 | [CA3061: Non aggiungere lo schema in base all'URL](../code-quality/ca3061.md) | Non usare l'overload unsafe del metodo Add perché potrebbe causare riferimenti esterni pericolosi. |
| CA3075 | [CA3075: Elaborazione DTD non protetta](../code-quality/ca3075.md) | Se si usano istanze di DTDProcessing non protette o si fa riferimento a origini di entità esterne, il parser può accettare un input non attendibile e divulgare informazioni riservate a utenti malintenzionati. |
| CA3076 | [CA3076: Esecuzione di script XSLT non protetta](../code-quality/ca3076.md) | Se si esegue Extensible Stylesheet Language Transformations (XSLT) in applicazioni .NET in modo non protetto, il processore può risolvere i riferimenti URI non attendibili che potrebbero divulgare informazioni riservate a utenti malintenzionati, causando attacchi Denial of Service e tra siti. |
| CA3077 | [CA3077: Elaborazione non sicura in progettazione API, documenti XML e lettori di testo XML](../code-quality/ca3077.md) | Quando si progetta un'API derivata da XMLDocument e XMLTextReader, tenere presente DtdProcessing. Se si usano istanze di DTDProcessing non protette per fare riferimento o risolvere origini di entità esterne oppure per impostare valori non protetti nel codice XML, si può causare la divulgazione di informazioni. |
| CA3147 | [CA3147: Contrassegnare i gestori di verbi con ValidateAntiForgeryToken](../code-quality/ca3147.md) | Quando si progetta un controller MVC ASP.NET, tenere presenti gli attacchi di richiesta intersito falsa. Un attacco di richiesta intersito falsificazione può inviare richieste dannose da un utente autenticato al controller MVC ASP.NET. |
| CA5350 | [CA5350: Non usare algoritmi di crittografia vulnerabili](../code-quality/ca5350.md) | Oggi si usano algoritmi di crittografia e funzioni hash deboli per diversi motivi, ma non dovrebbero essere usati per garantire la riservatezza o l'integrità dei dati che proteggono. Questa regola si attiva quando vengono rilevati algoritmi TripleDES, SHA1 o RIPEMD160 nel codice.|
| CA5351 | [CA5351: non usare algoritmi di crittografia interrotti](../code-quality/ca5351.md) | Gli algoritmi di crittografia violati non sono considerati sicuri e il loro uso è fortemente sconsigliato. Questa regola si attiva quando nel codice vengono rilevati l'algoritmo hash MD5 oppure gli algoritmi di crittografia DES o RC2. |
| CA5358 | [CA5358: Non usare modalità crittografia non sicure](../code-quality/ca5358.md) | Non usare modalità crittografia non sicure |
| CA5359 | [CA5359 non disabilitare la convalida del certificato](../code-quality/ca5359.md) | Un certificato può essere utile per autenticare l'identità del server. I client devono convalidare il certificato del server per garantire che le richieste vengano inviate al server desiderato. Se il ServerCertificateValidationCallback restituisce sempre `true` , qualsiasi certificato passerà la convalida. |
| CA5360 | [CA5360 non chiamano metodi pericolosi nella deserializzazione](../code-quality/ca5360.md) | La deserializzazione non sicura è una vulnerabilità che si verifica quando i dati non attendibili vengono usati per abusare la logica di un'applicazione, infliggendo un attacco Denial of Service (DoS) o persino eseguendo codice arbitrario al momento della deserializzazione. Spesso gli utenti malintenzionati possono usare queste funzionalità di deserializzazione quando l'applicazione deserializza dati non attendibili sotto il proprio controllo. In particolare, richiamare metodi pericolosi nel processo di deserializzazione. Gli attacchi di deserializzazione non sicuri riusciti potrebbero consentire a un utente malintenzionato di eseguire attacchi come attacchi DoS, bypass di autenticazione ed esecuzione di codice in modalità remota. |
| CA5361 | [CA5361: Non disabilitare l'uso della crittografia avanzata in Schannel](../code-quality/ca5361.md) | `Switch.System.Net.DontEnableSchUseStrongCrypto`L'impostazione di per `true` indebolisce la crittografia utilizzata nelle connessioni di Transport Layer Security in uscita (TLS). La crittografia più debole può compromettere la riservatezza delle comunicazioni tra l'applicazione e il server, semplificando l'intercettazione dei dati sensibili da parte degli utenti malintenzionati. |
| CA5362 | [CA5362 ciclo di riferimento potenziale nell'oggetto grafico deserializzato](../code-quality/ca5362.md) | In caso di deserializzazione di dati non attendibili, qualsiasi codice che elabora l'oggetto grafico deserializzato deve gestire i cicli di riferimento senza passare a cicli infiniti. Sono inclusi sia il codice che fa parte di un callback di deserializzazione che il codice che elabora l'oggetto grafico al termine della deserializzazione. In caso contrario, un utente malintenzionato potrebbe eseguire un attacco Denial of Service con dati dannosi contenenti un ciclo di riferimento. |
| CA5363 | [CA5363: Non disabilitare la convalida delle richieste](../code-quality/ca5363.md) | La convalida delle richieste è una funzionalità di ASP.NET che esamina le richieste HTTP e determina se contengono contenuti potenzialmente pericolosi che possono causare attacchi injection, incluso lo scripting tra siti. |
| CA5364 | [CA5364: Non usare protocolli di sicurezza deprecati](../code-quality/ca5364.md) | Transport Layer Security (TLS) protegge la comunicazione tra i computer, in genere con Hypertext Transfer Protocol Secure (HTTPS). Le versioni precedenti del protocollo TLS sono meno sicure di TLS 1,2 e TLS 1,3 ed è più probabile che abbiano nuove vulnerabilità. Evitare le versioni precedenti del protocollo per ridurre al minimo i rischi. |
| CA5365 | [CA5365 non disabilita il controllo dell'intestazione HTTP](../code-quality/ca5365.md) | Il controllo dell'intestazione HTTP consente la codifica dei caratteri di ritorno a capo e di nuova riga, ovvero e \n, presenti nelle intestazioni di risposta. Questa codifica può contribuire a evitare attacchi intrusivi che sfruttano un'applicazione che restituisce dati non attendibili contenuti nell'intestazione. |
| CA5366 | [CA5366 utilizzare XmlReader per il set di dati Read XML](../code-quality/ca5366.md) | L'utilizzo <xref:System.Data.DataSet> di un oggetto per la lettura di dati XML con dati non attendibili può caricare riferimenti esterni pericolosi, che devono essere limitati utilizzando un <xref:System.Xml.XmlReader> con un resolver sicuro o con l'elaborazione DTD disabilitata. |
| CA5367 | [CA5367 non serializzare i tipi con i campi puntatore](../code-quality/ca5367.md) | Questa regola consente di controllare se è presente una classe serializzabile con un campo o una proprietà del puntatore. I membri che non possono essere serializzati possono essere un puntatore, ad esempio i membri statici o i campi contrassegnati con <xref:System.NonSerializedAttribute> . |
| CA5368 | [CA5368 set ViewStateUserKey per le classi derivate dalla pagina](../code-quality/ca5368.md) | L'impostazione della proprietà consente di <xref:System.Web.UI.Page.ViewStateUserKey> impedire gli attacchi sull'applicazione consentendo di assegnare un identificatore alla variabile dello stato di visualizzazione per i singoli utenti, in modo che gli utenti malintenzionati non possano utilizzare la variabile per generare un attacco. In caso contrario, saranno presenti vulnerabilità per la richiesta tra siti falsa. |
| CA5369 | [CA5369: Usa XmlReader per la deserializzazione](../code-quality/ca5369.md) | L'elaborazione di schemi DTD e XML non attendibili può consentire il caricamento di riferimenti esterni pericolosi, che devono essere limitati utilizzando un oggetto XmlReader con un resolver sicuro oppure con la DTD e l'elaborazione dello schema inline XML disabilitata. |
| CA5370 | [CA5370: Usare XmlReader per la convalida del lettore](../code-quality/ca5370.md) | L'elaborazione di schemi DTD e XML non attendibili può consentire il caricamento di riferimenti esterni pericolosi. Questo caricamento pericoloso può essere limitato utilizzando un oggetto XmlReader con un resolver sicuro oppure con la DTD e l'elaborazione dello schema inline XML disabilitata. |
| CA5371 | [CA5371: Usa XmlReader per la lettura dello schema](../code-quality/ca5371.md) | L'elaborazione di schemi DTD e XML non attendibili può consentire il caricamento di riferimenti esterni pericolosi. L'utilizzo di un oggetto XmlReader con un resolver protetto o con la DTD e l'elaborazione dello schema inline XML disabilitato limita questa operazione. |
| CA5372 | [CA5372: Usa XmlReader per XPathDocument](../code-quality/ca5372.md) | L'elaborazione di dati XML da dati non attendibili può caricare riferimenti esterni pericolosi, che possono essere limitati utilizzando un XmlReader con un resolver sicuro o con l'elaborazione DTD disabilitata. |
| CA5373 | [CA5373: Non usare la funzione di derivazione di chiave obsoleta](../code-quality/ca5373.md) | Questa regola rileva la chiamata dei metodi di derivazione della chiave debole <xref:System.Security.Cryptography.PasswordDeriveBytes?displayProperty=fullName> e `Rfc2898DeriveBytes.CryptDeriveKey` . <xref:System.Security.Cryptography.PasswordDeriveBytes?displayProperty=fullName> è stato usato un algoritmo PBKDF1 vulnerabile. |
| CA5374 | [CA5374 non utilizzano XslTransform](../code-quality/ca5374.md) | Questa regola consente di controllare se <xref:System.Xml.Xsl.XslTransform?displayProperty=nameWithType> viene creata un'istanza nel codice. <xref:System.Xml.Xsl.XslTransform?displayProperty=nameWithType> è ora obsoleto e non deve essere usato. |
| CA5375 | [CA5375 non usa la firma di accesso condiviso dell'account](../code-quality/ca5375.md) | Una firma di accesso condiviso dell'account può delegare l'accesso alle operazioni di lettura, scrittura ed eliminazione su contenitori BLOB, tabelle, code e condivisioni file che non sono consentiti con una firma di accesso condiviso del servizio. Tuttavia, non supporta i criteri a livello di contenitore e ha meno flessibilità e controllo sulle autorizzazioni concesse. Una volta che gli utenti malintenzionati lo ottengono, l'account di archiviazione verrà compromesso con facilità. |
| CA5376 | [CA5376 usare SharedAccessProtocol HttpsOnly](../code-quality/ca5376.md) | SAS è dati sensibili che non possono essere trasportati in testo normale su HTTP. |
| CA5377 | [CA5377 usare i criteri di accesso a livello di contenitore](../code-quality/ca5377.md) | I criteri di accesso a livello di contenitore possono essere modificati o revocati in qualsiasi momento. Offre maggiore flessibilità e controllo sulle autorizzazioni concesse. |
| CA5378 | [CA5378: Non disabilitare ServicePointManagerSecurityProtocols](../code-quality/ca5378.md) | Impostando `Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols` su `true` , le connessioni di Windows Communication Framework (WCF) Transport Layer Security (TLS) a usano TLS 1,0. La versione di TLS sarà deprecata. |
| CA5379 | [CA5379 non usa l'algoritmo della funzione di derivazione della chiave debole](../code-quality/ca5379.md) | <xref:System.Security.Cryptography.Rfc2898DeriveBytes>Per impostazione predefinita, la classe usa l' <xref:System.Security.Cryptography.HashAlgorithmName.SHA1> algoritmo. È necessario specificare l'algoritmo hash da usare in alcuni overload del costruttore con <xref:System.Security.Cryptography.HashAlgorithmName.SHA256> o versione successiva. Si noti <xref:System.Security.Cryptography.Rfc2898DeriveBytes.HashAlgorithm> che la proprietà ha solo una `get` funzione di accesso e non ha un `overriden` modificatore. |
| CA5380 | [CA5380: Non aggiungere certificati all'archivio radice](../code-quality/ca5380.md) | Questa regola rileva il codice che aggiunge un certificato nell'archivio certificati delle autorità di certificazione radice attendibili. Per impostazione predefinita, l'archivio certificati delle autorità di certificazione radice attendibili è configurato con un set di CA pubbliche che soddisfa i requisiti del programma Microsoft Root Certificate. |
| CA5381 | [CA5381: Assicurarsi che i certificati non vengano aggiunti all'archivio radice](../code-quality/ca5381.md) | Questa regola rileva il codice che potenzialmente aggiunge un certificato all'archivio certificati delle autorità di certificazione radice attendibili. Per impostazione predefinita, l'archivio certificati delle autorità di certificazione radice attendibili è configurato con un set di autorità di certificazione pubbliche (CAs) che soddisfano i requisiti del programma Microsoft Root Certificate. |
| CA5382 | [CA5382 usare i cookie sicuri in ASP.NET Core](../code-quality/ca5382.md) | Le applicazioni disponibili tramite HTTPS devono usare cookie protetti, che indicano al browser che il cookie deve essere trasmesso solo usando Secure Sockets Layer (SSL). |
| CA5383 | [CA5383 assicurarsi di usare i cookie sicuri in ASP.NET Core](../code-quality/ca5383.md) | Le applicazioni disponibili tramite HTTPS devono usare cookie protetti, che indicano al browser che il cookie deve essere trasmesso solo usando Secure Sockets Layer (SSL). |
| CA5384 | [CA5384 non usa l'algoritmo di firma digitale (DSA)](../code-quality/ca5384.md) | DSA è un algoritmo di crittografia asimmetrica debole. |
| CA5385 | [CA5385 usare l'algoritmo Adleman (RSA) con la dimensione della chiave sufficiente](../code-quality/ca5385.md) | Una chiave RSA inferiore a 2048 bit è più vulnerabile agli attacchi di forza bruta. |
| CA5386 | [CA5386: Evitare di impostare il valore SecurityProtocolType come hardcoded](../code-quality/ca5386.md) | Transport Layer Security (TLS) protegge la comunicazione tra i computer, in genere con Hypertext Transfer Protocol Secure (HTTPS). Le versioni del protocollo TLS 1,0 e TLS 1,1 sono deprecate, mentre TLS 1,2 e TLS 1,3 sono correnti. In futuro, è possibile che TLS 1,2 e TLS 1,3 siano deprecati. Per assicurarsi che l'applicazione rimanga protetta, evitare di impostare come hardcoded una versione del protocollo e specificare come destinazione almeno .NET Framework v 4.7.1. |
| CA5387 | [CA5387 non utilizzano la funzione di derivazione della chiave debole con numero di iterazioni insufficiente](../code-quality/ca5387.md) | Questa regola consente di controllare se una chiave crittografica è stata generata da <xref:System.Security.Cryptography.Rfc2898DeriveBytes> con un numero di iterazioni inferiore a 100.000. Un numero di iterazioni superiore può contribuire a mitigare gli attacchi del dizionario che tentano di indovinare la chiave crittografica generata. |
| CA5388 | [CA5388 garantiscono un numero di iterazioni sufficiente quando si usa la funzione di derivazione della chiave](../code-quality/ca5388.md) | Questa regola consente di controllare se una chiave crittografica è stata generata da <xref:System.Security.Cryptography.Rfc2898DeriveBytes> con un numero di iterazioni inferiore a 100.000. Un numero di iterazioni superiore può contribuire a mitigare gli attacchi del dizionario che tentano di indovinare la chiave crittografica generata. |
| CA5389 | [CA5389: Non aggiungere il percorso dell'elemento di archiviazione al percorso del file system di destinazione](../code-quality/ca5389.md) | Il percorso del file può essere relativo e può comportare l'accesso file system al di fuori del percorso di destinazione file system previsto, causando modifiche di configurazione dannose e l'esecuzione di codice in modalità remota tramite la tecnica Lay-and-wait. |
| CA5390 | [CA5390 non hardcoded chiave di crittografia](../code-quality/ca5390.md) | Affinché un algoritmo simmetrico abbia esito positivo, la chiave privata deve essere nota solo al mittente e al ricevitore. Quando una chiave è hardcoded, viene individuata facilmente. Anche con i file binari compilati, è facile per l'estrazione da parte di utenti malintenzionati. Una volta compromessa la chiave privata, il testo crittografato può essere decrittografato direttamente e non è più protetto. |
| CA5391 | [CA5391 usa i token antifalsificazione in ASP.NET Core controller MVC](../code-quality/ca5391.md) | La gestione `POST` `PUT` di una richiesta,, `PATCH` o `DELETE` senza convalidare un token antifalsificazione può essere vulnerabile agli attacchi di richiesta intersito falsa. Un attacco di richiesta intersito falsificazione può inviare richieste dannose da un utente autenticato al controller ASP.NET Core MVC. |
| CA5392 | [CA5392 usare l'attributo DefaultDllImportSearchPaths per P/Invoke](../code-quality/ca5392.md) | Per impostazione predefinita, le funzioni P/Invoke che usano il <xref:System.Runtime.InteropServices.DllImportAttribute> Probe di un numero di directory, inclusa la directory di lavoro corrente per il caricamento della libreria. Questo può costituire un problema di sicurezza per determinate applicazioni, causando il Hijack della DLL. |
| CA5393 | [CA5393 non utilizza il valore DllImportSearchPath non sicuro](../code-quality/ca5393.md) | Potrebbe essere presente una DLL dannosa nelle directory di ricerca DLL e nelle directory di assembly predefinite. In alternativa, a seconda della posizione in cui viene eseguita l'applicazione, potrebbe essere presente una DLL dannosa nella directory dell'applicazione. |
| CA5394 | [CA5394 non usano la casualità non sicura](../code-quality/ca5394.md) | L'uso di un generatore di numeri pseudo-casuali a crittografia debole può consentire a un utente malintenzionato di stimare il valore che deve essere generato con distinzione di sicurezza. |
| CA5395 | [CA5395 manca l'attributo HttpVerb per i metodi di azione](../code-quality/ca5395.md) | Tutti i metodi di azione che creano, modificano, eliminano o modificano in altro modo i dati devono essere protetti con l'attributo antifalsificazione da attacchi di richiesta intersito falsa. L'esecuzione di un'operazione GET deve essere un'operazione sicura che non ha effetti collaterali e non modifica i dati persistenti. |
| CA5396 | [CA5396 impostare HttpOnly su true per HttpCookie](../code-quality/ca5396.md) | Come misura di difesa in profondità, assicurarsi che i cookie HTTP sensibili alla sicurezza siano contrassegnati come HttpOnly. Ciò indica che i Web browser non consentono l'accesso ai cookie da parte degli script. Gli script dannosi inseriti sono un metodo comune per il furto dei cookie. |
| CA5397 | [CA5397: Non usare valori SslProtocols deprecati](../code-quality/ca5397.md) | Transport Layer Security (TLS) protegge la comunicazione tra i computer, in genere con Hypertext Transfer Protocol Secure (HTTPS). Le versioni precedenti del protocollo TLS sono meno sicure di TLS 1,2 e TLS 1,3 ed è più probabile che abbiano nuove vulnerabilità. Evitare le versioni precedenti del protocollo per ridurre al minimo i rischi. |
| CA5398 | [CA5398: Evitare valori SslProtocols hardcoded](../code-quality/ca5398.md) | Transport Layer Security (TLS) protegge la comunicazione tra i computer, in genere con Hypertext Transfer Protocol Secure (HTTPS). Le versioni del protocollo TLS 1,0 e TLS 1,1 sono deprecate, mentre TLS 1,2 e TLS 1,3 sono correnti. In futuro, è possibile che TLS 1,2 e TLS 1,3 siano deprecati. Per assicurarsi che l'applicazione rimanga protetta, evitare di impostare come hardcoded una versione del protocollo. |
| CA5399 | [CA5399 Disabilita definitivamente la verifica dell'elenco di revoche di certificati HttpClient](../code-quality/ca5399.md) | Un certificato revocato non è più attendibile. Potrebbe essere utilizzato da utenti malintenzionati che passano alcuni dati dannosi o rubando dati sensibili nella comunicazione HTTPS. |
| Ca5400 | [Ca5400 assicurarsi che la verifica dell'elenco di revoche di certificati HttpClient non sia disabilitata](../code-quality/ca5400.md) | Un certificato revocato non è più attendibile. Potrebbe essere utilizzato da utenti malintenzionati che passano alcuni dati dannosi o rubando dati sensibili nella comunicazione HTTPS. |
| CA5401 | [CA5401 non USA al CreateDecryptor con IV non predefinito](../code-quality/ca5401.md) | La crittografia simmetrica deve sempre usare un vettore di inizializzazione non ripetibile per impedire gli attacchi con dizionario. |
| CA5402 | [CA5402 usare al CreateDecryptor con il valore di inizializzazione predefinito](../code-quality/ca5402.md) | La crittografia simmetrica deve sempre usare un vettore di inizializzazione non ripetibile per impedire gli attacchi con dizionario. |
| CA5403 | [CA5403: Non impostare il certificato come hardcoded](../code-quality/ca5403.md) | Il `data` `rawData` parametro o di un <xref:System.Security.Cryptography.X509Certificates.X509Certificate> <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> costruttore o è hardcoded. |
| IL3000 | [IL3000 evitare di accedere al percorso del file di assembly durante la pubblicazione come singolo file](../code-quality/il3000.md) | Evitare di utilizzare l'accesso al percorso del file di assembly durante la pubblicazione come singolo file |
| IL3001 | [IL3001 evitare di accedere al percorso del file di assembly durante la pubblicazione come file singolo](../code-quality/il3001.md) | Evitare di accedere al percorso del file di assembly durante la pubblicazione come file singolo |
