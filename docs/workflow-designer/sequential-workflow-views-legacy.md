---
title: Finestra di progettazione del flusso di lavoro - visualizzazioni del flusso di lavoro sequenziale (Legacy)
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- sequential workflow views
- sequential workflows, views
ms.assetid: 135f24b9-1b37-442b-9ef8-f0f2108a3212
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ce1217ea629ae0301b72b444161d61db4fe448b1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
ms.locfileid: "31976019"
---
# <a name="sequential-workflow-views-legacy"></a>Visualizzazioni del flusso di lavoro sequenziale (legacy)

Visual Studio 2010 offre una progettazione di flussi di lavoro Windows legacy che può essere utilizzato come destinazione .NET Framework versione 3.5 o la WinFX.

La finestra di progettazione del flusso di lavoro consente di creare graficamente le applicazioni di Windows Workflow Foundation (WF) tramite l'interfaccia utente di Visual Studio familiare. Applicazioni di Windows Workflow Foundation (WF) sono composte da passaggi del processo del flusso di lavoro chiamati attività. Per creare un flusso di lavoro, creare le attività nell'area di progettazione trascinando i rispettivi ActivityDesigner dalla **della casella degli strumenti** nell'area di progettazione.

Quando si crea un flusso di lavoro sequenza, ovvero un [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040), sono disponibili tre visualizzazioni del flusso di lavoro. Queste visualizzazioni sono accessibili dal **flusso di lavoro** menu e dal menu di scelta rapida nell'area di progettazione.

Nella tabella riportata di seguito vengono elencati il nome e la descrizione di ogni visualizzazione.

|Opzione di menu/scheda|Descrizione|
|----------------------|-----------------|
|**Visualizzazione flusso di lavoro sequenziale**|Fare doppio clic su area di progettazione e seleziona il **Visualizza flusso di lavoro sequenziale** opzione dal menu di scelta rapida per visualizzare il **flusso di lavoro sequenziale** visualizzazione, che mostra le attività basate su grafica rappresentazione del flusso di lavoro sequenza. Oppure selezionare **Visualizza flusso di lavoro sequenziale** dal **flusso di lavoro** menu.|
|**Visualizza gestore annullamento**|Fare doppio clic su area di progettazione e seleziona il **Visualizza gestore annullamento** opzione dal menu di scelta rapida per visualizzare il **flusso di lavoro sequenziale** cui viene mostrata la [CancellationHandlerActivity ](http://go.microsoft.com/fwlink?LinkID=65050) attività associata con il flusso di lavoro. Oppure selezionare **Visualizza gestore annullamento** dal **flusso di lavoro** menu.|
|**Visualizza gestori errori**|Fare doppio clic su area di progettazione e seleziona il **Visualizza gestori errori** opzione dal menu di scelta rapida per visualizzare il **errori** cui viene mostrata la [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) attività associata con il flusso di lavoro. Oppure selezionare **Visualizza gestori errori** dal **flusso di lavoro** menu.|

 Per ulteriori informazioni sulle visualizzazioni simili, vedere [visualizzazioni di attività (Legacy)](../workflow-designer/activity-views-legacy.md).

## <a name="see-also"></a>Vedere anche

- [Visualizzazioni delle attività (legacy)](../workflow-designer/activity-views-legacy.md)
- [Creazione di progetti flusso di lavoro legacy](../workflow-designer/creating-legacy-workflow-projects.md)
- [Modalità di creazione del flusso di lavoro](http://go.microsoft.com/fwlink?LinkID=65014)