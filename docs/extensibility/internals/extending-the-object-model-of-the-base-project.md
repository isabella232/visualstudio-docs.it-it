---
title: Estensione del modello a oggetti del progetto di base Documenti Microsoft
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- automation object model, extending
- project subtypes, extending automation object model
- automation object model
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 33186cd477ade7f562f6191393dabe8e94f4f194
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708392"
---
# <a name="extend-the-object-model-of-the-base-project"></a>Estendere il modello a oggetti del progetto di base

Un sottotipo di progetto può estendere il modello a oggetti di automazione del progetto di base nelle posizioni seguenti:

- Project.Extender("\<ProjectSubtypeName>"): consente a un sottotipo di progetto <xref:EnvDTE.Project> di offrire un oggetto con metodi personalizzati dall'oggetto. Un sottotipo di progetto può usare `Project` le estensioni di automazione per esporre l'oggetto. <xref:EnvDTE80.IInternalExtenderProvider> L'interfaccia implementata nell'aggregatore di sottotipi `VSHPROPID_ExtObjectCATID` <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> di progetto `itemid` principale deve offrire il relativo oggetto per il da (corrispondente a un valore di [VSITEMID. Radice](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) CATID.

- ProjectItem.Extender("\<ProjectSubtypeName>"): consente a un sottotipo di progetto <xref:EnvDTE.ProjectItem> di offrire un oggetto con metodi personalizzati da un particolare oggetto all'interno del progetto. Un sottotipo di progetto può utilizzare estensioni di automazione per esporre questo oggetto. <xref:EnvDTE80.IInternalExtenderProvider> L'interfaccia implementata nell'aggregatore di sottotipi `VSHPROPID_ExtObjectCATID` di <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> progetto principale <xref:Microsoft.VisualStudio.VSConstants.VSITEMID>deve offrire il proprio oggetto per il CATID from (corrispondente a un desiderato).

- Project.Properties: questo insieme espone le proprietà `Project` indipendenti dalla configurazione dell'oggetto. Per altre informazioni sulle proprietà di `Project`, vedere <xref:EnvDTE.Project.Properties%2A>. Un sottotipo di progetto può usare le estensioni di automazione per aggiungere le relative proprietà a questa raccolta. <xref:EnvDTE80.IInternalExtenderProvider> L'interfaccia implementata nell'aggregatore di sottotipi `VSHPROPID_BrowseObjectCATID` di <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> progetto principale `itemid` deve offrire il proprio oggetto per il da (corrispondente a un valore di [VSITEMID. Radice](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) CATID.

- Configuration.Properties: questa raccolta espone le proprietà dipendenti dalla configurazione del progetto per una particolare configurazione ( ad esempio, Debug). Per altre informazioni, vedere <xref:EnvDTE.Configuration>. Un sottotipo di progetto può usare le estensioni di automazione per aggiungere le relative proprietà a questa raccolta. L'interfaccia <xref:EnvDTE80.IInternalExtenderProvider> implementata nell'aggregatore di sottotipi `VSHPROPID_CfgBrowseObjectCATID` di progetto `itemid` principale offre il proprio oggetto per il CATID (corrispondente a un valore di [VSITEMID. Radice](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)). L'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject> viene utilizzata per distinguere un oggetto di ricerca di configurazione da un altro.

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>
