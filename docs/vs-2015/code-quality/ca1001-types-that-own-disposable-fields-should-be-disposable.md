---
title: 'CA1001: i tipi proprietari di campi Disposable devono essere Disposable | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
helpviewer_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
ms.assetid: c85c126c-2b16-4505-940a-b5ddf873fb22
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 42d21eb0bf32b3abb0eb26d3723123bf085914ed
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646325"
---
# <a name="ca1001-types-that-own-disposable-fields-should-be-disposable"></a>CA1001: I tipi proprietari di campi Disposable devono essere Disposable
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TypesThatOwnDisposableFieldsShouldBeDisposable|
|CheckId|CA1001|
|Category|Microsoft. Design|
|Modifica importante|Senza interruzioni: se il tipo non è visibile all'esterno dell'assembly.<br /><br /> Interruzioni: se il tipo è visibile all'esterno dell'assembly.|

## <a name="cause"></a>Causa
 Una classe dichiara e implementa un campo di istanza che è un tipo <xref:System.IDisposable?displayProperty=fullName> e la classe non implementa <xref:System.IDisposable>.

## <a name="rule-description"></a>Descrizione della regola
 Una classe implementa l'interfaccia <xref:System.IDisposable> per eliminare le risorse non gestite di sua proprietà. Un campo di istanza che è un tipo <xref:System.IDisposable> indica che il campo è proprietario di una risorsa non gestita. Una classe che dichiara un campo <xref:System.IDisposable> possiede indirettamente una risorsa non gestita e deve implementare l'interfaccia <xref:System.IDisposable>. Se la classe non possiede direttamente le risorse non gestite, non deve implementare un finalizzatore.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, implementare <xref:System.IDisposable> e dal metodo <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> chiamare il metodo <xref:System.IDisposable.Dispose%2A> del campo.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrata una classe che viola la regola e una classe che soddisfa la regola implementando <xref:System.IDisposable>. La classe non implementa un finalizzatore perché la classe non possiede direttamente le risorse non gestite.

 [!code-csharp[FxCop.Design.DisposableFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.DisposableFields/cs/FxCop.Design.DisposableFields.cs#1)]
 [!code-vb[FxCop.Design.DisposableFields#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.DisposableFields/vb/FxCop.Design.DisposableFields.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA2213: I campi Disposable devono essere eliminati](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

 [CA2216: I tipi Disposable devono dichiarare un finalizzatore](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

 [CA2215: I metodi Dispose devono chiamare il metodo Dispose della classe base](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)

 [CA1049: I tipi delle risorse native devono essere Disposable](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)
