---
title: Struttura VSPackage (VSPackage di controllo codice sorgente) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSPackages, structure
- source control packages, VSPackage overview
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
caps.latest.revision: 27
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 592f24a4fc4100f7c716c7fbec0c300c0adec906
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49305032"
---
# <a name="vspackage-structure-source-control-vspackage"></a>Struttura VSPackage (VSPackage di controllo del codice sorgente)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

il SDK di pacchetto di controllo di origine fornisce indicazioni per la creazione di un pacchetto VSPackage che consentono a un implementatore di controllo di origine per integrare la propria funzionalità di controllo di origine con il [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ambiente. Un pacchetto VSPackage è un componente COM che in genere viene caricato su richiesta per il [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ambiente di sviluppo integrato (IDE) in base ai servizi che vengono annunciati dal pacchetto in relative voci del Registro di sistema. Ogni pacchetto VSPackage deve implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>. Un pacchetto VSPackage Usa in genere i servizi offerti dal [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE e offre alcuni servizi specifici.  
  
 Un pacchetto VSPackage dichiara le voci di menu e viene stabilito uno stato dell'elemento predefinito tramite il file con estensione vsct. Il [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE visualizza le voci di menu in questo stato fino a quando non viene caricato il pacchetto VSPackage. Successivamente, l'implementazione di VSPackage del <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> viene chiamato per abilitare o disabilitare le voci di menu.  
  
## <a name="source-control-package-characteristics"></a>Caratteristiche di pacchetto di origine controllo  
 Un pacchetto VSPackage completamente integrato nel controllo del codice sorgente [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 La semantica di VSPackage include:  
  
-   Interfaccia da implementare poiché è un pacchetto VSPackage (il `IVsPackage` interfaccia)  
  
-   Implementazione dei comandi dell'interfaccia utente (file con estensione vsct e l'implementazione del <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia)  
  
-   Registrazione del pacchetto VSPackage con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 Il controllo del codice sorgente VSPackage deve comunicare con queste altre [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] entità:  
  
-   Progetti  
  
-   Editor  
  
-   Soluzioni  
  
-   WINDOWS  
  
-   La tabella documenti in esecuzione  
  
### <a name="visual-studio-environment-services-that-may-be-consumed"></a>Servizi dell'ambiente Visual Studio che possono essere usati  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 Servizio SVsRegisterScciProvider  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>  
  
### <a name="vsip-interfaces-implemented-and-called"></a>VSIP interfacce implementate e chiamato  
 Un pacchetto controllo del codice sorgente è un pacchetto VSPackage e pertanto può interagire direttamente con gli altri pacchetti VSPackage registrati con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Per garantire l'ampia gamma di controllo del codice sorgente, un controllo del codice sorgente VSPackage può gestire le interfacce fornite dai progetti o la shell.  
  
 Tutti i progetti di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] deve implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> venga riconosciuta come un progetto all'interno di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE. Tuttavia, questa interfaccia non specializzata sufficiente per controllo del codice sorgente. I progetti che dovrebbero essere nel gruppo origine controllano implementano il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>. Questa interfaccia viene utilizzata dal pacchetto VSPackage di controllo del codice sorgente per eseguire query di un progetto del relativo contenuto e fornire i glifi e informazioni di associazione (le informazioni necessarie per stabilire una connessione tra il percorso del server e il percorso del disco di un progetto che si trova sotto controllo del codice sorgente).  
  
 Il controllo del codice sorgente pacchetto VSPackage implementa il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>, che a sua volta consente ai progetti di registrarsi per il controllo di origine e recuperare le icone di stato.  
  
 Per un elenco completo di interfacce che debba prendere in considerazione un pacchetto VSPackage di controllo di origine, vedere [interfacce e servizi correlati](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Elementi di progettazione](../../extensibility/internals/source-control-vspackage-design-elements.md)   
 [Interfacce e servizi correlati](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)

