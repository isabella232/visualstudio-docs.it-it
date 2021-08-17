---
title: Determinazione dello stato dei comandi tramite assembly di interoperabilità | Microsoft Docs
description: Informazioni su come determinare lo stato dei comandi gestiti in un VSPackage usando l'interfaccia Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, determining command status
- command handling with interop assemblies, status
ms.assetid: 2f5104d1-7b4c-4ca0-a626-50530a8f7f5c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 992768a65be2c3fb12f55dec9e2b84571ee52e0f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122094867"
---
# <a name="determine-command-status-by-using-interop-assemblies"></a>Determinare lo stato del comando tramite assembly di interoperabilità
Un VSPackage deve tenere traccia dello stato dei comandi che può gestire. L'ambiente non può determinare quando un comando gestito all'interno del pacchetto VSPackage viene abilitato o disabilitato. È responsabilità del pacchetto VSPackage informare l'ambiente sugli stati dei comandi, ad esempio lo stato dei comandi generali, ad esempio **Taglia,** Copia e **Incolla.**

## <a name="status-notification-sources"></a>Origini di notifica dello stato
 L'ambiente riceve informazioni sui comandi tramite il metodo dei pacchetti VSPackage, che fa parte <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> dell'implementazione dell'interfaccia del pacchetto VSPackage. <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> L'ambiente chiama <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> il metodo del pacchetto VSPackage in due condizioni:

- Quando un utente apre un menu principale o un menu di scelta rapida (facendo clic con il pulsante destro del mouse), l'ambiente esegue il metodo su tutti i comandi in tale menu per <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> determinarne lo stato.

- Quando il pacchetto VSPackage richiede che l'ambiente aggiorni l'interfaccia utente corrente. Questo aggiornamento si verifica quando i comandi attualmente visibili all'utente, ad esempio il raggruppamento Taglia **,** Copia e Incolla sulla barra degli strumenti standard, vengono abilitati e disabilitati in risposta alle azioni del contesto e dell'utente. 

  Poiché la shell ospita più VSPackage, le prestazioni della shell potrebbero peggiorare in modo inaccettabile se fosse necessario eseguire il polling di ogni VSPackage per determinare lo stato del comando. Il pacchetto VSPackage deve invece inviare una notifica attiva all'ambiente quando la relativa interfaccia utente cambia al momento della modifica. Per altre informazioni sulla notifica di aggiornamento, vedere [Aggiornare l'interfaccia utente.](../../extensibility/updating-the-user-interface.md)

## <a name="status-notification-failure"></a>Errore di notifica dello stato
 Se il vspackage non invia una notifica all'ambiente di una modifica dello stato del comando, l'interfaccia utente può essere posizionata in uno stato incoerente. Tenere presente che qualsiasi comando di menu o di menu di scelta rapida può essere inserito su una barra degli strumenti dall'utente. Pertanto, l'aggiornamento dell'interfaccia utente solo quando si apre un menu o un menu di scelta rapida non è sufficiente.

## <a name="see-also"></a>Vedi anche
- [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Implementazione](../../extensibility/internals/command-implementation.md)
