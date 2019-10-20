---
title: "CA1019: definisce le funzioni di accesso per gli argomenti dell'attributo | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1019
- DefineAccessorsForAttributeArguments
helpviewer_keywords:
- CA1019
- DefineAccessorsForAttributeArguments
ms.assetid: 197f2378-3c43-427e-80de-9ec25006c05c
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 4e77f3a4eec7495e6b4abe13bec93d341f961463
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662005"
---
# <a name="ca1019-define-accessors-for-attribute-arguments"></a>CA1019: Definire le funzioni di accesso per gli argomenti degli attributi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DefineAccessorsForAttributeArguments|
|CheckId|CA1019|
|Category|Microsoft. Design|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
 Nel costruttore, un attributo definisce gli argomenti che non dispongono di proprietà corrispondenti.

## <a name="rule-description"></a>Descrizione della regola
 Gli attributi possono definire argomenti obbligatori che devono essere specificati quando si applica l'attributo a una destinazione. Sono inoltre noti come argomenti posizionali poiché vengono forniti ai costruttori di attributo come parametri posizionali. Per ogni argomento obbligatorio, l'attributo deve fornire anche una proprietà in sola lettura corrispondente in modo che il valore dell'argomento possa essere recuperato in fase di esecuzione. Questa regola consente di controllare che per ogni parametro del costruttore è stata definita la proprietà corrispondente.

 Gli attributi possono inoltre definire argomenti facoltativi, noti anche come argomenti denominati. Questi argomenti sono forniti ai costruttori degli attributi in base al nome e devono disporre di una proprietà in lettura e scrittura corrispondente.

 Per gli argomenti obbligatori e facoltativi, le proprietà e i parametri del costruttore corrispondenti devono usare lo stesso nome ma con maiuscole e minuscole diverse. Le proprietà usano la combinazione di maiuscole e minuscole Pascal e utilizzano la convenzione Camel.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, aggiungere una proprietà di sola lettura per ogni parametro del costruttore che non ne contiene uno.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Eliminare un avviso da questa regola se non si desidera che il valore dell'argomento obbligatorio sia recuperabile.

## <a name="custom-attributes-example"></a>Esempio di attributi personalizzati

### <a name="description"></a>Descrizione
 Nell'esempio seguente vengono illustrati due attributi che definiscono un parametro obbligatorio (posizionale). La prima implementazione dell'attributo è stata definita in modo errato. La seconda implementazione è corretta.

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Design.AttributeAccessors#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessors/cs/FxCop.Design.AttributeAccessors.cs#1)]
 [!code-vb[FxCop.Design.AttributeAccessors#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessors/vb/FxCop.Design.AttributeAccessors.vb#1)]

## <a name="positional-and-named-arguments"></a>Argomenti posizionali e denominati

### <a name="description"></a>Descrizione
 Gli argomenti posizionali e denominati rendono chiaro ai consumer della libreria gli argomenti obbligatori per l'attributo e gli argomenti facoltativi.

 Nell'esempio seguente viene illustrata un'implementazione di un attributo con argomenti sia posizionali che denominati.

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Design.AttributeAccessorsNamed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessorsNamed/cs/FxCop.Design.AttributeAccessorsNamed.cs#1)]

### <a name="comments"></a>Comments
 Nell'esempio seguente viene illustrato come applicare l'attributo personalizzato a due proprietà.

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Design.AttributeAccessorsNamedApplied#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessorsNamedApplied/cs/FxCop.Design.AttributeAccessorsNamedApplied.cs#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1813: Evitare attributi non sealed](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>Vedere anche
 [Attributi](https://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b)
