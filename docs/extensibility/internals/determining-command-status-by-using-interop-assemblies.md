---
title: Determinazione dello stato del comando mediante gli assembly di interoperabilità | Microsoft Docs
description: Informazioni su come determinare lo stato dei comandi gestiti in un pacchetto VSPackage usando l'interfaccia Microsoft. VisualStudio. OLE. Interop. IOleCommandTarget.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, determining command status
- command handling with interop assemblies, status
ms.assetid: 2f5104d1-7b4c-4ca0-a626-50530a8f7f5c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e46252cea550a2caaa81c92853220db4fa2b5b1a
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/30/2020
ms.locfileid: "96328379"
---
# <a name="determine-command-status-by-using-interop-assemblies"></a>Determinare lo stato del comando tramite assembly di interoperabilità
Un pacchetto VSPackage deve tenere traccia dello stato dei comandi che è in grado di gestire. L'ambiente non è in grado di determinare quando un comando gestito all'interno del pacchetto VSPackage viene abilitato o disabilitato. È responsabilità del VSPackage informare l'ambiente sugli stati dei comandi, ad esempio lo stato dei comandi generali come **taglia**, **copia** e **Incolla**.

## <a name="status-notification-sources"></a>Origini notifiche di stato
 L'ambiente riceve informazioni sui comandi tramite il metodo VSPackages <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> , che fa parte dell'implementazione di VSPackage dell' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia. L'ambiente chiama il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodo del pacchetto VSPackage in due condizioni:

- Quando un utente apre un menu principale o un menu di scelta rapida (facendo clic con il pulsante destro del mouse), l'ambiente esegue il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodo su tutti i comandi di tale menu per determinarne lo stato.

- Quando il pacchetto VSPackage richiede che l'ambiente aggiorni l'interfaccia utente corrente (UI). Questo aggiornamento si verifica quando i comandi attualmente visibili all'utente, ad esempio il raggruppamento **taglia**, **copia** e **Incolla** sulla barra degli strumenti standard, vengono abilitati e disabilitati in risposta a azioni utente e di contesto.

  Poiché la shell ospita più VSPackage, le prestazioni della shell potrebbero risultare inaccettabili se fosse necessario eseguire il polling di ogni VSPackage per determinare lo stato del comando. Al contrario, il pacchetto VSPackage deve informare attivamente l'ambiente quando l'interfaccia utente cambia al momento della modifica. Per ulteriori informazioni sulla notifica di aggiornamento, vedere [aggiornare l'interfaccia utente](../../extensibility/updating-the-user-interface.md).

## <a name="status-notification-failure"></a>Errore di notifica di stato
 Un errore del pacchetto VSPackage per notificare all'ambiente la modifica dello stato di un comando può inserire l'interfaccia utente in uno stato incoerente. Tenere presente che qualsiasi comando di menu o menu di scelta rapida può essere inserito su una barra degli strumenti dall'utente. Pertanto, l'aggiornamento dell'interfaccia utente solo quando si apre un menu o un menu di scelta rapida non è sufficiente.

## <a name="see-also"></a>Vedi anche
- [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Implementazione](../../extensibility/internals/command-implementation.md)
