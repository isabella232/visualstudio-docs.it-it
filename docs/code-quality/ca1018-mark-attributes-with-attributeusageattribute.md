---
title: 'CA1018: Contrassegnare gli attributi con AttributeUsageAttribute'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
helpviewer_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
ms.assetid: 6ab70ec0-220f-4880-af31-45067703133c
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 133ee073398817c037af95e2009c5acc98e1e5a2
ms.sourcegitcommit: 034c503ae04e22cf840ccb9770bffd012e40fb2d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/14/2019
ms.locfileid: "72306127"
---
# <a name="ca1018-mark-attributes-with-attributeusageattribute"></a>CA1018: Contrassegnare gli attributi con AttributeUsageAttribute

|||
|-|-|
|TypeName|MarkAttributesWithAttributeUsage|
|CheckId|CA1018|
|Category|Microsoft.Design|
|Modifica|Interruzione|

## <a name="cause"></a>Causa
L'attributo <xref:System.AttributeUsageAttribute?displayProperty=fullName> non è presente nell'attributo personalizzato.

## <a name="rule-description"></a>Descrizione della regola
Quando si definisce un attributo personalizzato, contrassegnarlo utilizzando <xref:System.AttributeUsageAttribute> per indicare dove è possibile applicare l'attributo personalizzato nel codice sorgente. Il significato e l'utilizzo previsto di un attributo ne determinano le posizioni valide nel codice. È possibile, ad esempio, definire un attributo che identifichi la persona responsabile della gestione e del miglioramento di ogni tipo in una libreria e che la responsabilità venga sempre assegnata a livello di tipo. In questo caso, i compilatori devono abilitare l'attributo su classi, enumerazioni e interfacce, ma non devono abilitarlo su metodi, eventi o proprietà. I criteri e le procedure aziendali stabiliscono se l'attributo deve essere abilitato negli assembly.

L'enumerazione <xref:System.AttributeTargets?displayProperty=fullName> definisce le destinazioni che è possibile specificare per un attributo personalizzato. Se si omette <xref:System.AttributeUsageAttribute>, l'attributo personalizzato sarà valido per tutte le destinazioni, come definito dal valore `All` dell'enumerazione <xref:System.AttributeTargets>.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Per correggere una violazione di questa regola, specificare le destinazioni per l'attributo utilizzando <xref:System.AttributeUsageAttribute>. Vedere l'esempio seguente.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
È necessario correggere una violazione di questa regola anziché escludere il messaggio. Anche se l'attributo eredita <xref:System.AttributeUsageAttribute>, l'attributo deve essere presente per semplificare la manutenzione del codice.

## <a name="example"></a>Esempio
Nell'esempio seguente vengono definiti due attributi. `BadCodeMaintainerAttribute` omette erroneamente l'istruzione <xref:System.AttributeUsageAttribute> e `GoodCodeMaintainerAttribute` implementa correttamente l'attributo descritto in precedenza in questa sezione. Si noti che la proprietà `DeveloperName` è richiesta dalla regola di progettazione [CA1019: Definire le funzioni di accesso per gli argomenti di attributo @ no__t-0 ed è incluso per completezza.

[!code-csharp[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/CSharp/ca1018-mark-attributes-with-attributeusageattribute_1.cs)]
[!code-vb[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/VisualBasic/ca1018-mark-attributes-with-attributeusageattribute_1.vb)]

## <a name="related-rules"></a>Regole correlate
[CA1019: Definire le funzioni di accesso per gli argomenti dell'attributo @ no__t-0

[CA1813: Evitare gli attributi non sealed @ no__t-0

## <a name="see-also"></a>Vedere anche

- [Attributi](/dotnet/standard/design-guidelines/attributes)