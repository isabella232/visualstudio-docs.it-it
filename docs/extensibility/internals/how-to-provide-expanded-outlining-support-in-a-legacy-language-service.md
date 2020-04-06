---
title: Fornire il supporto della struttura in un servizio di linguaggio Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], outlining support
- language services, supporting outlining
- outlining, supporting
ms.assetid: df759e89-8193-418c-8038-6626304d387b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 37deafa92477289a2124ecee101dd254e68ef01d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707962"
---
# <a name="how-to-provide-expanded-outlining-support-in-a-legacy-language-service"></a>Procedura: fornire il supporto della struttura espansa in un servizio di linguaggio legacyHow to: Provide expanded outlining support in a legacy language service
Sono disponibili due opzioni per estendere il supporto della struttura per il linguaggio oltre al supporto del comando **Comprimi alle definizioni.** È possibile aggiungere aree della struttura controllate dall'editor e aree della struttura controllate dal client.

## <a name="adding-editor-controlled-outline-regions"></a>Aggiunta di aree della struttura controllate dall'editor
 Utilizzare questo approccio per creare un'area della struttura e quindi consentire all'editor di gestire se l'area è espansa, compressa e così via. Delle due opzioni per fornire supporto di struttura, questa opzione è la meno affidabile. Per questa opzione, potete creare una nuova area <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>della struttura su un intervallo di testo specificato utilizzando . Dopo la creazione di questa area, il relativo comportamento è controllato dall'editor. Utilizzare la procedura seguente per implementare aree della struttura controllate dall'editor.

### <a name="to-implement-an-editor-controlled-outline-region"></a>Per implementare un'area della struttura controllata dall'editorTo implement an editor-controlled outline region

1. Invito `QueryService` a chiedere<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>

     Restituisce un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>puntatore a .

2. Chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, passando un puntatore per un buffer di testo specificato. Restituisce un puntatore all'oggetto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> per il buffer.

3. Chiamare <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> per un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession>puntatore a .

4. Chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> per aggiungere una o più nuove aree di struttura alla volta.

     Questo metodo consente di specificare l'intervallo di testo da strutturare, se le aree della struttura esistenti vengono rimosse o mantenute e se l'area della struttura viene espansa o compressa per impostazione predefinita.

## <a name="add-client-controlled-outline-regions"></a>Aggiungere aree della struttura controllate dal client
 Utilizzare questo approccio per implementare la struttura controllata [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] dal [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] client (o intelligente) come quella utilizzata dai servizi di linguaggio e . Un servizio di linguaggio che gestisce la propria struttura monitora il contenuto del buffer di testo per eliminare le aree della struttura precedenti quando diventano non valide e per creare nuove aree della struttura in base alle esigenze.

### <a name="to-implement-a-client-controlled-outline-region"></a>Per implementare un'area della struttura controllata dal clientTo implement a client-controlled outline region

1. Chiamare `QueryService` <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>per . Restituisce un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>puntatore a .

2. Chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, passando un puntatore per un buffer di testo specificato. Questo determina se esiste già una sessione di testo nascosto per il buffer.

3. Se esiste già una sessione di testo, non è necessario crearne una e viene restituito un puntatore all'oggetto esistente. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> Utilizzare questo puntatore per enumerare e creare aree della struttura. In caso <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> contrario, chiamare per creare una sessione di testo nascosto per il buffer. Viene restituito <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> un puntatore all'oggetto.

    > [!NOTE]
    > Quando si <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>chiama , è possibile specificare un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> client di testo nascosto, ovvero un oggetto. Questo client invia una notifica quando un testo nascosto o un'area della struttura viene espansa o compressa dall'utente.

4. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> Parametro struttura chiamata: specificare un valore di <xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE> nel `iType` membro della <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> struttura per indicare che si sta creando un'area della struttura, anziché un'area nascosta. Specificare se l'area è controllata `dwBehavior` dal client <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> o dall'editor nel membro della struttura. L'implementazione della struttura intelligente può contenere una combinazione di aree della struttura controllate dall'editor e dal client. Specificare il testo dell'intestazione che viene visualizzato quando l'area `pszBanner` della <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> struttura è compressa, ad esempio "...", nel membro della struttura. Il testo predefinito del banner dell'editor per un'area nascosta è "...".
