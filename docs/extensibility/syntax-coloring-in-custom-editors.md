---
title: Colorazione della sintassi negli editor personalizzati Documenti Microsoft
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
ms.openlocfilehash: 6296c8451684a121ac42dbde6619c0ebbb421908
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699330"
---
# <a name="syntax-coloring-in-custom-editors"></a>Colorazione della sintassi negli editor personalizzati
Gli editor di Visual Studio Environment SDK, incluso l'editor principale, usano i servizi di linguaggio per identificare elementi sintattici specifici e visualizzarli con colori specificati per una determinata visualizzazione del documento.

## <a name="colorization-requirements"></a>Requisiti di colorazione
 Tutti gli editor che implementano il colorizer di un servizio di linguaggio devono:All editors implementing a language service's colorizer must:

1. Utilizzare un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> oggetto che implementa per gestire il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> testo da colorare e un oggetto che implementa per fornire una visualizzazione del documento del testo.

2. Ottenere un'interfaccia a un servizio di linguaggio specifico eseguendo una query provider di servizi del pacchetto VSPackage utilizzando il GUID di identificazione del servizio di lingue.

3. Chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> il metodo dell'oggetto che implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>. Questo metodo associa il servizio <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> di linguaggio con l'implementazione che utilizza il pacchetto VSPackage per gestire il testo che deve essere colorato.

## <a name="core-editor-usage-of-a-language-services-colorizer"></a>Utilizzo dell'Editor di base di un servizio di linguaggioCore Editor Usage of a Language Service's Colorizer
 Quando un servizio di linguaggio con un colorizer viene ottenuto da un'istanza dell'editor principale, l'analisi e il rendering del testo dal colorizer di un servizio di linguaggio avviene automaticamente senza richiedere alcun ulteriore intervento da parte dell'utente.

 L'IDE in modo trasparente:

- Chiama il colorizer in base alle esigenze per analizzare e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>analizzare il testo quando viene aggiunto o modificato nell'implementazione di .

- Garantisce che la visualizzazione fornita dalla visualizzazione <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> del documento fornita dall'implementazione venga aggiornata e ridisegnata utilizzando le informazioni restituite dal colorizer.

## <a name="non-core-editor-usage-of-a-language-services-colorizer"></a>Utilizzo non-core Editor di un servizio di linguaggio
 Le istanze dell'editor non di base possono anche usare il servizio di colorazione della sintassi di un servizio di linguaggio, ma devono recuperare e applicare in modo esplicito il colorizer del servizio e ridisegnare autonomamente le visualizzazioni del documento.

 A tale scopo, un editor non-core deve:To do this, a non-core editor must:

1. Ottenere un oggetto colorizer del servizio <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>di linguaggio (che implementa e ). Il pacchetto VSPackage esegue <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> questa operazione chiamando il metodo sull'interfaccia del servizio di linguaggio.

2. Chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> il metodo per richiedere la colorazione di un determinato intervallo di testo.

     Il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metodo restituisce una matrice di valori, uno per ogni lettera nell'intervallo di testo da colorare. Identifica inoltre l'intervallo di testo come un particolare tipo di elemento colorabile, ad esempio un commento, una parola chiave o un tipo di dati.

3. Utilizzare le informazioni di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> colorazione restituite da per ridisegnare e visualizzare il testo.

> [!NOTE]
> Oltre a usare il colorizer di un servizio di linguaggio, un VSPackage può scegliere di utilizzare il meccanismo di colorazione del testo di Visual Studio Environment SDK generico. Per ulteriori informazioni su questo meccanismo, consultate Utilizzo di tipi di [carattere e colori.](/visualstudio/extensibility/using-fonts-and-colors?view=vs-2015)

## <a name="see-also"></a>Vedere anche

- [Colorazione della sintassi in un servizio di linguaggio legacy](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Implementazione della colorazione della sintassi](../extensibility/internals/implementing-syntax-coloring.md)
- [Procedura: Usare gli elementi colorabili incorporati](../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [Elementi colorabili personalizzati](../extensibility/internals/custom-colorable-items.md)
