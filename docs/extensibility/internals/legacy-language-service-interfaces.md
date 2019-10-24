---
title: Interfacce del servizio di linguaggio legacy | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IVsLanguageInfo interface
- language services, objects
ms.assetid: 03b2d507-f463-417e-bc22-bdac68eeda52
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 065ef972709ca78b516a9acc5f4a737d2963e4b7
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726850"
---
# <a name="legacy-language-service-interfaces"></a>Interfacce dei servizi di linguaggio legacy
Per qualsiasi linguaggio di programmazione specifico, può essere presente una sola istanza di un servizio di linguaggio alla volta. Tuttavia, un singolo servizio di linguaggio può servire più di un editor.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] non associa un servizio di linguaggio a un editor specifico. Pertanto, quando si richiede un'operazione del servizio di linguaggio, è necessario identificare l'editor appropriato come parametro.

## <a name="common-interfaces-associated-with-language-services"></a>Interfacce comuni associate ai servizi di linguaggio
 L'editor ottiene il servizio di linguaggio chiamando <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> sul pacchetto VSPackage appropriato. L'ID servizio (SID) passato in questa chiamata identifica il servizio di linguaggio richiesto.

 È possibile implementare le interfacce del servizio di linguaggio core su qualsiasi numero di classi separate. Tuttavia, un approccio comune consiste nell'implementare le interfacce seguenti in un'unica classe:

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageBlock> (facoltativo)

  L'interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> deve essere implementata in tutti i servizi di linguaggio. Fornisce informazioni sul servizio di linguaggio, ad esempio il nome localizzato della lingua, le estensioni dei nomi di file associate al servizio di linguaggio e il modo in cui recuperare un colorante.

## <a name="additional-language-service-interfaces"></a>Interfacce del servizio di linguaggio aggiuntive
 Altre interfacce possono essere fornite con il servizio di linguaggio. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] richiede un'istanza separata di queste interfacce per ogni istanza del buffer di testo. Pertanto, è necessario implementare ognuna di queste interfacce sul relativo oggetto. Nella tabella seguente vengono illustrate le interfacce che richiedono un'istanza per ogni istanza del buffer di testo.

|Interfaccia|Descrizione|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Gestisce le aree di strumenti della finestra del codice, ad esempio la barra a discesa. Per ottenere questa interfaccia, è possibile usare il metodo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A>. È presente una <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> per ogni finestra del codice.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>|Colora le parole chiave del linguaggio e i delimitatori. Per ottenere questa interfaccia, è possibile usare il metodo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> viene chiamato in fase di disegno. Evitare il lavoro a elevato utilizzo di calcolo all'interno <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> o le prestazioni potrebbero subire problemi.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>|Fornisce le descrizioni comandi del parametro IntelliSense. Quando il servizio di linguaggio riconosce un carattere che indica che i dati del metodo devono essere visualizzati, ad esempio una parentesi aperta, chiama il metodo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> per notificare alla visualizzazione di testo che il servizio di linguaggio è pronto per visualizzare una descrizione comando informazioni parametri. La visualizzazione di testo richiama quindi il servizio di linguaggio utilizzando i metodi dell'interfaccia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> per ottenere le informazioni necessarie per visualizzare la descrizione comando.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>|Fornisce il completamento delle istruzioni IntelliSense. Quando il servizio di linguaggio è pronto per visualizzare un elenco di completamento, chiama il metodo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> nella visualizzazione di testo. La visualizzazione di testo richiama quindi il servizio di linguaggio utilizzando i metodi sull'oggetto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|Consente di modificare la visualizzazione di testo utilizzando il gestore del comando. La classe in cui viene implementata l'interfaccia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> deve implementare anche l'interfaccia <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>. La visualizzazione di testo recupera l'oggetto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> eseguendo una query sull'oggetto <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> passato nel metodo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>. Deve essere presente un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> oggetto per ogni visualizzazione.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Intercetta i comandi che l'utente digita nella finestra del codice. Monitorare l'output dell'implementazione di <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> per fornire informazioni di completamento personalizzate e visualizzare le modifiche<br /><br /> Per passare l'oggetto <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> alla visualizzazione di testo, chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>.|

## <a name="see-also"></a>Vedere anche
- [Sviluppo di un servizio di linguaggio legacy](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Elenco di controllo: Creazione di un servizio di linguaggio legacy](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)