---
title: Comando disponibilità | Microsoft Docs
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- commands, context
- menu items, visibility contexts
ms.assetid: c74e3ccf-d771-48c8-a2f9-df323b166784
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7ac9a172ee2cb7a117a1d9b63c4f1fef9f631952
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53915870"
---
# <a name="command-availability"></a>Disponibilità dei comandi

Il contesto di Visual Studio determina quali comandi sono disponibili. Il contesto può cambiare a seconda del progetto corrente, l'editor corrente, i pacchetti VSPackage che vengono caricati e altri aspetti dell'ambiente di sviluppo integrato (IDE).

## <a name="command-contexts"></a>Contesti dei comandi

I contesti dei comandi seguenti sono i più comuni:

- IDE: I comandi forniti dall'IDE sono sempre disponibili.

- Pacchetto di Visual Studio: I VSPackage possono definire quando i comandi devono essere visualizzate o nascoste.

- Progetto: I comandi di progetto vengono visualizzati solo per il progetto attualmente selezionato.

- Editor: Solo un editor può essere attivo alla volta. Sono disponibili comandi dall'editor attivo. Un editor collabora con un servizio di linguaggio. Il servizio di linguaggio deve elaborare i relativi comandi nel contesto dell'editor associata.

- Tipo di file: Un editor può caricare più di un tipo di file. I comandi disponibili possono variare a seconda del tipo di file.

- Finestra attiva: L'ultima finestra di documento attivo imposta il contesto dell'interfaccia utente per i tasti di scelta rapida. Tuttavia, una finestra degli strumenti con una tabella di chiave di associazione che è simile al web browser interno è stato possibile impostare anche il contesto dell'interfaccia utente. Per le finestre di documento a più schede, ad esempio l'editor HTML, ogni scheda ha un contesto di comandi diversi GUID. Dopo aver registrata una finestra degli strumenti, è sempre disponibile nel **vista** menu.

- Contesto dell'interfaccia utente: Contesti dell'interfaccia utente sono identificati da valori del <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> classe, ad esempio <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid> quando viene compilata la soluzione, o <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid> quando il debugger è attivo. Più contesti dell'interfaccia utente possono essere attivi contemporaneamente.

## <a name="define-custom-context-guids"></a>Definire i GUID di contesto personalizzato

Se un contesto di comandi appropriata che GUID non è già definito, è possibile definire uno nel pacchetto VSPackage e programmarlo per essere attivi o inattivi in base alle esigenze per controllare la visibilità dei comandi:

1.  Registra i GUID di contesto chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> (metodo).

2.  Ottenere lo stato di un GUID di contesto chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> (metodo).

3.  Attivare e disattivare i GUID di contesto chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> (metodo).
   
> [!CAUTION]
> Assicurarsi che il pacchetto VSPackage non interferenze con qualsiasi contesto esistente GUID perché altri pacchetti VSPackage potrebbero dipendono da essi.

## <a name="see-also"></a>Vedere anche

- [Oggetti di contesto di selezione](../../extensibility/internals/selection-context-objects.md)
- [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)