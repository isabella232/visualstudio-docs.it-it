---
title: 'CA1024: usare le proprietà laddove appropriato | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UsePropertiesWhereAppropriate
- CA1024
helpviewer_keywords:
- CA1024
- UsePropertiesWhereAppropriate
ms.assetid: 3a04f765-af7c-4872-87ad-9cc29e8e657f
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a240a6eea86075bbf7f721f8620b6d135d594c20
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546666"
---
# <a name="ca1024-use-properties-where-appropriate"></a>CA1024: Usare proprietà dove appropriato
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|UsePropertiesWhereAppropriate|
|CheckId|CA1024|
|Category|Microsoft. Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un metodo pubblico o protetto ha un nome che inizia con `Get` , non accetta parametri e restituisce un valore che non è una matrice.

## <a name="rule-description"></a>Descrizione della regola
 Nella maggior parte dei casi, le proprietà rappresentano i dati e i metodi che eseguono azioni. È possibile accedere alle proprietà, ad esempio i campi, in modo da semplificarne l'uso. Un metodo è un buon candidato per diventare una proprietà se è presente una di queste condizioni:

- Non accetta argomenti e restituisce le informazioni sullo stato di un oggetto.

- Accetta un solo argomento per impostare una parte dello stato di un oggetto.

  Le proprietà devono comportarsi come se fossero campi; Se il metodo non può, non deve essere modificato in una proprietà. I metodi sono migliori delle proprietà nelle situazioni seguenti:

- Il metodo esegue un'operazione che richiede molto tempo. Il metodo è sensibilmente più lento del tempo necessario per impostare o ottenere il valore di un campo.

- Il metodo esegue una conversione. L'accesso a un campo non restituisce una versione convertita dei dati archiviati.

- Il metodo Get ha un effetto collaterale osservabile. Il recupero del valore di un campo non produce effetti collaterali.

- L'ordine di esecuzione è importante. L'impostazione del valore di un campo non si basa sull'occorrenza di altre operazioni.

- La chiamata del metodo due volte in successione crea risultati diversi.

- Il metodo è statico ma restituisce un oggetto che può essere modificato dal chiamante. Il recupero del valore di un campo non consente al chiamante di modificare i dati archiviati dal campo.

- Il metodo restituisce una matrice.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, modificare il metodo in una proprietà.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Eliminare un avviso da questa regola se il metodo soddisfa almeno uno dei criteri elencati in precedenza.

## <a name="controlling-property-expansion-in-the-debugger"></a>Controllo dell'espansione delle proprietà nel debugger
 Uno dei motivi per cui i programmatori evitano di utilizzare una proprietà è perché non desiderano che il debugger si espanda automaticamente. Ad esempio, la proprietà può implicare l'allocazione di un oggetto di grandi dimensioni o la chiamata di un P/Invoke, ma potrebbe non avere effetti collaterali osservabili.

 È possibile impedire al debugger di espandere automaticamente le proprietà applicando <xref:System.Diagnostics.DebuggerBrowsableAttribute?displayProperty=fullName> . Nell'esempio seguente viene illustrato l'applicazione di questo attributo a una proprietà dell'istanza.

```vb
Imports System
Imports System.Diagnostics

Namespace Microsoft.Samples

    Public Class TestClass

        ' [...]

        <DebuggerBrowsable(DebuggerBrowsableState.Never)> _
        Public ReadOnly Property LargeObject() As LargeObject
            Get
                ' Allocate large object
                ' [...]
            End Get
        End Property

    End Class

End Namespace
```

```csharp

      using System;
using System.Diagnostics;

namespace Microsoft.Samples
{
    publicclass TestClass
    {
        // [...]

        [DebuggerBrowsable(DebuggerBrowsableState.Never)]
        public LargeObject LargeObject
        {
            get
            {
                // Allocate large object
                // [...]

        }
    }
}
```

## <a name="example"></a>Esempio
 Nell'esempio seguente sono contenuti diversi metodi che devono essere convertiti in proprietà e diversi da quelli che non devono essere in quanto non si comportano come campi.

 [!code-csharp[FxCop.Design.MethodsProperties#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.MethodsProperties/cs/FxCop.Design.MethodsProperties.cs#1)]
