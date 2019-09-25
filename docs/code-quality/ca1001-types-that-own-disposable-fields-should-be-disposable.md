---
title: 'CA1001: I tipi proprietari di campi Disposable devono essere Disposable'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
helpviewer_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
ms.assetid: c85c126c-2b16-4505-940a-b5ddf873fb22
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 3bda8fc80992a2246c30e28582eb93b4624ab81c
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236686"
---
# <a name="ca1001-types-that-own-disposable-fields-should-be-disposable"></a>CA1001: I tipi proprietari di campi Disposable devono essere Disposable

|||
|-|-|
|TypeName|TypesThatOwnDisposableFieldsShouldBeDisposable|
|CheckId|CA1001|
|Category|Microsoft.Design|
|Modifica|Senza interruzioni: se il tipo non è visibile all'esterno dell'assembly.<br /><br /> Interruzioni: se il tipo è visibile all'esterno dell'assembly.|

## <a name="cause"></a>Causa
Una classe dichiara e implementa un campo di istanza che è un <xref:System.IDisposable?displayProperty=fullName> tipo e la classe non implementa. <xref:System.IDisposable>

## <a name="rule-description"></a>Descrizione della regola
Una classe implementa l' <xref:System.IDisposable> interfaccia per eliminare le risorse non gestite di sua proprietà. Un campo di istanza che è <xref:System.IDisposable> un tipo indica che il campo è proprietario di una risorsa non gestita. Una classe che dichiara un <xref:System.IDisposable> campo possiede indirettamente una risorsa non gestita e deve implementare l' <xref:System.IDisposable> interfaccia. Se la classe non possiede direttamente le risorse non gestite, non deve implementare un finalizzatore.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Per correggere una violazione di questa regola, implementare <xref:System.IDisposable> e <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> dal metodo chiamare il <xref:System.IDisposable.Dispose%2A> metodo del campo.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
Nell'esempio seguente viene illustrata una classe che viola la regola e una classe che soddisfa la regola implementando <xref:System.IDisposable>. La classe non implementa un finalizzatore perché la classe non possiede direttamente le risorse non gestite.

[!code-vb[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/VisualBasic/ca1001-types-that-own-disposable-fields-should-be-disposable_1.vb)]
[!code-csharp[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/CSharp/ca1001-types-that-own-disposable-fields-should-be-disposable_1.cs)]

## <a name="related-rules"></a>Regole correlate
[CA2213: I campi eliminabili devono essere eliminati](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

[CA2216 I tipi Disposable devono dichiarare Finalizer](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

[CA2215: I metodi Dispose devono chiamare Dispose della classe base](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)

[CA1049: I tipi che possiedono risorse native devono essere Disposable](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)