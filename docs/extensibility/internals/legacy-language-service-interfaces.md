---
title: Interfacce del servizio di linguaggio legacy | Microsoft Docs
description: Informazioni sulle interfacce disponibili in Visual Studio SDK che forniscono funzionalità del servizio di linguaggio legacy.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IVsLanguageInfo interface
- language services, objects
ms.assetid: 03b2d507-f463-417e-bc22-bdac68eeda52
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 670e8d5f8509aa3d61a23f674e2d584c9ce04c8f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122063187"
---
# <a name="legacy-language-service-interfaces"></a>Interfacce dei servizi di linguaggio legacy
Per qualsiasi linguaggio di programmazione specifico, può essere presente una sola istanza di un servizio di linguaggio alla volta. Tuttavia, un singolo servizio di linguaggio può servire più di un editor.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] non associa un servizio di linguaggio ad alcun editor specifico. Pertanto, quando si richiede un'operazione del servizio di linguaggio, è necessario identificare l'editor appropriato come parametro.

## <a name="common-interfaces-associated-with-language-services"></a>Interfacce comuni associate ai servizi di linguaggio
 L'editor ottiene il servizio di linguaggio chiamando <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> sul VSPackage appropriato. L'ID servizio (SID) passato in questa chiamata identifica il servizio di linguaggio richiesto.

 È possibile implementare le interfacce del servizio di linguaggio di base su un numero qualsiasi di classi separate. Tuttavia, un approccio comune consiste nell'implementare le interfacce seguenti in una singola classe:

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageBlock> (facoltativo)

  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>L'interfaccia deve essere implementata in tutti i servizi di linguaggio. Fornisce informazioni sul servizio di linguaggio, ad esempio il nome localizzato della lingua, le estensioni di file associate al servizio di linguaggio e come recuperare un colorizer.

## <a name="additional-language-service-interfaces"></a>Interfacce aggiuntive del servizio di linguaggio
 Altre interfacce possono essere fornite con il servizio di linguaggio. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] richiede un'istanza separata di queste interfacce per ogni istanza del buffer di testo. Pertanto, è necessario implementare ognuna di queste interfacce nel proprio oggetto . Nella tabella seguente vengono illustrate le interfacce che richiedono un'istanza per ogni istanza del buffer di testo.

|Interfaccia|Descrizione|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Gestisce le aree di controllo della finestra del codice, ad esempio la barra a discesa. È possibile ottenere questa interfaccia usando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> metodo . Ne esiste una <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> per finestra del codice.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>|Colora le parole chiave e i delimitatori del linguaggio. È possibile ottenere questa interfaccia usando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> metodo . <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> viene chiamato in fase di disegno. Evitare il lavoro a elevato utilizzo di calcolo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> all'interno di o le prestazioni potrebbero risentirne.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>|Fornisce descrizioni comando dei parametri intelliSense. Quando il servizio di linguaggio riconosce un carattere che indica che i dati del metodo devono essere visualizzati, ad esempio una parentesi aperta, chiama il metodo per notificare alla visualizzazione testo che il servizio di linguaggio è pronto per visualizzare una descrizione comando informazioni <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> parametro. La visualizzazione testo richiama quindi il servizio di linguaggio usando i metodi dell'interfaccia per ottenere le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> informazioni necessarie per visualizzare la descrizione comando.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>|Fornisce il completamento delle istruzioni IntelliSense. Quando il servizio di linguaggio è pronto per visualizzare un elenco di completamento, chiama <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> il metodo nella visualizzazione testo. La visualizzazione testo richiama quindi il servizio di linguaggio usando i metodi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> sull'oggetto .|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|Consente la modifica della visualizzazione testo usando il gestore del comando . Anche la classe in cui si implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> l'interfaccia deve implementare <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> l'interfaccia . La visualizzazione testo recupera <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> l'oggetto tramite una query <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> sull'oggetto passato nel <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> metodo . Deve essere presente un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> oggetto per ogni visualizzazione.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Intercetta i comandi che l'utente ha inserito nella finestra del codice. Monitorare l'output <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> dell'implementazione per fornire informazioni personalizzate sul completamento e visualizzare le modifiche<br /><br /> Per passare <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> l'oggetto alla visualizzazione testo, chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> .|

## <a name="see-also"></a>Vedi anche
- [Sviluppo di un servizio di linguaggio legacy](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Elenco di controllo: Creazione di un servizio di linguaggio legacy](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)
