---
title: 'CA1011: Provare a passare tipi di base come parametri'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ConsiderPassingBaseTypesAsParameters
- CA1011
helpviewer_keywords:
- CA1011
- ConsiderPassingBaseTypesAsParameters
ms.assetid: ce1e1241-dcf4-419b-9363-1d5bc4989279
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: dcb5937f58088684e7bfc204ab4143434b0684ae
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236400"
---
# <a name="ca1011-consider-passing-base-types-as-parameters"></a>CA1011: Provare a passare tipi di base come parametri

|||
|-|-|
|TypeName|ConsiderPassingBaseTypesAsParameters|
|CheckId|CA1011|
|Category|Microsoft.Design|
|Modifica|Interruzione|

## <a name="cause"></a>Causa

Una dichiarazione di metodo include un parametro formale che è un tipo derivato e il metodo chiama solo i membri del tipo di base del parametro.

## <a name="rule-description"></a>Descrizione della regola

Quando un tipo di base viene specificato come parametro in una dichiarazione di metodo, qualsiasi tipo derivato dal tipo di base può essere passato al metodo come argomento corrispondente. Quando l'argomento viene utilizzato all'interno del corpo del metodo, il metodo specifico eseguito dipende dal tipo dell'argomento. Se la funzionalità aggiuntiva fornita dal tipo derivato non è obbligatoria, l'utilizzo del tipo di base consente un uso più ampio del metodo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, modificare il tipo di parametro nel relativo tipo di base.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

È possibile eliminare un avviso da questa regola in modo sicuro

- Se il metodo richiede la funzionalità specifica fornita dal tipo derivato

     \- oppure -

- per applicare che al metodo viene passato solo il tipo derivato o un tipo più derivato.

In questi casi, il codice sarà più affidabile a causa del controllo del tipo sicuro fornito dal compilatore e dal runtime.

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato un metodo `ManipulateFileStream`,, che può essere utilizzato solo con <xref:System.IO.FileStream> un oggetto che viola questa regola. Un secondo metodo, `ManipulateAnyStream`, soddisfa la regola sostituendo il <xref:System.IO.FileStream> parametro utilizzando un oggetto <xref:System.IO.Stream>.

[!code-csharp[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/CSharp/ca1011-consider-passing-base-types-as-parameters_1.cs)]
[!code-cpp[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/CPP/ca1011-consider-passing-base-types-as-parameters_1.cpp)]
[!code-vb[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1011-consider-passing-base-types-as-parameters_1.vb)]

## <a name="related-rules"></a>Regole correlate

[CA1059: I membri non devono esporre tipi concreti specifici](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)