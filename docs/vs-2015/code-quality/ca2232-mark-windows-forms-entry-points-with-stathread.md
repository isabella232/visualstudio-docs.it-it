---
title: 'CA2232: contrassegnare i punti di ingresso Windows Forms con STAThread | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkWindowsFormsEntryPointsWithStaThread
- CA2232
helpviewer_keywords:
- CA2232
- MarkWindowsFormsEntryPointsWithStaThread
ms.assetid: a3c95130-8e7f-4419-9fcd-b67d077e8efb
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 42bb554f8e57c036d41a89fdc2657a25ecc74e20
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85540283"
---
# <a name="ca2232-mark-windows-forms-entry-points-with-stathread"></a>CA2232: Contrassegnare i punti di ingresso del Windows Form con STAThread
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|MarkWindowsFormsEntryPointsWithStaThread|
|CheckId|CA2232|
|Category|Microsoft. Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un assembly fa riferimento allo <xref:System.Windows.Forms> spazio dei nomi e il punto di ingresso non è contrassegnato con l' <xref:System.STAThreadAttribute?displayProperty=fullName> attributo.

## <a name="rule-description"></a>Descrizione della regola
 <xref:System.STAThreadAttribute> indica che il modello di threading COM per l'applicazione è un Apartment a thread singolo. Questo attributo deve essere presente sul punto di ingresso di qualsiasi applicazione che utilizza Windows Form; se omesso è possibile che il componente Windows non funzioni correttamente. Se l'attributo non è presente, l'applicazione utilizza il modello di Apartment a thread multipli, che non è supportato per Windows Forms.

> [!NOTE]
> [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] i progetti che usano il Framework dell'applicazione non devono contrassegnare il metodo **Main** con STAThread. Il [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] compilatore lo esegue automaticamente.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, aggiungere l' <xref:System.STAThreadAttribute> attributo al punto di ingresso. Se l' <xref:System.MTAThreadAttribute?displayProperty=fullName> attributo è presente, rimuoverlo.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se si sta sviluppando per il .NET Compact Framework, per il quale l' <xref:System.STAThreadAttribute> attributo non è necessario e non è supportato.

## <a name="example"></a>Esempio
 Negli esempi seguenti viene illustrato l'utilizzo corretto di <xref:System.STAThreadAttribute> .

 [!code-csharp[FxCop.Usage.StaThread#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.StaThread/cs/FxCop.Usage.StaThread.cs#1)]
 [!code-vb[FxCop.Usage.StaThread#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.StaThread/vb/FxCop.Usage.StaThread.vb#1)]
