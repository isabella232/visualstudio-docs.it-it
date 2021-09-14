---
title: Struttura VSPackage (VSPackage del controllo del codice sorgente) | Microsoft Docs
description: Informazioni sull'SDK del pacchetto di controllo del codice sorgente, che fornisce linee guida per un PACCHETTO VSPackage con un implementatore del controllo del codice sorgente per l'integrazione con Visual Studio.
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
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: d8d0ab61556e85c1ad817dd9ee454f58645ad96e
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126709487"
---
# <a name="vspackage-structure-source-control-vspackage"></a>Struttura VSPackage (VSPackage di controllo del codice sorgente)

L'SDK del pacchetto di controllo del codice sorgente fornisce linee guida per la creazione di un PACCHETTO VSPackage che consentono a un implementatore del controllo del codice sorgente di integrare la propria funzionalità di controllo del codice sorgente con l'Visual Studio codice sorgente. Un VSPackage è un componente COM che in genere viene caricato su richiesta dall'ambiente di sviluppo integrato (IDE) di Visual Studio in base ai servizi annunciati dal pacchetto nelle voci del Registro di sistema. Ogni VSPackage deve implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> . Un VSPackage in genere usa i servizi offerti dall'IDE Visual Studio e offre alcuni servizi propri.

Un VSPackage dichiara le voci di menu e stabilisce uno stato predefinito dell'elemento tramite il file con estensione vsct. L Visual Studio IDE visualizza le voci di menu in questo stato fino a quando non viene caricato il pacchetto VSPackage. Successivamente, viene chiamata l'implementazione del metodo del vspackage <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> per abilitare o disabilitare le voci di menu.

## <a name="source-control-package-characteristics"></a>Caratteristiche del pacchetto di controllo del codice sorgente

Un PACCHETTO VSPackage per il controllo del codice sorgente è completamente integrato Visual Studio. La semantica vspackage include:

- Interfaccia da implementare grazie all'essere un VSPackage (l'interfaccia `IVsPackage` )

- Implementazione del comando dell'interfaccia utente (file con estensione vsct e implementazione <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> dell'interfaccia)

- Registrazione del pacchetto VSPackage con Visual Studio.

Il pacchetto VSPackage del controllo del codice sorgente deve comunicare con Visual Studio seguenti:

- Progetti

- Editor

- Soluzioni

- Windows

- Tabella del documento in esecuzione

### <a name="visual-studio-environment-services-that-may-be-consumed"></a>Visual Studio Servizi dell'ambiente che possono essere utilizzati

<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>

Servizio SVsRegisterScciProvider

<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>

### <a name="vsip-interfaces-implemented-and-called"></a>Interfacce VSIP implementate e chiamate

Un pacchetto di controllo del codice sorgente è un VSPackage e pertanto può interagire direttamente con altri VSPackage registrati con Visual Studio. Per offrire l'intera gamma di funzionalità di controllo del codice sorgente, un VSPackage del controllo del codice sorgente può gestire le interfacce fornite dai progetti o dalla shell.

Ogni progetto in Visual Studio deve implementare per essere riconosciuto come progetto all'interno dell Visual Studio <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> IDE. Tuttavia, questa interfaccia non è sufficientemente specializzata per il controllo del codice sorgente. I progetti che devono essere nel controllo del codice sorgente implementano <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> . Questa interfaccia viene usata dal pacchetto VSPackage del controllo del codice sorgente per eseguire una query su un progetto per il relativo contenuto e per fornirne i glifi e le informazioni di associazione (le informazioni necessarie per stabilire una connessione tra il percorso del server e il percorso del disco di un progetto sotto il controllo del codice sorgente).

Il pacchetto VSPackage del controllo del codice sorgente implementa , che a sua volta consente ai progetti di registrarsi per il controllo del codice sorgente <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> e recuperare i relativi glifi di stato.

Per un elenco completo delle interfacce che un VSPackage del controllo del codice sorgente deve prendere in considerazione, vedere [Interfacce e servizi correlati.](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)

## <a name="see-also"></a>Vedi anche

- [Elementi di progettazione](../../extensibility/internals/source-control-vspackage-design-elements.md)
- [Interfacce e servizi correlati](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)
