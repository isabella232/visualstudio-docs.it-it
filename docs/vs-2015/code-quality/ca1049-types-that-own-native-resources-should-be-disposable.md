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
ms.openlocfilehash: aaaf95346c51e2cb5cadb01a39e482bb508bc764
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668899"
---
# <a name="ca1049-types-that-own-native-resources-should-be-disposable"></a>CA1049: I tipi delle risorse native devono essere Disposable
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TypesThatOwnNativeResourcesShouldBeDisposable|
|CheckId|CA1049|
|Category|Microsoft. Design|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
 Un tipo fa riferimento a un campo <xref:System.IntPtr?displayProperty=fullName>, a un campo <xref:System.UIntPtr?displayProperty=fullName> o a un campo <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>, ma non implementa <xref:System.IDisposable?displayProperty=fullName>.

## <a name="rule-description"></a>Descrizione della regola
 Questa regola presuppone che i campi <xref:System.IntPtr>, <xref:System.UIntPtr> e <xref:System.Runtime.InteropServices.HandleRef> memorizzino i puntatori alle risorse non gestite. I tipi che allocano risorse non gestite devono implementare <xref:System.IDisposable> per consentire ai chiamanti di rilasciare le risorse su richiesta e ridurre la durata degli oggetti che contengono le risorse.

 Il modello di progettazione consigliato per pulire le risorse non gestite consiste nel fornire sia un metodo implicito che un mezzo esplicito per liberare tali risorse usando rispettivamente il metodo <xref:System.Object.Finalize%2A?displayProperty=fullName> e il metodo <xref:System.IDisposable.Dispose%2A?displayProperty=fullName>. Il Garbage Collector chiama il metodo <xref:System.Object.Finalize%2A> di un oggetto in un momento indeterminato dopo che l'oggetto è stato determinato che non è più raggiungibile. Dopo la chiamata di <xref:System.Object.Finalize%2A>, è necessario un Garbage Collection aggiuntivo per liberare l'oggetto. Il metodo <xref:System.IDisposable.Dispose%2A> consente al chiamante di rilasciare in modo esplicito le risorse su richiesta, prima che vengano rilasciate le risorse se lasciate al Garbage Collector. Dopo la pulizia delle risorse non gestite, <xref:System.IDisposable.Dispose%2A> necessario chiamare il metodo <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> per consentire al Garbage Collector di tenere presente che non è più necessario chiamare <xref:System.Object.Finalize%2A>. in questo modo si elimina la necessità di Garbage Collection aggiuntivi e si abbrevia la durata dell'oggetto.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, implementare <xref:System.IDisposable>.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se il tipo non fa riferimento a una risorsa non gestita. In caso contrario, non eliminare un avviso da questa regola perché la mancata implementazione di <xref:System.IDisposable> può causare l'indisponibilità o il sottoutilizzo delle risorse non gestite.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo che implementa <xref:System.IDisposable> per pulire una risorsa non gestita.

 [!code-csharp[FxCop.Design.UnmanagedResources#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.UnmanagedResources/cs/FxCop.Design.UnmanagedResources.cs#1)]
 [!code-vb[FxCop.Design.UnmanagedResources#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.UnmanagedResources/vb/FxCop.Design.UnmanagedResources.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA2115: Chiamare GC.KeepAlive durante l'uso di risorse native](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

 [CA1816: Chiamare GC.SuppressFinalize correttamente](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

 [CA2216: I tipi Disposable devono dichiarare un finalizzatore](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

 [CA1001: I tipi proprietari di campi Disposable devono essere Disposable](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)

## <a name="see-also"></a>Vedere anche
  [Criterio Dispose](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
