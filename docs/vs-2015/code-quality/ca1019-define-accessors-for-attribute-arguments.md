---
title: 'CA1019: Definire funzioni di accesso per gli argomenti degli attributi | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1019
- DefineAccessorsForAttributeArguments
helpviewer_keywords:
- CA1019
- DefineAccessorsForAttributeArguments
ms.assetid: 197f2378-3c43-427e-80de-9ec25006c05c
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ff0329c5c9d565685d4e5c0ff950b31dea3299f6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49854888"
---
# <a name="ca1019-define-accessors-for-attribute-arguments"></a>CA1019: Definire le funzioni di accesso per gli argomenti degli attributi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Eliminare un avviso da questa regola se non si desidera il valore dell'argomento obbligatorio possa essere recuperato.

## <a name="custom-attributes-example"></a>Esempio di attributi personalizzati

### <a name="description"></a>Descrizione
 Nell'esempio seguente mostra due attributi che definiscono un parametro obbligatorio (posizionale). La prima implementazione dell'attributo è definita in modo errato. La seconda è corretta.

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Design.AttributeAccessors#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessors/cs/FxCop.Design.AttributeAccessors.cs#1)]
 [!code-vb[FxCop.Design.AttributeAccessors#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessors/vb/FxCop.Design.AttributeAccessors.vb#1)]

## <a name="positional-and-named-arguments"></a>Argomenti posizionali e denominati

### <a name="description"></a>Descrizione
 Gli argomenti posizionali e denominati rendono più chiaro ai consumer della libreria quali sono gli argomenti obbligatori per l'attributo e che gli argomenti sono facoltativi.

 Nell'esempio seguente viene illustrata un'implementazione di un attributo con argomenti posizionali e denominati.

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Design.AttributeAccessorsNamed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessorsNamed/cs/FxCop.Design.AttributeAccessorsNamed.cs#1)]

### <a name="comments"></a>Commenti
 Nell'esempio seguente viene illustrato come applicare l'attributo personalizzato a due proprietà.

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Design.AttributeAccessorsNamedApplied#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessorsNamedApplied/cs/FxCop.Design.AttributeAccessorsNamedApplied.cs#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1813: Evitare attributi non sealed](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>Vedere anche
 [Attributi](http://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b)



