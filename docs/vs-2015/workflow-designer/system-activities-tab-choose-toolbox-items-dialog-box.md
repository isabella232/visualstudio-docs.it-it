---
title: Scheda System. Activities, finestra di dialogo Scegli elementi della casella degli strumenti | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES_COMPONENTS
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES COMPONENTS
ms.assetid: cef390cd-eeda-42e6-9d2e-18c8325a4f06
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 95b2aa636b63523e06e3c931381e4506a0a03bac
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655175"
---
# <a name="systemactivities-tab-choose-toolbox-items-dialog-box"></a>Scheda System.Activities, finestra di dialogo Scegli elementi della Casella degli strumenti
Questa scheda della finestra di dialogo **Scegli elementi della casella degli strumenti** Visualizza un elenco di [!INCLUDE[wf](../includes/wf-md.md)] attività, modelli ed elementi disponibili. Per visualizzare questo elenco, **scegliere Scegli elementi della casella degli** strumenti dal menu **strumenti** oppure fare clic con il pulsante destro del mouse sulla **casella degli** strumenti e **scegliere Scegli elementi** per visualizzare la finestra di dialogo **Scegli elementi della casella degli strumenti** , quindi selezionare la scheda **System. Activities** . L'elenco contiene le attività del flusso di lavoro dagli assembly System. Activities, System. ServiceModel. Activities e System. Activities. Core. Presentation; Tuttavia, per impostazione predefinita vengono controllate solo le attività fornite dal sistema indicate e le attività aggiunte tramite altri assembly visualizzati nella **casella degli strumenti** . Le attività aggiunte di recente vengono controllate automaticamente e visualizzate nella casella **degli strumenti** quando si fa clic su **OK** nella finestra di dialogo. Inoltre, questi elementi vengono visualizzati nella **casella degli strumenti** in una nuova categoria corrispondente allo spazio dei nomi in cui risiede l'attività, l'elemento o il modello.

> [!WARNING]
> Se si prova ad aggiungere un assembly che non contiene attività del flusso di lavoro, viene visualizzata una finestra di errore in cui si segnala che l'assembly non contiene attività.

 Questa finestra di dialogo è indipendente dal progetto e, di conseguenza, la scheda **System. Activities** continua a essere visualizzata in XAML autonomo o in un tipo di progetto non di flusso di lavoro.

 Il filtro viene eseguito in ogni scheda. Ciò significa che non è possibile aggiungere attività del flusso di lavoro tramite la scheda **componente .NET** . Devono essere aggiunti tramite la scheda **System. Activities** .

 È possibile deselezionare gli elementi che non si desidera visualizzare nella **casella degli strumenti** da questa scheda della finestra di dialogo oppure, in alternativa, è possibile utilizzare l'opzione del menu di scelta rapida **Elimina** nella **casella degli** strumenti e dereferenziare un assembly non rimuove l'elemento dalla **casella degli strumenti**.

 Quando si crea un'istanza dell'attività trascinandola e rilasciandola nella finestra di progettazione, si aggiunge automaticamente all'elenco degli assembly di riferimento l'assembly che contiene l'elemento. Se inoltre l'attività fa riferimento a un assembly C, C non viene aggiunto all'elenco di assembly di riferimento. L'assembly C deve trovarsi nella GAC o nella stessa directory dell'attività B. Nel caso autonomo, l'assembly deve trovarsi nella GAC o nei percorsi di probe di VS. È quindi solo possibile trascinare e rilasciare le attività nell'area di progettazione flussi di lavoro.

 Le impostazioni della **casella degli strumenti** vengono salvate per impostazione predefinita come opzioni utente, quindi la volta successiva, quando si apre la **casella degli strumenti**, viene visualizzato l'elenco personalizzato delle attività del flusso di lavoro. Un effetto collaterale è che se sono stati aggiunti elementi di dominio specifici alla **casella degli strumenti** tramite la finestra di dialogo **Scegli elementi della casella degli strumenti** , gli elementi continuano a essere visualizzati anche quando si lavora in un'applicazione console del flusso di lavoro. Se non si desidera visualizzarli, eliminarli utilizzando il menu di scelta rapida o deselezionarli tramite la finestra di dialogo **Scegli elementi della casella degli strumenti** come indicato in precedenza.

 Le colonne di questa finestra di dialogo includono le informazioni seguenti:

 Nome elenca i nomi delle attività del flusso di lavoro attualmente registrate nel computer locale.

 Spazio dei nomi Visualizza la gerarchia dello spazio dei nomi della libreria di classi .NET Framework che definisce la struttura dell'attività.

 Nome assembly consente di visualizzare il nome e la versione dell'assembly .NET Framework che contiene l'attività.

 Directory Visualizza il percorso dell'assembly .NET Framework che contiene le attività del flusso di lavoro. Gli assembly si trovano, per impostazione predefinita, nella cartella Global Assembly Cache.

 Per ordinare i componenti elencati, selezionare una delle intestazioni di colonna.