---
title: Contratti di comando negli assembly di interoperabilità Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command handling with interop assemblies, command contracts
- interop assemblies, command contracts
ms.assetid: 57245708-f539-42dc-8963-2754a48f0189
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4f20a4f479d62cd1b64c3b13ff6e1a949656a668
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709679"
---
# <a name="command-contracts-in-interop-assemblies"></a>Contratti di comando negli assembly di interoperabilitàCommand contracts in interop assemblies
Il contratto di base <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> per la gestione <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> dei comandi tramite l'interfaccia è che l'ambiente chiama il metodo per determinare se il comando è supportato e, se è supportato, per determinarne lo stato e il testo. Quindi, l'ambiente <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> chiama il metodo per eseguire il comando.

 Il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodo viene gestito in modo identico per tutti i comandi. Ulteriori comunicazioni, se necessario (ad esempio, con elenchi a <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> discesa), viene gestita chiamando il metodo con i parametri appropriati. L'interpretazione di questi parametri dipende dal comando specificato.

 Se la destinazione del comando restituisce valori nel parametro di output, il chiamante è sempre responsabile di liberare le risorse allocate. Poiché questo parametro è una variante, la cancellazione della variante libera le risorse.

 Nei casi in cui i comandi <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> devono operare all'interno di una finestra della gerarchia, è necessario utilizzare l'interfaccia. L'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> ha un contratto <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>simile con metodi simili: e .

## <a name="see-also"></a>Vedere anche
- [Come VSPackage aggiungere elementi dell'interfaccia utenteHow VSPackages add user interface elements](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Routing dei comandi nei pacchetti VSPackageCommand routing in VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)
- [Implementazione dei comandi](../../extensibility/internals/command-implementation.md)
