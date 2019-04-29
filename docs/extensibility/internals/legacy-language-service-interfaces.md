---
title: Interfacce del servizio di linguaggio legacy | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IVsLanguageInfo interface
- language services, objects
ms.assetid: 03b2d507-f463-417e-bc22-bdac68eeda52
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c5c907885e91cc3b7765ff94528a30a84b17ee46
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62909565"
---
# <a name="legacy-language-service-interfaces"></a>Interfacce dei servizi di linguaggio legacy
Per qualsiasi linguaggio di programmazione specifico, può essere solo un'istanza di un servizio di linguaggio alla volta. Tuttavia, un servizio di linguaggio singolo può essere usato più di un editor.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] non associa un servizio di linguaggio con un editor specifico. Pertanto, quando si richiede un'operazione del servizio linguaggio, è necessario identificare l'editor appropriato come parametro.

## <a name="common-interfaces-associated-with-language-services"></a>Interfacce comuni associate ai servizi di linguaggio
 L'editor Ottiene il servizio di linguaggio chiamando <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> nel pacchetto VSPackage appropriato. Il servizio con ID (SID) vengono passate in questa chiamata identifica il servizio di linguaggio richiesto.

 È possibile implementare le interfacce del servizio del linguaggio core su un numero qualsiasi di classi separate. Tuttavia, un approccio comune consiste nell'implementare le interfacce seguenti in una singola classe:

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageBlock> (facoltativo)

  Il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interfaccia deve essere implementata in tutti i servizi di linguaggio. Fornisce informazioni sul servizio linguaggio, ad esempio il nome localizzato del linguaggio, le estensioni di file associati al servizio di linguaggio e come recuperare un colorizzatore.

## <a name="additional-language-service-interfaces"></a>Interfacce di servizio di linguaggio aggiuntivo
 Le altre interfacce possono essere forniti con il servizio di linguaggio. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] richiede un'istanza separata di queste interfacce per ogni istanza del buffer di testo. Pertanto, è necessario implementare ognuna di queste interfacce nel proprio oggetto. La tabella seguente mostra le interfacce che richiedono un'istanza per ogni istanza di buffer di testo.

|Interfaccia|Descrizione|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Consente di gestire aree di controllo finestra di codice, ad esempio la barra di riepilogo a discesa. È possibile ottenere questa interfaccia tramite il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> (metodo). È presente un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> per ogni finestra del codice.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>|Colora i delimitatori e parole chiave del linguaggio. È possibile ottenere questa interfaccia tramite il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> (metodo). <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> viene chiamato in fase di disegno. Evitare di lavoro a elevato utilizzo di calcolo all'interno di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> o potrebbe riscontrare un peggioramento delle prestazioni.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>|Fornisce le descrizioni comandi parametro IntelliSense. Quando il servizio di linguaggio riconosce un carattere che indica che i dati del metodo deve essere visualizzati, ad esempio una parentesi di apertura, chiama il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> metodo per notificare il testo consente di visualizzare che il servizio di linguaggio in grado di visualizzare una descrizione comando informazioni sul parametro. La visualizzazione di testo richiama il servizio di linguaggio da usando i metodi del <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> interfaccia per ottenere le informazioni necessarie per visualizzare la descrizione comando.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>|Fornisce il completamento delle istruzioni IntelliSense. Quando il servizio di linguaggio è pronto per visualizzare un elenco di completamento, chiama il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> metodo nella visualizzazione di testo. La visualizzazione di testo quindi richiama il servizio di linguaggio da utilizzando i metodi di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> oggetto.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|Consente la modifica della visualizzazione di testo utilizzando il gestore del comando. La classe in cui si implementa il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> interfaccia deve implementare anche il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia. Recupera la visualizzazione di testo il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> oggetto eseguendo una query di <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> oggetto che viene passato il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> (metodo). Dovrebbe esserci un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> oggetto per ogni visualizzazione.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Intercetta comandi che l'utente digita nella finestra del codice. Controllare l'output dal <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> implementazione per fornire informazioni sul completamento personalizzata e visualizzazione di modifica<br /><br /> Per passare le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> oggetto per la visualizzazione di testo, chiamata <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>.|

## <a name="see-also"></a>Vedere anche
- [Sviluppo di un servizio di linguaggio legacy](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Elenco di controllo: creazione di un servizio di linguaggio legacy](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)