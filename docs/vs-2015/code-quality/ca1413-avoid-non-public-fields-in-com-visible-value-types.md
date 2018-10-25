---
title: 'CA1413: Evitare i campi non pubblici nei tipi valore visibili a COM | Microsoft Docs'
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
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
helpviewer_keywords:
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
ms.assetid: 1352e7eb-fefc-4239-8847-25edc7804a54
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 041dbcb355a5aa3bd6925fcabe2d3f815f990890
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49935094"
---
# <a name="ca1413-avoid-non-public-fields-in-com-visible-value-types"></a>CA1413: Evitare i campi non pubblici nei tipi valore visibili a COM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidNonpublicFieldsInComVisibleValueTypes|
|CheckId|CA1413|
|Category|Microsoft.Interoperability|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo di valore contrassegnato specificatamente come visibile al modello COM (Component Object) consente di dichiarare un campo di istanza non pubblici.

## <a name="rule-description"></a>Descrizione della regola
 I campi di istanza non pubblici di tipi di valori visibili a COM sono visibili ai client COM. Esaminare il contenuto del campo per le informazioni che non devono essere esposte o che avrà un effetto indesiderato di progettazione e la protezione.

 Per impostazione predefinita, tutti i tipi di valore pubblico sono visibili a COM. Tuttavia, per ridurre i falsi positivi, questa regola richiede la visibilità COM per essere dichiarata in modo esplicito il tipo. L'assembly che contiene deve essere contrassegnato con il <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> impostata su `false` e il tipo deve essere contrassegnato con il <xref:System.Runtime.InteropServices.ComVisibleAttribute> impostato su `true`.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione della regola e mantenere il campo nascosto, modificare il tipo di valore a un tipo riferimento o rimuovere il <xref:System.Runtime.InteropServices.ComVisibleAttribute> dal tipo di attributo.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se esposizione pubblica del campo è accettabile.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo che viola la regola.

 [!code-csharp[FxCop.Interoperability.NonpublicField#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.NonpublicField/cs/FxCop.Interoperability.NonpublicField.cs#1)]
 [!code-vb[FxCop.Interoperability.NonpublicField#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.NonpublicField/vb/FxCop.Interoperability.NonpublicField.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1407: Evitare i membri statici nei tipi visibili a COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017: Contrassegnare gli assembly con ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Vedere anche
 [Interoperabilità con codice non gestito](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258) [qualificazione di tipi .NET per l'interoperabilità](http://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd)



