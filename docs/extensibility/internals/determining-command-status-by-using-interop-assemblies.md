---
title: Determinazione dello stato dei comandi tramite assembly di interoperabilità . Documenti Microsoft
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
ms.openlocfilehash: 52bea32997b083cd13349a37201411e357f94a90
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708706"
---
# <a name="determine-command-status-by-using-interop-assemblies"></a>Determinare lo stato dei comandi utilizzando gli assembly di interoperabilitàDetermine command status by using interop assemblies
Un pacchetto VSPackage deve tenere traccia dello stato dei comandi che è possibile gestire. L'ambiente non può determinare quando un comando gestito all'interno del pacchetto VSPackage viene abilitato o disabilitato. È responsabilità del pacchetto VSPackage informare l'ambiente sugli stati dei comandi, ad esempio lo stato dei comandi generali, ad esempio **Taglia**, **Copia**e **Incolla**.

## <a name="status-notification-sources"></a>Origini delle notifiche di stato
 L'ambiente riceve informazioni sui comandi <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> tramite il metodo VSPackage ', che <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> fa parte dell'implementazione del pacchetto VSPackage dell'interfaccia. L'ambiente <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> chiama il metodo del pacchetto VSPackage in due condizioni:

- Quando un utente apre un menu principale o un menu di <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> scelta rapida (facendo clic con il pulsante destro del mouse), l'ambiente esegue il metodo su tutti i comandi di tale menu per determinarne lo stato.

- Quando il pacchetto VSPackage richiede che l'ambiente aggiornare l'interfaccia utente corrente (UI). Questo aggiornamento si verifica quando i comandi attualmente visibili all'utente, ad esempio il raggruppamento **Taglia**, **Copia**e **Incolla** sulla barra degli strumenti standard, vengono abilitati e disabilitati in risposta al contesto e alle azioni dell'utente.

  Poiché la shell ospita più VSPackage, le prestazioni della shell si ridegradano in modo inaccettabile se fosse necessario eseguire il polling di ogni VSPackage per determinare lo stato del comando. Al contrario, il pacchetto VSPackage deve notificare attivamente l'ambiente quando l'interfaccia utente viene modificata al momento della modifica. Per ulteriori informazioni sulla notifica di aggiornamento, vedere [Aggiornare l'interfaccia utente](../../extensibility/updating-the-user-interface.md).

## <a name="status-notification-failure"></a>Errore di notifica dello stato
 Errore del pacchetto VSPackage per notificare l'ambiente di una modifica dello stato del comando può inserire l'interfaccia utente in uno stato incoerente. Tenere presente che qualsiasi comando del menu o del menu di scelta rapida può essere inserito in una barra degli strumenti dall'utente. Pertanto, l'aggiornamento dell'interfaccia utente solo quando si apre un menu o un menu di scelta rapida non è sufficiente.

## <a name="see-also"></a>Vedere anche
- [Come VSPackage aggiungere elementi dell'interfaccia utenteHow VSPackages add user interface elements](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Implementazione](../../extensibility/internals/command-implementation.md)
