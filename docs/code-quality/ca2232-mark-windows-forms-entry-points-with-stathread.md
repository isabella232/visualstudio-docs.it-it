---
title: 'CA2232: Contrassegnare i punti di ingresso del Windows Form con STAThread'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkWindowsFormsEntryPointsWithStaThread
- CA2232
helpviewer_keywords:
- CA2232
- MarkWindowsFormsEntryPointsWithStaThread
ms.assetid: a3c95130-8e7f-4419-9fcd-b67d077e8efb
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 97c5ad926ecc2a0480a612575eca7e4fe0af31e5
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2018
ms.locfileid: "45551441"
---
# <a name="ca2232-mark-windows-forms-entry-points-with-stathread"></a>CA2232: Contrassegnare i punti di ingresso del Windows Form con STAThread

|||
|-|-|
|TypeName|MarkWindowsFormsEntryPointsWithStaThread|
|CheckId|CA2232|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Fa riferimento a un assembly di <xref:System.Windows.Forms> dello spazio dei nomi e il punto di ingresso non è contrassegnato con il <xref:System.STAThreadAttribute?displayProperty=fullName> attributo.

## <a name="rule-description"></a>Descrizione della regola
 <xref:System.STAThreadAttribute> indica che il modello di threading COM per l'applicazione è un apartment a thread singolo. Questo attributo deve essere presente sul punto di ingresso di qualsiasi applicazione che utilizza Windows Form; se omesso è possibile che il componente Windows non funzioni correttamente. Se l'attributo non è presente, l'applicazione usa il modello di apartment a thread multipli, che non è supportato per Windows Form.

> [!NOTE]
> [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] i progetti che usano il Framework dell'applicazione non sono necessario contrassegnare il **Main** con STAThread (metodo). Il [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] compilatore operazione automaticamente.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, aggiungere il <xref:System.STAThreadAttribute> al punto di ingresso dell'attributo. Se il <xref:System.MTAThreadAttribute?displayProperty=fullName> attributo è presente, rimuoverlo.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 È possibile eliminare un avviso da questa regola se si sviluppa per .NET Compact Framework, per cui il <xref:System.STAThreadAttribute> attributo non è necessario e non è supportato.

## <a name="example"></a>Esempio
 Gli esempi seguenti illustrano l'uso corretto del <xref:System.STAThreadAttribute>:

 [!code-csharp[FxCop.Usage.StaThread#1](../code-quality/codesnippet/CSharp/ca2232-mark-windows-forms-entry-points-with-stathread_1.cs)]
 [!code-vb[FxCop.Usage.StaThread#1](../code-quality/codesnippet/VisualBasic/ca2232-mark-windows-forms-entry-points-with-stathread_1.vb)]