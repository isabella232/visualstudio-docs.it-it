---
title: Contratti di comando negli assembly di interoperabilità | Microsoft Docs
description: Informazioni sul contratto di base per la gestione dei comandi tramite l'interfaccia Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command handling with interop assemblies, command contracts
- interop assemblies, command contracts
ms.assetid: 57245708-f539-42dc-8963-2754a48f0189
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: f3e0921c37786c3be755f42a477c20465edfe1c2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122050208"
---
# <a name="command-contracts-in-interop-assemblies"></a>Contratti di comando negli assembly di interoperabilità
Il contratto di base per la gestione dei comandi tramite l'interfaccia è che l'ambiente chiama il metodo per determinare se il comando è supportato e, se supportato, per determinarne lo stato e <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> il testo. L'ambiente chiama quindi il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metodo per eseguire il comando.

 Il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodo viene gestito in modo identico per tutti i comandi. Un'ulteriore comunicazione, se necessaria ,ad esempio con elenchi a discesa, viene gestita chiamando il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metodo con i parametri appropriati. L'interpretazione di questi parametri dipende dal comando specificato.

 Se la destinazione del comando restituisce valori nel parametro di output, il chiamante è sempre responsabile della liberatura delle risorse allocate. Poiché questo parametro è una variante, la cancellazione della variante libera le risorse.

 Nei casi in cui i comandi devono operare all'interno di una finestra della gerarchia, è <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> necessario usare l'interfaccia . <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>L'interfaccia ha un contratto simile con metodi simili: e <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> .

## <a name="see-also"></a>Vedi anche
- [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Routing dei comandi in VSPackage](../../extensibility/internals/command-routing-in-vspackages.md)
- [Implementazione del comando](../../extensibility/internals/command-implementation.md)
