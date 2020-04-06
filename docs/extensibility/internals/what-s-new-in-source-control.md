---
title: Novità del controllo del codice sorgente in Visual Studio 2015 SDK Documenti Microsoft
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio SDK], source control
- source control [Visual Studio SDK], what's new
ms.assetid: bcf85418-18fb-4824-9dae-d14bf3d56a77
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f90ae3e1d327b10e99713ad28aa2d5a06c0be34b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703401"
---
# <a name="whats-new-in-source-control-for-the-visual-studio-2015-sdk"></a>Novità del controllo del codice sorgente per Visual Studio 2015 SDK

In [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], è possibile fornire una soluzione di controllo del codice sorgente profondamente integrata implementando un controllo del codice sorgente VSPackage. In questa sezione vengono descritte le funzionalità del controllo del codice sorgente VSPackage e viene fornita una panoramica dei passaggi di implementazione.

## <a name="the-source-control-vspackage"></a>Il controllo del codice sorgente VSPackageThe Source Control VSPackage

Visual Studio supporta due tipi di soluzioni di controllo del codice sorgente. In tutte le versioni di Visual Studio, è comunque possibile integrare un plug-in basato sull'API del plug-in del controllo del codice sorgente. È anche possibile creare un pacchetto VSPackage per [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] il controllo del codice sorgente che fornisce un'integrazione completa, percorso adatto per le soluzioni di controllo del codice sorgente che richiedono un elevato livello di sofisticazione e autonomia.

A VSPackage can add almost any kind of functionality to Visual Studio. Un controllo del codice sorgente VSPackage fornisce una funzionalità di controllo del codice sorgente completa per Visual Studio, dall'interfaccia utente presentata all'utente alla comunicazione back-end con il sistema di controllo del codice sorgente.

Implementazione di un controllo del codice sorgente VSPackage richiede una strategia "tutto o niente". Il creatore di un controllo del codice sorgente VSPackage deve investire una quantità significativa di sforzo nell'implementazione di una serie di interfacce di controllo del codice sorgente e nuovi elementi dell'interfaccia utente (finestre di dialogo, menu e barre degli strumenti) per coprire l'intera funzionalità del controllo del codice sorgente, nonché le interfacce necessarie per qualsiasi pacchetto per l'integrazione corretta con Visual Studio.

I passaggi seguenti forniscono una panoramica generale di ciò che è necessario per implementare un pacchetto di controllo del codice sorgente. Per informazioni dettagliate, vedere [creazione di un controllo del codice sorgente VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md).

1. Creare un pacchetto VSPackage che offre un servizio di controllo del codice sorgente privato.

2. Implementare le interfacce nei servizi correlati al controllo del codice sorgente <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> offerti <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> da Visual Studio (ad esempio, l'interfaccia e ).

3. Registrare il controllo del codice sorgente VSPackage.Register your source control VSPackage.

4. Implementare tutta l'interfaccia utente del controllo del codice sorgente, incluse le voci di menu, le finestre di dialogo, le barre degli strumenti e i menu di scelta rapida.

5. Tutti gli eventi correlati al controllo del codice sorgente vengono passati al controllo del codice sorgente VSackage quando è attivo e devono essere gestiti dal pacchetto VSPackage.All source control-related events are passed to your source control VSackage when it is active and must be handled by your VSPackage.

6. Il controllo del codice sorgente VSPackage deve <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> rimanere in ascolto di eventi quali quelli che <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> implementano l'interfaccia, nonché tenere traccia degli eventi del documento di progetto (TPD) (come implementato dall'interfaccia) ed eseguire le azioni necessarie.

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- [Panoramica](../../extensibility/internals/source-control-integration-overview.md)
- [Creazione di un pacchetto VSPackage di controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-vspackage.md)
