---
title: Interfaccia utente personalizzata (controllo del codice sorgente VSPackage) . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interface, source control packages
- source control packages, user interface
ms.assetid: f35ddb24-53bf-461e-b34f-7414f657c082
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a6ef807cef17a6ca3cddfee05ba57ace27e34a9e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708923"
---
# <a name="custom-user-interface-source-control-vspackage"></a>Interfaccia utente personalizzata (controllo del codice sorgente VSPackage)Custom user interface (source control VSPackage)
Un pacchetto VSPackage dichiara le voci di menu e i relativi stati predefiniti tramite il file della tabella dei comandi di Visual Studio (*.vsct*). L'ambiente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] di sviluppo integrato (IDE) visualizza le voci di menu nei relativi stati predefiniti fino a quando non viene caricato il pacchetto VSPackage.The integrated development environment (IDE) displays the menu items in their default states until the VSPackage is loaded. Successivamente, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> il metodo viene chiamato per abilitare o disabilitare le voci di menu.

 Un pacchetto VSPackage può impostare una chiave del Registro di sistema in modo che il pacchetto VSPackage può essere caricato automaticamente in base a un contesto dell'interfaccia utente di comando, anche se in genere un controllo del codice sorgente VSPackage deve caricare su richiesta anziché solo il passaggio a un particolare contesto dell'interfaccia utente. Per ulteriori informazioni sulla chiave del Registro di sistema **AutoLoadPackages,** vedere [Gestire VSPackage](../../extensibility/managing-vspackages.md).

## <a name="vspackage-ui"></a>Interfaccia utente di VSPackage
 Un pacchetto di controllo del codice sorgente viene implementato [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]come un VSPackage e non utilizza alcuna interfaccia utente da . Ogni controllo del codice sorgente VSPackage deve specificare i propri elementi dell'interfaccia utente, ad esempio voci di menu, gruppi di menu, finestre degli strumenti, barre degli strumenti e qualsiasi interfaccia utente necessaria per l'impostazione di opzioni specifiche per il controllo del codice sorgente VSPackage.Each source control VSPackage must specify its own UI elements such as menu items, menu groups, tool windows, toolbars, and any required UI for setting options specific to the source control VSPackage. Questi elementi dell'interfaccia utente possono essere abilitati in modo statico o dinamico. Gli elementi statici dell'interfaccia utente sono definiti in un file *con estensione vsct* e vengono visualizzati indipendentemente dal fatto che il pacchetto VSPackage venga caricato o meno. Gli elementi dinamici dell'interfaccia utente possono essere <xref:EnvDTE.Constants.vsContextNoSolution>visibili a seconda di un <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> particolare contesto dell'interfaccia utente del comando, ad esempio , o come risultato di una chiamata al metodo. La visibilità degli elementi dinamici dell'interfaccia utente è conforme alla strategia per il caricamento ritardato dei package VS.

## <a name="ui-constraints-on-source-control-vspackages"></a>Vincoli dell'interfaccia utente sui pacchetti VSPackage del controllo del codice sorgenteUI constraints on source control VSPackages
 Poiché il controllo del codice sorgente VSPackage non può essere rimosso dall'IDE dopo il caricamento, il pacchetto VSPackage deve essere in grado di immettere uno stato inattivo. Quando un VSPackage riceve la notifica che non è più attivo, il pacchetto VSPackage disabilita l'interfaccia utente e ignora qualsiasi interazione IDE esterno. L'implementazione del metodo <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> deve nascondere i comandi del pacchetto VSPackage quando il pacchetto VSPackage non è attivo.

 Ogni controllo del codice `IVsSccProvider` sorgente VSPackage deve implementare l'interfaccia. Due metodi <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> sull'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>e , devono essere implementati dal pacchetto VSPackage.

 Il controllo del codice sorgente VSPackage potrebbe aver sottoscritto <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>vari <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>eventi IDE, implementati da , e così via. Inoltre, il pacchetto VSPackage potrebbe aver implementato le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>interfacce di callback abilitate al Registro di sistema, ad esempio il file . Queste interfacce devono essere tutte ignorate quando sono inattive.

 The following list shows the interfaces affected by the active state of a source control VSPackage:

- Tenere traccia degli eventi dei documenti di progetto.

- Eventi di soluzione.

- Interfacce di persistenza della soluzione. Quando sono inattivi, i pacchetti non devono scrivere nei file *sln* e *suo.*

- Estensioni di proprietà.

  I <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> servizi <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>obbligatori e , e anche le interfacce facoltative associate al controllo del codice sorgente, non vengono chiamati quando il controllo del codice sorgente VSPackage è inattivo.

  Quando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l'IDE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] viene avviato, imposta il contesto dell'interfaccia utente di comando per l'ID del controllo del codice sorgente predefinito corrente VSPackage ID. In questo modo l'interfaccia utente statica del controllo del codice sorgente attivo VSPackage per visualizzare nell'IDE senza effettivamente caricare il pacchetto VSPackage. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]pause per il pacchetto VSPackage per la registrazione con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tramite il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> prima di effettuare qualsiasi chiamata al pacchetto VSPackage.

  Nella tabella seguente vengono descritti [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dettagli specifici su come l'IDE nasconde diversi elementi dell'interfaccia utente.

| Elemento dell'interfaccia utente | Descrizione |
| - | - |
| Menu e barre degli strumenti | Il pacchetto del controllo del codice sorgente deve impostare gli stati di visibilità iniziali del menu e della barra degli strumenti sull'ID del pacchetto del controllo del codice sorgente nella sezione [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) del file *vsct.* In questo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] modo l'IDE per impostare lo stato delle voci di <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> menu in modo appropriato senza caricare il pacchetto VSPackage e chiamare un'implementazione del metodo. |
| Finestre degli strumenti | Il controllo del codice sorgente VSPackage nasconde tutte le finestre degli strumenti che possiede quando viene reso inattivo. |
| Controllo del codice sorgente VSPackage-specifiche pagine di opzioni | La chiave del Registro di sistema **HKLM SOFTWARE Microsoft VisualStudio X.Y.ToolsOptionsPages VisibilityCmdUIContexts** consente a un VSPackage impostare i contesti in cui richiede le pagine di opzioni da visualizzare. Una voce del Registro di sistema in questa chiave dovrebbe essere creata utilizzando l'ID del servizio (SID) del servizio di controllo del codice sorgente e assegnandole un valore DWORD pari a 1. Ogni volta che si verifica un evento dell'interfaccia utente in un contesto il controllo del codice sorgente VSPackage viene registrato con, il pacchetto VSPackage verrà chiamato se è attivo. |

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>
- <xref:EnvDTE.Constants.vsContextNoSolution>
- [Gestire VSPackage](../../extensibility/managing-vspackages.md)
