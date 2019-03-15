---
title: 'CA1041: Specificare una proprietà ObsoleteAttribute.Message'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1041
- ProvideObsoleteAttributeMessage
helpviewer_keywords:
- ProvideObsoleteAttributeMessage
- CA1041
ms.assetid: be5bee69-d2d2-44e1-be2e-3ea451969003
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: ad693014a7f6c16484f03c2d2f746c8159cf160e
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2019
ms.locfileid: "57873081"
---
# <a name="ca1041-provide-obsoleteattribute-message"></a>CA1041: Specificare una proprietà ObsoleteAttribute.Message

|||
|-|-|
|TypeName|ProvideObsoleteAttributeMessage|
|CheckId|CA1041|
|Category|Microsoft.Design|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa

Un tipo o membro è contrassegnato utilizzando un <xref:System.ObsoleteAttribute?displayProperty=fullName> attributo che non è relativo <xref:System.ObsoleteAttribute.Message%2A?displayProperty=fullName> proprietà specificata.

Per impostazione predefinita, questa regola cerca solo a tipi e membri visibili esternamente, ma si tratta [configurabile](#configurability).

## <a name="rule-description"></a>Descrizione della regola

<xref:System.ObsoleteAttribute> Consente di contrassegnare i membri e tipi di libreria obsoleto. Consumer della libreria è consigliabile evitare l'uso di qualsiasi tipo o membro che è contrassegnato come obsoleto. Si tratta in quanto potrebbero non essere supportata e verranno infine rimosse dalle versioni successive della libreria. Quando un tipo o il membro contrassegnato utilizzando <xref:System.ObsoleteAttribute> viene compilato, la <xref:System.ObsoleteAttribute.Message%2A> proprietà dell'attributo viene visualizzata. In questo modo vengono fornite le informazioni utente sul tipo o sul membro obsoleto. Queste informazioni includono in genere il tempo di tipo obsoleto o membro sarà supportato per le finestre di progettazione di libreria e la sostituzione preferita da usare.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, aggiungere il `message` parametro per il <xref:System.ObsoleteAttribute> costruttore.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

Non escludere un avviso da questa regola poiché il <xref:System.ObsoleteAttribute.Message%2A> proprietà fornisce informazioni essenziali di tipo o membro obsoleto.

## <a name="configurability"></a>Configurabilità

Se si esegue la regola dai [analizzatori FxCop](install-fxcop-analyzers.md) (e non tramite analisi statica del codice), è possibile configurare quali parti della codebase per l'esecuzione di questa regola, in base i criteri di accesso. Ad esempio, per specificare che la regola deve essere eseguito solo per la superficie dell'API non pubblici, aggiungere la coppia chiave-valore seguente a un file con estensione editorconfig nel progetto:

```
dotnet_code_quality.ca1041.api_surface = private, internal
```

È possibile configurare questa opzione per questa regola, per tutte le regole o per tutte le regole in questa categoria (progettazione). Per altre informazioni, vedere [analizzatori FxCop configurare](configure-fxcop-analyzers.md).

## <a name="example"></a>Esempio

L'esempio seguente mostra un membro obsoleto che ha dichiarato in modo corretto <xref:System.ObsoleteAttribute>.

[!code-cpp[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CPP/ca1041-provide-obsoleteattribute-message_1.cpp)]
[!code-csharp[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CSharp/ca1041-provide-obsoleteattribute-message_1.cs)]
[!code-vb[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/VisualBasic/ca1041-provide-obsoleteattribute-message_1.vb)]

## <a name="see-also"></a>Vedere anche

- <xref:System.ObsoleteAttribute?displayProperty=fullName>