---
title: 'CA1819: Le proprietà non devono restituire matrici | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- PropertiesShouldNotReturnArrays
- CA1819
helpviewer_keywords:
- PropertiesShouldNotReturnArrays
- CA1819
ms.assetid: 85fcf312-57f8-438a-8b10-34441fe0bdeb
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f2f9c46b84da6cb25f04bb862bea8c4dcd81f968
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589989"
---
# <a name="ca1819-properties-should-not-return-arrays"></a>CA1819: Le proprietà non devono restituire matrici
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [CA1819: le proprietà non devono restituire matrici](https://docs.microsoft.com/visualstudio/code-quality/ca1819-properties-should-not-return-arrays).

|||
|-|-|
|TypeName|PropertiesShouldNotReturnArrays|
|CheckId|CA1819|
|Category|Microsoft.Performance|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Una proprietà pubblica o protetta in un tipo pubblico restituisce una matrice.

## <a name="rule-description"></a>Descrizione della regola
 Le matrici restituite dalle proprietà non sono protette in scrittura, anche se la proprietà è di sola lettura. Affinché la matrice sia protetta da eventuali alterazioni, la proprietà deve restituire una copia della matrice. In genere, gli utenti non comprendono le implicazioni negative sulle prestazioni derivanti dalla chiamata di tale proprietà. In particolare, si potrebbe usare la proprietà come una proprietà indicizzata.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, verificare la proprietà di un metodo o modificare le proprietà per restituire una raccolta.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Gli attributi possono contenere proprietà che restituiscono matrici, ma non possono contenere proprietà che restituiscono raccolte. È possibile eliminare un avviso che viene generato per una proprietà di un attributo derivato da [attribute] (<!-- TODO: review code entity reference <xref:assetId:///System.Attribute?qualifyHint=False&amp;autoUpgrade=True>  -->) classe. In caso contrario, non escludere un avviso da questa regola.

## <a name="example-violation"></a>Esempio di violazione

### <a name="description"></a>Descrizione
 Nell'esempio seguente viene illustrata una proprietà che violano questa regola.

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Performance.PropertyArrayViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayViolation/cs/FxCop.Performance.PropertyArrayViolation.cs#1)]
 [!code-vb[FxCop.Performance.PropertyArrayViolation#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayViolation/vb/FxCop.Performance.PropertyArrayViolation.vb#1)]

### <a name="comments"></a>Commenti
 Per correggere una violazione di questa regola, verificare la proprietà di un metodo o modificare le proprietà per restituire una raccolta invece di una matrice.

## <a name="change-the-property-to-a-method-example"></a>Impostare la proprietà su un esempio di metodo

### <a name="description"></a>Descrizione
 Nell'esempio seguente consente di correggere la violazione modificando la proprietà a un metodo.

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Performance.PropertyArrayFixedMethod#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayFixedMethod/cs/FxCop.Performance.PropertyArrayFixedMethod.cs#1)]
 [!code-vb[FxCop.Performance.PropertyArrayFixedMethod#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayFixedMethod/vb/FxCop.Performance.PropertyArrayFixedMethod.vb#1)]

## <a name="return-a-collection-example"></a>Restituisce un raccolta di esempio

### <a name="description"></a>Descrizione
 Nell'esempio seguente la violazione viene corretta modificando la proprietà per restituire un

 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>.

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Performance.PropertyArrayFixedCollection#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayFixedCollection/cs/FxCop.Performance.PropertyArrayFixedCollection.cs#1)]
 [!code-vb[FxCop.Performance.PropertyArrayFixedCollection#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayFixedCollection/vb/FxCop.Performance.PropertyArrayFixedCollection.vb#1)]

## <a name="allowing-users-to-modify-a-property"></a>Consentire agli utenti di modificare una proprietà

### <a name="description"></a>Descrizione
 Si potrebbe voler consentono al consumer della classe modificare una proprietà. Nell'esempio seguente viene illustrata una proprietà di lettura/scrittura che violano questa regola.

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Performance.PropertyModifyViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyModifyViolation/cs/FxCop.Performance.PropertyModifyViolation.cs#1)]
 [!code-vb[FxCop.Performance.PropertyModifyViolation#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyModifyViolation/vb/FxCop.Performance.PropertyModifyViolation.vb#1)]

### <a name="comments"></a>Commenti
 Nell'esempio seguente la violazione viene corretta modificando la proprietà per restituire un <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>.

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Performance.PropertyModifyFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyModifyFixed/cs/FxCop.Performance.PropertyModifyFixed.cs#1)]
 [!code-vb[FxCop.Performance.PropertyModifyFixed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyModifyFixed/vb/FxCop.Performance.PropertyModifyFixed.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1024: Usare proprietà dove appropriato](../code-quality/ca1024-use-properties-where-appropriate.md)


