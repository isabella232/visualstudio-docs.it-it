---
title: avvisi di prestazioni
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.performancerules
helpviewer_keywords:
- warnings, performance
- performance warnings
- performance, warnings
- managed code analysis warnings, performance warnings
ms.assetid: e014ac3a-02e6-46d9-942c-3491dd63782f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 42f188901db72378acfd1dee8e22c9a2261b8eb9
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587251"
---
# <a name="performance-warnings"></a>avvisi di prestazioni
Gli avvisi di prestazioni supportano applicazioni e librerie ad alte prestazioni.

## <a name="in-this-section"></a>In questa sezione

| Regola | Descrizione |
| - | - |
| [CA1800: Non eseguire il cast inutilmente](../code-quality/ca1800.md) | I cast duplicati comportano una riduzione delle prestazioni, in particolare quando i cast vengono eseguiti in istruzioni di iterazione compatte. |
| [CA1801: Rivedere i parametri non usati](../code-quality/ca1801.md) | Una firma di metodo include un parametro non utilizzato nel corpo del metodo. |
| [CA1802: Usa valori letterali dove appropriato](../code-quality/ca1802.md) | Un campo viene dichiarato statico e di sola lettura (Shared e ReadOnly in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) e viene inizializzato con un valore calcolabile in fase di compilazione. Poiché il valore assegnato al campo di destinazione è calcolabile in fase di compilazione, modificare la dichiarazione in una variabile const (Const in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) in modo che il valore viene calcolato in fase di compilazione anziché in fase di esecuzione. |
| [CA1804: Rimuovere locali non usati](../code-quality/ca1804.md) | Le variabili locali inutilizzate e le assegnazioni non necessarie comportano un aumento delle dimensioni dell'assembly e una riduzione delle prestazioni. |
| [CA1806: Non ignorare i risultati del metodo](../code-quality/ca1806.md) | Un nuovo oggetto viene creato, ma non viene mai usato, oppure un metodo che crea e restituisce una nuova stringa viene chiamato e la nuova stringa non viene mai usata oppure un metodo Component Object Model (COM) o P/Invoke restituisce un codice HRESULT o errore che non viene mai usato. |
| [CA1809: Evitare un numero eccessivo di variabili locali](../code-quality/ca1809.md) | Un'ottimizzazione comune delle prestazioni consiste nell'archiviare un valore in un registro del processore anziché in memoria. Tale procedura è definita "registrazione del valore".  Per aumentare la probabilità che tutte le variabili locali siano registrate, limitare il numero di variabili a 64. |
| [CA1810: Inizializzare i campi statici del tipo di riferimento inline](../code-quality/ca1810.md) | Quando un tipo dichiara un costruttore statico esplicito, tramite il compilatore JIT (Just-In-Time) viene aggiunto un controllo a ogni metodo statico del tipo e a ogni costruttore di istanza del tipo per assicurare che il costruttore statico sia stato precedentemente chiamato. I controlli dei costruttori statici possono ridurre le prestazioni. |
| [CA1811: Evitare il codice privato non chiamato](../code-quality/ca1811.md) | Un membro privato o interno (a livello di assembly) non contiene chiamanti nell'assembly, non viene richiamato dal Common Language Runtime e non viene richiamato da un delegato. |
| [CA1812: Evitare classi interne prive di istanze](../code-quality/ca1812.md) | Un'istanza di un tipo a livello di assembly non viene creata dal codice nell'assembly. |
| [CA1813: Evitare attributi non sealed](../code-quality/ca1813.md) | .NET fornisce metodi per il recupero di attributi personalizzati. Per impostazione predefinita, questi metodi eseguono ricerche nella gerarchia di ereditarietà dell'attributo. L'utilizzo di attributi sealed elimina la ricerca nella gerarchia di ereditarietà e può migliorare le prestazioni. |
| [CA1814: Preferire matrici di matrici rispetto a matrici multidimensionali](../code-quality/ca1814.md) | Una matrice di matrici contiene elementi sotto forma di matrici. Le matrici che compongono gli elementi possono avere dimensioni diverse, il che può comportare uno spazio meno sprecato per alcuni set di dati. |
| [CA1815: Eseguire l'override di Equals e dell'operatore "uguale a" sui tipi di valore](../code-quality/ca1815.md) | Per i tipi di valore, l'implementazione ereditata di Equals utilizza la libreria Reflection e confronta il contenuto di tutti i campi. La libreria Reflection è onerosa dal punto di vista del calcolo, inoltre il confronto di ogni campo per determinarne l'uguaglianza potrebbe essere superfluo. Se si prevede che gli utenti confrontino o ordinino le istanze oppure le utilizzino come chiavi di tabelle hash, il tipo di valore deve implementare Equals. |
| [CA1816: Chiamare GC.SuppressFinalize correttamente](../code-quality/ca1816.md) | Un metodo che rappresenta un'implementazione di Dispose non chiama GC. SuppressFinalize o un metodo che non è un'implementazione di Dispose chiama GC. SuppressFinalize oppure un metodo chiama GC. SuppressFinalize e passa un valore diverso da this (me in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). |
| [CA1819: Le proprietà non devono restituire matrici](../code-quality/ca1819.md) | Le matrici restituite dalle proprietà non sono protette da scrittura, anche se la proprietà è di sola lettura. Affinché la matrice sia protetta da eventuali alterazioni, la proprietà deve restituire una copia della matrice. In genere, gli utenti non comprendono le implicazioni negative sulle prestazioni derivanti dalla chiamata di tale proprietà. |
| [CA1820: Testare le stringhe vuote usando la lunghezza di stringa](../code-quality/ca1820.md) | Il confronto tra stringhe mediante la proprietà String.Length o il metodo String.IsNullOrEmpty è notevolmente più veloce rispetto all'utilizzo di Equals. |
| [CA1821: Rimuovere i finalizzatori vuoti](../code-quality/ca1821.md) | Quando possibile, evitare di utilizzare i finalizzatori per non sovraccaricare ulteriormente le prestazioni durante il rilevamento della durata dell'oggetto. Un finalizzatore vuoto comporta un sovraccarico aggiuntivo senza alcun vantaggio. |
| [CA1822: Contrassegna i membri come statici](../code-quality/ca1822.md) | I membri che non accedono ai dati di istanza o non chiamano metodi di istanza possono essere contrassegnati come static (Shared in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Tramite il compilatore verranno quindi inviati siti di chiamata non virtuali a tali membri. Si potrà così ottenere un sensibile miglioramento delle prestazioni per codici sensibili alle prestazioni. |
| [CA1823: Evitare campi privati non usati](../code-quality/ca1823.md) | Sono stati rilevati campi privati che non sembrano essere utilizzati all'interno dell'assembly. |
| [CA1824: Contrassegnare gli assembly con NeutralResourcesLanguageAttribute](../code-quality/ca1824.md) | L'attributo NeutralResourcesLanguage indica a ResourceManager la lingua utilizzata per visualizzare le risorse delle impostazioni cultura non associate ad alcun paese per un assembly. Tale approccio migliora le prestazioni delle ricerche per la prima risorsa caricata e riduce il working set. |
| [Ca1825: evitare allocazioni di matrici di lunghezza zero](../code-quality/ca1825.md) | L'inizializzazione di una matrice di lunghezza zero comporta l'allocazione di memoria non necessaria. Utilizzare invece l'istanza di matrice vuota allocata in modo statico chiamando <xref:System.Array.Empty%2A?displayProperty=nameWithType>. L'allocazione di memoria è condivisa tra tutte le chiamate di questo metodo. |
