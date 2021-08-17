---
title: Supporto dell'annullamento per le finestre di progettazione | Microsoft Docs
description: Informazioni su come fornire il supporto per l'annullamento nelle finestre di progettazione, automaticamente o usando le funzionalità di Visual Studio SDK.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: c8801dd0e9ca740a64a94a7f8ea5f251ab78950cbf7f0829ebd86bd6607da29f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121413921"
---
# <a name="supply-undo-support-to-designers"></a>Fornire supporto per l'annullamento alle finestre di progettazione

Le finestre di progettazione, come gli editor, devono in genere supportare le operazioni di annullamento in modo che gli utenti possano annullare le modifiche recenti durante la modifica di un elemento di codice.

La maggior parte delle finestre di progettazione implementate Visual Studio il supporto di "annullamento" fornito automaticamente dall'ambiente.

Implementazioni della finestra di progettazione che devono fornire supporto per la funzionalità di annullamento:

- Fornire la gestione dell'annullamento implementando la classe di base astratta <xref:System.ComponentModel.Design.UndoEngine>

- Fornire la persistenza e il supporto CodeDOM implementando le <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> classi  <xref:System.ComponentModel.Design.IComponentChangeService> e .

Per altre informazioni sulla scrittura di finestre di progettazione .NET Framework, vedere [Extend Design-Time Support](/previous-versions/37899azc(v=vs.140)).

fornisce [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] un'infrastruttura di annullamento predefinita tramite:

- Implementazione della gestione dell'annullamento tramite le <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> classi e .

- Fornire la persistenza e il supporto CodeDOM tramite le <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> implementazioni <xref:System.ComponentModel.Design.IComponentChangeService> predefinite e .

## <a name="obtain-undo-support-automatically"></a>Ottenere automaticamente il supporto per l'annullamento

Qualsiasi finestra di progettazione creata in Visual Studio supporta l'annullamento automatico e completo se la finestra di progettazione:

- Usa una classe <xref:System.Windows.Forms.Control> basata su per la relativa interfaccia utente.

- Usa il sistema standard di generazione e analisi del codice basato su CodeDOM per la generazione e la persistenza del codice.

   Per altre informazioni sull'uso del Visual Studio CodeDOM, vedere Generazione e compilazione dinamica del codice [sorgente.](/dotnet/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation)

## <a name="when-to-use-explicit-designer-undo-support"></a>Quando usare il supporto esplicito per l'annullamento della finestra di progettazione
 Le finestre di progettazione devono fornire la propria gestione dell'annullamento se utilizzano un'interfaccia utente grafica, definita adattatore di visualizzazione, diversa da quella fornita da <xref:System.Windows.Forms.Control> .

 Un esempio potrebbe essere la creazione di un prodotto con un'interfaccia grafica basata sul Web anziché con un'.NET Framework grafica basata sul Web.

 In questi casi, è necessario registrare questo adattatore di visualizzazione con Visual Studio utilizzando e fornire la gestione esplicita <xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute> dell'annullamento.

 Le finestre di progettazione devono fornire il supporto di CodeDOM e persistenza se non usano il modello Visual Studio di generazione del codice fornito nello spazio <xref:System.CodeDom> dei nomi.

## <a name="undo-support-features-of-the-designer"></a>Funzionalità di supporto dell'annullamento della finestra di progettazione
 Environment SDK fornisce implementazioni predefinite delle interfacce necessarie per fornire il supporto di annullamento che possono essere usate dalle finestre di progettazione che non usano classi basate per le interfacce utente o il modello CodeDOM e persistenza <xref:System.Windows.Forms.Control> standard.

 La <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> classe deriva dalla classe .NET Framework utilizzando <xref:System.ComponentModel.Design.UndoEngine> un'implementazione della classe per gestire le <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> operazioni di annullamento.

 Visual Studio offre la funzionalità seguente per l'annullamento della finestra di progettazione:

- Funzionalità di annullamento collegate tra più finestre di progettazione.

- Le unità figlio all'interno di una finestra di progettazione possono interagire con i relativi elementi padre implementando <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> e <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> in <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> .

Environment SDK fornisce codeDOM e supporto per la persistenza fornendo:

- <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> come implementazione di <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>

- Oggetto <xref:System.ComponentModel.Design.IComponentChangeService> fornito dall'host Visual Studio progettazione.

## <a name="use-the-environment-sdk-features-to-supply-undo-support"></a>Usare le funzionalità di Environment SDK per fornire il supporto per l'annullamento

Per ottenere il supporto dell'annullamento, un oggetto che implementa una finestra di progettazione deve creare un'istanza e inizializzare un'istanza della classe <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> con un'implementazione <xref:System.IServiceProvider> valida. Questa <xref:System.IServiceProvider> classe deve fornire i servizi seguenti:

- <xref:System.ComponentModel.Design.IDesignerHost>.

- <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>

   Le finestre di progettazione Visual Studio la serializzazione CodeDOM possono scegliere di utilizzare fornito con come <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] implementazione di <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> .

   In questo caso, la <xref:System.IServiceProvider> classe fornita al costruttore deve restituire questo oggetto come <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> implementazione della classe <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> .

- <xref:System.ComponentModel.Design.IComponentChangeService>

   Le finestre di progettazione che usano il valore predefinito fornito Visual Studio host di progettazione predefinito hanno <xref:System.ComponentModel.Design.DesignSurface> un'implementazione predefinita della <xref:System.ComponentModel.Design.IComponentChangeService> classe .

Le finestre di progettazione che implementano un <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> meccanismo di annullamento basato rilevano automaticamente le modifiche se:

- Le modifiche alle proprietà vengono apportate tramite <xref:System.ComponentModel.TypeDescriptor> l'oggetto .

- <xref:System.ComponentModel.Design.IComponentChangeService> Gli eventi vengono generati manualmente quando viene eseguito il commit di una modifica annullabile.

- La modifica nella finestra di progettazione è stata creata nel contesto di un oggetto <xref:System.ComponentModel.Design.DesignerTransaction> .

- La finestra di progettazione sceglie di creare in modo esplicito unità di annullamento usando l'unità di annullamento standard fornita da un'implementazione di o l'implementazione specifica di Visual Studio , che deriva da e fornisce anche un'implementazione di <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> e <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> .

## <a name="see-also"></a>Vedi anche

- <xref:System.ComponentModel.Design.UndoEngine>
- <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>
- [Estendere Design-Time supporto](/previous-versions/37899azc(v=vs.140))
