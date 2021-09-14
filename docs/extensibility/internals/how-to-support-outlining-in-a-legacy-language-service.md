---
title: 'Procedura: Supportare la struttura in un servizio di linguaggio legacy | Microsoft Docs'
description: Informazioni su come fornire supporto per la struttura, l'espansione o la compressione di aree di testo diverse, in un servizio di linguaggio legacy.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], collapse to definitions command
- language services, supporting Collapse to Definitions command
- hidden text, Collapse to Definitions command
ms.assetid: bb6e74c3-93e4-4ef7-afc7-1c9b342f083b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: cef8f5520ebd0034ff5d8852129b1f076bf53b28
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126711758"
---
# <a name="how-to-support-outlining-in-a-legacy-language-service"></a>Procedura: Supportare la struttura in un servizio di linguaggio legacy
La struttura viene usata per espandere o comprimere aree di testo diverse. Il modo in cui viene usata la struttura può essere definito in modo diverso da linguaggi diversi. Per altre informazioni, vedere [Struttura](../../ide/outlining.md).

 I servizi di linguaggio legacy vengono implementati come parte di un pacchetto VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio è usare le estensioni MEF. Per altre informazioni sul nuovo modo di implementare la struttura, vedere [Procedura dettagliata: struttura .](../../extensibility/walkthrough-outlining.md)

> [!NOTE]
> È consigliabile iniziare a usare la nuova API dell'editor appena possibile. In questo modo si miglioreranno le prestazioni del servizio di linguaggio e si potranno sfruttare le nuove funzionalità dell'editor.

 Di seguito viene illustrato come supportare questo comando per il servizio di linguaggio.

## <a name="to-support-outlining"></a>Per supportare la struttura

1. Implementare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage> nell'oggetto del servizio di linguaggio.

2. Chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> sull'oggetto sessione di struttura corrente per aggiungere nuove aree della struttura.

## <a name="robust-programming"></a>Programmazione efficiente
 Quando un utente seleziona **Comprimi in definizioni** dal menu **Struttura,** l'IDE chiama <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage.CollapseToDefinitions%2A> il servizio di linguaggio.

 Quando viene chiamato questo metodo, l'IDE passa un puntatore (un puntatore a un buffer di testo) e un (un puntatore alla <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> sessione di struttura corrente).

 È possibile chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> il metodo per più aree della struttura specificando queste aree nel parametro `rgOutlnReg` . Il `rgOutlnReg` parametro è una struttura <xref:Microsoft.VisualStudio.TextManager.Interop.NewOutlineRegion> . Questo processo consente di specificare caratteristiche diverse dell'area nascosta, ad esempio se una determinata area è espansa o compressa.

> [!NOTE]
> Prestare attenzione a nascondere i caratteri di nuova riga. Il testo nascosto deve estendersi dall'inizio della prima riga all'ultimo carattere dell'ultima riga di una sezione, lasciando visibile il carattere finale della nuova riga.

## <a name="see-also"></a>Vedi anche
- [Procedura: Fornire il supporto del testo nascosto in un servizio di linguaggio legacy](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)
- [Procedura: Fornire supporto della struttura espansa in un servizio di linguaggio legacy](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)
