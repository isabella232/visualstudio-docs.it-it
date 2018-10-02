---
title: Scheda System. Activities, Scegli elementi della finestra di dialogo casella | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES_COMPONENTS
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES COMPONENTS
ms.assetid: cef390cd-eeda-42e6-9d2e-18c8325a4f06
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 9c769058aaf86796780645c77b5bc2173db52048
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47519784"
---
# <a name="systemactivities-tab-choose-toolbox-items-dialog-box"></a>Scheda System.Activities, finestra di dialogo Scegli elementi della Casella degli strumenti
Questa scheda della finestra di **Scegli elementi della casella degli strumenti** finestra di dialogo Visualizza un elenco di [!INCLUDE[wf](../includes/wf-md.md)] attività, modelli e gli elementi disponibili all'utente. Per visualizzare l'elenco, selezionare **Scegli elementi della casella degli strumenti** dal **Tools** dal menu o facendo clic con il **della casella degli strumenti** e selezionando **Scegli elementi**per visualizzare la **Scegli elementi della casella degli strumenti** finestra di dialogo e quindi selezionare il **System. Activities** scheda. Per impostazione predefinita, l'elenco contiene le attività del flusso di lavoro dall'assembly System. Activities, System.ServiceModel.Activities e System.Activities.Core.Presentation; Tuttavia, solo fornito dal sistema nelle attività illustrate e le attività aggiunte mediante altri assembly visualizzati nella **casella degli strumenti** vengono controllati per impostazione predefinita. Aggiunti di recente le attività vengono controllate automaticamente e vengono visualizzati nei **casella degli strumenti** quando fa clic su **OK** nella finestra di dialogo. Inoltre, questi elementi vengono visualizzati nei **casella degli strumenti** sotto una nuova categoria che corrisponde allo spazio dei nomi in cui risiede l'attività di elemento o il modello.  
  
> [!WARNING]
>  Se si prova ad aggiungere un assembly che non contiene attività del flusso di lavoro, viene visualizzata una finestra di errore in cui si segnala che l'assembly non contiene attività.  
  
 Questa finestra di dialogo è indipendente dal progetto e pertanto il **System. Activities** scheda continua a presentarsi in XAML autonomo o un tipo di progetto senza flusso di lavoro.  
  
 Il filtro viene applicato in ogni scheda. Ciò significa che non è possibile aggiungere le attività del flusso di lavoro tramite il **componente .NET** scheda. Dovranno essere aggiunti tramite il **System. Activities** scheda stessa.  
  
 È possibile deselezionare tutti gli elementi non si desidera visualizzare nel **casella degli strumenti** dalla finestra di dialogo tab oppure in alternativa, è possibile farlo usando la **eliminare** opzione nel menu di scelta rapida nel **della casella degli strumenti** e deprovisioning che fanno riferimento a un assembly non rimuove l'elemento dal **casella degli strumenti**.  
  
 Quando si crea un'istanza dell'attività trascinandola e rilasciandola nella finestra di progettazione, si aggiunge automaticamente all'elenco degli assembly di riferimento l'assembly che contiene l'elemento. Se inoltre l'attività fa riferimento a un assembly C, C non viene aggiunto all'elenco di assembly di riferimento. Assembly C deve trovarsi nella Global Assembly Cache o nella stessa directory dell'attività B. Nel caso autonomo, l'assembly deve trovarsi nella GAC o nei percorsi di Probe di VS. È quindi solo possibile trascinare e rilasciare le attività nell'area di progettazione flussi di lavoro.  
  
 **Casella degli strumenti** impostazioni vengono salvate per impostazione predefinita come opzioni utente, in modo che l'ora successiva, quando si apre il **della casella degli strumenti**, viene visualizzato l'elenco personalizzato delle attività flusso di lavoro. Un effetto di questo oggetto consiste nel fatto che se sono stati aggiunti elementi di dominio specifico per il **casella degli strumenti** tramite il **Scegli elementi della casella degli strumenti** finestra di dialogo, comunque continuare a visualizzare questi elementi quando si lavora in un Flusso di lavoro e applicazione Console. Se non si desidera visualizzarli, quindi eliminarli utilizzando il menu di scelta rapida oppure deselezionarli il **Scegli elementi della casella degli strumenti** finestra di dialogo come indicato in precedenza.  
  
 Le colonne di questa finestra di dialogo includono le informazioni seguenti:  
  
 Nome  
 Elenca i nomi delle attività del flusso di lavoro attualmente registrate nel computer locale.  
  
 Spazio dei nomi  
 Visualizza la gerarchia dello spazio dei nomi della libreria di classi .NET Framework che definisce la struttura dell'attività.  
  
 Nome assembly  
 Visualizza il nome e la versione dell'assembly .NET Framework che include l'attività.  
  
 Directory  
 Visualizza il percorso dell'assembly .NET Framework che include le attività del flusso di lavoro. Gli assembly si trovano, per impostazione predefinita, nella cartella Global Assembly Cache.  
  
 Per ordinare i componenti elencati, selezionare una delle intestazioni di colonna.