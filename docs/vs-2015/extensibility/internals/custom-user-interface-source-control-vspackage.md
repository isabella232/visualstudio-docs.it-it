---
title: Interfaccia utente personalizzata (VSPackage del controllo del codice sorgente) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68154986"
---
# <a name="custom-user-interface-source-control-vspackage"></a>Interfaccia utente personalizzata (VSPackage di controllo del codice sorgente)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un pacchetto VSPackage dichiara le voci di menu e i relativi stati predefiniti tramite il file della tabella dei comandi di Visual Studio (con estensione vsct). Il [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Integrated Development Environment (IDE) Visualizza le voci di menu negli stati predefiniti fino a quando il pacchetto VSPackage non viene caricato. Successivamente, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> viene chiamato il metodo per abilitare o disabilitare le voci di menu.  
  
 Un pacchetto VSPackage può impostare una chiave del registro di sistema in modo che il pacchetto VSPackage possa essere caricato automaticamente in base a un contesto dell'interfaccia utente di comando, anche se in genere un VSPackage del controllo del codice sorgente deve essere caricato su richiesta anziché semplicemente passare a un particolare contesto dell'interfaccia utente. Per ulteriori informazioni sulla chiave del registro di sistema AutoLoadPackages, vedere [gestione dei pacchetti VSPackage](../../extensibility/managing-vspackages.md).  
  
## <a name="vspackage-ui"></a>Interfaccia utente VSPackage  
 Un pacchetto di controllo del codice sorgente viene implementato come VSPackage e non usa alcuna interfaccia utente da [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Ogni VSPackage del controllo del codice sorgente deve specificare i propri elementi dell'interfaccia utente, ad esempio le voci di menu, i gruppi di menu, le finestre degli strumenti, le barre degli strumenti e qualsiasi interfaccia utente necessaria per impostare le opzioni specifiche del pacchetto VSPackage del controllo Questi elementi dell'interfaccia utente possono essere abilitati in modo statico o dinamico. Gli elementi statici dell'interfaccia utente sono definiti in un file con estensione vsct e vengono visualizzati se il pacchetto VSPackage è stato caricato o meno. Gli elementi dinamici dell'interfaccia utente possono essere visibili a seconda del contesto dell'interfaccia utente di un comando specifico, ad esempio <xref:EnvDTE.Constants.vsContextNoSolution> o come risultato di una chiamata al <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodo. La visibilità degli elementi dinamici dell'interfaccia utente è conforme alla strategia per il caricamento ritardato dei pacchetti VSPackage.  
  
## <a name="ui-constraints-on-source-control-vspackages"></a>Vincoli dell'interfaccia utente nei pacchetti VSPackage del controllo del codice sorgente  
 Poiché il pacchetto VSPackage del controllo del codice sorgente non può essere rimosso dall'IDE dopo che è stato caricato, il pacchetto VSPackage deve essere in grado di entrare in uno stato inattivo. Quando un pacchetto VSPackage riceve una notifica che non è più attivo, il pacchetto VSPackage Disabilita la relativa interfaccia utente e ignora qualsiasi interazione IDE esterna. L'implementazione del pacchetto VSPackage del <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodo deve nascondere i comandi quando il pacchetto VSPackage non è attivo.  
  
 Ogni VSPackage del controllo del codice sorgente deve implementare l' `IVsSccProvider` interfaccia. Due metodi sull'interfaccia, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A> , devono essere implementati dal pacchetto VSPackage.  
  
 Il pacchetto VSPackage del controllo del codice sorgente potrebbe aver sottoscritto vari eventi IDE, implementati da <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> , <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> e così via. Inoltre, il pacchetto VSPackage potrebbe avere implementato interfacce di callback abilitate per il registro di sistema, ad esempio <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> . Questi devono essere tutti ignorati quando sono inattivi.  
  
 L'elenco seguente mostra le interfacce interessate dallo stato attivo di un pacchetto VSPackage del controllo del codice sorgente:  
  
- Tenere traccia degli eventi dei documenti di progetto.  
  
- Eventi della soluzione.  
  
- Interfacce di persistenza della soluzione. Quando è inattivo, i pacchetti non devono scrivere in file con estensione sln e suo.  
  
- Extender della proprietà.  
  
  Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> interfacce obbligatorie e <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> e tutte le interfacce facoltative associate al controllo del codice sorgente non vengono chiamate quando il pacchetto VSPackage del controllo del codice sorgente è inattivo.  
  
  Quando l' [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE viene avviato, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] imposta il contesto dell'interfaccia utente del comando sull'ID dell'ID VSPackage predefinito del controllo del codice sorgente corrente. In questo modo l'interfaccia utente statica del VSPackage del controllo del codice sorgente attivo viene visualizzata nell'IDE senza caricare effettivamente il pacchetto VSPackage. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] sospende il pacchetto VSPackage per la registrazione con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] tramite prima di effettuare <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> qualsiasi chiamata al pacchetto VSPackage.  
  
  Nella tabella seguente vengono descritti i dettagli specifici sul modo in cui l' [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE nasconde elementi dell'interfaccia utente diversi.  
  
|Elemento dell'interfaccia utente|Descrizione|  
|-------------|-----------------|  
|Menu e barre degli strumenti|Il pacchetto del controllo del codice sorgente deve impostare gli Stati di visibilità del menu iniziale e della barra degli strumenti sull'ID del pacchetto del controllo del codice sorgente nella sezione [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) del file. vsct. Ciò consente all' [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE di impostare lo stato delle voci di menu in modo appropriato senza caricare il pacchetto VSPackage e chiamare un'implementazione del <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodo.|  
|Finestre degli strumenti|Il pacchetto VSPackage del controllo del codice sorgente nasconde tutte le finestre degli strumenti di cui è proprietario quando viene reso inattivo.|  
|Pagine di opzioni specifiche del pacchetto VSPackage del controllo del codice sorgente|La chiave del registro di sistema HKLM\SOFTWARE\Microsoft\VisualStudio\X.Y\ToolsOptionsPages\VisibilityCmdUIContexts consente a un VSPackage di impostare i contesti in cui sono necessarie le pagine di opzioni da visualizzare. Una voce del registro di sistema sotto questa chiave deve essere creata usando l'ID del servizio (SID) del servizio di controllo del codice sorgente e assegnando a tale voce un valore DWORD pari a 1. Ogni volta che si verifica un evento dell'interfaccia utente in un contesto in cui è registrato il pacchetto VSPackage del controllo del codice sorgente, il pacchetto VSPackage verrà chiamato se è attivo.|  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>   
 <xref:EnvDTE.Constants.vsContextNoSolution>   
 [Gestione dei pacchetti VSPackage](../../extensibility/managing-vspackages.md)
