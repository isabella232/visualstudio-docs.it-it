---
title: Estensione del modello a oggetti del progetto di base | Microsoft Docs
description: Informazioni su come estendere il modello a oggetti di automazione del progetto di base in Visual Studio usando un sottotipo di progetto.
ms.custom: SEO-VS-2020
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- automation object model, extending
- project subtypes, extending automation object model
- automation object model
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 23541124e48df0c3760d38ff8205f086281034fe
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887042"
---
# <a name="extend-the-object-model-of-the-base-project"></a>Estendere il modello a oggetti del progetto di base

Un sottotipo di progetto può estendere il modello a oggetti di automazione del progetto di base nelle posizioni seguenti:

- Project. Extender (" \<ProjectSubtypeName> "): consente a un sottotipo di progetto di offrire un oggetto con metodi personalizzati dall' <xref:EnvDTE.Project> oggetto. Un sottotipo di progetto può utilizzare le estensioni di automazione per esporre l' `Project` oggetto. L' <xref:EnvDTE80.IInternalExtenderProvider> interfaccia implementata nell'aggregatore del sottotipo di progetto principale deve offrire il proprio oggetto per `VSHPROPID_ExtObjectCATID` da <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> (corrispondente a un `itemid` valore di [VSITEMID. Radice](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) CATID.

- ProjectItem. Extender (" \<ProjectSubtypeName> "): consente a un sottotipo di progetto di offrire un oggetto con metodi personalizzati da un <xref:EnvDTE.ProjectItem> oggetto specifico all'interno del progetto. Un sottotipo di progetto può usare gli Extender di automazione per esporre questo oggetto. L' <xref:EnvDTE80.IInternalExtenderProvider> interfaccia implementata nell'aggregatore del sottotipo di progetto principale deve offrire il proprio oggetto per il `VSHPROPID_ExtObjectCATID` <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> CATID di (corrispondente a un valore desiderato <xref:Microsoft.VisualStudio.VSConstants.VSITEMID> ).

- Project. Properties: questa raccolta espone le proprietà indipendenti dalla configurazione dell' `Project` oggetto. Per altre informazioni sulle proprietà di `Project`, vedere <xref:EnvDTE.Project.Properties%2A>. Un sottotipo di progetto può usare gli Extender di automazione per aggiungere le proprietà a questa raccolta. L' <xref:EnvDTE80.IInternalExtenderProvider> interfaccia implementata nell'aggregatore del sottotipo di progetto principale deve offrire il proprio oggetto per `VSHPROPID_BrowseObjectCATID` da <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (corrispondente a un `itemid` valore di [VSITEMID. Radice](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) CATID.

- Configuration. Properties: questa raccolta espone le proprietà dipendenti dalla configurazione del progetto per una particolare configurazione (ad esempio, debug). Per altre informazioni, vedere <xref:EnvDTE.Configuration>. Un sottotipo di progetto può usare gli Extender di automazione per aggiungere le proprietà a questa raccolta. L' <xref:EnvDTE80.IInternalExtenderProvider> interfaccia implementata nel sottotipo di progetto principale aggregator offre il relativo oggetto per il CATID `VSHPROPID_CfgBrowseObjectCATID` (corrispondente a un `itemid` valore di [VSITEMID. Radice](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)). L' <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject> interfaccia viene utilizzata per distinguere un oggetto di esplorazione della configurazione da un altro.

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>
