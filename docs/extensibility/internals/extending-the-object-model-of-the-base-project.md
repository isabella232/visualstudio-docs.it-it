---
title: Estensione del modello a oggetti del progetto di base | Microsoft Docs
description: Informazioni su come estendere il modello a oggetti di automazione del progetto di base in Visual Studio usando un sottotipo di progetto.
ms.custom: SEO-VS-2020
ms.date: 03/22/2018
ms.topic: reference
helpviewer_keywords:
- automation object model, extending
- project subtypes, extending automation object model
- automation object model
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 175571b374c6a54999b212b316301f3f775891ff
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899342"
---
# <a name="extend-the-object-model-of-the-base-project"></a>Estendere il modello a oggetti del progetto di base

Un sottotipo di progetto può estendere il modello a oggetti di automazione del progetto di base nelle posizioni seguenti:

- Project.Extender(" "): consente a un sottotipo di progetto di offrire \<ProjectSubtypeName> un oggetto con metodi personalizzati dall'oggetto. <xref:EnvDTE.Project> Un sottotipo di progetto può usare Extender di automazione per esporre `Project` l'oggetto. L'interfaccia implementata nell'aggregatore del sottotipo di progetto principale deve offrire il relativo oggetto per da <xref:EnvDTE80.IInternalExtenderProvider> `VSHPROPID_ExtObjectCATID` <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> (corrispondente a un `itemid` valore di [VSITEMID. CATID](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)radice.

- ProjectItem.Extender(" "): consente a un sottotipo di progetto di offrire un oggetto con metodi personalizzati da \<ProjectSubtypeName> un determinato <xref:EnvDTE.ProjectItem> oggetto all'interno del progetto. Un sottotipo di progetto può usare extender di automazione per esporre questo oggetto. L'interfaccia implementata nell'aggregatore del sottotipo di progetto principale deve offrire il relativo oggetto per l'oggetto <xref:EnvDTE80.IInternalExtenderProvider> `VSHPROPID_ExtObjectCATID` da <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (corrispondente a un <xref:Microsoft.VisualStudio.VSConstants.VSITEMID> CATID ) desiderato.

- Project.Properties: questa raccolta espone le proprietà indipendenti dalla configurazione `Project` dell'oggetto . Per altre informazioni sulle proprietà di `Project`, vedere <xref:EnvDTE.Project.Properties%2A>. Un sottotipo di progetto può usare Gli extender di automazione per aggiungere le relative proprietà a questa raccolta. L'interfaccia implementata nell'aggregatore del sottotipo di progetto principale deve offrire il relativo oggetto per da <xref:EnvDTE80.IInternalExtenderProvider> `VSHPROPID_BrowseObjectCATID` <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (corrispondente a un `itemid` valore di [VSITEMID. CATID](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)radice.

- Configuration.Properties: questa raccolta espone le proprietà dipendenti dalla configurazione del progetto per una configurazione specifica, ad esempio Debug. Per altre informazioni, vedere <xref:EnvDTE.Configuration>. Un sottotipo di progetto può usare Gli extender di automazione per aggiungere le relative proprietà a questa raccolta. L'interfaccia implementata nell'aggregatore del sottotipo di progetto principale offre il relativo oggetto per <xref:EnvDTE80.IInternalExtenderProvider> il CATID `VSHPROPID_CfgBrowseObjectCATID` (corrispondente a un `itemid` valore [di VSITEMID. Radice](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>). <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>L'interfaccia viene usata per distinguere un oggetto di esplorazione della configurazione da un altro.

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>
