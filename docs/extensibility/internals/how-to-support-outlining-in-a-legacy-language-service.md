---
title: 'Procedura: supportare la struttura in un servizio di linguaggio legacy | Microsoft Docs'
description: Informazioni su come fornire supporto per la struttura, l'espansione o la compressione di diverse aree di testo in un servizio di linguaggio legacy.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], collapse to definitions command
- language services, supporting Collapse to Definitions command
- hidden text, Collapse to Definitions command
ms.assetid: bb6e74c3-93e4-4ef7-afc7-1c9b342f083b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c9d1d7b7a74b6565c666e4d5e3293caaef3c7732
ms.sourcegitcommit: 2f964946d7044cc7d49b3fc10b413ca06cb2d11b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/07/2020
ms.locfileid: "96761322"
---
# <a name="how-to-support-outlining-in-a-legacy-language-service"></a>Procedura: supportare la struttura in un servizio di linguaggio legacy
La struttura viene utilizzata per espandere o comprimere aree diverse del testo. Il modo in cui viene utilizzata la struttura può essere definito in modo diverso da linguaggi diversi. Per altre informazioni, vedere [Struttura](../../ide/outlining.md).

 I servizi di linguaggio legacy sono implementati come parte di un pacchetto VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio consiste nell'usare le estensioni MEF. Per ulteriori informazioni sul nuovo metodo di implementazione della struttura, vedere [procedura dettagliata: struttura](../../extensibility/walkthrough-outlining.md).

> [!NOTE]
> Si consiglia di iniziare a usare la nuova API editor appena possibile. Ciò consente di migliorare le prestazioni del servizio di linguaggio e di sfruttare i vantaggi delle nuove funzionalità dell'editor.

 Di seguito viene illustrato come supportare questo comando per il servizio di linguaggio.

## <a name="to-support-outlining"></a>Per supportare la struttura

1. Implementare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage> nell'oggetto servizio di linguaggio.

2. Chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> sull'oggetto sessione della struttura corrente per aggiungere nuove aree della struttura.

## <a name="robust-programming"></a>Programmazione efficiente
 Quando un utente seleziona **Comprimi a definizioni** nel menu **struttura** , l'IDE chiama il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage.CollapseToDefinitions%2A> servizio di linguaggio.

 Quando viene chiamato questo metodo, l'IDE passa un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> puntatore (un puntatore a un buffer di testo) e un oggetto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> (un puntatore alla sessione di struttura corrente).

 È possibile chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> metodo per più aree della struttura specificando queste aree nel `rgOutlnReg` parametro. Il `rgOutlnReg` parametro è una <xref:Microsoft.VisualStudio.TextManager.Interop.NewOutlineRegion> struttura. Questo processo consente di specificare caratteristiche diverse dell'area nascosta, ad esempio se un'area specifica viene espansa o compressa.

> [!NOTE]
> Prestare attenzione a nascondere i caratteri di nuova riga. Il testo nascosto deve estendersi dall'inizio della prima riga fino all'ultimo carattere dell'ultima riga di una sezione, lasciando visibile il carattere di nuova riga finale.

## <a name="see-also"></a>Vedi anche
- [Procedura: fornire il supporto per testo nascosto in un servizio di linguaggio legacy](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)
- [Procedura: fornire il supporto per la struttura espansa in un servizio di linguaggio legacy](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)
