---
title: Novità del controllo del codice sorgente
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio SDK], source control
- source control [Visual Studio SDK], what's new
ms.assetid: bcf85418-18fb-4824-9dae-d14bf3d56a77
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 31b55c57f47f25814eff24f13bcf91408468d0f4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200948"
---
# <a name="what39s-new-in-source-control-in-visual-studio-2015"></a>Novità del controllo del codice sorgente in Visual Studio 2015&#39;

[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

In [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] è possibile fornire una soluzione di controllo del codice sorgente strettamente integrata implementando un pacchetto VSPackage del controllo del codice sorgente. In questa sezione vengono descritte le funzionalità dei pacchetti VSPackage del controllo del codice sorgente e viene fornita una panoramica dei passaggi di implementazione.  
  
## <a name="the-source-control-vspackage"></a>VSPackage del controllo del codice sorgente  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] supporta due tipi di soluzioni di controllo del codice sorgente. In tutte le versioni di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , è ancora possibile integrare un plug-in del controllo del codice sorgente basato sull'API. È anche possibile creare un pacchetto VSPackage per il controllo del codice sorgente che fornisce un percorso di integrazione approfondita [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] adatto per soluzioni di controllo del codice sorgente che richiedono un livello elevato di complessità e autonomia.  
  
 Un pacchetto VSPackage può aggiungere quasi qualsiasi tipo di funzionalità a [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Un VSPackage del controllo del codice sorgente fornisce una funzionalità di controllo del codice sorgente completa per [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , dall'interfaccia utente presentata all'utente per la comunicazione back-end con il sistema di controllo del codice sorgente.  
  
 Per l'implementazione di un pacchetto VSPackage del controllo del codice sorgente è necessaria una strategia "tutto o niente". L'autore di un pacchetto VSPackage di controllo del codice sorgente deve investire una notevole quantità di impegno nell'implementazione di una serie di interfacce di controllo del codice sorgente e di nuovi elementi dell'interfaccia utente (finestre di dialogo, menu e barre degli strumenti) per coprire l'intera funzionalità del controllo del codice sorgente, nonché le interfacce necessarie per l'integrazione corretta con il pacchetto [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 I passaggi seguenti forniscono una panoramica generale degli elementi necessari per implementare un pacchetto di controllo del codice sorgente. Per informazioni dettagliate, vedere [creazione di un pacchetto VSPackage del controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-vspackage.md).  
  
1. Creare un pacchetto VSPackage che dichiara un servizio di controllo del codice sorgente privato.  
  
2. Implementare le interfacce nei servizi correlati al controllo del codice sorgente offerti da [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , ad esempio <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> e dall' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> interfaccia.  
  
3. Registrare il pacchetto VSPackage del controllo del codice sorgente.  
  
4. Implementare tutte le interfacce utente del controllo del codice sorgente, incluse voci di menu, finestre di dialogo, barre degli strumenti e menu di scelta rapida.  
  
5. Tutti gli eventi correlati al controllo del codice sorgente vengono passati al controllo del codice sorgente VSackage quando è attivo e devono essere gestiti dal pacchetto VSPackage.  
  
6. Il pacchetto VSPackage del controllo del codice sorgente deve restare in ascolto di eventi come quelli che implementano l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> interfaccia, nonché tenere traccia degli eventi del documento di progetto (come implementato dall' <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> interfaccia) e intraprendere le azioni necessarie.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [Panoramica](../../extensibility/internals/source-control-integration-overview.md)   
 [Creazione di un pacchetto VSPackage di controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-vspackage.md)
