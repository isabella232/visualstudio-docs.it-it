---
title: Utilizzo dell'ActivityDesigner Legacy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- activities, configuring
- custom activities
- Activity Designer
- child activities, adding
- activities, adding child
- activities, creating custom
ms.assetid: 2fea8a05-6e58-423d-94bf-a822b15ffb80
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e083da3dce7ed6b69309557d9e960a302f5b3d60
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58968499"
---
# <a name="using-the-legacy-activity-designer"></a>Utilizzo dell'ActivityDesigner legacy
In questo argomento viene descritto come usare ActivityDesigner in [!INCLUDE[wfd1](../includes/wfd1-md.md)] legacy. Usare la finestra di progettazione legacy quando si fa riferimento a [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o a [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 La Finestra di progettazione dell’attività consente di creare attività personalizzate.  
  
## <a name="creating-a-custom-activity"></a>Creazione di un'attività personalizzata  
 Seguire questi passaggi per creare un'attività personalizzata usando la Finestra di progettazione dell’attività:  
  
1. Nel **Project** menu, fare clic su **Aggiungi attività**.  
  
2. Selezionare il **impegno** oppure **attività (con separazione del codice)** modello.  
  
   1.  Usare la **attività** modello per creare un'attività con la definizione di attività e il codice utente nello stesso file di codice.  
  
   2.  Usare la **attività (con separazione del codice)** modello per creare un'attività con la definizione di attività espressa come markup del flusso di lavoro e il codice utente in un file di codice separato.  
  
3. Digitare un nome di attività o mantenere il nome predefinito e quindi fare clic su **Add**.  
  
   È anche possibile creare un set di attività personalizzate creando un nuovo progetto di tipo **Workflow Activity Library**. Per altre informazioni su questo tipo di progetto, vedere [come: Creare una libreria di attività del flusso di lavoro (Legacy)](../workflow-designer/how-to-create-a-workflow-activity-library-legacy.md).  
  
## <a name="configuring-an-activity"></a>Configurazione di un'attività.  
 Mentre la Finestra di progettazione dell’attività è attiva, è possibile usare il visualizzatore proprietà per configurare le proprietà elencate nella tabella seguente.  
  
|Proprietà|Commenti|  
|--------------|--------------|  
|**Name**|Nome dell’attività.|  
|**Classe di base**|Classe base dalla quale è derivata l’attività. La classe base predefinita è [SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020). Nel **delle proprietà** finestra, fare clic sul **una classe Base** puntini di sospensione **[...]**  per selezionare un'altra classe di base nel [individuare e selezionare una finestra di dialogo tipo .NET (Legacy)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md).|  
|**Descrizione**|Descrizione dell'attività definita dall'utente.|  
|**Enabled**|Impostare su **True** per impostazione predefinita per consentire l'esecuzione dell'attività e la convalida. Impostare su **False** per disabilitare la convalida e l'esecuzione dell'attività. Per informazioni sull'esecuzione dell'attività e la convalida, vedere [sviluppo di attività del flusso di lavoro](http://go.microsoft.com/fwlink?LinkID=65024).|  
  
## <a name="adding-child-activities"></a>Aggiunta di attività figlio.  
 È possibile trascinare le attività figlio dalla Casella degli strumenti all'attività che si sta progettando. È quindi possibile configurare ogni attività figlio usando il visualizzatore proprietà.  
  
## <a name="see-also"></a>Vedere anche  
 [Sviluppo di attività del flusso di lavoro](http://go.microsoft.com/fwlink?LinkID=65024)   
 [Creazione di attività personalizzate](http://go.microsoft.com/fwlink?LinkID=65021)   
 [Attività flusso di lavoro legacy](../workflow-designer/legacy-workflow-activities.md)   
 [Esempi di attività personalizzate](http://go.microsoft.com/fwlink?LinkID=65022)   
 [Procedura: Creare una libreria di attività del flusso di lavoro (Legacy)](../workflow-designer/how-to-create-a-workflow-activity-library-legacy.md)   
 [Uso di Progettazione flussi di lavoro legacy](../workflow-designer/using-the-legacy-workflow-designer.md)