---
title: 'CA1011: considerare il passaggio di tipi di base come parametri | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ConsiderPassingBaseTypesAsParameters
- CA1011
helpviewer_keywords:
- CA1011
- ConsiderPassingBaseTypesAsParameters
ms.assetid: ce1e1241-dcf4-419b-9363-1d5bc4989279
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 3968d81e8ee18b4b0a56bed50f7aa1f121e1c074
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663248"
---
# <a name="ca1011-consider-passing-base-types-as-parameters"></a>CA1011: Considerare il passaggio di tipi di base come parametri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ConsiderPassingBaseTypesAsParameters|
|CheckId|CA1011|
|Category|Microsoft. Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Una dichiarazione di metodo include un parametro formale che è un tipo derivato e il metodo chiama solo i membri del tipo di base del parametro.

## <a name="rule-description"></a>Descrizione della regola
 Quando un tipo di base viene specificato come parametro in una dichiarazione di metodo, qualsiasi tipo derivato dal tipo di base può essere passato al metodo come argomento corrispondente. Quando l'argomento viene utilizzato all'interno del corpo del metodo, il metodo specifico eseguito dipende dal tipo dell'argomento. Se la funzionalità aggiuntiva fornita dal tipo derivato non è obbligatoria, l'utilizzo del tipo di base consente un uso più ampio del metodo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, modificare il tipo di parametro nel relativo tipo di base.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola in modo sicuro

- Se il metodo richiede la funzionalità specifica fornita dal tipo derivato

   \- oppure -

- per applicare che al metodo viene passato solo il tipo derivato o un tipo più derivato.

  In questi casi, il codice sarà più affidabile a causa del controllo del tipo sicuro fornito dal compilatore e dal runtime.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un metodo, `ManipulateFileStream`, che può essere utilizzato solo con un oggetto <xref:System.IO.FileStream>, che viola questa regola. Un secondo metodo, `ManipulateAnyStream`, soddisfa la regola sostituendo il parametro <xref:System.IO.FileStream> usando un <xref:System.IO.Stream>.

 [!code-cpp[FxCop.Design.ConsiderPassingBaseTypes#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ConsiderPassingBaseTypes/cpp/FxCop.Design.ConsiderPassingBaseTypes.cpp#1)]
 [!code-csharp[FxCop.Design.ConsiderPassingBaseTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ConsiderPassingBaseTypes/cs/FxCop.Design.ConsiderPassingBaseTypes.cs#1)]
 [!code-vb[FxCop.Design.ConsiderPassingBaseTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ConsiderPassingBaseTypes/vb/FxCop.Design.ConsiderPassingBaseTypes.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1059: I membri non devono esporre tipi concreti specifici](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)
