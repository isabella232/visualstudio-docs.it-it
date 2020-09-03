---
title: 'CA1406: evitare gli argomenti Int64 per Visual Basic 6 client | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
helpviewer_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
ms.assetid: d5d0d3fc-f105-43da-be5b-923ab023309c
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b6ab93c24cd97d498ae886c7a9184fd4a5f111f1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534914"
---
# <a name="ca1406-avoid-int64-arguments-for-visual-basic-6-clients"></a>CA1406: Evitare gli argomenti Int64 per i client Visual Basic 6
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|AvoidInt64ArgumentsForVB6Clients|
|CheckId|CA1406|
|Category|Microsoft. interoperabilità|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo contrassegnato in modo specifico come visibile a Component Object Model (COM) dichiara un membro che accetta un <xref:System.Int64?displayProperty=fullName> argomento.

## <a name="rule-description"></a>Descrizione della regola
 I client COM Visual Basic 6 non sono in grado di accedere a Integer a 64 bit.

 Per impostazione predefinita, i seguenti elementi sono visibili a COM: assembly, tipi pubblici, membri di istanze pubbliche nei tipi pubblici e tutti i membri dei tipi di valore pubblici. Tuttavia, per ridurre i falsi positivi, questa regola richiede che la visibilità COM del tipo venga dichiarata in modo esplicito; l'assembly contenitore deve essere contrassegnato con <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> impostato su `false` e il tipo deve essere contrassegnato con <xref:System.Runtime.InteropServices.ComVisibleAttribute> impostato su `true` .

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola per un parametro il cui valore può essere sempre espresso come integrale a 32 bit, modificare il tipo di parametro in <xref:System.Int32?displayProperty=fullName> . Se il valore del parametro potrebbe essere maggiore di quello che può essere espresso come integrale a 32 bit, modificare il tipo di parametro in <xref:System.Decimal?displayProperty=fullName> . Si noti che <xref:System.Single?displayProperty=fullName> e <xref:System.Double?displayProperty=fullName> perdono la precisione in corrispondenza degli intervalli superiori del <xref:System.Int64> tipo di dati. Se il membro non è destinato a essere visibile a COM, contrassegnarlo con <xref:System.Runtime.InteropServices.ComVisibleAttribute> impostato su `false` .

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se è certo che Visual Basic 6 client COM non accederanno al tipo.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo che viola la regola.

 [!code-csharp[FxCop.Interoperability.LongArgument#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LongArgument/cs/FxCop.Interoperability.LongArgument.cs#1)]
 [!code-vb[FxCop.Interoperability.LongArgument#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LongArgument/vb/FxCop.Interoperability.LongArgument.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1413: Evitare i campi non pubblici nei tipi valore visibili a COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

 [CA1407: Evitare i membri statici nei tipi visibili a COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017: Contrassegnare gli assembly con ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Vedere anche
 [Interoperabilità con tipo di dati Long di codice non gestito](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258) [Long Data Type](https://msdn.microsoft.com/library/b4770c34-1804-4f8c-b512-c10b0893e516)
