---
title: Fornitura di supporto per l'annullamento ai progettisti . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0580f974c362a71c3e400946f2ad34f565ad1232
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699669"
---
# <a name="supply-undo-support-to-designers"></a>Fornire supporto di annullamento ai progettisti

Le finestre di progettazione, come gli editor, in genere devono supportare le operazioni di annullamento in modo che gli utenti possano invertire le modifiche recenti durante la modifica di un elemento di codice.

La maggior parte delle finestre di progettazione implementate in Visual Studio dispone del supporto "Annulla" fornito automaticamente dall'ambiente.

Implementazioni della finestra di progettazione che devono fornire supporto per la funzionalità di annullamento:Designer implementations that need to provide support for the undo feature:

- Fornire la gestione degli annullamenti implementando la classe base astrattaProvide undo management by implementing the abstract base class<xref:System.ComponentModel.Design.UndoEngine>

- Fornire la persistenza e <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> il <xref:System.ComponentModel.Design.IComponentChangeService> supporto CodeDOM implementando le classi e .

Per ulteriori informazioni sulla scrittura di finestre di progettazione mediante .NET Framework, vedere Estendere il supporto in fase di [progettazione](/previous-versions/37899azc(v=vs.140)).

Fornisce [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] un'infrastruttura di annullamento predefinita:

- Fornire implementazioni di gestione <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> degli annullamenti tramite le classi e .

- Fornitura di persistenza e <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> supporto <xref:System.ComponentModel.Design.IComponentChangeService> CodeDOM tramite le implementazioni e predefinite.

## <a name="obtain-undo-support-automatically"></a>Ottenere automaticamente il supporto di annullamento

Qualsiasi finestra di progettazione creata in Visual Studio dispone del supporto di annullamento automatico e completo se, la finestra di progettazione:Any designer created in Visual Studio has automatic and full undo support if, the designer:

- Utilizza una <xref:System.Windows.Forms.Control> classe basata per la relativa interfaccia utente.

- Utilizza il sistema di generazione e analisi di codice standard basato su CodeDOM per la generazione e la persistenza del codice.

   Per ulteriori informazioni sull'utilizzo del supporto di Visual Studio CodeDOM, vedere [Compilazione e generazione](/dotnet/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation)dinamica di codice sorgente .

## <a name="when-to-use-explicit-designer-undo-support"></a>Quando utilizzare il supporto di annullamento della finestra di progettazione esplicitaWhen to Use Explicit Designer Undo Support
 I progettisti devono fornire la propria gestione degli annullamenti se utilizzano un'interfaccia utente grafica, denominata adattatore di visualizzazione, diversa da quella fornita da <xref:System.Windows.Forms.Control>.

 Un esempio potrebbe essere la creazione di un prodotto con un'interfaccia di progettazione grafica basata sul Web anziché un'interfaccia grafica basata su .NET Framework.

 In questi casi, è necessario registrare questo <xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute>adattatore di visualizzazione con Visual Studio utilizzando , e fornire la gestione di annullamento esplicita.

 Le finestre di progettazione devono fornire il supporto CodeDOM e persistenza <xref:System.CodeDom> se non usano il modello di generazione del codice di Visual Studio fornito nello spazio dei nomi.

## <a name="undo-support-features-of-the-designer"></a>Annullare le funzionalità di supporto della finestra di progettazione
 L'SDK dell'ambiente fornisce implementazioni predefinite delle interfacce necessarie per fornire <xref:System.Windows.Forms.Control> il supporto di annullamento che possono essere utilizzate dalle finestre di progettazione che non utilizzano classi basate per le interfacce utente o il modello CodeDOM e di persistenza standard.

 La <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> classe deriva dalla classe <xref:System.ComponentModel.Design.UndoEngine> .NET Framework <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> utilizzando un'implementazione della classe per gestire le operazioni di annullamento.

 Visual Studio fornisce la funzionalità seguente per l'annullamento della finestra di progettazione:Visual Studio provides the following feature to designer undo:

- Funzionalità di annullamento collegato tra più finestre di progettazione.

- Le unità figlio all'interno di <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> un <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>progettista possono interagire con i genitori implementando e su .

L'SDK di ambiente fornisce il supporto CodeDOM e persistenza fornendo:

- <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>come un'attuazione del<xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>

- Oggetto <xref:System.ComponentModel.Design.IComponentChangeService> fornito dall'host di progettazione di Visual Studio.

## <a name="use-the-environment-sdk-features-to-supply-undo-support"></a>Usare le funzionalità SDK dell'ambiente per fornire il supporto per l'annullamentoUse the Environment SDK Features to Supply Undo Support

Per ottenere il supporto per l'annullamento, un oggetto <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> che implementa <xref:System.IServiceProvider> una finestra di progettazione deve creare un'istanza e inizializzare un'istanza della classe con un'implementazione valida. Questa <xref:System.IServiceProvider> classe deve fornire i servizi seguenti:This class must provide the following services:

- <xref:System.ComponentModel.Design.IDesignerHost>.

- <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>

   Le finestre di progettazione che utilizzano la serializzazione CodeDOM di Visual Studio possono scegliere di utilizzare <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> con fornito con l'implementazione [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] dell'oggetto <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>.

   In questo caso, la <xref:System.IServiceProvider> <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> classe fornita al costruttore deve <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> restituire questo oggetto come implementazione della classe.

- <xref:System.ComponentModel.Design.IComponentChangeService>

   Le finestre di <xref:System.ComponentModel.Design.DesignSurface> progettazione che utilizzano il valore predefinito fornito <xref:System.ComponentModel.Design.IComponentChangeService> dall'host di progettazione di Visual Studio sono garantite per avere un'implementazione predefinita della classe.

Le finestre <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> di progettazione che implementano un meccanismo di annullamento basato tengono traccia delle modifiche automaticamente se:Designers implementing a based undo mechanism automatically tracks changes if:

- Le modifiche alle <xref:System.ComponentModel.TypeDescriptor> proprietà vengono apportate tramite l'oggetto.

- <xref:System.ComponentModel.Design.IComponentChangeService>gli eventi vengono generati manualmente quando viene eseguito il commit di una modifica annullabile.

- La modifica della finestra di progettazione è stata creata nel contesto di un oggetto . <xref:System.ComponentModel.Design.DesignerTransaction>

- La finestra di progettazione sceglie di creare in modo esplicito <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> le unità di annullamento utilizzando l'unità di annullamento standard fornita da un'implementazione di o <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>dell'implementazione specifica di Visual Studio , che deriva <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> da e fornisce anche un'implementazione di entrambi <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> e <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit>.

## <a name="see-also"></a>Vedere anche

- <xref:System.ComponentModel.Design.UndoEngine>
- <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>
- [Estendi il supporto in fase di progettazione](/previous-versions/37899azc(v=vs.140))
