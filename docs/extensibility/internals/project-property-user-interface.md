---
title: Interfaccia utente delle proprietà del progetto Documenti Microsoft
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- project properties [Visual Studio], user interface
- projects [Visual Studio SDK], properties UI
- project properties UI
ms.assetid: b6aec634-8533-476c-9ebd-36536a2288e2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4634eb5edaab16752bc5df82d70371a580845d28
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706390"
---
# <a name="project-property-user-interface"></a>Interfaccia utente delle proprietà del progetto

Un sottotipo di progetto può utilizzare gli elementi nella finestra di dialogo **Pagine delle proprietà** del progetto come vengono forniti dal progetto di base, nascondere o rendere i controlli di sola lettura e le pagine intere come fornito o aggiungere pagine specifiche del sottotipo di progetto per le pagine delle **proprietà.**

## <a name="extending-the-project-property-dialog-box"></a>Estensione della finestra di dialogo Proprietà progettoExtending the Project Property Dialog Box

Un sottotipo di progetto implementa estensioni di automazione e oggetti di esplorazione della configurazione del progetto. Questi Extender implementano l'interfaccia <xref:EnvDTE.IFilterProperties> per rendere nascoste le proprietà particolari o di sola lettura. La finestra di dialogo **Pagine delle proprietà** del progetto di base, implementata dal progetto di base, rispetta il filtro eseguito dalle estensioni di automazione.

Il processo di estensione di una finestra di dialogo Proprietà progetto è descritto di seguito:The process of extending a **Project Property** dialog box is outlined below:

- Il progetto di base recupera gli extender dal <xref:EnvDTE80.IInternalExtenderProvider> sottotipo di progetto implementando l'interfaccia . Gli oggetti Sfoglia, automazione del progetto e Configurazione progetto esplorano gli oggetti del progetto di base implementano questa interfaccia.

- L'implementazione <xref:EnvDTE80.IInternalExtenderProvider> di per l'oggetto sfoglia del <xref:EnvDTE80.IInternalExtenderProvider> progetto e il delegato dell'oggetto di `QueryInterface` automazione del progetto all'implementazione dell'aggregatore di sottotipi di progetto (vale a dire, per loro nell'oggetto <xref:EnvDTE80.IInternalExtenderProvider> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> progetto).

- L'oggetto sfoglia della <xref:EnvDTE80.IInternalExtenderProvider> configurazione del progetto di base implementa anche per collegare direttamente l'estensione di automazione dall'oggetto di configurazione del sottotipo di progetto. L'implementazione <xref:EnvDTE80.IInternalExtenderProvider> delega all'interfaccia implementata dall'aggregatore di sottotipi di progetto.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>, implementato dall'oggetto sfoglia della <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> configurazione del progetto, restituisce l'oggetto.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>, implementato anche dall'oggetto sfoglia <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> della configurazione del progetto, restituisce l'oggetto.

- Un sottotipo di progetto può determinare i CATID appropriati per i vari oggetti estensibili del progetto di base in fase di esecuzione recuperando i valori seguenti: <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_ExtObjectCATID>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_BrowseObjectCATID>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_CfgBrowseObjectCATID>

Per determinare i CATID per l'ambito del progetto, il sottotipo di progetto recupera le proprietà precedenti per [VSITEMID. Radice](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>) dal `VSITEMID typedef`file . Un sottotipo di progetto può anche decidere di controllare quali **pagine delle proprietà** vengono visualizzate le pagine della finestra di dialogo per il progetto, sia dipendenti dalla configurazione che indipendenti dalla configurazione. Alcuni sottotipi di progetto potrebbero dover rimuovere le pagine predefinite e aggiungere pagine specifiche del sottotipo di progetto. A tale scopo, il progetto client <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> gestito chiama il metodo per le proprietà seguenti:In order to enable this, the managed client project calls the method for the following properties:

- `VSHPROPID_PropertyPagesCLSIDList`: un elenco delimitato da punti e virgola di CLSID delle pagine delle proprietà indipendenti dalla configurazione.

- `VSHPROPID_CfgPropertyPagesCLSIDList —`un elenco delimitato da punti e virgola di CLSID di pagine delle proprietà dipendenti dalla configurazione.

Poiché il sottotipo <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> di progetto aggrega l'oggetto, può eseguire l'override della definizione di queste proprietà per controllare quali **pagine delle proprietà** vengono visualizzate le finestre di dialogo. Il sottotipo di progetto può recuperare queste proprietà dal progetto di base interno e quindi aggiungere o rimuovere CLSID in base alle esigenze.

Alle nuove pagine delle proprietà aggiunte da un sottotipo di progetto viene passato un oggetto sfoglia della configurazione del progetto dall'implementazione del progetto di base. Questo oggetto Sfoglia configurazione progetto supporta le estensioni di automazione. Per ulteriori informazioni su AutomationExtenders, vedere [Implementazione e utilizzo di estensioni](https://msdn.microsoft.com/Library/0d5c218c-f412-4b28-ab0c-33a611f62356)di automazione . Le pagine delle proprietà implementate <xref:EnvDTE.Project.Extender%2A> dalla chiamata del sottotipo di progetto per recuperare il proprio oggetto di visualizzazione di configurazione di sottotipo di progetto che estende l'oggetto di visualizzazione della configurazione del progetto di base.

## <a name="see-also"></a>Vedere anche

- <xref:EnvDTE.IFilterProperties>
- [Finestra di dialogo Pagine delle proprietà](/previous-versions/visualstudio/visual-studio-2010/as5chysf(v=vs.100))
