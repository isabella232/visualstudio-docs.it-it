---
title: Utilizzo dell'ActivityDesigner legacy | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a13aeeb3394ee6b8896376c0e7d520b90fb56fa6
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302830"
---
# <a name="using-the-legacy-activity-designer"></a>Utilizzo dell'ActivityDesigner legacy
In questo argomento viene descritto come usare ActivityDesigner in [!INCLUDE[wfd1](../includes/wfd1-md.md)] legacy. Usare la finestra di progettazione legacy quando si fa riferimento a [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o a [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 La Finestra di progettazione dell’attività consente di creare attività personalizzate.

## <a name="creating-a-custom-activity"></a>Creazione di un'attività personalizzata
 Seguire questi passaggi per creare un'attività personalizzata usando la Finestra di progettazione dell’attività:

1. Scegliere **Aggiungi attività**dal menu **progetto** .

2. Selezionare il modello **attività** o **attività (con separazione del codice)** .

   1. Usare il modello di **attività** per creare un'attività con la definizione di attività e il codice utente nello stesso file di codice.

   2. Usare il modello **attività (con separazione del codice)** per creare un'attività con la definizione di attività espressa come markup del flusso di lavoro e il codice utente in un file di codice separato.

3. Digitare un nome di attività o mantenendone il nome predefinito, quindi fare clic su **Aggiungi**.

   È inoltre possibile creare un set di attività personalizzate creando un nuovo progetto di tipo **libreria attività flusso di lavoro**. Per ulteriori informazioni su questo tipo di progetto, vedere [procedura: creare una libreria di attività del flusso di lavoro (legacy)](../workflow-designer/how-to-create-a-workflow-activity-library-legacy.md).

## <a name="configuring-an-activity"></a>Configurazione di un'attività.
 Mentre la Finestra di progettazione dell’attività è attiva, è possibile usare il visualizzatore proprietà per configurare le proprietà elencate nella tabella seguente.

|Proprietà|Comments|
|--------------|--------------|
|**Nome**|Nome dell’attività.|
|**Classe di base**|Classe base dalla quale è derivata l’attività. La classe base predefinita è [SequenceActivity](https://go.microsoft.com/fwlink?LinkID=65020). Nella finestra **Proprietà** fare clic sui puntini di sospensione **[...]** della **classe di base** per selezionare un'altra classe di base nella finestra di [dialogo Cerca e seleziona un tipo .NET (legacy)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md).|
|**Descrizione**|Descrizione dell'attività definita dall'utente.|
|**Enabled**|Per impostazione predefinita, impostare su **true** per abilitare l'esecuzione e la convalida delle attività. Impostare su **false** per disabilitare l'esecuzione e la convalida delle attività. Per informazioni sull'esecuzione e la convalida delle attività, vedere [sviluppo di attività del flusso di lavoro](https://go.microsoft.com/fwlink?LinkID=65024).|

## <a name="adding-child-activities"></a>Aggiunta di attività figlio.
 È possibile trascinare le attività figlio dalla Casella degli strumenti all'attività che si sta progettando. È quindi possibile configurare ogni attività figlio usando il visualizzatore proprietà.

## <a name="see-also"></a>Vedere anche
 [Sviluppo di attività del flusso di lavoro](https://go.microsoft.com/fwlink?LinkID=65024) [creazione](https://go.microsoft.com/fwlink?LinkID=65021) di attività personalizzate attività [del flusso di lavoro legacy](../workflow-designer/legacy-workflow-activities.md) attività [personalizzate esempi](https://go.microsoft.com/fwlink?LinkID=65022) [procedura: creare una libreria di attività del flusso di lavoro (legacy)](../workflow-designer/how-to-create-a-workflow-activity-library-legacy.md) [utilizzando la progettazione flussi di lavoro legacy](../workflow-designer/using-the-legacy-workflow-designer.md)