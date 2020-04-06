---
title: Oggetti di contesto di selezione Documenti Microsoft
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
ms.openlocfilehash: 4e4f33dd0168a667b8f266ea606cecf0c26d62f1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705505"
---
# <a name="selection-context-objects"></a>Oggetti del contesto di selezione
L'ambiente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] di sviluppo integrato (IDE) utilizza un oggetto di contesto di selezione globale per determinare cosa deve essere visualizzato nell'IDE. Ogni finestra nell'IDE può avere il proprio oggetto contesto di selezione inserito nel contesto di selezione globale. L'IDE aggiorna il contesto di selezione globale con i valori da una finestra quando tale finestra ha lo stato attivo. Per ulteriori informazioni, consultate [Feedback all'utente.](../../extensibility/internals/feedback-to-the-user.md)

 Ogni cornice di finestra o sito nell'IDE dispone di un servizio denominato <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>. L'oggetto creato dal pacchetto VSPackage che si trova `QueryService` nella cornice della <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> finestra deve chiamare il metodo per ottenere un puntatore all'interfaccia.

 Le finestre cornice possono impedire che parti delle informazioni sul contesto di selezione vengano propagate al contesto di selezione globale all'avvio. Questa funzionalità è utile per le finestre degli strumenti che potrebbero dover iniziare con una selezione vuota.

 Modifica del contesto di selezione globale attiva gli eventi che VSPackage può monitorare. VSPackage possono eseguire le `IVsTrackSelectionEx` attività <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> seguenti implementando e interfacce:

- Aggiornare il file attualmente attivo in una gerarchia.

- Monitorare le modifiche a determinati tipi di elementi. Ad esempio, se il pacchetto VSPackage utilizza una finestra **Proprietà** speciale, è possibile monitorare le modifiche nella finestra **Proprietà** attiva e riavviare il proprio quando necessario.

  La sequenza seguente mostra il corso tipico del monitoraggio della selezione.

1. L'IDE recupera il contesto di selezione dalla finestra appena aperta e lo inserisce nel contesto di selezione globale. Se il contesto di selezione utilizza HIERARCHY_DONTPROPAGATE o SELCONTAINER_DONTPROPAGATE, tali informazioni non vengono propagate al contesto globale. Per ulteriori informazioni, consultate [Feedback all'utente.](../../extensibility/internals/feedback-to-the-user.md)

2. Gli eventi di notifica vengono trasmessi a qualsiasi VSPackage che li ha richiesti.

3. Il pacchetto VSPackage agisce sugli eventi che riceve eseguendo attività quali l'aggiornamento di una gerarchia, la riattivazione di uno strumento o altre attività simili.

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>
- [Gerarchie in Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)
- [Selezione e valuta nell'IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [Tipi di progetto](../../extensibility/internals/project-types.md)
