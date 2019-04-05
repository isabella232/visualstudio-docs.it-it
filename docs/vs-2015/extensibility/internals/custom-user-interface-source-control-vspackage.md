---
title: Interfaccia utente personalizzata (VSPackage di controllo codice sorgente) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- user interface, source control packages
- source control packages, user interface
ms.assetid: f35ddb24-53bf-461e-b34f-7414f657c082
caps.latest.revision: 29
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f03713213ec2e54ed8d82d7528dae12cefab7ebc
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58955046"
---
# <a name="custom-user-interface-source-control-vspackage"></a>Interfaccia utente personalizzata (VSPackage di controllo del codice sorgente)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un pacchetto VSPackage dichiara le voci di menu e i relativi stati predefinito tramite il file di Visual Studio Command Table (vsct). Il [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ambiente di sviluppo integrato (IDE) le voci di menu viene visualizzato nei rispettivi Stati predefiniti fino a quando non viene caricato il pacchetto VSPackage. Successivamente, il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> viene chiamato per abilitare o disabilitare le voci di menu.  
  
 Un pacchetto VSPackage può impostare una chiave del Registro di sistema in modo che il pacchetto VSPackage può essere caricato automaticamente in base a un contesto dell'interfaccia utente del comando, anche se in genere controllo del codice sorgente VSPackage verrà caricato su richiesta anziché semplicemente il passaggio a un determinato contesto dell'interfaccia utente. Per altre informazioni sulla chiave del Registro di sistema AutoLoadPackages, vedere [gestione dei pacchetti VSPackage](../../extensibility/managing-vspackages.md).  
  
## <a name="vspackage-ui"></a>VSPackage dell'interfaccia utente  
 Un pacchetto controllo del codice sorgente viene implementato come un pacchetto VSPackage e non usa alcuna interfaccia utente da [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Ogni controllo del codice sorgente VSPackage è necessario specificare i proprio elementi dell'interfaccia utente, ad esempio voci di menu, gruppi di menu, finestre degli strumenti, barre degli strumenti e qualsiasi interfaccia utente necessaria per l'impostazione di opzioni specifico per il controllo del codice sorgente VSPackage. Questi elementi dell'interfaccia utente possono essere abilitati in modo statico o dinamico. Elementi dell'interfaccia utente statici sono definiti in un file vsct e vengono visualizzati se il VSPackage viene caricato o non. Elementi dell'interfaccia utente dinamici potrebbero essere visibili a seconda del contesto dell'interfaccia utente un comando specifico, ad esempio <xref:EnvDTE.Constants.vsContextNoSolution>, o come risultato di una chiamata al <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> (metodo). La visibilità degli elementi dell'interfaccia utente dinamici è conforme con la strategia per il caricamento ritardato di VSPackage.  
  
## <a name="ui-constraints-on-source-control-vspackages"></a>Vincoli di interfaccia utente per pacchetti VSPackage di controllo di origine  
 Poiché VSPackage di controllo del codice sorgente non può essere rimosso dall'IDE di dopo essere stato caricato, il pacchetto VSPackage deve essere in grado di passare a uno stato inattivo. Quando un pacchetto VSPackage riceve una notifica che non è più attivo, il pacchetto VSPackage disabilita la relativa interfaccia utente e ignora qualsiasi interazione IDE esterno. L'implementazione di VSPackage del <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodo consigliabile nascondere i comandi quando il pacchetto VSPackage non è attivo.  
  
 Ogni controllo del codice sorgente pacchetto VSPackage deve implementare il `IVsSccProvider` interfaccia. Due metodi sull'interfaccia, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>, deve essere implementata da VSPackage.  
  
 Il controllo del codice sorgente VSPackage può sottoscritti a vari eventi IDE, che vengono implementati mediante il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>e così via. Inoltre, il pacchetto VSPackage hanno implementato le interfacce di callback basate sul Registro di sistema, ad esempio il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>. Questi devono tutte essere ignorati quando è inattivo.  
  
 Nell'elenco seguente mostra le interfacce impatto lo stato attivo di un pacchetto VSPackage di controllo di origine:  
  
- Tenere traccia degli eventi di documenti di progetto.  
  
- Eventi della soluzione.  
  
- Interfacce di persistenza di soluzione. Quando è inattivo, i pacchetti non devono scrivere i file con estensione sln e suo.  
  
- Estensioni della proprietà.  
  
  Richiesti <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>, e anche eventuali interfacce facoltative associate al controllo del codice sorgente, non vengono chiamati quando il pacchetto VSPackage di controllo di origine è inattivo.  
  
  Quando la [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] avvio dell'IDE, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] imposta il contesto dell'interfaccia utente del comando per l'ID del controllo sorgente predefinito corrente ID del pacchetto VSPackage. In questo modo l'interfaccia utente statico del pacchetto VSPackage venga visualizzata nell'IDE senza effettivamente il caricamento di VSPackage di controllo del codice sorgente attivo. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] viene sospeso per il pacchetto VSPackage registrarsi [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] attraverso il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> prima di inviare tutte le chiamate al pacchetto VSPackage.  
  
  La tabella seguente descrive i dettagli specifici sul modo in cui [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE nasconde gli elementi dell'interfaccia utente diversi.  
  
|Elemento dell'interfaccia utente|Descrizione|  
|-------------|-----------------|  
|Menu e barre degli strumenti|Il pacchetto del controllo codice sorgente è necessario impostare gli stati iniziali di visibilità della barra degli strumenti e menu per l'ID di pacchetto di controllo di origine nel [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) sezione del file con estensione vsct. In questo modo, il [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE per impostare in modo appropriato lo stato delle voci di menu senza il caricamento di VSPackage e la chiamata a un'implementazione del <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> (metodo).|  
|Finestre degli strumenti|Il controllo del codice sorgente VSPackage nasconde le finestre degli strumenti che cui diventa proprietaria quando viene reso inattivo.|  
|Pagine delle opzioni di controllo del codice sorgente specifico del VSPackage|La chiave del Registro di sistema HKLM\SOFTWARE\Microsoft\VisualStudio\X.Y\ToolsOptionsPages\VisibilityCmdUIContexts consente a un pacchetto VSPackage di impostare i contesti in cui sono necessarie relative pagine di opzioni da visualizzare. Una voce del Registro di sistema sotto questa chiave dovrà essere creato usando il servizio di ID (SID) del servizio di controllo di origine e assegnarle un valore DWORD pari a 1. Ogni volta che l'interfaccia utente si verifica un evento nel contesto di un pacchetto VSPackage è registrato con il controllo del codice sorgente, verrà chiamato il pacchetto VSPackage se è attiva.|  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>   
 <xref:EnvDTE.Constants.vsContextNoSolution>   
 [Gestione dei pacchetti VSPackage](../../extensibility/managing-vspackages.md)
