---
title: Fornire supporto di annullamento alle finestre di progettazione | Microsoft Docs
description: Informazioni su come fornire supporto di annullamento nelle finestre di progettazione, automaticamente o usando le funzionalità di Visual Studio SDK.
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
ms.openlocfilehash: e53cf66118bbc98526c3daa029b07fba0df2d3ba
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122144405"
---
# <a name="supply-undo-support-to-designers"></a>Fornire supporto di annullamento alle finestre di progettazione

Le finestre di progettazione, come gli editor, in genere devono supportare le operazioni di annullamento in modo che gli utenti possano annullare le modifiche recenti durante la modifica di un elemento di codice.

La maggior parte delle finestre di progettazione implementate Visual Studio il supporto "annulla" fornito automaticamente dall'ambiente.

Implementazioni della finestra di progettazione che devono fornire supporto per la funzionalità di annullamento:

- Fornire la gestione dell'annullamento implementando la classe di base astratta <xref:System.ComponentModel.Design.UndoEngine>

- Fornire la persistenza e il supporto CodeDOM implementando <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> le classi  <xref:System.ComponentModel.Design.IComponentChangeService> e .

Per altre informazioni sulla scrittura di finestre di progettazione .NET Framework, vedere [Extend Design-Time Support](/previous-versions/37899azc(v=vs.140)).

Fornisce [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] un'infrastruttura di annullamento predefinita tramite:

- Fornire implementazioni di gestione dell'annullamento tramite <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> le <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> classi e .

- Fornire la persistenza e il supporto CodeDOM tramite le <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> implementazioni e <xref:System.ComponentModel.Design.IComponentChangeService> predefinite.

## <a name="obtain-undo-support-automatically"></a>Ottenere automaticamente il supporto per l'annullamento

Qualsiasi finestra di progettazione creata in Visual Studio supporta l'annullamento automatico e completo se, la finestra di progettazione:

- Usa una classe <xref:System.Windows.Forms.Control> basata su per la relativa interfaccia utente.

- Usa il sistema standard di generazione e analisi del codice basato su CodeDOM per la generazione e la persistenza del codice.

   Per altre informazioni sull'uso del Visual Studio CodeDOM, vedere Generazione e compilazione dinamica del codice [sorgente.](/dotnet/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation)

## <a name="when-to-use-explicit-designer-undo-support"></a>Quando usare il supporto dell'annullamento esplicito della finestra di progettazione
 Le finestre di progettazione devono fornire la propria gestione dell'annullamento se usano un'interfaccia utente grafica, definita adattatore di visualizzazione, diversa da quella fornita da <xref:System.Windows.Forms.Control> .

 Un esempio potrebbe essere la creazione di un prodotto con un'interfaccia grafica basata sul Web anziché con un'.NET Framework grafica basata su .NET Framework grafica.

 In questi casi, è necessario registrare questo adattatore di visualizzazione con Visual Studio usando e fornire <xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute> una gestione esplicita dell'annullamento.

 Le finestre di progettazione devono fornire il supporto codeDOM e persistenza se non usano il modello Visual Studio di generazione del codice specificato nello spazio <xref:System.CodeDom> dei nomi.

## <a name="undo-support-features-of-the-designer"></a>Annullare le funzionalità di supporto della finestra di progettazione
 Environment SDK fornisce implementazioni predefinite delle interfacce necessarie per fornire il supporto dell'annullamento che può essere usato dalle finestre di progettazione che non usano classi basate per le interfacce utente o il modello CodeDOM e persistenza <xref:System.Windows.Forms.Control> standard.

 La <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> classe deriva dalla classe .NET Framework utilizzando <xref:System.ComponentModel.Design.UndoEngine> un'implementazione della <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> classe per gestire le operazioni di annullamento.

 Visual Studio fornisce la funzionalità seguente per l'annullamento della finestra di progettazione:

- Funzionalità di annullamento collegata in più finestre di progettazione.

- Le unità figlio all'interno di una finestra di progettazione possono interagire con gli elementi padre implementando <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> e <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> in <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> .

Environment SDK fornisce codedom e supporto per la persistenza fornendo:

- <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> come implementazione dell'oggetto <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>

- Oggetto <xref:System.ComponentModel.Design.IComponentChangeService> fornito dall'Visual Studio di progettazione.

## <a name="use-the-environment-sdk-features-to-supply-undo-support"></a>Usare le funzionalità di Environment SDK per fornire il supporto dell'annullamento

Per ottenere il supporto dell'annullamento, un oggetto che implementa una finestra di progettazione deve creare un'istanza e inizializzare un'istanza della <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> classe con un'implementazione <xref:System.IServiceProvider> valida. Questa <xref:System.IServiceProvider> classe deve fornire i servizi seguenti:

- <xref:System.ComponentModel.Design.IDesignerHost>.

- <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>

   Le finestre di progettazione Visual Studio la serializzazione CodeDOM possono scegliere di usare fornito con come <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] implementazione di <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> .

   In questo caso, la <xref:System.IServiceProvider> classe fornita al costruttore deve restituire questo oggetto come <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> implementazione della classe <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> .

- <xref:System.ComponentModel.Design.IComponentChangeService>

   Le finestre di progettazione che usano il valore predefinito fornito Visual Studio host di progettazione predefinito hanno <xref:System.ComponentModel.Design.DesignSurface> un'implementazione predefinita della <xref:System.ComponentModel.Design.IComponentChangeService> classe .

Le finestre di progettazione che implementano un <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> meccanismo di annullamento basato rilevano automaticamente le modifiche se:

- Le modifiche alle proprietà vengono apportate tramite <xref:System.ComponentModel.TypeDescriptor> l'oggetto .

- <xref:System.ComponentModel.Design.IComponentChangeService> Gli eventi vengono generati manualmente quando viene eseguito il commit di una modifica annullabile.

- La modifica nella finestra di progettazione è stata creata nel contesto di un <xref:System.ComponentModel.Design.DesignerTransaction> oggetto .

- La finestra di progettazione sceglie di creare in modo esplicito unità di annullamento usando l'unità di annullamento standard fornita da un'implementazione di o l'implementazione specifica di Visual Studio , che deriva da e fornisce anche un'implementazione di e <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> .

## <a name="see-also"></a>Vedi anche

- <xref:System.ComponentModel.Design.UndoEngine>
- <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>
- [Estendere Design-Time supporto](/previous-versions/37899azc(v=vs.140))
