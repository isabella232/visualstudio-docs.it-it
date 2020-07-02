---
title: 'CA2208: creare istanze di eccezioni di argomento corrette | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2208
- InstantiateArgumentExceptionsCorrectly
helpviewer_keywords:
- InstantiateArgumentExceptionsCorrectly
- CA2208
ms.assetid: e2a48939-d9fa-478c-b2f9-3bdbce07dff7
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6a63ebb7f3946926864c4dd882c281b5dcd7c6c5
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85535837"
---
# <a name="ca2208-instantiate-argument-exceptions-correctly"></a>CA2208: Creare istanze di eccezioni di argomento correttamente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|InstantiateArgumentExceptionsCorrectly|
|CheckId|CA2208|
|Category|Microsoft. Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Tra le cause possibili sono incluse le situazioni seguenti:

- Viene eseguita una chiamata al costruttore predefinito (senza parametri) di un tipo di eccezione che è o deriva da [System. ArgumentException] (<!-- TODO: review code entity reference <xref:assetId:///System.ArgumentException?qualifyHint=True&amp;autoUpgrade=True>  -->).

- Un argomento stringa errato viene passato a un costruttore con parametri di un tipo di eccezione che è o deriva da [System. ArgumentException.] (<!-- TODO: review code entity reference <xref:assetId:///System.ArgumentException.?qualifyHint=True&amp;autoUpgrade=True>  -->)

## <a name="rule-description"></a>Descrizione della regola
 Anziché chiamare il costruttore predefinito, chiamare uno degli overload del costruttore che consente di fornire un messaggio di eccezione più significativo. Il messaggio di eccezione deve avere come destinazione lo sviluppatore e spiegare chiaramente la condizione di errore e come correggere o evitare l'eccezione.

 Le firme di uno e due costruttori di stringa di <xref:System.ArgumentException> e dei relativi tipi derivati non sono coerenti rispetto ai `message` `paramName` parametri e. Assicurarsi che questi costruttori vengano chiamati con gli argomenti stringa corretti. Le firme sono le seguenti:

 <xref:System.ArgumentException>(stringa `message` )

 <xref:System.ArgumentException>(String `message` , String `paramName` )

 <xref:System.ArgumentNullException>(stringa `paramName` )

 <xref:System.ArgumentNullException>(String `paramName` , String `message` )

 <xref:System.ArgumentOutOfRangeException>(stringa `paramName` )

 <xref:System.ArgumentOutOfRangeException>(String `paramName` , String `message` )

 <xref:System.DuplicateWaitObjectException>(stringa `parameterName` )

 <xref:System.DuplicateWaitObjectException>(String `parameterName` , String `message` )

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, chiamare un costruttore che accetta un messaggio, un nome di parametro o entrambi e verificare che gli argomenti siano appropriati per il tipo di <xref:System.ArgumentException> chiamata.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola solo se un costruttore con parametri viene chiamato con gli argomenti stringa corretti.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un costruttore che crea erroneamente un'istanza del tipo ArgumentNullException.

 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cpp/FxCop.Usage.InheritedPublic.cpp#1)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cs/FxCop.Usage.InheritedPublic.cs#1)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/vb/FxCop.Usage.InstantiateArgumentExceptionsCorrectly.vb#1)]

## <a name="example"></a>Esempio
 Nell'esempio seguente viene risolta la violazione precedente cambiando gli argomenti del costruttore.

 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cpp/FxCop.Usage.InheritedPublic.cpp#2)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cs/FxCop.Usage.InheritedPublic.cs#2)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/vb/FxCop.Usage.InstantiateArgumentExceptionsCorrectly.vb#2)]
