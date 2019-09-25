---
title: 'CA2232: Contrassegnare i punti di ingresso del Windows Form con STAThread'
ms.date: 11/04/2016
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
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 06772f8dd91c27834b329293d06cfbc2a7dcfcef
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71230763"
---
# <a name="ca2232-mark-windows-forms-entry-points-with-stathread"></a>CA2232: Contrassegnare i punti di ingresso del Windows Form con STAThread

|||
|-|-|
|TypeName|MarkWindowsFormsEntryPointsWithStaThread|
|CheckId|CA2232|
|Category|Microsoft.Usage|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa
Un assembly fa riferimento <xref:System.Windows.Forms> allo spazio dei nomi e il punto di ingresso non è <xref:System.STAThreadAttribute?displayProperty=fullName> contrassegnato con l'attributo.

## <a name="rule-description"></a>Descrizione della regola
 <xref:System.STAThreadAttribute>indica che il modello di threading COM per l'applicazione è un Apartment a thread singolo. Questo attributo deve essere presente sul punto di ingresso di qualsiasi applicazione che utilizza Windows Form; se omesso è possibile che il componente Windows non funzioni correttamente. Se l'attributo non è presente, l'applicazione utilizza il modello di Apartment a thread multipli, che non è supportato per Windows Forms.

> [!NOTE]
> [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]i progetti che usano il Framework dell'applicazione non devono contrassegnare il metodo **Main** con STAThread. Il [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] compilatore lo esegue automaticamente.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Per correggere una violazione di questa regola, aggiungere l' <xref:System.STAThreadAttribute> attributo al punto di ingresso. Se l' <xref:System.MTAThreadAttribute?displayProperty=fullName> attributo è presente, rimuoverlo.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
È possibile eliminare un avviso da questa regola se si sta sviluppando per il .NET Compact Framework, per il quale l' <xref:System.STAThreadAttribute> attributo non è necessario e non è supportato.

## <a name="example"></a>Esempio
Negli esempi seguenti viene illustrato l'utilizzo corretto <xref:System.STAThreadAttribute>di:

[!code-csharp[FxCop.Usage.StaThread#1](../code-quality/codesnippet/CSharp/ca2232-mark-windows-forms-entry-points-with-stathread_1.cs)]
[!code-vb[FxCop.Usage.StaThread#1](../code-quality/codesnippet/VisualBasic/ca2232-mark-windows-forms-entry-points-with-stathread_1.vb)]