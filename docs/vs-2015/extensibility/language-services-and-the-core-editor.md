---
title: Servizi di linguaggio e editor principale | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - language services
ms.assetid: e03199a6-ad5f-4075-bfba-8d36865112b7
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1e708ffe796bfc9342bc20c3e7f20d5cf0d05058
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180295"
---
# <a name="language-services-and-the-core-editor"></a>Servizi di linguaggio ed editor principale
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gli editor in Visual Studio sono spesso associati a un servizio di linguaggio. Tra le altre cose, un servizio di linguaggio fornisce la colorazione della sintassi, il completamento delle istruzioni, IntelliSense e la formattazione del testo.  
  
## <a name="core-editors-and-document-data-objects"></a>Editor di base e oggetti dati del documento  
 Quando si accede all'editor principale, non vengono creati oggetti dati del documento e visualizzazione documento. L'IDE crea e controlla questi due oggetti ed è possibile ottenerne gli handle effettuando le chiamate appropriate nell'implementazione della factory dell'editor.  
  
 Per ulteriori informazioni, vedere [determinazione dell'editor che apre un file in un progetto](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md).  
  
## <a name="language-services-and-the-core-editor"></a>Servizi di linguaggio ed editor principale  
 Implementando un servizio di linguaggio, è possibile controllare la modalità di visualizzazione dei dati nella visualizzazione del documento. Un servizio di linguaggio fornisce informazioni e comportamenti specifici di un determinato linguaggio, ad esempio Visual C++. Quando si crea un buffer di testo e si determina l'estensione del nome file per il documento che si sta aprendo, il buffer di testo determina il servizio di linguaggio associato all'estensione di file da una chiave del registro di sistema, HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Editors \\ {YOURLANGUAGESERVICE GUID} \Extensions. La procedura di caricamento VSPackage standard carica quindi il pacchetto VSPackage e viene creata un'istanza del servizio di linguaggio.  
  
 Nella figura seguente è illustrato un servizio di linguaggio di base.  
  
 ![Rappresentazione grafica di Language Service Model](../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel")  
Editor principale e oggetti servizio di linguaggio  
  
 L'oggetto dati del documento per l'editor principale è denominato buffer di testo ed è rappresentato dall' <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> oggetto. L'oggetto visualizzazione documento viene chiamato visualizzazione testo ed è rappresentato dall' <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> oggetto. Questi due oggetti interagiscono tra loro tramite il servizio di linguaggio per offrire una visualizzazione unificata dell'editor principale. Le informazioni del buffer di testo e la visualizzazione di testo vengono visualizzate in una finestra del documento denominata finestra del codice. Il documento della finestra del codice è gestito da un gestore di finestre di codice.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 [Fornire un contesto del servizio di linguaggio tramite l'API legacy](../extensibility/providing-a-language-service-context-by-using-the-legacy-api.md)   
 [Hosting di IntelliSense](../extensibility/intellisense-hosting.md)   
 [Linguaggi contenuti](../extensibility/contained-languages.md)   
 [Sviluppo di un servizio di linguaggio legacy](../extensibility/internals/developing-a-legacy-language-service.md)
