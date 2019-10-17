---
title: 'CA1300: Specificare MessageBoxOptions'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SpecifyMessageBoxOptions
- CA1300
helpviewer_keywords:
- SpecifyMessageBoxOptions
- CA1300
ms.assetid: 9357a724-026e-4a3d-a03a-f14635064ec6
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 4403b1f565698ae170bbccf152d5866250c0f114
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444448"
---
# <a name="ca1300-specify-messageboxoptions"></a>CA1300: Specificare MessageBoxOptions

|||
|-|-|
|TypeName|SpecifyMessageBoxOptions|
|CheckId|CA1300|
|Category|Microsoft. globalizzazione|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa

Un metodo chiama un overload del metodo <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName> che non accetta un argomento <xref:System.Windows.Forms.MessageBoxOptions?displayProperty=fullName>.

## <a name="rule-description"></a>Descrizione della regola

Per visualizzare correttamente una finestra di messaggio per le impostazioni cultura che utilizzano un ordine di lettura da destra a sinistra, passare i campi [MessageBoxOptions. RightAlign](<xref:System.Windows.Forms.MessageBoxOptions.RightAlign>) e [MessageBoxOptions. RtlReading](<xref:System.Windows.Forms.MessageBoxOptions.RtlReading>) al metodo <xref:System.Windows.Forms.MessageBox.Show%2A>. Esaminare la proprietà <xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=fullName> del controllo che lo contiene per determinare se utilizzare un ordine di lettura da destra a sinistra.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, chiamare un overload del metodo <xref:System.Windows.Forms.MessageBox.Show%2A> che accetta un argomento <xref:System.Windows.Forms.MessageBoxOptions>.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

È possibile eliminare un avviso da questa regola quando la libreria di codice non verrà localizzata per le impostazioni cultura che utilizzano un ordine di lettura da destra a sinistra.

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato un metodo che visualizza una finestra di messaggio con opzioni appropriate per l'ordine di lettura delle impostazioni cultura. Per compilare l'esempio, è necessario un file di risorse, che non è visualizzato. Seguire i commenti nell'esempio per compilare l'esempio senza un file di risorse e per testare la funzionalità da destra a sinistra.

[!code-vb[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/VisualBasic/ca1300-specify-messageboxoptions_1.vb)]
[!code-csharp[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/CSharp/ca1300-specify-messageboxoptions_1.cs)]

## <a name="see-also"></a>Vedere anche

- <xref:System.Resources.ResourceManager?displayProperty=fullName>
- [Risorse nelle applicazioni desktop (.NET Framework)](/dotnet/framework/resources/index)
