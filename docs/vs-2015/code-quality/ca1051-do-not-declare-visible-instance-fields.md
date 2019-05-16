---
title: 'CA1051: Non dichiarare campi di istanza visibili | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
helpviewer_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
ms.assetid: 2805376c-824c-462c-81d1-c51aaf7cabe7
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 96e518977e12f2ae061d5ab73803d51dad733149
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65686816"
---
# <a name="ca1051-do-not-declare-visible-instance-fields"></a>CA1051: Non dichiarare campi di istanza visibili
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotDeclareVisibleInstanceFields|
|CheckId|CA1051|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo visibile esternamente contiene un campo di istanza visibili esternamente.

## <a name="rule-description"></a>Descrizione della regola
 L'utilizzo principale di un campo deve essere come dettaglio di implementazione. I campi devono essere `private` o `internal` e devono essere esposti tramite proprietà. È sufficiente accedere a una proprietà è di accedere a un campo e può modificare il codice in funzioni di accesso di una proprietà come espandono le funzionalità del tipo senza introdurre modifiche di rilievo. Le proprietà che restituiscono il valore di un campo privato o interno sono ottimizzate per l'esecuzione coerente con l'accesso a un campo. molto piccolo miglioramento delle prestazioni è associato l'utilizzo di campi visibili esternamente rispetto alle proprietà.

 Visibile esternamente si intende `public`, `protected`, e `protected internal` (`Public`, `Protected`, e `Protected Friend` in Visual Basic) dei livelli di accessibilità.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, impostare il campo `private` o `internal` ed esporlo tramite una proprietà visibile esternamente.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola. Campi visibili esternamente non offre vantaggi che non sono disponibili per le proprietà. Inoltre, i campi pubblici non possono essere protetti da [richieste di collegamento](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d). Vedere [CA2112: I tipi protetti non devono esporre campi](../code-quality/ca2112-secured-types-should-not-expose-fields.md).

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo (`BadPublicInstanceFields`) che violano questa regola. `GoodPublicInstanceFields` Mostra il codice corretto.

 [!code-csharp[FxCop.Design.TypesPublicInstanceFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TypesPublicInstanceFields/cs/FxCop.Design.TypesPublicInstanceFields.cs#1)]

## <a name="related-rules"></a>Regole correlate
 [CA2112: I tipi protetti non devono esporre campi](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

## <a name="see-also"></a>Vedere anche
 [Richieste di collegamento](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)
