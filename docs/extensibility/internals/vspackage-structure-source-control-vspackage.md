---
title: Struttura VSPackage (VSPackage del controllo del codice sorgente) | Microsoft Docs
description: Informazioni sull'SDK del pacchetto di controllo del codice sorgente, che fornisce linee guida per un pacchetto VSPackage con un implementatore del controllo del codice sorgente da integrare con Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSPackages, structure
- source control packages, VSPackage overview
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b95c382342675d79c0c6e854b5fc087d495827e2
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898822"
---
# <a name="vspackage-structure-source-control-vspackage"></a>Struttura VSPackage (VSPackage di controllo del codice sorgente)

L'SDK del pacchetto di controllo del codice sorgente fornisce linee guida per la creazione di un pacchetto VSPackage che consentono a un implementatore del controllo del codice sorgente di integrare la propria funzionalità di controllo del codice sorgente con l'ambiente Visual Studio codice sorgente. Un VSPackage è un componente COM che viene in genere caricato su richiesta dall'ambiente di sviluppo integrato (IDE) di Visual Studio in base ai servizi annunciati dal pacchetto nelle voci del Registro di sistema. Ogni VSPackage deve implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> . Un VSPackage in genere usa i servizi offerti dall'IDE Visual Studio e offre alcuni servizi propri.

Un VSPackage dichiara le voci di menu e stabilisce uno stato predefinito dell'elemento tramite il file con estensione vsct. L Visual Studio IDE visualizza le voci di menu in questo stato fino al caricamento del pacchetto VSPackage. Successivamente, viene chiamata l'implementazione del metodo del pacchetto VSPackage <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> per abilitare o disabilitare le voci di menu.

## <a name="source-control-package-characteristics"></a>Caratteristiche del pacchetto di controllo del codice sorgente

Un VSPackage del controllo del codice sorgente è completamente integrato in Visual Studio. La semantica vspackage include:

- Interfaccia da implementare in virtù dell'essere un VSPackage `IVsPackage` (interfaccia)

- Implementazione del comando dell'interfaccia utente (file con estensione vsct e implementazione <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> dell'interfaccia)

- Registrazione del pacchetto VSPackage con Visual Studio.

Il controllo del codice sorgente VSPackage deve comunicare con queste Visual Studio seguenti:

- Progetti

- Editor

- Soluzioni

- Windows

- Tabella del documento in esecuzione

### <a name="visual-studio-environment-services-that-may-be-consumed"></a>Visual Studio di ambiente che possono essere utilizzati

<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>

Servizio SVsRegisterScciProvider

<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>

### <a name="vsip-interfaces-implemented-and-called"></a>Interfacce VSIP implementate e chiamate

Un pacchetto di controllo del codice sorgente è un vspackage e pertanto può interagire direttamente con altri VSPackage registrati con Visual Studio. Per offrire l'intera gamma di funzionalità di controllo del codice sorgente, un VSPackage del controllo del codice sorgente può gestire le interfacce fornite dai progetti o dalla shell.

Ogni progetto in Visual Studio deve implementare per essere riconosciuto come progetto all'interno dell Visual Studio <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> IDE. Questa interfaccia, tuttavia, non è sufficientemente specializzata per il controllo del codice sorgente. I progetti che devono essere sotto controllo del codice sorgente implementano <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> . Questa interfaccia viene usata dal controllo del codice sorgente VSPackage per eseguire una query su un progetto per il relativo contenuto e per fornirne glifi e informazioni di associazione (le informazioni necessarie per stabilire una connessione tra il percorso del server e il percorso del disco di un progetto sotto il controllo del codice sorgente).

Il controllo del codice sorgente VSPackage implementa , che a sua volta consente ai progetti di registrarsi per il controllo del codice sorgente <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> e recuperare i relativi glifi di stato.

Per un elenco completo delle interfacce che un VSPackage del controllo del codice sorgente deve prendere in considerazione, vedere [Servizi e interfacce correlati.](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)

## <a name="see-also"></a>Vedere anche

- [Elementi di progettazione](../../extensibility/internals/source-control-vspackage-design-elements.md)
- [Interfacce e servizi correlati](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)
