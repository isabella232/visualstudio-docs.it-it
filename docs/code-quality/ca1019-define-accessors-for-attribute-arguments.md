---
title: 'CA1019: Definire le funzioni di accesso per gli argomenti degli attributi'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1019
- DefineAccessorsForAttributeArguments
helpviewer_keywords:
- CA1019
- DefineAccessorsForAttributeArguments
ms.assetid: 197f2378-3c43-427e-80de-9ec25006c05c
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8a604ea8731108c73c3dfb1c279f2f243c0a05ad
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54931180"
---
# <a name="ca1019-define-accessors-for-attribute-arguments"></a>CA1019: Definire le funzioni di accesso per gli argomenti degli attributi

|||
|-|-|
|TypeName|DefineAccessorsForAttributeArguments|
|CheckId|CA1019|
|Category|Microsoft.Design|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Nel relativo costruttore, un attributo definisce gli argomenti che non dispongono di proprietà corrispondente.

## <a name="rule-description"></a>Descrizione della regola
 Gli attributi possono definire argomenti obbligatori che devono essere specificati quando si applica l'attributo a una destinazione. Sono inoltre noti come argomenti posizionali poiché vengono forniti ai costruttori di attributo come parametri posizionali. Per ogni argomento obbligatorio, l'attributo deve fornire anche una proprietà in sola lettura corrispondente in modo che il valore dell'argomento possa essere recuperato in fase di esecuzione. Questa regola verifica che per ogni parametro di costruttore, è stata definita la proprietà corrispondente.

 Gli attributi possono inoltre definire argomenti facoltativi, noti anche come argomenti denominati. Questi argomenti sono forniti ai costruttori degli attributi in base al nome e devono disporre di una proprietà in lettura e scrittura corrispondente.

 Per gli argomenti obbligatori e facoltativi, le proprietà corrispondenti e i parametri del costruttore devono utilizzare lo stesso nome ma con una diversa maiuscole e minuscole. Le proprietà utilizzano la convenzione Pascal maiuscole e minuscole e maiuscole/minuscole la convenzione camel parametri.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, aggiungere una proprietà di sola lettura per ogni parametro del costruttore che non è presente.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 Eliminare un avviso da questa regola se non si desidera il valore dell'argomento obbligatorio possa essere recuperato.

## <a name="custom-attributes-example"></a>Esempio di attributi personalizzati

Nell'esempio seguente mostra due attributi che definiscono un parametro obbligatorio (posizionale). La prima implementazione dell'attributo è definita in modo errato. La seconda è corretta.

[!code-csharp[FxCop.Design.AttributeAccessors#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_1.cs)]
[!code-vb[FxCop.Design.AttributeAccessors#1](../code-quality/codesnippet/VisualBasic/ca1019-define-accessors-for-attribute-arguments_1.vb)]

## <a name="positional-and-named-arguments"></a>Argomenti posizionali e denominati

Gli argomenti posizionali e denominati rendono chiaro ai consumer della libreria quali sono gli argomenti obbligatori per l'attributo e che gli argomenti sono facoltativi.

Nell'esempio seguente viene illustrata un'implementazione di un attributo con argomenti posizionali e denominati:

[!code-csharp[FxCop.Design.AttributeAccessorsNamed#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_2.cs)]

Nell'esempio seguente viene illustrato come applicare l'attributo personalizzato a due proprietà:

[!code-csharp[FxCop.Design.AttributeAccessorsNamedApplied#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_3.cs)]

## <a name="related-rules"></a>Regole correlate
 [CA1813: Evitare attributi unsealed](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>Vedere anche
 [Attributi](/dotnet/standard/design-guidelines/attributes)