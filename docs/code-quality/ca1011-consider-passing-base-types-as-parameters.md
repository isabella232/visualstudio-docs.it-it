---
title: 'CA1011: Considerare il passaggio di tipi di base come parametri'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: b968a94b76f0b2161eef84fdad2cf01288165e65
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49899409"
---
# <a name="ca1011-consider-passing-base-types-as-parameters"></a>CA1011: Considerare il passaggio di tipi di base come parametri

|||
|-|-|
|TypeName|ConsiderPassingBaseTypesAsParameters|
|CheckId|CA1011|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa

Una dichiarazione di metodo include un parametro formale che è un tipo derivato e il metodo viene chiamato solo i membri del tipo di base del parametro.

## <a name="rule-description"></a>Descrizione della regola

Quando un tipo di base viene specificato come parametro in una dichiarazione di metodo, qualsiasi tipo derivato dal tipo di base può essere passato al metodo come argomento corrispondente. Quando l'argomento viene usato all'interno del corpo del metodo, il metodo specifico che viene eseguito dipende dal tipo dell'argomento. Se la funzionalità aggiuntiva fornita dal tipo derivato non è obbligatorio, utilizzo del tipo di base consente un utilizzo più ampio del metodo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, modificare il tipo del parametro al tipo di base.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

È possibile eliminare un avviso da questa regola

- Se il metodo richiede la funzionalità specifica fornita dal tipo derivato

     \- oppure -

- Per imporre che solo il tipo derivato o un tipo più derivato, viene passato al metodo.

In questi casi, il codice sarà più affidabile a causa di tipo sicuro controllo fornito dal compilatore e runtime.

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato un metodo, `ManipulateFileStream`, che può essere utilizzato solo con un <xref:System.IO.FileStream> oggetto, che viola la regola. Un secondo metodo, `ManipulateAnyStream`, soddisfa la regola, sostituendo il <xref:System.IO.FileStream> parametro utilizzando un <xref:System.IO.Stream>.

[!code-csharp[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/CSharp/ca1011-consider-passing-base-types-as-parameters_1.cs)]
[!code-cpp[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/CPP/ca1011-consider-passing-base-types-as-parameters_1.cpp)]
[!code-vb[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1011-consider-passing-base-types-as-parameters_1.vb)]

## <a name="related-rules"></a>Regole correlate

[CA1059: I membri non devono esporre tipi concreti specifici](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)