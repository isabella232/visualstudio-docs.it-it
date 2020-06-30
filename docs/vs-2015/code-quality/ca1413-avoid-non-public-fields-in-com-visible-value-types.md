---
title: 'CA1413: evitare i campi non pubblici nei tipi valore visibili a COM | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
helpviewer_keywords:
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
ms.assetid: 1352e7eb-fefc-4239-8847-25edc7804a54
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1054330b26cf145ebcbc943a56dc699fe793999f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548460"
---
# <a name="ca1413-avoid-non-public-fields-in-com-visible-value-types"></a>CA1413: Evitare i campi non pubblici nei tipi valore visibili a COM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|AvoidNonpublicFieldsInComVisibleValueTypes|
|CheckId|CA1413|
|Category|Microsoft. interoperabilità|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo di valore che viene contrassegnato in modo specifico come visibile a Component Object Model (COM) dichiara un campo di istanza non pubblico.

## <a name="rule-description"></a>Descrizione della regola
 I campi di istanza non pubblici di tipi di valori visibili a COM sono visibili ai client COM. Esaminare il contenuto del campo per ottenere informazioni che non devono essere esposte o che avranno un effetto di progettazione o di sicurezza imprevisto.

 Per impostazione predefinita, tutti i tipi di valore pubblico sono visibili a COM. Tuttavia, per ridurre i falsi positivi, questa regola richiede che la visibilità COM del tipo venga dichiarata in modo esplicito. L'assembly contenitore deve essere contrassegnato con <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> impostato su `false` e il tipo deve essere contrassegnato con <xref:System.Runtime.InteropServices.ComVisibleAttribute> impostato su `true` .

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola e lasciare il campo nascosto, modificare il tipo di valore in un tipo riferimento o rimuovere l' <xref:System.Runtime.InteropServices.ComVisibleAttribute> attributo dal tipo.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se l'esposizione pubblica del campo è accettabile.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo che viola la regola.

 [!code-csharp[FxCop.Interoperability.NonpublicField#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.NonpublicField/cs/FxCop.Interoperability.NonpublicField.cs#1)]
 [!code-vb[FxCop.Interoperability.NonpublicField#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.NonpublicField/vb/FxCop.Interoperability.NonpublicField.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1407: Evitare i membri statici nei tipi visibili a COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017: Contrassegnare gli assembly con ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Vedere anche
 [Interoperabilità con codice non gestito](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258) [qualificazione di tipi .NET per l'interoperabilità](https://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd)
