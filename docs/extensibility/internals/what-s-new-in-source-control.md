---
title: Novità del controllo del codice sorgente in Visual Studio 2015 SDK | Microsoft Docs
description: Informazioni sulle funzionalità dei pacchetti VSPackage del controllo del codice sorgente ed esaminare una panoramica dei passaggi di implementazione.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio SDK], source control
- source control [Visual Studio SDK], what's new
ms.assetid: bcf85418-18fb-4824-9dae-d14bf3d56a77
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 9f828aa153ddba9fcc0bb6db07084277b48b7c862447bd2b8fc4e6681123ab44
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121431734"
---
# <a name="whats-new-in-source-control-for-the-visual-studio-2015-sdk"></a>Novità del controllo del codice sorgente per Visual Studio 2015 SDK

In è possibile fornire una soluzione di controllo del codice sorgente completamente integrata [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] implementando un VSPackage del controllo del codice sorgente. In questa sezione vengono descritte le funzionalità dei pacchetti VSPackage del controllo del codice sorgente e viene fornita una panoramica dei passaggi di implementazione.

## <a name="the-source-control-vspackage"></a>VsPackage del controllo del codice sorgente

Visual Studio supporta due tipi di soluzioni di controllo del codice sorgente. In tutte le versioni di Visual Studio, è comunque possibile integrare un plug-in basato sull'API del plug-in del controllo del codice sorgente. È anche possibile creare un PACCHETTO VSPackage per il controllo del codice sorgente che fornisce un percorso di integrazione completa e adatto per le soluzioni di controllo del codice sorgente che richiedono un elevato livello di sofisticatità [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] e autonomia.

Un PACCHETTO VSPackage può aggiungere quasi tutti i tipi di funzionalità Visual Studio. Un pacchetto VSPackage del controllo del codice sorgente offre una funzionalità di controllo del codice sorgente completa per Visual Studio, dall'interfaccia utente presentata all'utente alla comunicazione back-end con il sistema di controllo del codice sorgente.

L'implementazione di un pacchetto VSPackage del controllo del codice sorgente richiede una strategia "tutto o niente". L'autore di un pacchetto VSPackage per il controllo del codice sorgente deve investire una notevole quantità di impegno nell'implementazione di una serie di interfacce di controllo del codice sorgente e di nuovi elementi dell'interfaccia utente (finestre di dialogo, menu e barre degli strumenti) per coprire l'intera funzionalità di controllo del codice sorgente, nonché le interfacce necessarie a qualsiasi pacchetto per integrarsi correttamente con Visual Studio.

I passaggi seguenti offrono una panoramica generale degli elementi necessari per implementare un pacchetto di controllo del codice sorgente. Per informazioni dettagliate, vedere [Creazione di un pacchetto VSPackage del controllo del codice sorgente.](../../extensibility/internals/creating-a-source-control-vspackage.md)

1. Creare un VSPackage che proffersa un servizio di controllo del codice sorgente privato.

2. Implementare le interfacce nei servizi correlati al controllo del codice sorgente che vengono Visual Studio (ad esempio, <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> l'interfaccia ).

3. Registrare il pacchetto VSPackage del controllo del codice sorgente.

4. Implementare tutta l'interfaccia utente del controllo del codice sorgente, incluse le voci di menu, le finestre di dialogo, le barre degli strumenti e i menu di scelta rapida.

5. Tutti gli eventi correlati al controllo del codice sorgente vengono passati a VSackage del controllo del codice sorgente quando è attivo e devono essere gestiti dal pacchetto VSPackage.

6. Il pacchetto VSPackage del controllo del codice sorgente deve essere in ascolto di eventi quali quelli che implementano l'interfaccia e gli eventi <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> TPD (Track Project Document) (implementati dall'interfaccia ) ed eseguire le azioni <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> necessarie.

## <a name="see-also"></a>Vedi anche

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- [Overview](../../extensibility/internals/source-control-integration-overview.md)
- [Creazione di un pacchetto VSPackage di controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-vspackage.md)
