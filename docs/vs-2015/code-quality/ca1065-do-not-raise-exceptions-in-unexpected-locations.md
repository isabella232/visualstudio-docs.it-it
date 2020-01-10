---
title: 'CA1065: non generare eccezioni in posizioni impreviste | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1065
- DoNotRaiseExceptionsInUnexpectedLocations
helpviewer_keywords:
- DoNotRaiseExceptionsInUnexpectedLocations
- CA1065
ms.assetid: 4e1bade4-4ca2-4219-abc3-c7b2d741e157
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2df740abf25344253627b614fdbd80dce86c7bfa
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2020
ms.locfileid: "75847476"
---
# <a name="ca1065-do-not-raise-exceptions-in-unexpected-locations"></a>CA1065: Non generare eccezioni in posizioni non previste
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotRaiseExceptionsInUnexpectedLocations|
|CheckId|CA1065|
|Categoria|Microsoft.Design|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un metodo che normalmente non genera eccezioni genera un'eccezione.

## <a name="rule-description"></a>Descrizione della regola
 I metodi che non si prevede di generare eccezioni possono essere categorizzati come segue:

- Metodi get della proprietà

- Metodi della funzione di accesso agli eventi

- Metodi Equals

- Metodi GetHashCode

- Metodi ToString

- Costruttori statici

- Finalizzatori

- Metodi Dispose

- Operatori di uguaglianza

- Operatori cast impliciti

  Le sezioni seguenti illustrano questi tipi di metodo.

### <a name="property-get-methods"></a>Metodi get della proprietà
 Le proprietà sono essenzialmente campi intelligenti. Pertanto, devono comportarsi come un campo quanto più possibile. I campi non generano eccezioni né devono essere proprietà. Se si dispone di una proprietà che genera un'eccezione, è consigliabile renderla un metodo.

 Le eccezioni seguenti possono essere generate da un metodo Get della proprietà:

- <xref:System.InvalidOperationException?displayProperty=fullName> e tutti i derivati (incluso <xref:System.ObjectDisposedException?displayProperty=fullName>)

- <xref:System.NotSupportedException?displayProperty=fullName> e tutti i derivati

- <xref:System.ArgumentException?displayProperty=fullName> (solo da Get indicizzato)

- <xref:System.Collections.Generic.KeyNotFoundException> (solo da Get indicizzato)

### <a name="event-accessor-methods"></a>Metodi della funzione di accesso agli eventi
 Le funzioni di accesso agli eventi devono essere semplici operazioni che non generano eccezioni. Un evento non deve generare un'eccezione quando si tenta di aggiungere o rimuovere un gestore eventi.

 Le eccezioni seguenti possono essere generate da un accesore eventi:

- <xref:System.InvalidOperationException?displayProperty=fullName> e tutti i derivati (incluso <xref:System.ObjectDisposedException?displayProperty=fullName>)

- <xref:System.NotSupportedException?displayProperty=fullName> e tutti i derivati

- <xref:System.ArgumentException> e derivati

### <a name="equals-methods"></a>Metodi Equals
 I seguenti metodi **Equals** non devono generare eccezioni:

- <xref:System.Object.Equals%2A?displayProperty=fullName>

- [M:IEquatable.Equals](https://msdn2.microsoft.com/library/ms131190(VS.80).aspx)

  Un metodo **Equals** deve restituire `true` o `false` anziché generare un'eccezione. Se, ad esempio, viene passato un valore uguale a due tipi non corrispondenti, deve restituire solo `false` anziché generare una <xref:System.ArgumentException>.

### <a name="gethashcode-methods"></a>Metodi GetHashCode
 I metodi **GetHashCode** seguenti non devono in genere generare eccezioni:

- <xref:System.Object.GetHashCode%2A>

- [M:IEqualityComparer.GetHashCode(T)](https://msdn2.microsoft.com/library/system.collections.iequalitycomparer.gethashcode.aspx)

  **GetHashCode** deve sempre restituire un valore. In caso contrario, è possibile perdere gli elementi nella tabella hash.

  Le versioni di **GetHashCode** che accettano un argomento possono generare un <xref:System.ArgumentException>. Tuttavia, **Object. GetHashCode** non deve mai generare un'eccezione.

### <a name="tostring-methods"></a>Metodi ToString
 Il debugger utilizza <xref:System.Object.ToString%2A?displayProperty=fullName> per visualizzare informazioni sugli oggetti in formato stringa. Pertanto, **ToString** non deve modificare lo stato di un oggetto e non deve generare eccezioni.

### <a name="static-constructors"></a>Costruttori statici
 Generando eccezioni da un costruttore statico, il tipo è inutilizzabile nel dominio applicazione corrente. È necessario avere un motivo molto valido, ad esempio un problema di sicurezza, per generare un'eccezione da un costruttore statico.

### <a name="finalizers"></a>Finalizzatori
 La generazione di un'eccezione da parte di un finalizzatore causa un errore veloce di CLR, che consente di ridurre il processo. Pertanto, la generazione di eccezioni in un finalizzatore dovrebbe essere sempre evitata.

### <a name="dispose-methods"></a>Metodi Dispose
 Un metodo di <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> non deve generare un'eccezione. Dispose viene spesso chiamato come parte della logica di pulizia in una clausola `finally`. Pertanto, la generazione esplicita di un'eccezione da Dispose impone all'utente di aggiungere la gestione delle eccezioni all'interno della clausola `finally`.

 Il percorso del codice **Dispose (false)** non deve mai generare eccezioni perché questo viene quasi sempre chiamato da un finalizzatore.

### <a name="equality-operators--"></a>Operatori di uguaglianza (= =,! =)
 Analogamente ai metodi Equals, gli operatori di uguaglianza devono restituire `true` o `false` e non devono generare eccezioni.

### <a name="implicit-cast-operators"></a>Operatori cast impliciti
 Poiché l'utente spesso non è a conoscenza del fatto che è stato chiamato un operatore cast implicito, un'eccezione generata dall'operatore cast implicito è completamente imprevista. Pertanto, non deve essere generata alcuna eccezione dagli operatori cast impliciti.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per i getter della proprietà, modificare la logica in modo che non debba più generare un'eccezione o modificare la proprietà in un metodo.

 Per tutti gli altri tipi di metodo elencati in precedenza, modificare la logica in modo che non venga più generata un'eccezione.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se la violazione è stata causata da una dichiarazione di eccezione anziché da un'eccezione generata.

## <a name="related-rules"></a>Regole correlate
 [CA2219: Non generare eccezioni in clausole di eccezione](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)

## <a name="see-also"></a>Vedere anche
 [Avvisi di progettazione](../code-quality/design-warnings.md)
