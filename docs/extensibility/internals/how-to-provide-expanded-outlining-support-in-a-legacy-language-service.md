---
title: Fornire supporto per la struttura in un servizio di linguaggio | Microsoft Docs
description: Informazioni su come fornire il supporto della struttura espansa in un servizio di linguaggio legacy aggiungendo aree struttura controllate dall'editor e aree struttura controllate dal client.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], outlining support
- language services, supporting outlining
- outlining, supporting
ms.assetid: df759e89-8193-418c-8038-6626304d387b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: f3360c51e1cc2e7bc7d9e2841fc2e6f0b1a98077
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122042393"
---
# <a name="how-to-provide-expanded-outlining-support-in-a-legacy-language-service"></a>Procedura: Fornire supporto della struttura espansa in un servizio di linguaggio legacy
Sono disponibili due opzioni per estendere il supporto della struttura per il linguaggio oltre al supporto del **comando Comprimi in** definizioni. È possibile aggiungere aree struttura controllate dall'editor e aree struttura controllate dal client.

## <a name="adding-editor-controlled-outline-regions"></a>Aggiunta di aree struttura controllate dall'editor
 Usare questo approccio per creare un'area della struttura e quindi consentire all'editor di gestire se l'area è espansa, compressa e così via. Tra le due opzioni per fornire il supporto della struttura, questa opzione è la meno affidabile. Per questa opzione, si crea una nuova area della struttura in un intervallo di testo specificato usando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> . Dopo la creazione di questa area, il relativo comportamento viene controllato dall'editor. Usare la procedura seguente per implementare aree struttura controllate dall'editor.

### <a name="to-implement-an-editor-controlled-outline-region"></a>Per implementare un'area della struttura controllata dall'editor

1. Chiamare `QueryService` per <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>

     Verrà restituito un puntatore a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager> .

2. Chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A> , passando un puntatore per un buffer di testo specificato. Restituisce un puntatore <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> all'oggetto per il buffer.

3. Chiamare <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> su per un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> puntatore a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> .

4. Chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> per aggiungere una o più nuove aree struttura alla volta.

     Questo metodo consente di specificare l'intervallo di testo da strutturare, se le aree della struttura esistenti vengono rimosse o mantenute e se l'area della struttura è espansa o compressa per impostazione predefinita.

## <a name="add-client-controlled-outline-regions"></a>Aggiungere aree della struttura controllate dal client
 Usare questo approccio per implementare una struttura controllata dal client (o intelligente) come quella usata dai [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] servizi di linguaggio [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] e . Un servizio di linguaggio che gestisce la propria struttura monitora il contenuto del buffer di testo per eliminare le aree di struttura non più valide quando diventano non valide e per creare nuove aree struttura in base alle esigenze.

### <a name="to-implement-a-client-controlled-outline-region"></a>Per implementare un'area della struttura controllata dal client

1. Chiamare `QueryService` per <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> . Verrà restituito un puntatore a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager> .

2. Chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A> , passando un puntatore per un buffer di testo specificato. Questo determina se esiste già una sessione di testo nascosto per il buffer.

3. Se esiste già una sessione di testo, non è necessario crearne una e viene restituito un puntatore <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> all'oggetto esistente. Usare questo puntatore per enumerare e creare aree struttura. In caso contrario, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> chiamare per creare una sessione di testo nascosto per il buffer. Viene restituito un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> puntatore all'oggetto .

    > [!NOTE]
    > Quando si chiama <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> , è possibile specificare un client di testo nascosto, ovvero un oggetto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> . Questo client invia una notifica quando un'area di testo o struttura nascosta viene espansa o compressa dall'utente.

4. Parametro Struttura chiamata: specificare un valore di nel membro della struttura per indicare che si sta creando un'area della <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE> `iType` <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> struttura, anziché un'area nascosta. Specificare se l'area è controllata dal client o controllata dall'editor nel `dwBehavior` membro della <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> struttura . L'implementazione intelligente della struttura può contenere una combinazione di aree struttura controllate dall'editor e dal client. Specificare il testo del banner visualizzato quando l'area della struttura è compressa, ad esempio "...", nel `pszBanner` membro della <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> struttura . Il testo del banner predefinito dell'editor per un'area nascosta è "...".
