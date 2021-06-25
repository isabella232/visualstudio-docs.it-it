---
title: Proprietà di progetto Interfaccia utente | Microsoft Docs
description: Informazioni su come i sottotipi di progetto possono modificare la finestra di dialogo Pagine delle proprietà del progetto come specificato dal progetto di base.
ms.custom: SEO-VS-2020
ms.date: 03/22/2018
ms.topic: reference
helpviewer_keywords:
- project properties [Visual Studio], user interface
- projects [Visual Studio SDK], properties UI
- project properties UI
ms.assetid: b6aec634-8533-476c-9ebd-36536a2288e2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 77e3554f2a3fd3b0dc1d608bb7d0a1198116a4e3
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903589"
---
# <a name="project-property-user-interface"></a>Interfaccia utente delle proprietà del progetto

Un sottotipo di progetto può  usare gli elementi nella finestra di dialogo Pagine delle proprietà del progetto così come vengono forniti dal progetto di  base, nascondere o rendere disponibili controlli di sola lettura e pagine intere oppure aggiungere pagine specifiche del sottotipo di progetto alla finestra di dialogo Pagine delle proprietà.

## <a name="extending-the-project-property-dialog-box"></a>Estensione della finestra di dialogo Proprietà progetto

Un sottotipo di progetto implementa gli extender di automazione e gli oggetti di esplorazione della configurazione del progetto. Questi extender implementano <xref:EnvDTE.IFilterProperties> l'interfaccia per rendere nascoste o di sola lettura determinate proprietà. La **finestra di dialogo** Pagine delle proprietà del progetto di base, implementata dal progetto di base, rispetta il filtro eseguito dagli extender di automazione.

Il processo di estensione di una **finestra di dialogo Proprietà** progetto è descritto di seguito:

- Il progetto di base recupera gli extender dal sottotipo di progetto implementando <xref:EnvDTE80.IInternalExtenderProvider> l'interfaccia . Gli oggetti browse, project automation e project configuration del progetto del progetto di base implementano questa interfaccia.

- L'implementazione di per l'oggetto di esplorazione del progetto e il delegato dell'oggetto di automazione del progetto all'implementazione dell'aggregatore del sottotipo di progetto, ovvero per <xref:EnvDTE80.IInternalExtenderProvider> <xref:EnvDTE80.IInternalExtenderProvider> `QueryInterface` l'oggetto del <xref:EnvDTE80.IInternalExtenderProvider> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> progetto.

- L'oggetto browse della configurazione del progetto di base implementa anche per collegare <xref:EnvDTE80.IInternalExtenderProvider> direttamente l'extender di automazione dall'oggetto di configurazione del sottotipo di progetto. La relativa implementazione delega <xref:EnvDTE80.IInternalExtenderProvider> all'interfaccia implementata dall'aggregatore del sottotipo di progetto.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>, implementato dall'oggetto di esplorazione della configurazione del progetto, restituisce <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> l'oggetto .

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>, implementato anche dall'oggetto di esplorazione della configurazione del progetto, restituisce <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> l'oggetto .

- Un sottotipo di progetto può determinare i CATID appropriati per i vari oggetti estendibili del progetto di base in fase di esecuzione recuperando i valori <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> seguenti:

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_ExtObjectCATID>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_BrowseObjectCATID>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_CfgBrowseObjectCATID>

Per determinare i CATID per l'ambito del progetto, il sottotipo di progetto recupera le proprietà precedenti per [VSITEMID. Radice](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>) da `VSITEMID typedef` . Un sottotipo di progetto  può anche voler controllare quali pagine della finestra di dialogo Pagine delle proprietà vengono visualizzate per il progetto, sia dipendenti dalla configurazione che indipendenti dalla configurazione. Alcuni sottotipi di progetto potrebbero dover rimuovere pagine incorporate e aggiungere pagine specifiche del sottotipo di progetto. Per abilitare questa funzionalità, il progetto client gestito chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> metodo per le proprietà seguenti:

- `VSHPROPID_PropertyPagesCLSIDList` : elenco delimitato da punti e virgola di CLSID delle pagine delle proprietà indipendenti dalla configurazione.

- `VSHPROPID_CfgPropertyPagesCLSIDList —` elenco delimitato da punti e virgola di CLSID delle pagine delle proprietà dipendenti dalla configurazione.

Poiché il sottotipo di progetto aggrega l'oggetto, può eseguire l'override della definizione di queste proprietà per controllare quali finestre di dialogo delle pagine delle proprietà <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> vengono visualizzate.  Il sottotipo di progetto può recuperare queste proprietà dal progetto di base interno e quindi aggiungere o rimuovere i CLSID in base alle esigenze.

Alle nuove pagine delle proprietà aggiunte da un sottotipo di progetto viene passato un oggetto di esplorazione della configurazione del progetto dall'implementazione del progetto di base. Questo oggetto di esplorazione della configurazione del progetto supporta Gli extender di automazione. Per altre informazioni su AutomationExtenders, vedere [Implementazione e uso di Extender di automazione](/previous-versions/0y92k2w2(v=vs.140)). Le pagine delle proprietà implementate dalla chiamata al sottotipo di progetto per recuperare il proprio oggetto di esplorazione della configurazione del sottotipo di progetto che estende l'oggetto di esplorazione della configurazione <xref:EnvDTE.Project.Extender%2A> del progetto di base.

## <a name="see-also"></a>Vedere anche

- <xref:EnvDTE.IFilterProperties>
- [Finestra di dialogo Pagine delle proprietà](/previous-versions/visualstudio/visual-studio-2010/as5chysf(v=vs.100))