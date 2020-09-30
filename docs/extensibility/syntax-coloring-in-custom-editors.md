---
title: Colorazione della sintassi negli editor personalizzati | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - syntax coloring
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dec1cf1e3ec4301b1f219f7345957877ea420528
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585641"
---
# <a name="syntax-coloring-in-custom-editors"></a>Colorazione della sintassi negli editor personalizzati
Gli editor dell'ambiente Visual Studio SDK, incluso l'editor principale, utilizzano i servizi di linguaggio per identificare elementi sintattici specifici e visualizzarli con i colori specificati per una determinata visualizzazione del documento.

## <a name="colorization-requirements"></a>Requisiti di colorazione
 Tutti gli editor che implementano il colorante di un servizio di linguaggio devono:

1. Utilizzare un oggetto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> che implementa per gestire il testo da colorare e un oggetto che implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> per fornire una visualizzazione documento del testo.

2. Ottenere un'interfaccia per un particolare servizio di linguaggio eseguendo una query sul provider di servizi del VSPackage usando il GUID di identificazione del servizio linguaggi.

3. Chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> metodo dell'oggetto che implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> . Questo metodo associa il servizio di linguaggio all' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> implementazione di utilizzata da Vspackage per gestire il testo da colorare.

## <a name="core-editor-usage-of-a-language-services-colorizer"></a>Utilizzo dell'editor principale del colorante di un servizio di linguaggio
 Quando un servizio di linguaggio con un colorante viene ottenuto da un'istanza dell'editor principale, l'analisi e il rendering del testo da parte del colorante di un servizio di linguaggio si verificano automaticamente senza richiedere ulteriori interventi da parte dell'utente.

 L'IDE in modo trasparente:

- Chiama il coloratore in base alle esigenze per analizzare e analizzare il testo quando viene aggiunto o modificato nell'implementazione di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> .

- Garantisce che la visualizzazione fornita dalla visualizzazione del documento fornita dall' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> implementazione di venga aggiornata e ridisegnata usando le informazioni restituite dal coloratore.

## <a name="non-core-editor-usage-of-a-language-services-colorizer"></a>Utilizzo dell'editor non core del colorante di un servizio di linguaggio
 Le istanze dell'editor non core possono anche usare il servizio di colorazione della sintassi di un servizio di linguaggio, ma devono recuperare e applicare in modo esplicito il colorante del servizio e ridisegnare le visualizzazioni del documento.

 A tale scopo, un editor non core deve:

1. Ottenere un oggetto coloring del servizio di linguaggio, che implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> . Il pacchetto VSPackage esegue questa operazione chiamando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> metodo sull'interfaccia del servizio di linguaggio.

2. Chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metodo per richiedere che un particolare intervallo di testo venga colorato.

     Il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metodo restituisce una matrice di valori, uno per ogni lettera nell'intervallo di testo da colorare. Identifica inoltre l'intervallo di testo come un particolare tipo di elemento colorabile, ad esempio un commento, una parola chiave o un tipo di dati.

3. Usare le informazioni di colorazione restituite da <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> per ridisegnare e visualizzare il relativo testo.

> [!NOTE]
> Oltre a usare il colorante di un servizio di linguaggio, un pacchetto VSPackage può scegliere di usare il meccanismo di colorazione del testo di Visual Studio Environment SDK per utilizzo generico. Per ulteriori informazioni su questo meccanismo, vedere [utilizzo di tipi di carattere e colori](../vs-2015/extensibility/using-fonts-and-colors.md?view=vs-2015&preserve-view=true).

## <a name="see-also"></a>Vedi anche

- [Colorazione della sintassi in un servizio di linguaggio legacy](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Implementazione della colorazione della sintassi](../extensibility/internals/implementing-syntax-coloring.md)
- [Procedura: Usare gli elementi colorabili incorporati](../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [Elementi colorabili personalizzati](../extensibility/internals/custom-colorable-items.md)