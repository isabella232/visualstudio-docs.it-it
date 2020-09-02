---
title: Interfaccia utente della proprietà del progetto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project properties [Visual Studio], user interface
- projects [Visual Studio SDK], properties UI
- project properties UI
ms.assetid: b6aec634-8533-476c-9ebd-36536a2288e2
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 31840c40f2a494ffd32f5241e2770938138877e9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704092"
---
# <a name="project-property-user-interface"></a>Interfaccia utente delle proprietà del progetto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
  Per determinare il CATID per l'ambito del progetto, il sottotipo di progetto recupera le proprietà precedenti per <xref:Microsoft.VisualStudio.VSConstants.VSITEMID>  da `VSITEMID``typedef` . Un sottotipo di progetto può anche voler controllare le pagine delle finestre di dialogo delle **pagine delle proprietà** visualizzate per il progetto, sia dipendenti dalla configurazione che indipendenti dalla configurazione. Alcuni sottotipi di progetto possono dover rimuovere pagine predefinite e aggiungere pagine specifiche del sottotipo di progetto. Per abilitare questa operazione, il progetto client gestito chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> metodo per le proprietà seguenti:  
  
- `VSHPROPID_PropertyPagesCLSIDList` : elenco delimitato da punti e virgola di CLSID delle pagine delle proprietà indipendenti dalla configurazione.  
  
- `VSHPROPID_CfgPropertyPagesCLSIDList —` elenco delimitato da punti e virgola di CLSID delle pagine delle proprietà dipendenti dalla configurazione.  
  
  Poiché il sottotipo di progetto aggrega l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> oggetto, può eseguire l'override della definizione di queste proprietà per controllare le finestre di dialogo delle **pagine delle proprietà** visualizzate. Il sottotipo di progetto può recuperare queste proprietà dal progetto di base interno e quindi aggiungere o rimuovere i CLSID secondo le necessità.  
  
  Alle nuove pagine delle proprietà aggiunte da un sottotipo di progetto viene passato un oggetto browse della configurazione del progetto dall'implementazione del progetto di base. Questo oggetto browse della configurazione del progetto supporta Extender di automazione. Per altre informazioni su AutomationExtenders, vedere [implementazione e uso di Extender di automazione](https://msdn.microsoft.com/library/0d5c218c-f412-4b28-ab0c-33a611f62356). Le pagine delle proprietà implementate dalla chiamata del sottotipo <xref:EnvDTE.Project.Extender%2A> di progetto per recuperare il proprio oggetto browse della configurazione del sottotipo di progetto che estende l'oggetto browse della configurazione del progetto di base.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:EnvDTE.IFilterProperties>   
 [Finestra di dialogo Pagine delle proprietà](https://msdn.microsoft.com/4a3d34ac-ed03-45e8-ae60-a0e1aad300e4)
