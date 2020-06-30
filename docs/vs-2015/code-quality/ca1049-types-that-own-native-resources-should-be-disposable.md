---
title: 'CA1049: i tipi che possiedono risorse native devono essere Disposable | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1049
- TypesThatOwnNativeResourcesShouldBeDisposable
helpviewer_keywords:
- TypesThatOwnNativeResourcesShouldBeDisposable
- CA1049
ms.assetid: 084e587d-0e45-4092-b767-49eed30d6a35
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 49c56b98e3be01675c2c21cd11c2961dd75f4877
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546809"
---
# <a name="ca1049-types-that-own-native-resources-should-be-disposable"></a>CA1049: I tipi delle risorse native devono essere disposable
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|TypesThatOwnNativeResourcesShouldBeDisposable|
|CheckId|CA1049|
|Category|Microsoft. Design|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
 Un tipo fa riferimento a un campo, <xref:System.IntPtr?displayProperty=fullName> a un <xref:System.UIntPtr?displayProperty=fullName> campo o a un <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName> campo, ma non implementa <xref:System.IDisposable?displayProperty=fullName> .

## <a name="rule-description"></a>Descrizione della regola
 Questa regola presuppone che <xref:System.IntPtr> i <xref:System.UIntPtr> campi, e <xref:System.Runtime.InteropServices.HandleRef> memorizzino i puntatori alle risorse non gestite. I tipi che allocano risorse non gestite devono implementare <xref:System.IDisposable> per consentire ai chiamanti di rilasciare le risorse su richiesta e abbreviare la durata degli oggetti che contengono le risorse.

 Il modello di progettazione consigliato per pulire le risorse non gestite consiste nel fornire sia un metodo implicito che un mezzo esplicito per liberare tali risorse usando <xref:System.Object.Finalize%2A?displayProperty=fullName> rispettivamente il metodo e il <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> metodo. Il Garbage Collector chiama il <xref:System.Object.Finalize%2A> metodo di un oggetto in un determinato momento indeterminato dopo che l'oggetto non è più raggiungibile. Dopo <xref:System.Object.Finalize%2A> la chiamata a, è necessario un Garbage Collection aggiuntivo per liberare l'oggetto. Il <xref:System.IDisposable.Dispose%2A> metodo consente al chiamante di rilasciare in modo esplicito le risorse su richiesta, prima che le risorse vengano rilasciate se lasciate al Garbage Collector. Dopo la pulizia delle risorse non gestite, <xref:System.IDisposable.Dispose%2A> deve chiamare il <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> metodo per informare il Garbage Collector che <xref:System.Object.Finalize%2A> non è più necessario chiamare. in questo modo si elimina la necessità del Garbage Collection aggiuntivo e si abbrevia la durata dell'oggetto.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, implementare <xref:System.IDisposable> .

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se il tipo non fa riferimento a una risorsa non gestita. In caso contrario, non eliminare un avviso da questa regola perché la mancata implementazione può comportare <xref:System.IDisposable> che le risorse non gestite diventino non disponibili o sottoutilizzate.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo che implementa <xref:System.IDisposable> per pulire una risorsa non gestita.

 [!code-csharp[FxCop.Design.UnmanagedResources#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.UnmanagedResources/cs/FxCop.Design.UnmanagedResources.cs#1)]
 [!code-vb[FxCop.Design.UnmanagedResources#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.UnmanagedResources/vb/FxCop.Design.UnmanagedResources.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA2115: Chiamare GC.KeepAlive durante l'uso di risorse native](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

 [CA1816: Chiamare GC.SuppressFinalize correttamente](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

 [CA2216: I tipi eliminabili devono dichiarare un finalizzatore](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

 [CA1001: I tipi proprietari di campi Disposable devono essere Disposable](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)

## <a name="see-also"></a>Vedere anche
  [Modello Dispose](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
