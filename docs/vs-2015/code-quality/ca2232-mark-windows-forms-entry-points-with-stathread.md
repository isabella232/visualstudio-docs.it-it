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
ms.openlocfilehash: 084e7a093f92aa8eda9d9edc11865ac319adfad0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662786"
---
# <a name="ca2232-mark-windows-forms-entry-points-with-stathread"></a>CA2232: Contrassegnare i punti di ingresso del Windows Form con STAThread
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkWindowsFormsEntryPointsWithStaThread|
|CheckId|CA2232|
|Category|Microsoft. Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un assembly fa riferimento allo spazio dei nomi <xref:System.Windows.Forms> e il punto di ingresso non è contrassegnato con l'attributo <xref:System.STAThreadAttribute?displayProperty=fullName>.

## <a name="rule-description"></a>Descrizione della regola
 <xref:System.STAThreadAttribute> indica che il modello di threading COM per l'applicazione è un Apartment a thread singolo. Questo attributo deve essere presente sul punto di ingresso di qualsiasi applicazione che utilizza Windows Form; se omesso è possibile che il componente Windows non funzioni correttamente. Se l'attributo non è presente, l'applicazione utilizza il modello di Apartment a thread multipli, che non è supportato per Windows Forms.

> [!NOTE]
> [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] progetti che usano il Framework dell'applicazione non devono contrassegnare il metodo **Main** con STAThread. Il compilatore [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] lo esegue automaticamente.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, aggiungere l'attributo <xref:System.STAThreadAttribute> al punto di ingresso. Se è presente l'attributo <xref:System.MTAThreadAttribute?displayProperty=fullName>, rimuoverlo.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se si sta sviluppando per il .NET Compact Framework, per cui l'attributo <xref:System.STAThreadAttribute> non è necessario e non è supportato.

## <a name="example"></a>Esempio
 Negli esempi seguenti viene illustrato l'utilizzo corretto di <xref:System.STAThreadAttribute>.

 [!code-csharp[FxCop.Usage.StaThread#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.StaThread/cs/FxCop.Usage.StaThread.cs#1)]
 [!code-vb[FxCop.Usage.StaThread#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.StaThread/vb/FxCop.Usage.StaThread.vb#1)]
