---
title: Estensione del modello a oggetti dell'Project | Microsoft Docs
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
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 20f241515e70f161792279a98bac61bb8801377e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122094815"
---
# <a name="extend-the-object-model-of-the-base-project"></a>Estendere il modello a oggetti del progetto di base

Un sottotipo di progetto può estendere il modello a oggetti di automazione del progetto di base nelle posizioni seguenti:

- Project. Extender(" \<ProjectSubtypeName> "): consente a un sottotipo di progetto di offrire un oggetto con metodi personalizzati dall'oggetto. <xref:EnvDTE.Project> Un sottotipo di progetto può usare extender di automazione per esporre `Project` l'oggetto . L'interfaccia implementata nell'aggregatore del sottotipo di progetto principale deve offrire il relativo oggetto per l'oggetto da <xref:EnvDTE80.IInternalExtenderProvider> `VSHPROPID_ExtObjectCATID` <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> (corrispondente a un `itemid` valore di [VSITEMID. RADICE](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) CATID.

- ProjectItem.Extender(" "): consente a un sottotipo di progetto di offrire un oggetto con metodi personalizzati da \<ProjectSubtypeName> un determinato <xref:EnvDTE.ProjectItem> oggetto all'interno del progetto. Un sottotipo di progetto può usare gli extender di automazione per esporre questo oggetto. L'interfaccia implementata nell'aggregatore del sottotipo di progetto principale deve offrire il relativo oggetto per l'elemento <xref:EnvDTE80.IInternalExtenderProvider> `VSHPROPID_ExtObjectCATID` da <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (corrispondente a un <xref:Microsoft.VisualStudio.VSConstants.VSITEMID> CATID desiderato).

- Project. Proprietà: questa raccolta espone le proprietà indipendenti dalla configurazione `Project` dell'oggetto . Per altre informazioni sulle proprietà di `Project`, vedere <xref:EnvDTE.Project.Properties%2A>. Un sottotipo di progetto può usare i controlli Extender di automazione per aggiungerne le proprietà a questa raccolta. L'interfaccia implementata nell'aggregatore del sottotipo di progetto principale deve offrire il relativo oggetto per l'oggetto da <xref:EnvDTE80.IInternalExtenderProvider> `VSHPROPID_BrowseObjectCATID` <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (corrispondente a un `itemid` valore di [VSITEMID. RADICE](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) CATID.

- Configuration.Properties: questa raccolta espone le proprietà dipendenti dalla configurazione del progetto per una particolare configurazione , ad esempio Debug. Per altre informazioni, vedere <xref:EnvDTE.Configuration>. Un sottotipo di progetto può usare i controlli Extender di automazione per aggiungerne le proprietà a questa raccolta. L'interfaccia implementata nell'aggregatore del sottotipo di progetto principale offre il proprio oggetto per <xref:EnvDTE80.IInternalExtenderProvider> il CATID `VSHPROPID_CfgBrowseObjectCATID` (corrispondente a `itemid` un valore [di VSITEMID. Radice](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)). <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>L'interfaccia viene usata per distinguere un oggetto di esplorazione della configurazione da un altro.

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>
