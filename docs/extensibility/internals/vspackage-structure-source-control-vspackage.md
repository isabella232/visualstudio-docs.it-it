---
title: Struttura VSPackage (VSPackage del controllo del codice sorgente) | Microsoft Docs
description: Informazioni sull'SDK del pacchetto del controllo del codice sorgente, che fornisce linee guida per un VSPackage con un implementatore del controllo del codice sorgente per l'integrazione con Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: f5850dfb2448364124c8f1778eac48ac9c653269
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2020
ms.locfileid: "97487959"
---
# <a name="vspackage-structure-source-control-vspackage"></a>Struttura VSPackage (VSPackage di controllo del codice sorgente)

L'SDK del pacchetto del controllo del codice sorgente fornisce linee guida per la creazione di un pacchetto VSPackage che consente all'implementatore del controllo del codice sorgente di integrare la propria funzionalità di controllo del codice sorgente con l'ambiente Visual Studio. Un pacchetto VSPackage è un componente COM che in genere viene caricato su richiesta da Visual Studio Integrated Development Environment (IDE) in base ai servizi annunciati dal pacchetto nelle voci del registro di sistema. Ogni VSPackage deve implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> . Un pacchetto VSPackage USA in genere i servizi offerti dall'IDE di Visual Studio e dichiara alcuni servizi.

Un pacchetto VSPackage dichiara le voci di menu e stabilisce uno stato di elemento predefinito tramite il file con estensione vsct. L'IDE di Visual Studio Visualizza le voci di menu in questo stato fino a quando il pacchetto VSPackage non viene caricato. Successivamente, l'implementazione del pacchetto VSPackage del <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodo viene chiamata per abilitare o disabilitare le voci di menu.

## <a name="source-control-package-characteristics"></a>Caratteristiche del pacchetto del controllo del codice sorgente

Un pacchetto VSPackage del controllo del codice sorgente è strettamente integrato in Visual Studio. La semantica VSPackage include:

- Interfaccia da implementare in base a un pacchetto VSPackage ( `IVsPackage` interfaccia)

- Implementazione del comando dell'interfaccia utente (file con estensione vsct e implementazione dell' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia)

- Registrazione del pacchetto VSPackage con Visual Studio.

Il pacchetto VSPackage del controllo del codice sorgente deve comunicare con le altre entità di Visual Studio:

- Progetti

- Editor

- Soluzioni

- Windows

- Tabella documenti in esecuzione

### <a name="visual-studio-environment-services-that-may-be-consumed"></a>Servizi di ambiente Visual Studio che possono essere utilizzati

<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>

Servizio SVsRegisterScciProvider

<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>

### <a name="vsip-interfaces-implemented-and-called"></a>Interfacce VSIP implementate e chiamate

Un pacchetto di controllo del codice sorgente è un VSPackage e pertanto può interagire direttamente con altri pacchetti VSPackage registrati con Visual Studio. Per fornire l'ampia gamma di funzionalità del controllo del codice sorgente, un pacchetto VSPackage del controllo del codice sorgente può gestire le interfacce fornite dai progetti o dalla Shell.

Ogni progetto in Visual Studio deve implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> per essere riconosciuto come progetto all'interno dell'IDE di Visual Studio. Questa interfaccia non è tuttavia sufficientemente specializzata per il controllo del codice sorgente. I progetti che dovrebbero essere inclusi nel controllo del codice sorgente implementano <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> . Questa interfaccia viene utilizzata dal pacchetto VSPackage del controllo del codice sorgente per eseguire una query su un progetto per il relativo contenuto e per fornire glifi e informazioni di associazione (le informazioni necessarie per stabilire una connessione tra il percorso del server e il percorso del disco di un progetto che si trova nel controllo del codice sorgente).

Il pacchetto VSPackage del controllo del codice sorgente implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> , che a sua volta consente ai progetti di registrarsi per il controllo del codice sorgente e recuperare i relativi glifi di stato.

Per un elenco completo delle interfacce che devono essere prese in considerazione da un VSPackage del controllo del codice sorgente, vedere [interfacce e servizi correlati](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md).

## <a name="see-also"></a>Vedere anche

- [Elementi di progettazione](../../extensibility/internals/source-control-vspackage-design-elements.md)
- [Interfacce e servizi correlati](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)
