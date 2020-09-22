---
title: Disponibilità comando | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, context
- menu items, visibility contexts
ms.assetid: c74e3ccf-d771-48c8-a2f9-df323b166784
caps.latest.revision: 35
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f060f6c49fc02c75b3fe9f792133c9ee88c6d56c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839312"
---
# <a name="command-availability"></a>Disponibilità dei comandi
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Il contesto di Visual Studio determina i comandi disponibili. Il contesto può variare a seconda del progetto corrente, dell'editor corrente, dei pacchetti VSPackage caricati e di altri aspetti del Integrated Development Environment (IDE).  
  
## <a name="command-contexts"></a>Contesti di comando  
 I contesti dei comandi seguenti sono i più comuni.  
  
- **IDE** I comandi forniti dall'IDE sono sempre disponibili.  
  
- **Pacchetto VSPackage** I pacchetti VSPackage possono definire quando i comandi devono essere visualizzati o nascosti.  
  
- **Progetto** di I comandi di progetto vengono visualizzati solo per il progetto attualmente selezionato.  
  
- **Editor** di Può essere attivo un solo editor alla volta. Sono disponibili i comandi dell'editor attivo. Un editor opera a stretto contatto con un servizio di linguaggio. Il servizio di linguaggio deve elaborare i comandi nel contesto dell'editor associato.  
  
- **Tipo di file** Un editor può caricare più di un tipo di file. I comandi disponibili possono variare a seconda del tipo di file.  
  
- **Finestra attiva** L'ultima finestra del documento attivo consente di impostare il contesto dell'interfaccia utente per le combinazioni di tasti. Tuttavia, una finestra degli strumenti con una tabella di associazione delle chiavi simile alla Web browser interna potrebbe anche impostare il contesto dell'interfaccia utente. Per le finestre di documento a più schede, ad esempio l'editor HTML, ogni scheda ha un GUID del contesto del comando diverso. Una volta registrata, una finestra degli strumenti è sempre disponibile nel menu **Visualizza** .  
  
- **Contesto dell'interfaccia utente** I contesti dell'interfaccia utente sono identificati dai valori della <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> classe, ad esempio <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid> quando la soluzione viene compilata o <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid> quando il debugger è attivo. Più contesti dell'interfaccia utente possono essere attivi contemporaneamente.  
  
## <a name="defining-custom-context-guids"></a>Definizione di GUID di contesto personalizzati  
 Se non è già stato definito un GUID del contesto del comando appropriato, è possibile definirne uno nel pacchetto VSPackage e quindi programmarlo come attivo o inattivo come richiesto per controllare la visibilità dei comandi.  
  
1. Registrare GUID di contesto chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> metodo.  
  
2. Ottenere lo stato di un GUID di contesto chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> metodo.  
  
3. Attivare e disattivare i GUID di contesto chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> metodo.  
  
    > [!CAUTION]
    > Verificare che il pacchetto VSPackage non influisca sui GUID di contesto esistenti, perché altri pacchetti VSPackage possono dipendere da essi.  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetti contesto selezione](../../extensibility/internals/selection-context-objects.md)   
 [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
