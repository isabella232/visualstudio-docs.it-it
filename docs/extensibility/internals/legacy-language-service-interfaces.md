---
title: Interfacce del servizio di linguaggio Legacy Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IVsLanguageInfo interface
- language services, objects
ms.assetid: 03b2d507-f463-417e-bc22-bdac68eeda52
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 89d80d6961f5eaf91721567ccb0efa73bbe31406
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707376"
---
# <a name="legacy-language-service-interfaces"></a>Interfacce dei servizi di linguaggio legacy
Per qualsiasi linguaggio di programmazione specifico, può essere presente una sola istanza di un servizio di linguaggio alla volta. Tuttavia, un singolo servizio di linguaggio può servire più di un editor.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]non associa un servizio di linguaggio ad alcun editor particolare. Pertanto, quando si richiede un'operazione del servizio di linguaggio, è necessario identificare l'editor appropriato come parametro.

## <a name="common-interfaces-associated-with-language-services"></a>Interfacce comuni associate ai servizi di linguaggioCommon Interfaces Associated with Language Services
 L'editor ottiene il <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> servizio di linguaggio chiamando il pacchetto VSPackage appropriato. L'ID servizio (SID) passato in questa chiamata identifica il servizio di linguaggio richiesto.

 È possibile implementare le interfacce del servizio di linguaggio di base in un numero qualsiasi di classi separate. Tuttavia, un approccio comune consiste nell'implementare le interfacce seguenti in una singola classe:However, a common approach is to implement the following interfaces in a single class:

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageBlock> (facoltativo)

  L'interfaccia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> deve essere implementata in tutti i servizi di linguaggio. Fornisce informazioni sul servizio di linguaggio, ad esempio il nome localizzato della lingua, le estensioni di file associate al servizio di linguaggio e come recuperare un colorizzatore.

## <a name="additional-language-service-interfaces"></a>Interfacce aggiuntive del servizio di linguaggioAdditional Language Service Interfaces
 Altre interfacce possono essere fornite con il servizio di linguaggio. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]richiede un'istanza separata di queste interfacce per ogni istanza del buffer di testo. Pertanto, è necessario implementare ognuna di queste interfacce nel proprio oggetto. Nella tabella seguente vengono illustrate le interfacce che richiedono un'istanza per ogni istanza del buffer di testo.

|Interfaccia|Descrizione|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Gestisce le aree di controllo della finestra del codice, ad esempio la barra a discesa. È possibile ottenere questa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> interfaccia utilizzando il metodo . Ce n'è uno <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> per ogni finestra del codice.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>|Colora le parole chiave del linguaggio e i delimitatori. È possibile ottenere questa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> interfaccia utilizzando il metodo . <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>viene chiamato in fase di vernice. Evitare il lavoro <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> ad alta intensità di calcolo all'interno o le prestazioni potrebbero risentirne.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>|Fornisce descrizioni comandi dei parametri IntelliSense. Quando il servizio di linguaggio riconosce un carattere che indica che i dati del <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> metodo devono essere visualizzati, ad esempio una parentesi aperta, chiama il metodo per notificare alla visualizzazione di testo che il servizio di linguaggio è pronto per visualizzare un suggerimento per le informazioni sui parametri. La visualizzazione di testo richiama quindi il servizio <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> di linguaggio utilizzando i metodi dell'interfaccia per ottenere le informazioni necessarie per visualizzare la descrizione comando.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>|Fornisce il completamento dell'istruzione IntelliSense. Quando il servizio di linguaggio è pronto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> per visualizzare un elenco di completamento, chiama il metodo nella visualizzazione di testo. La visualizzazione di testo richiama quindi il servizio <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> di linguaggio utilizzando i metodi sull'oggetto .|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|Consente la modifica della visualizzazione di testo utilizzando il gestore di comando. La classe in cui <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> si implementa <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> l'interfaccia deve implementare anche l'interfaccia. La visualizzazione di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> testo recupera l'oggetto eseguendo una query sull'oggetto <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> passato nel <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> metodo. Deve essere <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> presente un oggetto per ogni visualizzazione.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Intercetta i comandi digitati dall'utente nella finestra del codice. Monitorare l'output dall'implementazione per fornire informazioni di completamento personalizzate e modificare la visualizzazioneMonitor output from your <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> implementation to provide custom completion information and view modification<br /><br /> Per passare <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> l'oggetto alla <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>visualizzazione di testo, chiamare .|

## <a name="see-also"></a>Vedere anche
- [Sviluppo di un servizio di linguaggio legacy](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Elenco di controllo: Creazione di un servizio di linguaggio legacy](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)
