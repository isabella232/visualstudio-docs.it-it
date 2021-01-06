---
title: Interfaccia utente della proprietà del progetto | Microsoft Docs
description: Informazioni su come i sottotipi di progetto possono modificare la finestra di dialogo Pagine delle proprietà del progetto come fornito dal progetto di base.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 2c9bba8b163b7fd21cfa829bb26e06cf37b887bd
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877390"
---
# <a name="project-property-user-interface"></a>Interfaccia utente delle proprietà del progetto

Un sottotipo di progetto può utilizzare gli elementi della finestra di dialogo **pagine delle proprietà** del progetto in modo che vengano forniti dal progetto di base, nascondere o rendere i controlli di sola lettura e le pagine intere fornite o aggiungere pagine specifiche del sottotipo di progetto alla finestra di dialogo **pagine delle proprietà** .

## <a name="extending-the-project-property-dialog-box"></a>Estensione della finestra di dialogo Proprietà progetto

Un sottotipo di progetto implementa gli oggetti Extender di automazione e gli oggetti browse della configurazione del progetto. Questi Extender implementano l' <xref:EnvDTE.IFilterProperties> interfaccia per rendere particolari le proprietà nascoste o di sola lettura. La finestra di dialogo **pagine delle proprietà** del progetto di base, implementata dal progetto di base, rispetta il filtro eseguito dagli Extender di automazione.

Il processo di estensione di una finestra di dialogo delle **proprietà del progetto** è illustrato di seguito:

- Il progetto di base recupera gli Extender dal sottotipo di progetto implementando l' <xref:EnvDTE80.IInternalExtenderProvider> interfaccia. Gli oggetti browse, Automation Project e Project Configuration per esplorare il progetto di base implementano tutte questa interfaccia.

- Implementazione di <xref:EnvDTE80.IInternalExtenderProvider> per l'oggetto browse del progetto e l'oggetto di automazione del progetto delegato all' <xref:EnvDTE80.IInternalExtenderProvider> implementazione del sottotipo di progetto aggregator, ovvero per l'oggetto del `QueryInterface` <xref:EnvDTE80.IInternalExtenderProvider> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> progetto.

- L'oggetto di esplorazione della configurazione del progetto di base implementa anche <xref:EnvDTE80.IInternalExtenderProvider> per collegare direttamente nell'Extender di automazione dall'oggetto di configurazione del sottotipo di progetto. La relativa implementazione delega all' <xref:EnvDTE80.IInternalExtenderProvider> interfaccia implementata dal sottotipo di progetto Aggregator.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>, implementato dall'oggetto browse della configurazione del progetto, restituisce l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> oggetto.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>, implementato anche dall'oggetto browse della configurazione del progetto, restituisce l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> oggetto.

- Un sottotipo di progetto può determinare il CATID appropriato per i vari oggetti estendibili del progetto di base in fase di esecuzione recuperando i <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> valori seguenti:

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_ExtObjectCATID>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_BrowseObjectCATID>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_CfgBrowseObjectCATID>

Per determinare il CATID per l'ambito del progetto, il sottotipo di progetto recupera le proprietà precedenti per [VSITEMID. Radice](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>) da `VSITEMID typedef` . Un sottotipo di progetto può anche voler controllare le pagine delle finestre di dialogo delle **pagine delle proprietà** visualizzate per il progetto, sia dipendenti dalla configurazione che indipendenti dalla configurazione. Alcuni sottotipi di progetto possono dover rimuovere pagine predefinite e aggiungere pagine specifiche del sottotipo di progetto. Per abilitare questa operazione, il progetto client gestito chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> metodo per le proprietà seguenti:

- `VSHPROPID_PropertyPagesCLSIDList` : elenco delimitato da punti e virgola di CLSID delle pagine delle proprietà indipendenti dalla configurazione.

- `VSHPROPID_CfgPropertyPagesCLSIDList —` elenco delimitato da punti e virgola di CLSID delle pagine delle proprietà dipendenti dalla configurazione.

Poiché il sottotipo di progetto aggrega l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> oggetto, può eseguire l'override della definizione di queste proprietà per controllare le finestre di dialogo delle **pagine delle proprietà** visualizzate. Il sottotipo di progetto può recuperare queste proprietà dal progetto di base interno e quindi aggiungere o rimuovere i CLSID secondo le necessità.

Alle nuove pagine delle proprietà aggiunte da un sottotipo di progetto viene passato un oggetto browse della configurazione del progetto dall'implementazione del progetto di base. Questo oggetto browse della configurazione del progetto supporta Extender di automazione. Per altre informazioni su AutomationExtenders, vedere [implementazione e uso di Extender di automazione](/previous-versions/0y92k2w2(v=vs.140)). Le pagine delle proprietà implementate dalla chiamata del sottotipo <xref:EnvDTE.Project.Extender%2A> di progetto per recuperare il proprio oggetto browse della configurazione del sottotipo di progetto che estende l'oggetto browse della configurazione del progetto di base.

## <a name="see-also"></a>Vedi anche

- <xref:EnvDTE.IFilterProperties>
- [Finestra di dialogo Pagine delle proprietà](/previous-versions/visualstudio/visual-studio-2010/as5chysf(v=vs.100))