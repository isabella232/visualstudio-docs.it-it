---
title: Novità del controllo del codice sorgente in Visual Studio 2015 SDK | Microsoft Docs
description: Informazioni sulle funzionalità dei pacchetti VSPackage del controllo del codice sorgente e su come esaminare una panoramica dei passaggi di implementazione.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio SDK], source control
- source control [Visual Studio SDK], what's new
ms.assetid: bcf85418-18fb-4824-9dae-d14bf3d56a77
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5a7df9af8dbd4af708483b638c0a86470a7d2220
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99940046"
---
# <a name="whats-new-in-source-control-for-the-visual-studio-2015-sdk"></a>Novità del controllo del codice sorgente per Visual Studio 2015 SDK

In [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] è possibile fornire una soluzione di controllo del codice sorgente strettamente integrata implementando un pacchetto VSPackage del controllo del codice sorgente. In questa sezione vengono descritte le funzionalità dei pacchetti VSPackage del controllo del codice sorgente e viene fornita una panoramica dei passaggi di implementazione.

## <a name="the-source-control-vspackage"></a>VSPackage del controllo del codice sorgente

Visual Studio supporta due tipi di soluzioni di controllo del codice sorgente. In tutte le versioni di Visual Studio è comunque possibile integrare un plug-in del controllo del codice sorgente basato sull'API. È anche possibile creare un pacchetto VSPackage per il controllo del codice sorgente che fornisce un percorso di integrazione approfondita [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] adatto per soluzioni di controllo del codice sorgente che richiedono un livello elevato di complessità e autonomia.

Un pacchetto VSPackage può aggiungere quasi qualsiasi tipo di funzionalità a Visual Studio. Un VSPackage del controllo del codice sorgente fornisce una funzionalità di controllo del codice sorgente completa per Visual Studio, dall'interfaccia utente presentata all'utente alla comunicazione back-end con il sistema di controllo del codice sorgente.

Per l'implementazione di un pacchetto VSPackage del controllo del codice sorgente è necessaria una strategia "tutto o niente". L'autore di un pacchetto VSPackage di controllo del codice sorgente deve investire una notevole quantità di sforzi nell'implementazione di una serie di interfacce di controllo del codice sorgente e di nuovi elementi dell'interfaccia utente (finestre di dialogo, menu e barre degli strumenti) per coprire l'intera funzionalità del controllo del codice sorgente, nonché le interfacce necessarie per l'integrazione corretta di qualsiasi pacchetto con Visual Studio.

I passaggi seguenti forniscono una panoramica generale degli elementi necessari per implementare un pacchetto di controllo del codice sorgente. Per informazioni dettagliate, vedere [creazione di un pacchetto VSPackage del controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-vspackage.md).

1. Creare un pacchetto VSPackage che dichiara un servizio di controllo del codice sorgente privato.

2. Implementare le interfacce nei servizi correlati al controllo del codice sorgente offerti da Visual Studio, ad esempio <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> e l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> interfaccia.

3. Registrare il pacchetto VSPackage del controllo del codice sorgente.

4. Implementare tutte le interfacce utente del controllo del codice sorgente, incluse voci di menu, finestre di dialogo, barre degli strumenti e menu di scelta rapida.

5. Tutti gli eventi correlati al controllo del codice sorgente vengono passati al controllo del codice sorgente VSackage quando è attivo e devono essere gestiti dal pacchetto VSPackage.

6. Il pacchetto VSPackage del controllo del codice sorgente deve restare in ascolto di eventi come quelli che implementano l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> interfaccia, nonché tenere traccia degli eventi del documento di progetto (come implementato dall' <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> interfaccia) e intraprendere le azioni necessarie.

## <a name="see-also"></a>Vedi anche

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- [Overview](../../extensibility/internals/source-control-integration-overview.md)
- [Creazione di un pacchetto VSPackage di controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-vspackage.md)
