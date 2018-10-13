---
title: Comando disponibilità | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- commands, context
- menu items, visibility contexts
ms.assetid: c74e3ccf-d771-48c8-a2f9-df323b166784
caps.latest.revision: 35
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bfaff5de68bd9d81b6cba6a03a4acec4ad1f0959
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49182650"
---
# <a name="command-availability"></a>Disponibilità dei comandi
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Il contesto di Visual Studio determina quali comandi sono disponibili. Il contesto può cambiare a seconda del progetto corrente, l'editor corrente, i pacchetti VSPackage che vengono caricati e altri aspetti dell'ambiente di sviluppo integrato (IDE).  
  
## <a name="command-contexts"></a>Contesti dei comandi  
 I contesti dei comandi seguenti sono i più comuni.  
  
-   **IDE** comandi forniti dall'IDE sono sempre disponibili.  
  
-   **VSPackage** i VSPackage possono definire quando i comandi devono essere visualizzate o nascoste.  
  
-   **Progetto** i comandi di progetto vengono visualizzati solo per il progetto attualmente selezionato.  
  
-   **Editor** editor solo uno possono essere attive contemporaneamente. Sono disponibili comandi dall'editor attivo. Un editor collabora con un servizio di linguaggio. Il servizio di linguaggio deve elaborare i relativi comandi nel contesto dell'editor associata.  
  
-   **Tipo di file** un editor può caricare più di un tipo di file. I comandi disponibili possono variare a seconda del tipo di file.  
  
-   **Finestra attiva** l'ultima finestra di documento attivo imposta il contesto dell'interfaccia utente per i tasti di scelta rapida. Tuttavia, una finestra degli strumenti con una tabella di chiave di associazione che è simile al Web browser interno è stato possibile impostare anche il contesto dell'interfaccia utente. Per le finestre di documento a più schede, ad esempio l'editor HTML, ogni scheda ha un contesto di comandi diversi GUID. Dopo aver registrata una finestra degli strumenti, è sempre disponibile nel **vista** menu.  
  
-   **Contesto dell'interfaccia utente** contesti dell'interfaccia utente sono identificati da valori del <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> classe, ad esempio <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid> quando viene compilata la soluzione, o <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid> quando il debugger è attivo. Più contesti dell'interfaccia utente possono essere attivi contemporaneamente.  
  
## <a name="defining-custom-context-guids"></a>Che definisce i GUID di contesto personalizzato  
 Se un contesto di comandi appropriata che GUID non è già definito, è possibile definire uno nel pacchetto VSPackage e programmarlo per essere attivi o inattivi in base alle esigenze per controllare la visibilità dei comandi.  
  
1.  Registra i GUID di contesto chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> (metodo).  
  
2.  Ottenere lo stato di un GUID di contesto chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> (metodo).  
  
3.  Attivare e disattivare i GUID di contesto chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> (metodo).  
  
    > [!CAUTION]
    >  Assicurarsi che il pacchetto VSPackage non interferenze con qualsiasi contesto esistente GUID perché altri pacchetti VSPackage potrebbero dipendono da essi.  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetti di contesto di selezione](../../extensibility/internals/selection-context-objects.md)   
 [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

