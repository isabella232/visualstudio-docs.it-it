---
title: Fornisce supporto per le finestre di progettazione per l'annullamento | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 62cbce66521ecdadca948f6fbb20fc20e60714c2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54947660"
---
# <a name="supplying-undo-support-to-designers"></a>Aggiunta del supporto dell'annullamento alle finestre di progettazione
Finestre di progettazione, come editor, in genere necessario supportare le operazioni di annullamento in modo che gli utenti possono invertire le modifiche recenti quando si modifica un elemento di codice.  
  
 La maggior parte delle finestre di progettazione implementate in Visual Studio include il supporto di annullamento automaticamente fornito dall'ambiente.  
  
 Implementazioni della finestra di progettazione che è necessario fornire supporto per la funzionalità di annullamento:  
  
- Fornisce la gestione dell'annullamento implementando la classe base astratta <xref:System.ComponentModel.Design.UndoEngine>  
  
- Persistenza forniture e CodeDOM supportano implementando il <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> e il <xref:System.ComponentModel.Design.IComponentChangeService> classi.  
  
  Per altre informazioni su come scrivere le finestre di progettazione utilizzando [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], vedere [Extending Design-Time Support](https://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2).  
  
  Il [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] fornisce un'infrastruttura di annullamento predefinito per:  
  
- Fornendo annullare le implementazioni di gestione tramite il <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> e <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> classi.  
  
- Fornisce la persistenza e il supporto CodeDOM tramite l'impostazione predefinita <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> e <xref:System.ComponentModel.Design.IComponentChangeService> implementazioni.  
  
## <a name="obtaining-undo-support-automatically"></a>Come ottenere supporto per l'annullamento automaticamente  
 Qualsiasi finestra di progettazione creata in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] supporta in modo automatico e l'intera operazione di annullamento if, la finestra di progettazione:  
  
-   Usa un <xref:System.Windows.Forms.Control> basati su classi per la propria interfaccia utente.  
  
-   Usa la generazione di codice standard basato su CodeDOM e sistema di analisi per la persistenza e la generazione di codice.  
  
     Per altre informazioni sull'uso di supporto di Visual Studio CodeDOM, vedere [Dynamic Source Code Generation and Compilation](/dotnet/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation)  
  
## <a name="when-to-use-explicit-designer-undo-support"></a>Quando usare il supporto di annullamento della finestra di progettazione esplicita  
 Finestre di progettazione è necessario fornire le proprie gestione dell'annullamento se usano un'interfaccia utente grafica, definita come un adattatore della visualizzazione, diverso da quello fornito da <xref:System.Windows.Forms.Control>.  
  
 Un esempio di questo oggetto può consistere nella creazione un prodotto con un'interfaccia di progettazione con interfaccia grafica basata su web anziché un [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] basato su interfaccia grafica.  
  
 In questi casi, uno sarebbe necessario registrare questo adattatore della visualizzazione con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] usando <xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute>e fornire la gestione esplicita di annullamento.  
  
 Finestre di progettazione necessari fornire supporto CodeDOM e persistenza se non usano il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] modello di generazione di codice fornito nel <xref:System.CodeDom> lo spazio dei nomi.  
  
## <a name="undo-support-features-of-the-designer"></a>Annullare le funzionalità di supporto della finestra di progettazione  
 il SDK di ambiente fornisce le implementazioni predefinite delle interfacce necessarie per fornire supporto che può essere utilizzato dalle finestre di progettazione non usa per l'annullamento <xref:System.Windows.Forms.Control> basati su classi per le proprie interfacce utente o il modello standard di persistenza e CodeDOM.  
  
 Il <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> deriva dalla classe la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] <xref:System.ComponentModel.Design.UndoEngine> classe utilizzando un'implementazione del <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> classe per la gestione delle operazioni di annullamento.  
  
 Visual Studio offre la funzionalità di annullamento della finestra di progettazione seguente:  
  
- Funzionalità di annullamento collegata tra più finestre di progettazione.  
  
- Unità figlio all'interno di una finestra di progettazione può interagire con i genitori implementando <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> e <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> sul <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>.  
  
  il SDK di ambiente fornisce il supporto CodeDOM e persistenza fornendo:  
  
- <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> come un implementazioni del <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
  Oggetto <xref:System.ComponentModel.Design.IComponentChangeService> fornite dal [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]' host di progettazione.  
  
## <a name="using-the-environment-sdk-features-to-supply-undo-support"></a>Tramite la funzionalità SDK dell'ambiente per fornire supporto dell'annullamento  
 Per ottenere supporto per l'annullamento, è necessario un oggetto che implementa una finestra di progettazione:  
  
- Creare un'istanza e inizializzare un'istanza di <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> classe con un valore valido <xref:System.IServiceProvider> implementazione.  
  
- Ciò <xref:System.IServiceProvider> classe deve fornire i servizi seguenti:  
  
  - <xref:System.ComponentModel.Design.IDesignerHost>.  
  
  - <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
     Le finestre di progettazione utilizzando [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] serializzazione CodeDOM può scegliere di usare <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> fornito con il [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] come relativa implementazione del <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>.  
  
     In questo caso, il <xref:System.IServiceProvider> classe fornita per il <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> costruttore deve restituire tale oggetto come un'implementazione del <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> classe.  
  
  - <xref:System.ComponentModel.Design.IComponentChangeService>  
  
     Le finestre di progettazione utilizzando il valore predefinito <xref:System.ComponentModel.Design.DesignSurface> fornite dal [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] viene garantito che un'implementazione predefinita dell'host di progettazione di <xref:System.ComponentModel.Design.IComponentChangeService> classe.  
  
  Le finestre di progettazione che implementa un <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> meccanismo di annullamento basato su tiene automaticamente traccia delle modifiche se:  
  
- Le modifiche alle proprietà vengono effettuate tramite il <xref:System.ComponentModel.TypeDescriptor> oggetto.  
  
- <xref:System.ComponentModel.Design.IComponentChangeService> gli eventi vengono generati manualmente quando è eseguito il commit di una modifica di annullabile.  
  
- Modifica della finestra di progettazione è stata creata nel contesto di un <xref:System.ComponentModel.Design.DesignerTransaction>.  
  
- La finestra di progettazione sceglie di creare in modo esplicito le unità di annullamento tramite l'unità di annullamento standard fornito da un'implementazione di <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> o l'implementazione specifica di Visual Studio <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>, che deriva da <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> e fornisce inoltre un implementazione di entrambi <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> e <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit>.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.ComponentModel.Design.UndoEngine>   
 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>   
 [Estensione del supporto in fase di progettazione](https://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)