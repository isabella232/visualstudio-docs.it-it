---
title: Disponibilità dei comandi Documenti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709691"
---
# <a name="command-availability"></a>Disponibilità dei comandi

Il contesto di Visual Studio determina quali comandi sono disponibili. Il contesto può cambiare a seconda del progetto corrente, l'editor corrente, i pacchetti VSPackage che vengono caricati e altri aspetti dell'ambiente di sviluppo integrato (IDE).

## <a name="command-contexts"></a>Contesti dei comandiCommand contexts

I contesti di comando seguenti sono i più comuni:The following command contexts are the most common:

- IDE: i comandi forniti dall'IDE sono sempre disponibili.

- VSPackage: VSPackage possono definire quando i comandi devono essere visualizzati o nascosti.

- Progetto: i comandi del progetto vengono visualizzati solo per il progetto attualmente selezionato.

- Editor: può essere attivo un solo editor alla volta. Sono disponibili comandi dall'editor attivo. Un editore lavora a stretto contatto con un servizio di linguaggio. Il servizio di linguaggio deve elaborare i comandi nel contesto dell'editor associato.

- Tipo di file: un editor può caricare più di un tipo di file. I comandi disponibili possono variare a seconda del tipo di file.

- Finestra attiva: l'ultima finestra del documento attivo imposta il contesto dell'interfaccia utente per le associazioni di tasti. Tuttavia, una finestra degli strumenti che dispone di una tabella di associazione di tasti simile al web browser interno potrebbe anche impostare il contesto dell'interfaccia utente. Per le finestre di documento a più schede, ad esempio l'editor HTML, ogni scheda ha un GUID di contesto di comando diverso. Dopo la registrazione, una finestra degli strumenti è sempre disponibile nel menu **Visualizza.**

- Contesto dell'interfaccia utente: i contesti dell'interfaccia utente sono identificati dai valori della <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> classe, ad esempio quando <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid> la soluzione viene compilata o <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid> quando il debugger è attivo. Più contesti dell'interfaccia utente possono essere attivi contemporaneamente.

## <a name="define-custom-context-guids"></a>Definire GUID di contesto personalizzatiDefine custom context GUIDs

Se un contesto di comando appropriato GUID non è già definito, è possibile definirne uno nel pacchetto VSPackage e quindi programmarlo per essere attivo o inattivo come richiesto per controllare la visibilità dei comandi:If an appropriate command context GUID is not already defined, you can define one in your VSPackage and then program it to be active or inactive as required to control the visibility of your commands:

1. Registrare i GUID di <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> contesto chiamando il metodo .

2. Ottenere lo stato di un <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> GUID di contesto chiamando il metodo .

3. Attivare e disattivare i GUID <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> di contesto chiamando il metodo .

> [!CAUTION]
> Assicurarsi che il pacchetto VSPackage non influisce su qualsiasi GUID di contesto esistente perché altri pacchetti VSPackage possono dipendere da essi.

## <a name="see-also"></a>Vedere anche

- [Oggetti di contesto di selezione](../../extensibility/internals/selection-context-objects.md)
- [Come VSPackage aggiungere elementi dell'interfaccia utenteHow VSPackages add user interface elements](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
