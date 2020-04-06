---
title: Struttura VSPackage (controllo del codice sorgente VSPackage) . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, structure
- source control packages, VSPackage overview
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b3f09b189e1e4b47187586e66c74315ee32495c8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703801"
---
# <a name="vspackage-structure-source-control-vspackage"></a>Struttura VSPackage (VSPackage di controllo del codice sorgente)

L'SDK del pacchetto di controllo del codice sorgente fornisce linee guida per la creazione di un pacchetto VSPackage che consentono a un implementatore del controllo del codice sorgente di integrare la propria funzionalità di controllo del codice sorgente con l'ambiente di Visual Studio.The Source Control Package SDK provides guidelines for creating a VSPackage that allow a source control implementer to integrate his or his source control functionality with the Visual Studio environment. Un pacchetto VSPackage è un componente COM che viene in genere caricato su richiesta dall'ambiente di sviluppo integrato (IDE) di Visual Studio in base ai servizi annunciati dal pacchetto nelle relative voci del Registro di sistema. Ogni VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>deve implementare . Un VSPackage in genere utilizza i servizi offerti dall'IDE di Visual Studio e offre alcuni servizi propri.

Un pacchetto VSPackage dichiara le voci di menu e stabilisce uno stato di elemento predefinito tramite il file vsct. L'IDE di Visual Studio visualizza le voci di menu in questo stato fino a quando non viene caricato il pacchetto VSPackage. Successivamente, l'implementazione del <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> VSPackage del metodo viene chiamato per abilitare o disabilitare le voci di menu.

## <a name="source-control-package-characteristics"></a>Caratteristiche del pacchetto di controllo del codice sorgenteSource Control Package Characteristics

Un controllo del codice sorgente VSPackage è profondamente integrato in Visual Studio.A source control VSPackage is deeply integrated into Visual Studio. La semantica VSPackage include:The VSPackage semantics include:

- Interfaccia da implementare in virtù di `IVsPackage` essere un VSPackage (l'interfaccia)Interface to be implemented by virtue of being a VSPackage (the interface)

- Implementazione del comando dell'interfaccia utente <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> (file con estensione vsct e implementazione dell'interfaccia)

- Registrazione del pacchetto VSPackage con Visual Studio.

Il controllo del codice sorgente VSPackage deve comunicare con queste altre entità di Visual Studio:The source control VSPackage must communicate with these other Visual Studio entities:

- Progetti

- Editor

- Soluzioni

- Windows

- Tabella dei documenti in esecuzione

### <a name="visual-studio-environment-services-that-may-be-consumed"></a>Servizi di ambiente di Visual Studio che possono essere utilizzati

<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>

Servizio SVsRegisterScciProvider

<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>

### <a name="vsip-interfaces-implemented-and-called"></a>Interfacce VSIP implementate e chiamate

A source control package is a VSPackage, and therefore it can interact directly with other VSPackages that are registered with Visual Studio. Per fornire l'ampiezza completa della funzionalità di controllo del codice sorgente, un controllo del codice sorgente VSPackage può gestire le interfacce fornite dai progetti o la shell.

Ogni progetto in Visual <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> Studio deve implementare per essere riconosciuto come un progetto all'interno dell'IDE di Visual Studio.Every project in Visual Studio must implement to be recognized as a project within the Visual Studio IDE. Tuttavia, questa interfaccia non è sufficientemente specializzata per il controllo del codice sorgente. I progetti che si prevede <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>siano nel controllo del codice sorgente implementano . Questa interfaccia viene utilizzata dal controllo del codice sorgente VSPackage per eseguire una query di un progetto per il relativo contenuto e per fornire glifi e informazioni di associazione (le informazioni necessarie per stabilire una connessione tra il percorso del server e il percorso del disco di un progetto incluso nel controllo del codice sorgente).

Il controllo del <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>codice sorgente VSPackage implementa , che a sua volta consente ai progetti di registrarsi per il controllo del codice sorgente e recuperare i glifi di stato.

Per un elenco completo delle interfacce che un controllo del codice sorgente VSPackage deve considerare, vedere [collegamenti e interfacce](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md).

## <a name="see-also"></a>Vedere anche

- [Elementi di progettazione](../../extensibility/internals/source-control-vspackage-design-elements.md)
- [Interfacce e servizi correlati](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)
