---
title: Pacchetto Interfaccia utente personalizzato (VSPackage del controllo del codice sorgente) | Microsoft Docs
description: Informazioni su come creare un'interfaccia utente personalizzata in Visual Studio usando un VSPackage del controllo del codice sorgente per specificare gli elementi dell'interfaccia utente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interface, source control packages
- source control packages, user interface
ms.assetid: f35ddb24-53bf-461e-b34f-7414f657c082
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: b688933859a4993b3032ab5b3fd1672eeae7261a4afb0788f5329435f12f98d7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121275515"
---
# <a name="custom-user-interface-source-control-vspackage"></a>Interfaccia utente personalizzata (VSPackage del controllo del codice sorgente)
Un PACCHETTO VSPackage dichiara le voci di menu e i relativi stati predefiniti tramite il file Visual Studio di comando (con estensione *vsct).* [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]L'ambiente di sviluppo integrato (IDE, Integrated Development Environment) visualizza le voci di menu negli stati predefiniti fino al caricamento del pacchetto VSPackage. Successivamente, viene <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> chiamato il metodo per abilitare o disabilitare le voci di menu.

 Un PACCHETTO VSPackage può impostare una chiave del Registro di sistema in modo che il PACCHETTO VSPackage possa essere caricato automaticamente in base a un contesto dell'interfaccia utente dei comandi, anche se in genere un pacchetto VSPackage del controllo del codice sorgente deve essere caricato su richiesta invece di passare semplicemente a un contesto dell'interfaccia utente specifico. Per altre informazioni sulla chiave del Registro di sistema **AutoLoadPackages,** vedere [Gestire i pacchetti VSPackage.](../../extensibility/managing-vspackages.md)

## <a name="vspackage-ui"></a>Interfaccia utente di VSPackage
 Un pacchetto di controllo del codice sorgente viene implementato come VSPackage e non usa alcuna interfaccia utente da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Ogni pacchetto VSPackage del controllo del codice sorgente deve specificare i propri elementi dell'interfaccia utente, ad esempio voci di menu, gruppi di menu, finestre degli strumenti, barre degli strumenti e qualsiasi interfaccia utente necessaria per l'impostazione di opzioni specifiche del pacchetto VSPackage del controllo del codice sorgente. Questi elementi dell'interfaccia utente possono essere abilitati in modo statico o dinamico. Gli elementi statici dell'interfaccia utente sono definiti in un file con estensione *vsct* e vengono visualizzati indipendentemente dal fatto che il VSPackage sia caricato o meno. Gli elementi dell'interfaccia utente dinamica possono essere visibili a seconda di un particolare contesto dell'interfaccia utente del comando, ad esempio , o come risultato di <xref:EnvDTE.Constants.vsContextNoSolution> una chiamata al metodo <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> . La visibilità degli elementi dinamici dell'interfaccia utente è conforme alla strategia per il caricamento ritardato dei pacchetti VSPackage.

## <a name="ui-constraints-on-source-control-vspackages"></a>Vincoli dell'interfaccia utente nei pacchetti VSPackage del controllo del codice sorgente
 Poiché il pacchetto VSPackage del controllo del codice sorgente non può essere rimosso dall'IDE dopo il caricamento, il VSPackage deve essere in grado di entrare in uno stato inattivo. Quando un PACCHETTO VSPackage riceve una notifica che indica che non è più attivo, il pacchetto VSPackage disabilita l'interfaccia utente e ignora qualsiasi interazione ide esterna. L'implementazione del metodo del VSPackage <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> deve nascondere i comandi quando il VSPackage non è attivo.

 Ogni VSPackage del controllo del codice sorgente deve implementare `IVsSccProvider` l'interfaccia . Due metodi sull'interfaccia, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> e , devono essere <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A> implementati dal pacchetto VSPackage.

 Il pacchetto VSPackage del controllo del codice sorgente potrebbe aver sottoscritto vari eventi IDE, implementati da <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> , e così via. È anche possibile che il pacchetto VSPackage abbia implementato interfacce di callback abilitate per il Registro di sistema, ad esempio <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> . Queste interfacce devono essere tutte ignorate quando sono inattive.

 L'elenco seguente mostra le interfacce interessate dallo stato attivo di un VSPackage del controllo del codice sorgente:

- Tenere traccia degli eventi dei documenti di progetto.

- Eventi della soluzione.

- Interfacce di persistenza della soluzione. Se inattivi, i pacchetti non devono scrivere nei file con estensione *sln* *e suo.*

- Controlli Extender di proprietà.

  Le interfacce obbligatorie e , oltre a eventuali interfacce facoltative associate al controllo del codice sorgente, non vengono chiamate quando il pacchetto VSPackage del controllo del codice <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> sorgente è inattivo.

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]All'avvio dell'IDE, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] imposta il contesto dell'interfaccia utente del comando sull'ID dell'ID VSPackage del controllo del codice sorgente predefinito corrente. In questo modo l'interfaccia utente statica del VSPackage del controllo del codice sorgente attivo viene visualizzata nell'IDE senza caricare effettivamente il pacchetto VSPackage. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sospende la registrazione del pacchetto VSPackage con tramite prima di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] effettuare chiamate al pacchetto <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> VSPackage.

  La tabella seguente descrive dettagli specifici sul modo in cui [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l'IDE nasconde diversi elementi dell'interfaccia utente.

| Elemento dell'interfaccia utente | Descrizione |
| - | - |
| Menu e barre degli strumenti | Il pacchetto di controllo del codice sorgente deve impostare gli stati di visibilità del menu iniziale e della barra degli strumenti sull'ID del pacchetto di controllo del codice sorgente nella [sezione VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) del file *con estensione vsct.* Ciò consente all'IDE di impostare lo stato delle voci di menu in modo appropriato senza caricare il VSPackage e chiamare [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] un'implementazione del <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodo . |
| Finestre degli strumenti | Il pacchetto VSPackage del controllo del codice sorgente nasconde tutte le finestre degli strumenti di cui è proprietario quando viene reso inattivo. |
| Pagine di opzioni specifiche del pacchetto VSPackage per il controllo del codice sorgente | La chiave del Registro di sistema **HKLM\SOFTWARE\Microsoft\VisualStudio\X.Y\ToolsOptionsPages\VisibilityCmdUIContexts** consente a un PACCHETTO VSPackage di impostare i contesti in cui è necessario visualizzare le pagine delle opzioni. Una voce del Registro di sistema in questa chiave deve essere creata usando l'ID del servizio (SID) del servizio di controllo del codice sorgente e assegnando alla voce un valore DWORD pari a 1. Ogni volta che si verifica un evento dell'interfaccia utente in un contesto con cui è registrato il VSPackage del controllo del codice sorgente, il VSPackage verrà chiamato se è attivo. |

## <a name="see-also"></a>Vedi anche
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>
- <xref:EnvDTE.Constants.vsContextNoSolution>
- [Gestire VSPackage](../../extensibility/managing-vspackages.md)
