---
title: Estendere il modello a oggetti del progetto di Base | Microsoft Docs
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- automation object model, extending
- project subtypes, extending automation object model
- automation object model
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 607a63dc84db2811a4a2d158be07f158b849e1ad
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66329037"
---
# <a name="extend-the-object-model-of-the-base-project"></a>Estendere il modello a oggetti del progetto di base

Un sottotipo di progetto possa estendere il modello oggetto di automazione del progetto di base nelle posizioni seguenti:

- Project.Extender("\<ProjectSubtypeName>"): In questo modo un sottotipo di progetto offrire un oggetto con metodi personalizzati dal <xref:EnvDTE.Project> oggetto. Un sottotipo di progetto è possibile usare estensioni di automazione per esporre il `Project` oggetto. Il <xref:EnvDTE80.IInternalExtenderProvider> interfaccia implementata di Sil Aggregator sottotipo di progetto principale deve offrire il proprio oggetto per il `VSHPROPID_ExtObjectCATID` dalla <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> (corrispondente a un `itemid` valore [VSITEMID. Radice](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) CATID.

- ProjectItem.Extender("\<ProjectSubtypeName>"): In questo modo un sottotipo di progetto offrire un oggetto con metodi personalizzati da un particolare <xref:EnvDTE.ProjectItem> oggetto all'interno del progetto. Un sottotipo di progetto è possibile usare estensioni di automazione per esporre questo oggetto. Il <xref:EnvDTE80.IInternalExtenderProvider> interfaccia implementata di Sil Aggregator sottotipo di progetto principale deve offrire il proprio oggetto per il `VSHPROPID_ExtObjectCATID` dalla <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (corrispondente a un desiderato <xref:Microsoft.VisualStudio.VSConstants.VSITEMID>) CATID.

- Project. Properties: Questa raccolta espone le proprietà indipendenti dalla configurazione della `Project` oggetto. Per altre informazioni sulle proprietà di `Project`, vedere <xref:EnvDTE.Project.Properties%2A>. Un sottotipo di progetto è possibile usare estensioni di automazione per aggiungere le relative proprietà a questa raccolta. Il <xref:EnvDTE80.IInternalExtenderProvider> interfaccia implementata di Sil Aggregator sottotipo di progetto principale deve offrire il proprio oggetto per il `VSHPROPID_BrowseObjectCATID` dal <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (corrispondente a un `itemid` valore [VSITEMID. Radice](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) CATID.

- Configuration.Properties: Questa raccolta espone le proprietà dipendenti dalla configurazione del progetto per una particolare configurazione (ad esempio, di Debug). Per altre informazioni, vedere <xref:EnvDTE.Configuration>. Un sottotipo di progetto è possibile usare estensioni di automazione per aggiungere le relative proprietà a questa raccolta. Il <xref:EnvDTE80.IInternalExtenderProvider> interfaccia implementata di Sil Aggregator sottotipo di progetto principale offre il proprio oggetto per il CATID `VSHPROPID_CfgBrowseObjectCATID` (corrispondente a un `itemid` valore [VSITEMID. Radice](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)). Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject> interfaccia viene utilizzata per distinguere un oggetto di esplorazione di configurazione da un altro.

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>