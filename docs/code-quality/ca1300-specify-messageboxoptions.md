---
title: 'CA1300: Specificare MessageBoxOptions'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 6b72d40bbb2f83eeb8a402b2d389a941f64bfef2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53845376"
---
# <a name="ca1300-specify-messageboxoptions"></a>CA1300: Specificare MessageBoxOptions

|||
|-|-|
|TypeName|SpecifyMessageBoxOptions|
|CheckId|CA1300|
|Category|Microsoft.Globalization|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa

Un metodo chiama un overload del <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName> metodo che non accetta un <xref:System.Windows.Forms.MessageBoxOptions?displayProperty=fullName> argomento.

## <a name="rule-description"></a>Descrizione della regola

Per visualizzare una finestra di messaggio in modo corretto per le lingue che utilizzano un ordine di lettura da destra a sinistra, passare il [MessageBoxOptions. RightAlign](<xref:System.Windows.Forms.MessageBoxOptions.RightAlign>) e [MessageBoxOptions. RtlReading](<xref:System.Windows.Forms.MessageBoxOptions.RtlReading>) campi per il <xref:System.Windows.Forms.MessageBox.Show%2A> metodo. Esaminare il <xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=fullName> proprietà del controllo che lo contiene per determinare se utilizzare un ordine di lettura da destra a sinistra.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, chiamare un overload del <xref:System.Windows.Forms.MessageBox.Show%2A> metodo che accetta un <xref:System.Windows.Forms.MessageBoxOptions> argomento.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

È possibile eliminare un avviso da questa regola quando la libreria di codice non verrà localizzata per una lingua che usa un ordine di lettura da destra a sinistra.

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato un metodo che visualizza una finestra di messaggio con le opzioni appropriate per l'ordine di lettura delle impostazioni cultura. Un file di risorse che non è visibile, è necessario per compilare l'esempio. Seguire i commenti nell'esempio per compilare l'esempio senza un file di risorse e per testare la funzione right-to-left.

[!code-vb[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/VisualBasic/ca1300-specify-messageboxoptions_1.vb)]
[!code-csharp[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/CSharp/ca1300-specify-messageboxoptions_1.cs)]

## <a name="see-also"></a>Vedere anche

- <xref:System.Resources.ResourceManager?displayProperty=fullName>
- [Risorse nelle applicazioni desktop (.NET Framework)](/dotnet/framework/resources/index)