---
title: Interfaccia utente delle proprietà del progetto | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project properties [Visual Studio], user interface
- projects [Visual Studio SDK], properties UI
- project properties UI
ms.assetid: b6aec634-8533-476c-9ebd-36536a2288e2
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e295bff2f8398765f90c3fd537ca4f546208ce4b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51768301"
---
# <a name="project-property-user-interface"></a>Interfaccia utente delle proprietà del progetto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un sottotipo di progetto è possibile usare gli elementi nel progetto **pagine delle proprietà** nella finestra di dialogo come vengono forniti dal progetto di base, nascondere o rendere intere pagine e controlli di sola lettura, come fornito o aggiungere pagine specifici del sottotipo di progetto per il **Pagine delle proprietà** nella finestra di dialogo.  
  
## <a name="extending-the-project-property-dialog-box"></a>Estendere la finestra di dialogo delle proprietà del progetto  
 Un sottotipo di progetto implementa estensioni di automazione e visualizzare oggetti configurazione di progetto. Implementare questi dispositivi Extender di <xref:EnvDTE.IFilterProperties> interfaccia apportare determinate proprietà nascosta o di sola lettura. Il **pagine delle proprietà** finestra di dialogo del progetto di base, implementato dal progetto di base, rispetta il filtro eseguite da dispositivi Extender di automazione.  
  
 Il processo di estensione una **proprietà del progetto** nella finestra di dialogo viene indicata di seguito:  
  
- Il progetto di base recupera le estensioni dal sottotipo del progetto mediante l'implementazione di <xref:EnvDTE80.IInternalExtenderProvider> interfaccia. L'esplorazione, automazione dei progetti e oggetti di esplorazione di configurazione di progetto del progetto di base tutti i implementano questa interfaccia.  
  
- L'implementazione di <xref:EnvDTE80.IInternalExtenderProvider> per l'oggetto di esplorazione di progetto e l'oggetto di automazione progetto delegato per il <xref:EnvDTE80.IInternalExtenderProvider> implementazione di Sil aggregator sottotipo di progetto (, ovvero `QueryInterface` per <xref:EnvDTE80.IInternalExtenderProvider> sul <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> oggetto del progetto).  
  
- Oggetto di visualizzazione configurazione progetto di base implementa anche <xref:EnvDTE80.IInternalExtenderProvider> per collegare direttamente in Extender di automazione dall'oggetto di configurazione sottotipo di progetto. Delega l'implementazione di <xref:EnvDTE80.IInternalExtenderProvider> interfaccia implementata da Sil aggregator sottotipo di progetto.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>, implementata dall'oggetto di visualizzazione configurazione progetto, restituisce il <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> oggetto.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>, anche implementata dall'oggetto di visualizzazione configurazione progetto, restituisce il <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> oggetto.  
  
- Un sottotipo di progetto può determinare il CATID appropriato per gli oggetti estensibili varie del progetto di base in fase di esecuzione tramite il recupero dei seguenti <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> valori:  
  
  -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
  -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
  -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
  Per determinare il CATID per l'ambito del progetto, il sottotipo di progetto recupera proprietà sopra menzionate per <xref:Microsoft.VisualStudio.VSConstants.VSITEMID> dal `VSITEMID``typedef`. Un sottotipo di progetto anche possibile controllare quali **pagine delle proprietà** pagine delle finestre di dialogo vengono visualizzati per il progetto dipendente sia configurazione indipendenti. Alcuni sottotipi di progetto potrebbe essere necessario rimuovere le pagine predefinite e aggiungere pagine specifiche sottotipo di progetto. Per abilitare questa opzione, il progetto client gestito chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> metodo per le proprietà seguenti:  
  
- `VSHPROPID_PropertyPagesCLSIDList` ovvero un elenco delimitato da punto e virgola di CLSID delle pagine delle proprietà indipendenti dalla configurazione.  
  
- `VSHPROPID_CfgPropertyPagesCLSIDList —` elenco delimitato da punto e virgola di CLSID delle pagine delle proprietà dipendenti dalla configurazione.  
  
  Poiché le aggregazioni di sottotipo di progetto di <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> dell'oggetto, è possibile sostituire la definizione di queste proprietà per controllare quali **pagine delle proprietà** vengono visualizzate le finestre di dialogo. Il sottotipo di progetto possa recuperare queste proprietà dal progetto di base interno e quindi aggiungere o rimuovere i CLSID in base alle esigenze.  
  
  Pagine delle proprietà aggiunte da un sottotipo di progetto usati presentano un oggetto di esplorazione di configurazione progetto rispetto all'implementazione di progetto di base. Questo oggetto di visualizzazione configurazione progetto supporta estensioni di automazione. Per altre informazioni su AutomationExtenders, vedere [implementazione ed estensioni di automazione usando](http://msdn.microsoft.com/library/0d5c218c-f412-4b28-ab0c-33a611f62356). Le pagine delle proprietà implementati dalla chiamata al sottotipo di progetto <xref:EnvDTE.Project.Extender%2A> per recuperare le proprie oggetto Sfoglia sottotipo configurazione del progetto che estende l'oggetto di esplorazione di configurazione del progetto di base.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:EnvDTE.IFilterProperties>   
 [Finestra di dialogo Pagine delle proprietà](http://msdn.microsoft.com/en-us/4a3d34ac-ed03-45e8-ae60-a0e1aad300e4)

