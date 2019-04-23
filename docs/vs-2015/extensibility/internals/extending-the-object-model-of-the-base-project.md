---
title: Estendere il modello a oggetti del progetto di Base | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation object model, extending
- project subtypes, extending automation object model
- automation object model
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7723881bce81824b66a936793175077a0ec67666
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60106072"
---
# <a name="extending-the-object-model-of-the-base-project"></a>Estensione del modello a oggetti del progetto di base
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un sottotipo di progetto possa estendere il modello oggetto di automazione del progetto di base nelle posizioni seguenti:  
  
- Project.Extender ("\<ProjectSubtypeName >"): in questo modo un sottotipo di progetto offrire un oggetto con metodi personalizzati dal <xref:EnvDTE.Project>. Un sottotipo di progetto è possibile usare estensioni di automazione per esporre il `Project` oggetto. Il <xref:EnvDTE80.IInternalExtenderProvider>interfaccia implementata di Sil Aggregator sottotipo di progetto principale deve offrire il proprio oggetto per il `VSHPROPID_ExtObjectCATID` dalla <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> (corrispondente a un `itemid` valore VSITEMID_ROOT, da `VSITEMID`) CATID.  
  
- ProjectItem.Extender ("\<ProjectSubtypeName >"): in questo modo un sottotipo di progetto offrire un oggetto con metodi personalizzati da un particolare <xref:EnvDTE.ProjectItem> oggetto all'interno del progetto. Un sottotipo di progetto è possibile usare estensioni di automazione per esporre questo oggetto. Il <xref:EnvDTE80.IInternalExtenderProvider> interfaccia implementata di Sil Aggregator sottotipo di progetto principale deve offrire il proprio oggetto per il `VSHPROPID_ExtObjectCATID` dalla <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (corrispondente a un desiderato `VSITEMID`) CATID.  
  
- Project: questa raccolta espone le proprietà di configurazione indipendente del `Project` oggetto. Per altre informazioni sulle proprietà di progetto, vedere <xref:EnvDTE.Project.Properties%2A>. Un sottotipo di progetto è possibile usare estensioni di automazione per aggiungere le relative proprietà a questa raccolta. Il <xref:EnvDTE80.IInternalExtenderProvider> interfaccia implementata di Sil Aggregator sottotipo di progetto principale deve offrire il proprio oggetto per il `VSHPROPID_BrowseObjectCATID` da VSHPROPID2 (corrispondente a un `itemid` valore VSITEMID_ROOT, da <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>) CATID.  
  
- Configuration.Properties – questa raccolta espone le proprietà dipendenti di configurazione del progetto per una particolare configurazione (ad esempio, di Debug). Per altre informazioni, vedere <xref:EnvDTE.Configuration>. Un sottotipo di progetto è possibile usare estensioni di automazione per aggiungere le relative proprietà a questa raccolta. Il <xref:EnvDTE80.IInternalExtenderProvider> interfaccia implementata di Sil Aggregator sottotipo di progetto principale offre il proprio oggetto per il CATID `VSHPROPID_CfgBrowseObjectCATID` (corrispondente a un `itemid` valore <xref:Microsoft.VisualStudio.VSConstants.VSITEMID>). Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>interfaccia viene utilizzata per distinguere un oggetto di esplorazione di configurazione da un altro.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>
