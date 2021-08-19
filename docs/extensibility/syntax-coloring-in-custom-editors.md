---
title: Colorazione della sintassi negli editor personalizzati | Microsoft Docs
description: Informazioni sulla colorazione della sintassi Visual Studio editor personalizzati di Environment SDK, che visualizza i colori specificati per una determinata visualizzazione del documento.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - syntax coloring
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 21710df4971581f95e82ff394b4880c262dd7bf3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122158112"
---
# <a name="syntax-coloring-in-custom-editors"></a>Colorazione della sintassi negli editor personalizzati
Visual Studio Gli editor di Environment SDK, incluso l'editor principale, usano i servizi di linguaggio per identificare elementi sintattici specifici e visualizzarli con i colori specificati per una determinata visualizzazione del documento.

## <a name="colorization-requirements"></a>Requisiti di colorazione
 Tutti gli editor che implementano il colorizer di un servizio di linguaggio devono:

1. Usare un oggetto che implementa per gestire il testo da colorare e un oggetto che implementa per fornire <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> una visualizzazione documento del <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> testo.

2. Ottenere un'interfaccia per un particolare servizio di linguaggio tramite una query sul provider di servizi del pacchetto VSPackage usando il GUID di identificazione del servizio languages.

3. Chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> metodo dell'oggetto che implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> . Questo metodo associa il servizio di linguaggio all'implementazione utilizzata dal pacchetto VSPackage per gestire il testo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> da colorare.

## <a name="core-editor-usage-of-a-language-services-colorizer"></a>Utilizzo dell'editor principale di colorizer di un servizio di linguaggio
 Quando un servizio di linguaggio con colorizer viene ottenuto da un'istanza dell'editor principale, l'analisi e il rendering del testo da parte del colorizer di un servizio di linguaggio si verifica automaticamente senza richiedere ulteriori interventi da parte dell'utente.

 L'IDE in modo trasparente:

- Chiama il colorizer in base alle esigenze per analizzare e analizzare il testo quando viene aggiunto o modificato nell'implementazione di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> .

- Garantisce che la visualizzazione fornita dalla visualizzazione documento fornita dall'implementazione sia aggiornata e ridisegnata usando le informazioni <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> restituite dal colorizer.

## <a name="non-core-editor-usage-of-a-language-services-colorizer"></a>Utilizzo non core dell'editor di colorizer di un servizio di linguaggio
 Le istanze dell'editor non core possono anche usare il servizio di colorazione della sintassi di un servizio di linguaggio, ma devono recuperare e applicare in modo esplicito il colorizer del servizio e ridisegnare le visualizzazioni documento.

 A tale scopo, un editor non core deve:

1. Ottenere l'oggetto colorizer di un servizio di linguaggio (che implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> ). Il pacchetto VSPackage esegue questa operazione chiamando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> il metodo sull'interfaccia del servizio di linguaggio.

2. Chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metodo per richiedere la colorazione di un determinato intervallo di testo.

     Il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metodo restituisce una matrice di valori, uno per ogni lettera nell'intervallo di testo da colorare. Identifica anche l'intervallo di testo come un particolare tipo di elemento colorabile, ad esempio un commento, una parola chiave o un tipo di dati.

3. Usare le informazioni sulla colorazione restituite da <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> per ridisegnare e visualizzare il testo.

> [!NOTE]
> Oltre a usare il colorizer di un servizio di linguaggio, un pacchetto VSPackage può scegliere di usare il meccanismo di colorazione del testo dell Visual Studio Environment SDK per utilizzo generico. Per altre informazioni su questo meccanismo, vedere [Uso di tipi di carattere e colori](/previous-versions/visualstudio/visual-studio-2015/extensibility/using-fonts-and-colors?preserve-view=true&view=vs-2015).

## <a name="see-also"></a>Vedi anche

- [Colorazione della sintassi in un servizio di linguaggio legacy](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Implementazione della colorazione della sintassi](../extensibility/internals/implementing-syntax-coloring.md)
- [Procedura: Usare gli elementi colorabili incorporati](../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [Elementi colorabili personalizzati](../extensibility/internals/custom-colorable-items.md)