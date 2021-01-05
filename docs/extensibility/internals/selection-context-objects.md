---
title: Oggetti contesto selezione | Microsoft Docs
description: Informazioni sugli elementi interni del modo in cui l'IDE di Visual Studio usa un oggetto contesto di selezione globale per determinare gli elementi da visualizzare nell'IDE.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- selection, tracking
- selection, context objects
ms.assetid: 7308ea8f-a42c-47e5-954e-7dee933dce7a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf5e54f00ecbac03eaebe68c6fb4de410987b63f
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/05/2021
ms.locfileid: "97875570"
---
# <a name="selection-context-objects"></a>Oggetti del contesto di selezione
Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Integrated Development Environment (IDE) usa un oggetto contesto di selezione globale per determinare gli elementi da visualizzare nell'IDE. Ogni finestra nell'IDE può avere un proprio oggetto contesto di selezione inserito nel contesto di selezione globale. L'IDE aggiorna il contesto di selezione globale con i valori di una finestra quando la finestra ha lo stato attivo. Per ulteriori informazioni, vedere [feedback all'utente](../../extensibility/internals/feedback-to-the-user.md).

 Ogni frame o sito della finestra nell'IDE dispone di un servizio denominato <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> . L'oggetto creato dal pacchetto VSPackage, che è posizionato nella cornice della finestra, deve chiamare il `QueryService` metodo per ottenere un puntatore all' <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> interfaccia.

 Le finestre cornice possono impedire la propagazione delle parti delle informazioni sul contesto di selezione al contesto di selezione globale quando vengono avviate. Questa funzionalità è utile per le finestre degli strumenti che potrebbero dover iniziare con una selezione vuota.

 La modifica del contesto di selezione globale attiva gli eventi che i pacchetti VSPackage possono monitorare. I pacchetti VSPackage possono eseguire le attività seguenti implementando le `IVsTrackSelectionEx` <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> interfacce e:

- Aggiornare il file attualmente attivo in una gerarchia.

- Monitorare le modifiche apportate a determinati tipi di elementi. Ad esempio, se il pacchetto VSPackage usa una finestra delle **Proprietà** speciali, è possibile monitorare le modifiche nella finestra **Proprietà** attive e riavviare il computer quando richiesto.

  Nella sequenza seguente viene illustrato il tipico corso di rilevamento della selezione.

1. L'IDE Recupera il contesto di selezione dalla finestra appena aperta e lo inserisce nel contesto di selezione globale. Se il contesto di selezione USA HIERARCHY_DONTPROPAGATE o SELCONTAINER_DONTPROPAGATE, tali informazioni non vengono propagate al contesto globale. Per ulteriori informazioni, vedere [feedback all'utente](../../extensibility/internals/feedback-to-the-user.md).

2. Gli eventi di notifica vengono trasmessi a tutti i pacchetti VSPackage che li hanno richiesti.

3. Il pacchetto VSPackage agisce sugli eventi ricevuti eseguendo attività quali l'aggiornamento di una gerarchia, la riattivazione di uno strumento o altre attività simili.

## <a name="see-also"></a>Vedi anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>
- [Gerarchie in Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)
- [Selezione e valuta nell'IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [Project Types](../../extensibility/internals/project-types.md) (Tipi di progetto)
