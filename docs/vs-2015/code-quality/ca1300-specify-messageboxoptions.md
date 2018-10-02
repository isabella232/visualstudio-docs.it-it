---
title: 'CA1300: Specificare MessageBoxOptions | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SpecifyMessageBoxOptions
- CA1300
helpviewer_keywords:
- SpecifyMessageBoxOptions
- CA1300
ms.assetid: 9357a724-026e-4a3d-a03a-f14635064ec6
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: bf2cf17b41248032caf01b0cfedbe9b70ecbefb2
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2018
ms.locfileid: "47590034"
---
# <a name="ca1300-specify-messageboxoptions"></a>CA1300: Specificare MessageBoxOptions
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [CA1300: specificare MessageBoxOptions](https://docs.microsoft.com/visualstudio/code-quality/ca1300-specify-messageboxoptions).

|||
|-|-|
|TypeName|SpecifyMessageBoxOptions|
|CheckId|CA1300|
|Category|Microsoft.Globalization|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Un metodo chiama un overload del <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName> metodo che non accetta un <xref:System.Windows.Forms.MessageBoxOptions?displayProperty=fullName> argomento.

## <a name="rule-description"></a>Descrizione della regola
 Per visualizzare una finestra di messaggio in modo corretto per le lingue che utilizzano un ordine di lettura da destra a sinistra, il <xref:System.Windows.Forms.MessageBoxOptions> e <xref:System.Windows.Forms.MessageBoxOptions> i membri delle <xref:System.Windows.Forms.MessageBoxOptions> enumerazione deve essere passato al <xref:System.Windows.Forms.MessageBox.Show%2A> (metodo). Esaminare il <xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=fullName> proprietà del controllo che lo contiene per determinare se utilizzare un ordine di lettura da destra a sinistra.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, chiamare un overload del <xref:System.Windows.Forms.MessageBox.Show%2A> metodo che accetta un <xref:System.Windows.Forms.MessageBoxOptions> argomento.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola quando la libreria di codice non verrà localizzata per una lingua che usa un ordine di lettura da destra a sinistra.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un metodo che visualizza una finestra di messaggio con le opzioni appropriate per l'ordine di lettura delle impostazioni cultura. Un file di risorse che non è visibile, è necessario per compilare l'esempio. Seguire i commenti nell'esempio per compilare l'esempio senza un file di risorse e per testare la funzione right-to-left.

 [!code-csharp[FxCop.Globalization.SpecifyMBOptions#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.SpecifyMBOptions/cs/FxCop.Globalization.SpecifyMBOptions.cs#1)]
 [!code-vb[FxCop.Globalization.SpecifyMBOptions#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.SpecifyMBOptions/vb/FxCop.Globalization.SpecifyMBOptions.vb#1)]

## <a name="see-also"></a>Vedere anche
 <xref:System.Resources.ResourceManager?displayProperty=fullName> [Risorse nelle App Desktop](http://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)



