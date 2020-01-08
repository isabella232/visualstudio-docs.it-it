---
title: 'Progettazione flussi di lavoro: System. Activities, scegliere gli elementi della casella degli strumenti'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES_COMPONENTS
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES COMPONENTS
ms.assetid: cef390cd-eeda-42e6-9d2e-18c8325a4f06
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3f1a7030b6c351407814314ccd41e0e2ed6a880e
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593109"
---
# <a name="systemactivities-tab-choose-toolbox-items-dialog-box"></a>Scheda System. Activities, finestra di dialogo Scegli elementi della casella degli strumenti

Questa scheda della finestra di dialogo **Scegli elementi della casella degli strumenti** Visualizza un elenco di attività, modelli ed elementi di Windows Workflow Foundation (WF) disponibili. Per visualizzare l'elenco, **scegliere Scegli elementi della casella degli** strumenti dal menu **strumenti** oppure fare clic con il pulsante destro del mouse sulla **casella degli** strumenti e **scegliere Scegli elementi** per visualizzare la finestra di dialogo **Scegli elementi della casella degli strumenti** , quindi selezionare la scheda **System. Activities** . all'interno dell'elenco sono contenute le attività del flusso di lavoro degli assembly System. Activities, System. ServiceModel Tuttavia, per impostazione predefinita vengono controllate solo le attività fornite dal sistema indicate e le attività aggiunte tramite altri assembly visualizzati nella **casella degli strumenti** . Le attività aggiunte di recente vengono controllate automaticamente e visualizzate nella casella **degli strumenti** quando si fa clic su **OK** nella finestra di dialogo. Inoltre, questi elementi vengono visualizzati nella **casella degli strumenti** in una nuova categoria corrispondente allo spazio dei nomi in cui risiede l'attività, l'elemento o il modello.

> [!WARNING]
> Se si prova ad aggiungere un assembly che non contiene attività del flusso di lavoro, viene visualizzata una finestra di errore in cui si segnala che l'assembly non contiene attività.

Questa finestra di dialogo è indipendente dal progetto e, di conseguenza, la scheda **System. Activities** continua a essere visualizzata in XAML autonomo o in un tipo di progetto non di flusso di lavoro.

Il filtro viene eseguito in ogni scheda e non è possibile aggiungere attività del flusso di lavoro tramite la scheda **componente .NET** . aggiungerle tramite la scheda **System. Activities** .

È possibile deselezionare gli elementi che non si desidera visualizzare nella **casella degli strumenti** da questa scheda della finestra di dialogo oppure, in alternativa, è possibile utilizzare l'opzione del menu di scelta rapida **Elimina** nella **casella degli** strumenti e dereferenziare un assembly non rimuove l'elemento dalla **casella degli strumenti**.

Quando si crea un'istanza dell'attività trascinandola e rilasciandola nella finestra di progettazione, si aggiunge automaticamente all'elenco degli assembly di riferimento l'assembly che contiene l'elemento. Se inoltre l'attività fa riferimento a un assembly C, C non viene aggiunto all'elenco di assembly di riferimento. L'assembly C deve trovarsi nella GAC o nella stessa directory dell'attività B. Nel caso autonomo, l'assembly deve trovarsi nella GAC o nei percorsi di probe di VS. È quindi solo possibile trascinare e rilasciare le attività nell'area di progettazione flussi di lavoro.

Le impostazioni della **casella degli strumenti** vengono salvate per impostazione predefinita come opzioni utente, quindi la volta successiva, quando si apre la **casella degli strumenti**, viene visualizzato l'elenco personalizzato delle attività del flusso di lavoro. Un effetto collaterale è che se sono stati aggiunti elementi di dominio specifici alla **casella degli strumenti** tramite la finestra di dialogo **Scegli elementi della casella degli strumenti** , gli elementi continuano a essere visualizzati anche quando si lavora in un'applicazione console del flusso di lavoro. Se non si desidera visualizzarli, eliminarli usando il menu di scelta rapida o deselezionarli tramite la finestra di dialogo **Scegli elementi della casella degli strumenti** come indicato in precedenza.

Le colonne di questa finestra di dialogo includono le informazioni seguenti:

Nome\
Elenca i nomi delle attività del flusso di lavoro attualmente registrate nel computer locale.

Namespace
Visualizza la gerarchia dello spazio dei nomi .NET che definisce la struttura dell'attività.

Nome assembly \
Consente di visualizzare il nome e la versione dell'assembly .NET che contiene l'attività.

Directory
Visualizza il percorso dell'assembly .NET che contiene le attività del flusso di lavoro. Gli assembly si trovano, per impostazione predefinita, nella cartella Global Assembly Cache.

Per ordinare i componenti elencati, selezionare una delle intestazioni di colonna.
