---
title: Fornisce supporto per le finestre di progettazione per l'annullamento | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e243ccfc92c5e17dd25e6d77dede439daac08761
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/06/2019
ms.locfileid: "66747725"
---
# <a name="supply-undo-support-to-designers"></a>Alimentatore supporto dell'annullamento alle finestre di progettazione

Finestre di progettazione, come editor, in genere necessario supportare le operazioni di annullamento in modo che gli utenti possono invertire le modifiche recenti quando si modifica un elemento di codice.

La maggior parte delle finestre di progettazione implementate in Visual Studio hanno "Annulla" supporto viene fornito automaticamente dall'ambiente.

Implementazioni della finestra di progettazione che è necessario fornire supporto per la funzionalità di annullamento:

- Fornisce la gestione dell'annullamento implementando la classe base astratta <xref:System.ComponentModel.Design.UndoEngine>

- Persistenza forniture e CodeDOM supportano implementando il <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> e <xref:System.ComponentModel.Design.IComponentChangeService> classi.

Per altre informazioni su come scrivere le finestre di progettazione utilizzando .NET Framework, vedere [estendere Design-Time Support](/previous-versions/37899azc(v=vs.140)).

Il [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] fornisce un'infrastruttura di annullamento predefinito per:

- Fornendo annullare le implementazioni di gestione tramite il <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> e <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> classi.

- Fornisce la persistenza e il supporto CodeDOM tramite l'impostazione predefinita <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> e <xref:System.ComponentModel.Design.IComponentChangeService> implementazioni.

## <a name="obtain-undo-support-automatically"></a>Ottieni supporto per l'annullamento automaticamente

Qualsiasi finestra di progettazione creata in Visual Studio offre supporto automatico e l'intera operazione di annullamento if, la finestra di progettazione:

- Usa un <xref:System.Windows.Forms.Control> basati su classi per la propria interfaccia utente.

- Usa la generazione di codice standard basato su CodeDOM e sistema di analisi per la persistenza e la generazione di codice.

   Per altre informazioni sull'utilizzo di supporto di Visual Studio CodeDOM, vedere [Dynamic Source Code Generation and Compilation](/dotnet/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation).

## <a name="when-to-use-explicit-designer-undo-support"></a>Quando usare il supporto di annullamento della finestra di progettazione esplicita
 Finestre di progettazione è necessario fornire le proprie gestione dell'annullamento se usano un'interfaccia utente grafica, definita come un adattatore della visualizzazione, diverso da quello fornito da <xref:System.Windows.Forms.Control>.

 Un esempio potrebbe essere creazione di un prodotto con un'interfaccia basata sul web di progettazione grafica anziché un'interfaccia grafica basata su .NET Framework.

 In questi casi, uno dovrà registrare questo adattatore della visualizzazione con Visual Studio usando <xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute>e fornire la gestione esplicita di annullamento.

 Finestre di progettazione necessari fornire supporto CodeDOM e persistenza se non utilizzano il modello di generazione di codice di Visual Studio disponibili nel <xref:System.CodeDom> lo spazio dei nomi.

## <a name="undo-support-features-of-the-designer"></a>Annullare le funzionalità di supporto della finestra di progettazione
 il SDK di ambiente fornisce le implementazioni predefinite delle interfacce necessarie per fornire supporto che può essere utilizzato dalle finestre di progettazione non usa per l'annullamento <xref:System.Windows.Forms.Control> basati su classi per le proprie interfacce utente o il modello standard di persistenza e CodeDOM.

 Il <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> classe deriva da .NET Framework <xref:System.ComponentModel.Design.UndoEngine> classe utilizzando un'implementazione del <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> classe per la gestione delle operazioni di annullamento.

 Visual Studio offre la funzionalità di annullamento della finestra di progettazione seguente:

- Funzionalità di annullamento collegata tra più finestre di progettazione.

- Unità figlio all'interno di una finestra di progettazione può interagire con i genitori implementando <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> e <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> sul <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>.

il SDK di ambiente fornisce il supporto CodeDOM e persistenza fornendo:

- <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> come un'implementazione del <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>

- Oggetto <xref:System.ComponentModel.Design.IComponentChangeService> fornito dall'host di progettazione di Visual Studio.

## <a name="use-the-environment-sdk-features-to-supply-undo-support"></a>Utilizzare la funzionalità SDK dell'ambiente per fornire supporto dell'annullamento

Per ottenere supporto per l'annullamento, è necessario creare un'istanza e inizializzare un'istanza di un oggetto che implementa una finestra di progettazione di <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> classe con un valore valido <xref:System.IServiceProvider> implementazione. Ciò <xref:System.IServiceProvider> classe deve fornire i servizi seguenti:

- <xref:System.ComponentModel.Design.IDesignerHost>.

- <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>

   Le finestre di progettazione utilizzando la serializzazione CodeDOM di Visual Studio è possibile scegliere di usare <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> forniti con il [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] come relativa implementazione del <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>.

   In questo caso, il <xref:System.IServiceProvider> classe fornita per il <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> costruttore deve restituire tale oggetto come un'implementazione del <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> classe.

- <xref:System.ComponentModel.Design.IComponentChangeService>

   Le finestre di progettazione utilizzando il valore predefinito <xref:System.ComponentModel.Design.DesignSurface> fornito per la progettazione di Visual Studio viene garantito che un'implementazione predefinita dell'host di <xref:System.ComponentModel.Design.IComponentChangeService> classe.

Le finestre di progettazione che implementa un <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> meccanismo di annullamento basato su tiene automaticamente traccia delle modifiche se:

- Le modifiche alle proprietà vengono effettuate tramite il <xref:System.ComponentModel.TypeDescriptor> oggetto.

- <xref:System.ComponentModel.Design.IComponentChangeService> gli eventi vengono generati manualmente quando è eseguito il commit di una modifica di annullabile.

- Modifica della finestra di progettazione è stata creata nel contesto di un <xref:System.ComponentModel.Design.DesignerTransaction>.

- La finestra di progettazione sceglie di creare in modo esplicito le unità di annullamento tramite l'unità di annullamento standard fornito da un'implementazione di <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> o l'implementazione specifica di Visual Studio <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>, che deriva da <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> e fornisce inoltre un implementazione di entrambi <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> e <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit>.

## <a name="see-also"></a>Vedere anche

- <xref:System.ComponentModel.Design.UndoEngine>
- <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>
- [Estendere il supporto in fase di progettazione](/previous-versions/37899azc(v=vs.140))