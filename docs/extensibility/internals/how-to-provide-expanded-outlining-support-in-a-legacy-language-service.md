---
title: Fornire supporto per la struttura in un servizio di linguaggio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 450ef1430e86467d116cc635a27600756bc36075
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85905289"
---
# <a name="how-to-provide-expanded-outlining-support-in-a-legacy-language-service"></a>Procedura: fornire il supporto per la struttura espansa in un servizio di linguaggio legacy
Sono disponibili due opzioni per estendere il supporto della struttura per il linguaggio oltre al supporto del comando **Comprimi a definizioni** . È possibile aggiungere aree della struttura controllate dall'editor e aggiungere aree della struttura controllate dal client.

## <a name="adding-editor-controlled-outline-regions"></a>Aggiunta di aree del contorno controllate dall'editor
 Usare questo approccio per creare un'area della struttura e quindi consentire all'editor di gestire se l'area è espansa, compressa e così via. Tra le due opzioni per fornire supporto per la struttura, questa opzione è la meno affidabile. Per questa opzione, si crea una nuova area della struttura in un intervallo di testo specificato usando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> . Dopo la creazione di questa area, il relativo comportamento viene controllato dall'editor. Utilizzare la procedura seguente per implementare aree della struttura controllate dall'editor.

### <a name="to-implement-an-editor-controlled-outline-region"></a>Per implementare un'area del contorno controllata dall'editor

1. Chiama `QueryService` per <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>

     Viene restituito un puntatore a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager> .

2. Chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A> , passando un puntatore per un buffer di testo specificato. Viene restituito un puntatore all' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> oggetto per il buffer.

3. Chiamare <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> per un puntatore a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> .

4. Chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> per aggiungere una o più nuove aree della struttura alla volta.

     Questo metodo consente di specificare l'intervallo di testo da delineare, se le aree della struttura esistenti vengono rimosse o mantenute e se l'area della struttura è espansa o compressa per impostazione predefinita.

## <a name="add-client-controlled-outline-regions"></a>Aggiungere aree della struttura controllate dal client
 Usare questo approccio per implementare la struttura controllata dal client (o intelligente) come quella usata dai [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] servizi di [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] linguaggio e. Un servizio di linguaggio che gestisce la propria struttura monitora il contenuto del buffer di testo per eliminare le aree di struttura obsolete quando non sono più valide e per creare nuove aree della struttura in base alle esigenze.

### <a name="to-implement-a-client-controlled-outline-region"></a>Per implementare un'area della struttura controllata dal client

1. Chiamare `QueryService` per <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> . Viene restituito un puntatore a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager> .

2. Chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A> , passando un puntatore per un buffer di testo specificato. Determina se una sessione di testo nascosto esiste già per il buffer.

3. Se una sessione di testo esiste già, non è necessario crearne una e viene restituito un puntatore all'oggetto esistente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> . Utilizzare questo puntatore per enumerare e creare aree della struttura. In caso contrario, chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> per creare una sessione di testo nascosta per il buffer. Viene restituito un puntatore all' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> oggetto.

    > [!NOTE]
    > Quando si chiama <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> , è possibile specificare un client di testo nascosto, ovvero un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> oggetto. Questo client invia una notifica quando un testo nascosto o un'area del contorno viene espansa o compressa dall'utente.

4. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A>Struttura chiamata) parametro: specificare il valore <xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE> nel `iType` membro della <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> struttura per indicare che si sta creando un'area della struttura, anziché un'area nascosta. Consente di specificare se l'area è controllata dal client o dall'editor nel `dwBehavior` membro della <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> struttura. L'implementazione intelligente della struttura può contenere un insieme di aree della struttura controllate dall'editor e dal client. Consente di specificare il testo del banner visualizzato quando l'area della struttura è compressa, ad esempio "...", nel `pszBanner` membro della <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> struttura. Il testo del banner predefinito dell'editor per un'area nascosta è "...".
