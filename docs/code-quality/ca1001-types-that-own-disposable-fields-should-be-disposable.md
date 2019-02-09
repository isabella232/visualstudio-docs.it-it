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
ms.openlocfilehash: 581bc75c22326275dcb3657910f60c2977094037
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55907166"
---
# <a name="ca1001-types-that-own-disposable-fields-should-be-disposable"></a>CA1001: I tipi proprietari di campi Disposable devono essere Disposable

|||
|-|-|
|TypeName|TypesThatOwnDisposableFieldsShouldBeDisposable|
|CheckId|CA1001|
|Category|Microsoft.Design|
|Modifica importante|Non sostanziale - Se il tipo non è visibile all'esterno dell'assembly.<br /><br /> Rilievo - se il tipo è visibile all'esterno dell'assembly.|

## <a name="cause"></a>Causa
 Una classe dichiara e implementa un campo di istanza che è un <xref:System.IDisposable?displayProperty=fullName> tipo e la classe non implementa <xref:System.IDisposable>.

## <a name="rule-description"></a>Descrizione della regola
 Una classe che implementa il <xref:System.IDisposable> interfaccia per l'eliminazione delle risorse non gestite che possiede. Un campo di istanza che è un <xref:System.IDisposable> tipo indica che il campo proprietario di una risorsa non gestita. Una classe che dichiara un <xref:System.IDisposable> campo indirettamente proprietaria di una risorsa non gestita e deve implementare il <xref:System.IDisposable> interfaccia. Se la classe non è direttamente proprietario delle risorse non gestite, non deve implementare un finalizzatore.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, implementare <xref:System.IDisposable> e dal <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> chiamata al metodo il <xref:System.IDisposable.Dispose%2A> metodo del campo.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 L'esempio seguente mostra una classe che viola la regola e una classe che soddisfa la regola implementando <xref:System.IDisposable>. La classe non implementa un finalizzatore in quanto la classe non dispone direttamente delle risorse non gestite.

 [!code-vb[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/VisualBasic/ca1001-types-that-own-disposable-fields-should-be-disposable_1.vb)]
 [!code-csharp[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/CSharp/ca1001-types-that-own-disposable-fields-should-be-disposable_1.cs)]

## <a name="related-rules"></a>Regole correlate
 [CA2213: I campi eliminabili devono essere eliminati](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

 [CA2216: I tipi Disposable devono dichiarare un finalizzatore](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

 [CA2215: I metodi Dispose devono chiamare dispose della classe base](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)

 [CA1049: I tipi proprietari di risorse native devono essere disposable](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)