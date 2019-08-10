---
title: 'CA1049: I tipi delle risorse native devono essere disposable'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1049
- TypesThatOwnNativeResourcesShouldBeDisposable
helpviewer_keywords:
- TypesThatOwnNativeResourcesShouldBeDisposable
- CA1049
ms.assetid: 084e587d-0e45-4092-b767-49eed30d6a35
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- cplusplus
ms.openlocfilehash: 415b8c95dda3fca084fcb103dfa5e4f39e1a73da
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922533"
---
# <a name="ca1049-types-that-own-native-resources-should-be-disposable"></a>CA1049: I tipi delle risorse native devono essere disposable

|||
|-|-|
|TypeName|TypesThatOwnNativeResourcesShouldBeDisposable|
|CheckId|CA1049|
|Category|Microsoft.Design|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa

Un tipo fa riferimento <xref:System.IntPtr?displayProperty=fullName> a un campo <xref:System.UIntPtr?displayProperty=fullName> , a un campo <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName> o a un campo, ma <xref:System.IDisposable?displayProperty=fullName>non implementa.

## <a name="rule-description"></a>Descrizione della regola

Questa regola presuppone che <xref:System.IntPtr>i <xref:System.UIntPtr>campi, <xref:System.Runtime.InteropServices.HandleRef> e memorizzino i puntatori alle risorse non gestite. I tipi che allocano risorse non gestite devono <xref:System.IDisposable> implementare per consentire ai chiamanti di rilasciare le risorse su richiesta e abbreviare la durata degli oggetti che contengono le risorse.

Il modello di progettazione consigliato per pulire le risorse non gestite consiste nel fornire sia un metodo implicito che un mezzo esplicito per liberare tali risorse <xref:System.Object.Finalize%2A?displayProperty=fullName> usando rispettivamente il <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> metodo e il metodo. Il Garbage Collector chiama il <xref:System.Object.Finalize%2A> metodo di un oggetto in un determinato momento indeterminato dopo che l'oggetto non è più raggiungibile. Dopo <xref:System.Object.Finalize%2A> la chiamata a, è necessario un Garbage Collection aggiuntivo per liberare l'oggetto. Il <xref:System.IDisposable.Dispose%2A> metodo consente al chiamante di rilasciare in modo esplicito le risorse su richiesta, prima che le risorse vengano rilasciate se lasciate al Garbage Collector. Dopo la pulizia delle risorse non gestite, <xref:System.IDisposable.Dispose%2A> è necessario chiamare il <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> metodo per informare il Garbage Collector che <xref:System.Object.Finalize%2A> non è più necessario chiamare. in questo modo si elimina la necessità di Garbage Collection aggiuntivi e si abbrevia il durata dell'oggetto.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Per correggere una violazione di questa regola, implementare <xref:System.IDisposable>.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
È possibile eliminare un avviso da questa regola se il tipo non fa riferimento a una risorsa non gestita. In caso contrario, non eliminare un avviso da questa regola perché la mancata implementazione <xref:System.IDisposable> può comportare che le risorse non gestite diventino non disponibili o sottoutilizzate.

## <a name="example"></a>Esempio
Nell'esempio seguente viene illustrato un tipo che <xref:System.IDisposable> implementa per pulire una risorsa non gestita.

[!code-csharp[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/CSharp/ca1049-types-that-own-native-resources-should-be-disposable_1.cs)]
[!code-vb[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/VisualBasic/ca1049-types-that-own-native-resources-should-be-disposable_1.vb)]

## <a name="related-rules"></a>Regole correlate
[CA2115 Chiamare GC. KeepAlive quando si utilizzano risorse native](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

[CA1816: Chiamare GC. SuppressFinalize correttamente](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

[CA2216 I tipi Disposable devono dichiarare Finalizer](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

[CA1001: I tipi proprietari di campi eliminabili devono essere eliminabili](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)

## <a name="see-also"></a>Vedere anche

- [Pulizia delle risorse non gestite](/dotnet/standard/garbage-collection/unmanaged)
- [Criterio Dispose](/dotnet/standard/design-guidelines/dispose-pattern)