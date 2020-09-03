---
title: Disponibilità comando | Microsoft Docs
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- commands, context
- menu items, visibility contexts
ms.assetid: c74e3ccf-d771-48c8-a2f9-df323b166784
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dca47d9ed9968c101e3b6b859b51c1cd8d7404db
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709691"
---
# <a name="command-availability"></a>Disponibilità comando

Il contesto di Visual Studio determina i comandi disponibili. Il contesto può variare a seconda del progetto corrente, dell'editor corrente, dei pacchetti VSPackage caricati e di altri aspetti del Integrated Development Environment (IDE).

## <a name="command-contexts"></a>Contesti di comando

I contesti dei comandi seguenti sono i più comuni:

- IDE: i comandi forniti dall'IDE sono sempre disponibili.

- VSPackage: i pacchetti VSPackage possono definire quando i comandi devono essere visualizzati o nascosti.

- Progetto: i comandi di progetto vengono visualizzati solo per il progetto attualmente selezionato.

- Editor: può essere attivo un solo editor alla volta. Sono disponibili i comandi dell'editor attivo. Un editor opera a stretto contatto con un servizio di linguaggio. Il servizio di linguaggio deve elaborare i comandi nel contesto dell'editor associato.

- Tipo di file: un editor può caricare più di un tipo di file. I comandi disponibili possono variare a seconda del tipo di file.

- Finestra attiva: l'ultima finestra del documento attivo imposta il contesto dell'interfaccia utente per le combinazioni di tasti. Tuttavia, una finestra degli strumenti con una tabella di associazione di chiavi simile al Web browser interno può anche impostare il contesto dell'interfaccia utente. Per le finestre di documento a più schede, ad esempio l'editor HTML, ogni scheda ha un GUID del contesto del comando diverso. Una volta registrata, una finestra degli strumenti è sempre disponibile nel menu **Visualizza** .

- Contesto dell'interfaccia utente: i contesti dell'interfaccia utente sono identificati dai valori della <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> classe, ad esempio <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid> quando la soluzione viene compilata o <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid> quando il debugger è attivo. Più contesti dell'interfaccia utente possono essere attivi contemporaneamente.

## <a name="define-custom-context-guids"></a>Definire GUID di contesto personalizzati

Se non è già stato definito un GUID del contesto del comando appropriato, è possibile definirne uno nel pacchetto VSPackage e quindi programmarlo come attivo o inattivo come richiesto per controllare la visibilità dei comandi:

1. Registrare GUID di contesto chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> metodo.

2. Ottenere lo stato di un GUID di contesto chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> metodo.

3. Attivare e disattivare i GUID di contesto chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> metodo.

> [!CAUTION]
> Verificare che il pacchetto VSPackage non influisca sui GUID di contesto esistenti, perché altri pacchetti VSPackage possono dipendere da essi.

## <a name="see-also"></a>Vedere anche

- [Oggetti contesto selezione](../../extensibility/internals/selection-context-objects.md)
- [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
