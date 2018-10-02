---
title: Modello di un servizio di linguaggio Legacy | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- language services, model
ms.assetid: d8ae1c0c-ee3d-4937-a581-ee78d0499793
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1ccea832f1979601a764c0b979b0f7d4d72bd796
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47519511"
---
# <a name="model-of-a-legacy-language-service"></a>Modello di un servizio di linguaggio legacy
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [modello di un servizio di linguaggio Legacy](https://docs.microsoft.com/visualstudio/extensibility/internals/model-of-a-legacy-language-service).  
  
Un servizio di linguaggio definisce gli elementi e le funzionalità per una lingua specifica e viene usato per fornire l'editor con informazioni specifiche per tale lingua. Ad esempio, l'editor deve conoscere gli elementi e le parole chiave del linguaggio per supportare la colorazione della sintassi.  
  
 Il servizio di linguaggio è ben integrata con il buffer di testo gestito da editor e la vista che contiene l'editor. Microsoft IntelliSense **informazioni rapide** opzione è un esempio di una funzionalità fornita da un servizio di linguaggio.  
  
## <a name="a-minimal-language-service"></a>Un servizio di linguaggio minimo  
 Il servizio di linguaggio più semplice contiene i due oggetti seguenti:  
  
-   Il *servizio di linguaggio* implementa il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interfaccia. Un servizio di linguaggio conterrà informazioni sul linguaggio, inclusi nome, estensioni di file, gestione di finestre di codice e colorizzatore.  
  
-   Il *colorizzatore* implementa il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interfaccia.  
  
 La rappresentazione concettuale seguente illustra un modello di un servizio di linguaggio di base.  
  
 ![Rappresentazione grafica del modello di servizio di linguaggio](../../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel")  
Modello di servizio di linguaggio di base  
  
 Gli host della finestra documento la *visualizzazione di documenti* dell'editor, in questo caso il [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] editor principale. La visualizzazione del documento e il buffer di testo sono di proprietà dall'editor. Questi oggetti rivolgersi [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] tramite una finestra del documento specializzato chiamato un *finestra del codice*. La finestra del codice è contenuta in un <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> oggetto che viene creato e controllato dall'IDE.  
  
 Quando viene caricato un file con una determinata estensione, l'editor consente di individuare il servizio di linguaggio associato a tale estensione e passa a tale finestra del codice chiamando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> (metodo). Il servizio di linguaggio restituisce un *gestione di finestre di codice*, che implementa il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> interfaccia.  
  
 Nella tabella seguente fornisce una panoramica degli oggetti nel modello.  
  
|Componente|Object|Funzione|  
|---------------|------------|--------------|  
|Buffer di testo|<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>|Un flusso di testo Unicode di lettura/scrittura. È possibile che il testo da utilizzare altre codifiche.|  
|Finestra del codice|<xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>|Una finestra del documento che contiene uno o più visualizzazioni di testo. Quando si [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] è in modalità interfaccia a documenti multipli (MDI), la finestra del codice è un figlio MDI.|  
|Visualizzazione di testo|<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>|Una finestra che consente all'utente di esplorare e visualizzare il testo usando la tastiera e mouse. Una visualizzazione di testo viene visualizzato dall'utente come editor. È possibile usare le visualizzazioni di testo nelle finestre dell'editor comune, la finestra di Output e finestra controllo immediato. Inoltre, è possibile configurare uno o più visualizzazioni di testo all'interno di una finestra del codice.|  
|Gestione di testo|Gestito dal <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> del servizio, da cui ottenere un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> puntatore|Un componente che gestisce informazioni comuni condivise da tutti i componenti descritti in precedenza.|  
|servizio di linguaggio|Implementazione dipendenti; implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>|Un oggetto che fornisce l'editor con informazioni specifiche del linguaggio, ad esempio l'evidenziazione della sintassi, completamento delle istruzioni e corrispondenza delle parentesi graffe.|  
  
## <a name="see-also"></a>Vedere anche  
 [Dati documento e visualizzazione documento negli editor personalizzati](../../extensibility/document-data-and-document-view-in-custom-editors.md)

