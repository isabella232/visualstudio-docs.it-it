---
title: Aggiornare i progetti alla versione corrente degli strumenti di Azure
description: Informazioni su come aggiornare un progetto Azure in Visual Studio alla versione attuale degli strumenti di Azure
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/18/2016
ms.author: ghogen
ms.openlocfilehash: 1bf1fc53eb6444772beb5566ef4b9141af8176b2
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633000"
---
# <a name="how-to-upgrade-projects-to-the-current-version-of-the-azure-tools-for-visual-studio"></a>Come aggiornare i progetti alla versione attuale degli strumenti di Microsoft Azure per Visual Studio
## <a name="overview"></a>Panoramica
Dopo avere installato la versione corrente degli strumenti di Azure (o successiva alla versione 1.6), eventuali progetti creati mediante una versione precedente alla 1.6 (novembre 2011) verranno automaticamente aggiornati all'apertura. Se sono stati creati progetti con la versione 1.6 (novembre 2011) di questi strumenti e la versione è ancora installata, è possibile aprire i progetti nella versione precedente e decidere in seguito se aggiornarli.

## <a name="how-your-project-changes-when-you-upgrade-it"></a>Modifiche apportate al progetto durante l'aggiornamento
Se un progetto viene aggiornato automaticamente o si specifica di volerlo aggiornare, verrà modificato in modo da funzionare con le versioni correnti di determinati assembly e verranno anche modificate alcune proprietà, come descritto in questa sezione. Se il progetto richiede altre modifiche per la compatibilità con la versione più recente degli strumenti, è necessario apportarle manualmente.

* Il file web.config per i ruoli Web e il file app.config per i ruoli di lavoro vengono aggiornati in modo da fare riferimento alla versione più recente di Microsoft.WindowsAzure.Diagnostics.DiagnosticMonitorTraceListener.dll.
* Gli assembly Microsoft.WindowsAzure.StorageClient.dll, Microsoft.WindowsAzure.Diagnostics.dll e Microsoft.WindowsAzure.ServiceRuntime.dll vengono aggiornati alle nuove versioni.
* I profili di pubblicazione archiviati nel file di progetto Azure (con estensione ccproj) vengono spostati in un file separato con estensione azurePubxml nella sottodirectory **Publish** .
* Alcune proprietà del profilo di pubblicazione vengono aggiornate per supportare funzionalità nuove e modificate. **AllowUpgrade** viene sostituita da **DeploymentReplacementMethod** perché è possibile aggiornare un servizio cloud distribuito in modo simultaneo o incrementale.
* Viene aggiunta la proprietà **UseIISExpressByDefault** è impostata su false in modo che il server Web usato per il debug non passi automaticamente da Internet Information Services (IIS) a IIS Express. IIS Express è il server Web predefinito dei progetti creati con le versioni più recenti degli strumenti.
* Se Azure Caching è ospitato in uno o più ruoli del progetto, alcune proprietà nella configurazione del servizio (file con estensione cscfg) e nella definizione del servizio (file con estensione csdef) vengono modificate al momento dell'aggiornamento di un progetto. Se il progetto usa il pacchetto NuGet di Azure Caching, verrà aggiornato alla versione più recente del pacchetto. È necessario aprire il file web.config e verificare che la configurazione client sia stata gestita correttamente durante il processo di aggiornamento. Se si aggiungono riferimenti agli assembly del client Azure Caching senza usare il pacchetto NuGet, questi assembly non verranno aggiornati. È necessario aggiornare manualmente i riferimenti alle nuove versioni.

> [!IMPORTANT]
> Per i progetti in F#, è necessario aggiornare manualmente i riferimenti agli assembly di Azure in modo che facciano riferimento alle versioni più recenti.
>
>

### <a name="how-to-upgrade-an-azure-project-to-the-current-release"></a>Come aggiornare un progetto Azure alla versione corrente
1. Installare la versione corrente degli strumenti di Azure nell'installazione di Visual Studio da usare per il progetto aggiornato, quindi aprire il progetto da aggiornare. Se il progetto è stato creato con una versione degli strumenti di Azure precedente alla 1.6 (novembre 2011), verrà automaticamente aggiornato alla versione corrente. Se il progetto è stato creato con la versione di novembre 2011 e tale versione è ancora installata, verrà aperto in quest'ultima.
2. In Esplora soluzioni aprire il menu di scelta rapida per il nodo del progetto, scegliere **Proprietà** e quindi la scheda **Applicazione** della finestra di dialogo visualizzata.

    Nella scheda **Applicazione** viene indicata la versione degli strumenti associata al progetto. Se viene visualizzata la versione corrente degli strumenti di Azure, il progetto è già stato aggiornato. Se è stata installata una versione più recente degli strumenti rispetto a quella indicata nella scheda, viene visualizzato il pulsante **Aggiorna**.
3. Scegliere il pulsante **Aggiorna** per aggiornare un progetto alla versione corrente degli strumenti.
4. Creare il progetto, quindi trovare eventuali errori risultanti dalle modifiche API. Per informazioni su come modificare il codice per la nuova versione, vedere la documentazione per l'API specifica.
