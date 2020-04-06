---
title: 'Procedura: Supportare la struttura in un servizio di linguaggio Legacy Documenti Microsoft'
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
ms.openlocfilehash: 28396d513c83ed83e2769e75a6020a98b10251b4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707911"
---
# <a name="how-to-support-outlining-in-a-legacy-language-service"></a>Procedura: supportare la struttura in un servizio di linguaggio legacyHow to: Support outlining in a legacy language service
La struttura viene utilizzata per espandere o comprimere diverse aree di testo. Il modo in cui viene utilizzata la struttura può essere definito in modo diverso da lingue diverse. Per altre informazioni, vedere [Struttura](../../ide/outlining.md).

 Servizi di linguaggio legacy vengono implementati come parte di un VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio consiste nell'utilizzare le estensioni MEF. Per ulteriori informazioni sul nuovo modo di implementare la struttura, vedere [Procedura dettagliata: struttura](../../extensibility/walkthrough-outlining.md).

> [!NOTE]
> Si consiglia di iniziare a utilizzare la nuova API dell'editor il prima possibile. Ciò migliorerà le prestazioni del servizio di linguaggio e consentirà di sfruttare le nuove funzionalità dell'editor.

 Di seguito viene illustrato come supportare questo comando per il servizio di linguaggio.

## <a name="to-support-outlining"></a>Per supportare la struttura

1. Implementare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage> l'oggetto servizio di linguaggio.

2. Chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> l'oggetto sessione struttura corrente per aggiungere nuove aree della struttura.

## <a name="robust-programming"></a>Programmazione efficiente
 Quando un utente seleziona **Comprimi alle definizioni** nel <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage.CollapseToDefinitions%2A> **struttura** menu, l'IDE chiama sul servizio di linguaggio.

 Quando questo metodo viene chiamato, l'IDE passa un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> puntatore <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> (un puntatore a un buffer di testo) e un (un puntatore alla sessione di struttura corrente).

 È possibile <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> chiamare il metodo per più aree `rgOutlnReg` di struttura specificando queste aree nel parametro. Il `rgOutlnReg` parametro <xref:Microsoft.VisualStudio.TextManager.Interop.NewOutlineRegion> è una struttura. Questo processo consente di specificare caratteristiche diverse dell'area nascosta, ad esempio se una determinata area viene espansa o compressa.

> [!NOTE]
> Prestare attenzione a nascondere i caratteri di nuova riga. Il testo nascosto deve estendersi dall'inizio della prima riga all'ultimo carattere dell'ultima riga di una sezione, lasciando visibile il carattere di nuova riga finale.

## <a name="see-also"></a>Vedere anche
- [Procedura: fornire supporto per testo nascosto in un servizio di linguaggio legacyHow to: Provide hidden text support in a legacy language service](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)
- [Procedura: fornire il supporto della struttura espansa in un servizio di linguaggio legacyHow to: Provide expanded outlining support in a legacy language service](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)
