---
title: Fornire il supporto per l'annullamento alle finestre di progettazione | Microsoft Docs
description: Informazioni su come fornire il supporto di annullamento nelle finestre di progettazione, automaticamente o usando le funzionalità di Visual Studio SDK.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6b56eb762cf4a2746af04ed69c7c4c49afc15dec
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056311"
---
# <a name="supply-undo-support-to-designers"></a>Fornire il supporto per l'annullamento alle finestre di progettazione

Le finestre di progettazione, come gli editor, in genere devono supportare le operazioni di annullamento in modo che gli utenti possano invertire le modifiche recenti durante la modifica di un elemento di codice.

La maggior parte delle finestre di progettazione implementate in Visual Studio dispone del supporto "Annulla" fornito automaticamente dall'ambiente.

Implementazioni della finestra di progettazione che devono fornire supporto per la funzionalità di annullamento:

- Fornire la gestione dell'annullamento implementando la classe di base astratta <xref:System.ComponentModel.Design.UndoEngine>

- Fornire la persistenza e il supporto CodeDOM implementando le <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  <xref:System.ComponentModel.Design.IComponentChangeService> classi e.

Per ulteriori informazioni sulla creazione di finestre di progettazione con .NET Framework, vedere [estendere Design-Time Supporto](/previous-versions/37899azc(v=vs.140)).

[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]Fornisce un'infrastruttura di annullamento predefinita per:

- Fornire implementazioni di gestione di annullamento tramite le <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> classi e.

- Fornire supporto per la persistenza e CodeDOM tramite <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> le <xref:System.ComponentModel.Design.IComponentChangeService> implementazioni e predefinite.

## <a name="obtain-undo-support-automatically"></a>Ottenere il supporto di annullamento automaticamente

Qualsiasi finestra di progettazione creata in Visual Studio dispone del supporto di annullamento automatico e completo se, la finestra di progettazione:

- Usa una <xref:System.Windows.Forms.Control> classe basata per la relativa interfaccia utente.

- Usa il sistema di analisi e generazione del codice basato su CodeDOM standard per la generazione e la persistenza del codice.

   Per ulteriori informazioni sull'utilizzo del supporto di Visual Studio CodeDOM, vedere [generazione e compilazione di codice sorgente dinamico](/dotnet/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation).

## <a name="when-to-use-explicit-designer-undo-support"></a>Quando usare il supporto di annullamento esplicito della finestra di progettazione
 I progettisti devono fornire la propria gestione degli annullamenti se utilizzano un'interfaccia utente grafica, definita scheda di visualizzazione, diversa da quella fornita da <xref:System.Windows.Forms.Control> .

 Un esempio potrebbe essere la creazione di un prodotto con un'interfaccia di progettazione grafica basata sul Web anziché un'interfaccia grafica basata su .NET Framework.

 In questi casi, è necessario registrare questa scheda di visualizzazione con Visual Studio usando <xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute> e fornire una gestione esplicita di annullamento.

 Se non usano il modello di generazione del codice di Visual Studio disponibile nello spazio dei nomi, le finestre di progettazione devono fornire il supporto per CodeDOM e persistenza <xref:System.CodeDom> .

## <a name="undo-support-features-of-the-designer"></a>Annullare le funzionalità di supporto della finestra di progettazione
 L'SDK dell'ambiente fornisce le implementazioni predefinite delle interfacce necessarie per fornire il supporto di annullamento che può essere utilizzato da progettisti che non utilizzano <xref:System.Windows.Forms.Control> classi basate per le interfacce utente o il modello CodeDOM e di persistenza standard.

 La <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> classe deriva dalla <xref:System.ComponentModel.Design.UndoEngine> classe .NET Framework usando un'implementazione della <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> classe per gestire le operazioni di annullamento.

 Visual Studio fornisce la funzionalità seguente per la finestra di progettazione Annulla:

- Funzionalità di annullamento collegate tra più finestre di progettazione.

- Le unità figlio all'interno di una finestra di progettazione possono interagire con i relativi elementi padre implementando <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> e <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> su <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> .

L'SDK dell'ambiente fornisce il supporto per CodeDOM e persistenza fornendo:

- <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> come implementazione del <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>

- Oggetto <xref:System.ComponentModel.Design.IComponentChangeService> fornito dall'host di progettazione di Visual Studio.

## <a name="use-the-environment-sdk-features-to-supply-undo-support"></a>Usare le funzionalità dell'SDK per gli ambienti per fornire supporto per l'annullamento

Per ottenere il supporto di annullamento, un oggetto che implementa una finestra di progettazione deve creare un'istanza di e inizializzare un'istanza della <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> classe con un' <xref:System.IServiceProvider> implementazione valida. Questa <xref:System.IServiceProvider> classe deve fornire i servizi seguenti:

- <xref:System.ComponentModel.Design.IDesignerHost>.

- <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>

   Le finestre di progettazione che usano la serializzazione CodeDOM di Visual Studio possono scegliere di usare <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> fornito con [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] come implementazione di <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> .

   In questo caso, la <xref:System.IServiceProvider> classe fornita al <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> costruttore deve restituire questo oggetto come implementazione della <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> classe.

- <xref:System.ComponentModel.Design.IComponentChangeService>

   Per le finestre di progettazione che usano l'impostazione predefinita <xref:System.ComponentModel.Design.DesignSurface> fornita dall'host di progettazione di Visual Studio è garantita un'implementazione predefinita della <xref:System.ComponentModel.Design.IComponentChangeService> classe.

Le finestre di progettazione che implementano un <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> meccanismo di annullamento basato su rileva automaticamente le modifiche se

- Le modifiche alle proprietà vengono apportate tramite l' <xref:System.ComponentModel.TypeDescriptor> oggetto.

- <xref:System.ComponentModel.Design.IComponentChangeService> gli eventi vengono generati manualmente quando viene eseguito il commit di una modifica annullabile.

- La modifica nella finestra di progettazione è stata creata nel contesto di un oggetto <xref:System.ComponentModel.Design.DesignerTransaction> .

- La finestra di progettazione sceglie di creare in modo esplicito le unità di annullamento usando l'unità di annullamento standard fornita da un'implementazione di <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> o l'implementazione specifica di Visual Studio <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> , che deriva da <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> e fornisce anche un'implementazione di <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> e <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> .

## <a name="see-also"></a>Vedi anche

- <xref:System.ComponentModel.Design.UndoEngine>
- <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>
- [Estendi supporto Design-Time](/previous-versions/37899azc(v=vs.140))
