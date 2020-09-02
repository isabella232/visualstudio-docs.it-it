---
title: Fornire il supporto per l'annullamento alle finestre di progettazione | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6136caaec0cb8f0d79e3fb7b96245fc3fd070710
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675346"
---
# <a name="supplying-undo-support-to-designers"></a>Aggiunta del supporto dell'annullamento alle finestre di progettazione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le finestre di progettazione, come gli editor, in genere devono supportare le operazioni di annullamento in modo che gli utenti possano invertire le modifiche recenti durante la modifica di un elemento di codice.  
  
 La maggior parte delle finestre di progettazione implementate in Visual Studio dispone del supporto di annullamento automaticamente fornito dall'ambiente.  
  
 Implementazioni della finestra di progettazione che devono fornire supporto per la funzionalità di annullamento:  
  
- Fornire la gestione dell'annullamento implementando la classe di base astratta <xref:System.ComponentModel.Design.UndoEngine>  
  
- Fornire la persistenza e il supporto CodeDOM implementando le <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> <xref:System.ComponentModel.Design.IComponentChangeService> classi e.  
  
  Per ulteriori informazioni sulla scrittura di finestre di progettazione utilizzando [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , vedere [estensione del supporto in fase di progettazione](https://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2).  
  
  [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]Fornisce un'infrastruttura di annullamento predefinita per:  
  
- Fornire implementazioni di gestione di annullamento tramite le <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> classi e.  
  
- Fornire supporto per la persistenza e CodeDOM tramite <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> le <xref:System.ComponentModel.Design.IComponentChangeService> implementazioni e predefinite.  
  
## <a name="obtaining-undo-support-automatically"></a>Recupero automatico del supporto di annullamento  
 Qualsiasi finestra di progettazione creata in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dispone del supporto di annullamento automatico e completo se, la finestra di progettazione:  
  
- Usa una <xref:System.Windows.Forms.Control> classe basata per la relativa interfaccia utente.  
  
- Usa il sistema di analisi e generazione del codice basato su CodeDOM standard per la generazione e la persistenza del codice.  
  
     Per ulteriori informazioni sull'utilizzo del supporto di Visual Studio CodeDOM, vedere [generazione e compilazione di codice sorgente dinamico](https://msdn.microsoft.com/library/d077a3e8-bd81-4bdf-b6a3-323857ea30fb) .  
  
## <a name="when-to-use-explicit-designer-undo-support"></a>Quando usare il supporto di annullamento esplicito della finestra di progettazione  
 I progettisti devono fornire la propria gestione degli annullamenti se utilizzano un'interfaccia utente grafica, definita scheda di visualizzazione, diversa da quella fornita da <xref:System.Windows.Forms.Control> .  
  
 Un esempio potrebbe essere la creazione di un prodotto con un'interfaccia di progettazione grafica basata sul Web anziché un' [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] interfaccia grafica basata sul Web.  
  
 In questi casi, è necessario registrare questa scheda di visualizzazione con [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] utilizzando <xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute> e fornire una gestione esplicita di annullamento.  
  
 Se non utilizzano il [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] modello di generazione del codice fornito nello spazio dei nomi, le finestre di progettazione devono fornire il supporto CodeDom e di persistenza <xref:System.CodeDom> .  
  
## <a name="undo-support-features-of-the-designer"></a>Annullare le funzionalità di supporto della finestra di progettazione  
 L'SDK dell'ambiente fornisce le implementazioni predefinite delle interfacce necessarie per fornire il supporto di annullamento che può essere utilizzato da progettisti che non utilizzano <xref:System.Windows.Forms.Control> classi basate per le interfacce utente o il modello CodeDOM e di persistenza standard.  
  
 La <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> classe deriva dalla [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] <xref:System.ComponentModel.Design.UndoEngine> classe usando un'implementazione della <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> classe per gestire le operazioni di annullamento.  
  
 Visual Studio fornisce la funzionalità seguente per la finestra di progettazione Annulla:  
  
- Funzionalità di annullamento collegate tra più finestre di progettazione.  
  
- Le unità figlio all'interno di una finestra di progettazione possono interagire con i relativi elementi padre implementando <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> e <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> su <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> .  
  
  L'SDK dell'ambiente fornisce il supporto per CodeDOM e persistenza fornendo:  
  
- <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> come implementazioni di <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
  Oggetto <xref:System.ComponentModel.Design.IComponentChangeService> fornito dall' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] host di progettazione ''.  
  
## <a name="using-the-environment-sdk-features-to-supply-undo-support"></a>Uso delle funzionalità dell'SDK per l'ambiente per fornire supporto per l'annullamento  
 Per ottenere il supporto di annullamento, un oggetto che implementa una finestra di progettazione deve:  
  
- Creare un'istanza della classe e inizializzarla <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> con un'implementazione valida <xref:System.IServiceProvider> .  
  
- Questa <xref:System.IServiceProvider> classe deve fornire i servizi seguenti:  
  
  - <xref:System.ComponentModel.Design.IDesignerHost>.  
  
  - <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
       Le finestre di progettazione [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] che usano la serializzazione CodeDom possono scegliere di usare <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> fornito con [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] come implementazione di <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> .  
  
       In questo caso, la <xref:System.IServiceProvider> classe fornita al <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> costruttore deve restituire questo oggetto come implementazione della <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> classe.  
  
  - <xref:System.ComponentModel.Design.IComponentChangeService>  
  
       Per le finestre di progettazione che usano l'impostazione predefinita <xref:System.ComponentModel.Design.DesignSurface> fornita dall' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] host di progettazione è garantita un'implementazione predefinita della <xref:System.ComponentModel.Design.IComponentChangeService> classe.  
  
  Le finestre di progettazione che implementano un <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> meccanismo di annullamento basato su rileva automaticamente le modifiche se  
  
- Le modifiche alle proprietà vengono apportate tramite l' <xref:System.ComponentModel.TypeDescriptor> oggetto.  
  
- <xref:System.ComponentModel.Design.IComponentChangeService> gli eventi vengono generati manualmente quando viene eseguito il commit di una modifica annullabile.  
  
- La modifica nella finestra di progettazione è stata creata nel contesto di un oggetto <xref:System.ComponentModel.Design.DesignerTransaction> .  
  
- La finestra di progettazione sceglie di creare in modo esplicito le unità di annullamento usando l'unità di annullamento standard fornita da un'implementazione di <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> o l'implementazione specifica di Visual Studio <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> , che deriva da <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> e fornisce anche un'implementazione di <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> e <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> .  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.ComponentModel.Design.UndoEngine>   
 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>   
 [Estensione del supporto in fase di progettazione](https://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)
