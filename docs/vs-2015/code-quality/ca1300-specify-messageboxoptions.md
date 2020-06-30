---
title: 'CA1300: Specificare MessageBoxOptions | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SpecifyMessageBoxOptions
- CA1300
helpviewer_keywords:
- SpecifyMessageBoxOptions
- CA1300
ms.assetid: 9357a724-026e-4a3d-a03a-f14635064ec6
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: af0017a7ee6918a80a93ca90c7cf3de78885d61f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85539191"
---
# <a name="ca1300-specify-messageboxoptions"></a>CA1300: Specificare MessageBoxOptions
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|SpecifyMessageBoxOptions|
|CheckId|CA1300|
|Category|Microsoft. globalizzazione|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
 Un metodo chiama un overload del <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName> metodo che non accetta un <xref:System.Windows.Forms.MessageBoxOptions?displayProperty=fullName> argomento.

## <a name="rule-description"></a>Descrizione della regola
 Per visualizzare correttamente una finestra di messaggio per le impostazioni cultura che utilizzano un ordine di lettura da destra a sinistra, i <xref:System.Windows.Forms.MessageBoxOptions> <xref:System.Windows.Forms.MessageBoxOptions> membri e dell' <xref:System.Windows.Forms.MessageBoxOptions> enumerazione devono essere passati al <xref:System.Windows.Forms.MessageBox.Show%2A> metodo. Esaminare la <xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=fullName> proprietà del controllo che lo contiene per determinare se utilizzare un ordine di lettura da destra a sinistra.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, chiamare un overload del <xref:System.Windows.Forms.MessageBox.Show%2A> metodo che accetta un <xref:System.Windows.Forms.MessageBoxOptions> argomento.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola quando la libreria di codice non verrà localizzata per le impostazioni cultura che utilizzano un ordine di lettura da destra a sinistra.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un metodo che visualizza una finestra di messaggio con opzioni appropriate per l'ordine di lettura delle impostazioni cultura. Per compilare l'esempio, è necessario un file di risorse, che non è visualizzato. Seguire i commenti nell'esempio per compilare l'esempio senza un file di risorse e per testare la funzionalità da destra a sinistra.

 [!code-csharp[FxCop.Globalization.SpecifyMBOptions#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.SpecifyMBOptions/cs/FxCop.Globalization.SpecifyMBOptions.cs#1)]
 [!code-vb[FxCop.Globalization.SpecifyMBOptions#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.SpecifyMBOptions/vb/FxCop.Globalization.SpecifyMBOptions.vb#1)]

## <a name="see-also"></a>Vedere anche
 <xref:System.Resources.ResourceManager?displayProperty=fullName>[Risorse nelle applicazioni desktop](https://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)
