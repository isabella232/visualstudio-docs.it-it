---
title: Disponibilità dei comandi | Microsoft Docs
description: Informazioni su come il contesto dei comandi, che cambia in base al progetto corrente, all'editor corrente e ad altri fattori, determina quali comandi sono disponibili in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- commands, context
- menu items, visibility contexts
ms.assetid: c74e3ccf-d771-48c8-a2f9-df323b166784
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: f2874909b772d6427dfa8869b203c1843f6ac153
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122086872"
---
# <a name="command-availability"></a>Disponibilità dei comandi

Il Visual Studio determina quali comandi sono disponibili. Il contesto può cambiare a seconda del progetto corrente, dell'editor corrente, dei pacchetti VSPackage caricati e di altri aspetti dell'ambiente di sviluppo integrato (IDE).

## <a name="command-contexts"></a>Contesti di comando

I contesti di comando seguenti sono i più comuni:

- IDE: i comandi forniti dall'IDE sono sempre disponibili.

- VSPackage: i pacchetti VSPackage possono definire quando i comandi devono essere visualizzati o nascosti.

- Project: Project comandi vengono visualizzati solo per il progetto attualmente selezionato.

- Editor: può essere attivo un solo editor alla volta. Sono disponibili i comandi dell'editor attivo. Un editor funziona a stretto contatto con un servizio di linguaggio. Il servizio di linguaggio deve elaborare i comandi nel contesto dell'editor associato.

- Tipo di file: un editor può caricare più di un tipo di file. I comandi disponibili possono cambiare a seconda del tipo di file.

- Finestra attiva: l'ultima finestra del documento attiva imposta il contesto dell'interfaccia utente per i tasti di scelta rapida. Tuttavia, anche una finestra degli strumenti con una tabella di associazione di tasti simile al Web browser interno può impostare il contesto dell'interfaccia utente. Per le finestre dei documenti a schede diverse, ad esempio l'editor HTML, ogni scheda ha un GUID del contesto di comando diverso. Dopo la registrazione, una finestra degli strumenti è sempre disponibile **nel** menu Visualizza.

- Contesto dell'interfaccia utente: i contesti dell'interfaccia utente sono identificati dai valori della classe , ad esempio quando la soluzione viene compilata <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> o quando il debugger è <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid> <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid> attivo. Più contesti dell'interfaccia utente possono essere attivi contemporaneamente.

## <a name="define-custom-context-guids"></a>Definire GUID di contesto personalizzati

Se non è già stato definito un GUID del contesto di comando appropriato, è possibile definirne uno nel vspackage e programmarlo in modo che sia attivo o inattivo in base alle esigenze per controllare la visibilità dei comandi:

1. Registrare i GUID di contesto chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> metodo .

2. Ottenere lo stato di un GUID di contesto chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> metodo .

3. Attivare e disattivare i GUID di contesto chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> metodo .

> [!CAUTION]
> Assicurarsi che il pacchetto VSPackage non influisca sui GUID di contesto esistenti perché altri PACCHETTI VSPackage possono dipendere da essi.

## <a name="see-also"></a>Vedi anche

- [Oggetti del contesto di selezione](../../extensibility/internals/selection-context-objects.md)
- [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
