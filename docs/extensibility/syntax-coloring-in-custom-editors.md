---
title: Colorazione della sintassi negli editor personalizzati | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - syntax coloring
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e5e627d758a1249a1e9b5e877255a67cfb255cf9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62799064"
---
# <a name="syntax-coloring-in-custom-editors"></a>Colorazione della sintassi negli editor personalizzati
Editor di Visual Studio SDK ambiente, tra cui l'editor principale, utilizzare servizi di linguaggio per identificare gli elementi di sintassi specifici e visualizzati con colori specificati per una visualizzazione documento specificata.

## <a name="colorization-requirements"></a>Requisiti di colorazione
 Tutti gli editor implementa colorizzatore del servizio di linguaggio devono:

1. Usare un oggetto che implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> per gestire il testo da colorare e un oggetto che implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> per fornire una visualizzazione del documento di testo.

2. Ottenere un'interfaccia per un servizio di linguaggio specifico eseguendo una query di provider di servizi di un VSPackage utilizzando il GUID di identificazione del servizio lingue.

3. Chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> metodo dell'oggetto che implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>. Questo metodo associa il servizio linguaggio di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> implementazione che usa il pacchetto VSPackage per gestire il testo da colorare.

## <a name="core-editor-usage-of-a-language-services-colorizer"></a>Editor principale di utilizzo del Colorizzatore del servizio di linguaggio
 Quando un servizio di linguaggio con un colorizzatore viene ottenuto da un'istanza di editor principale, l'analisi e il rendering del testo dal colorizzatore del servizio di linguaggio viene eseguita automaticamente senza richiedere alcun ulteriore intervento da parte dell'utente.

 L'IDE in modo trasparente:

- Chiama il colorizzatore in base alle esigenze per analizzare e analizzare il testo come che viene aggiunto o modificato nell'implementazione di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.

- Assicura che la visualizzazione fornita per la visualizzazione del documento fornita dal <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> implementazione è aggiornato e ridisegnato usando le informazioni restituite dal colorizzatore.

## <a name="non-core-editor-usage-of-a-language-services-colorizer"></a>Utilizzo di Editor non core del Colorizzatore del servizio di linguaggio
 Le istanze dell'editor non core possono anche usare servizio di colorazione della sintassi di un servizio di linguaggio, ma sono in modo esplicito deve recuperare e applicare colorizzatore del servizio e le visualizzazioni di documento autonomamente viene ridisegnata.

 A tale scopo, è necessario un editor non core:

1. Ottenere l'oggetto colorizzatore del servizio di linguaggio (che implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>). Il pacchetto VSPackage esegue questa operazione chiamando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> metodo sull'interfaccia del servizio di linguaggio.

2. Chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metodo per richiedere che un determinato intervallo di testo da colorare.

     Il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metodo restituisce una matrice di valori, uno per ogni lettera in testo span viene colorato. Identifica anche l'intervallo di testo come un particolare tipo di elemento colorabile predefinito, ad esempio un commento, parola chiave o tipo di dati.

3. Usare le informazioni di colorazione restituite da <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> ridisegnare e visualizzarne il testo.

> [!NOTE]
> Oltre a usare colorizzatore del servizio di linguaggio, un pacchetto VSPackage può scegliere di usare il meccanismo di colorazione della sintassi testo SDK di ambiente di Visual Studio per utilizzo generico. Per altre informazioni su questo meccanismo, vedere [utilizzando i tipi di carattere e colori](../extensibility/using-fonts-and-colors.md).

## <a name="see-also"></a>Vedere anche

- [Colorazione della sintassi in un servizio di linguaggio legacy](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Implementazione della colorazione della sintassi](../extensibility/internals/implementing-syntax-coloring.md)
- [Procedura: Usare elementi colorabili incorporati](../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [Elementi colorabili personalizzati](../extensibility/internals/custom-colorable-items.md)