---
title: Come aggiornare i progetti alla versione corrente degli strumenti di Azure | Microsoft Docs
description: Informazioni su come aggiornare un progetto Azure in Visual Studio alla versione corrente degli strumenti di Azure
author: ghogen
manager: douge
assetId: 1d64070a-078d-468a-87f4-e6715de6475f
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/18/2016
ms.author: ghogen
ms.openlocfilehash: c5fb70f2dd09338dd2e2f6b01cb60bf2be0cdbdd
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002910"
---
# <a name="how-to-upgrade-projects-to-the-current-version-of-the-azure-tools-for-visual-studio"></a>Come aggiornare i progetti alla versione corrente di Strumenti di Azure per Visual Studio
## <a name="overview"></a>Panoramica
Dopo aver installato la versione corrente degli strumenti di Azure (o una versione precedente che è successiva alla versione 1.6), eventuali progetti creati usando gli strumenti di Azure una versione precedente alla 1.6 (novembre 2011) verranno aggiornate automaticamente non appena vengono aperti. Se sono stati creati progetti con la versione 1.6 (novembre 2011) di questi strumenti e si dispone ancora di tale versione installata, è possibile aprire i progetti nella versione precedente e decidere in seguito se aggiornarli.

## <a name="how-your-project-changes-when-you-upgrade-it"></a>Modifiche ai progetti in caso di aggiornamento
Se un progetto viene aggiornato automaticamente oppure specificare che si desidera eseguire l'aggiornamento, il progetto viene modificato per funzionare con le versioni correnti di determinati assembly e alcune proprietà vengono modificate anche come descritto in questa sezione. Se il progetto richiede altre modifiche per renderle compatibili con la versione più recente degli strumenti, è necessario apportare queste modifiche manualmente.

* Il file Web. config per i ruoli web e il file app. config per i ruoli di lavoro vengono aggiornati per fare riferimento alla versione più recente di diagnosticmonitoirtracelistener.
* Gli assembly storageclient Microsoft.WindowsAzure.Diagnostics.dll e Microsoft.WindowsAzure.ServiceRuntime.dll vengono aggiornati alle nuove versioni.
* I profili di pubblicazione sono stati archiviati nel file di progetto di Azure (. ccproj) vengono spostati in un file separato con estensione azurepubxml, il **pubblica** sottodirectory.
* Alcune proprietà nel profilo di pubblicazione vengono aggiornate per supportare le funzionalità nuove e modificate. **AllowUpgrade** viene sostituito dal **DeploymentReplacementMethod** perché è possibile aggiornare un servizio cloud distribuito in modo simultaneo o incrementale.
* La proprietà **UseIISExpressByDefault** viene aggiunta e impostata su false, in modo che il server web che viene usato per eseguire il debug non passi automaticamente da Internet Information Services (IIS) a IIS Express. IIS Express è il server web predefinito per i progetti creati con le versioni più recenti degli strumenti.
* Se la memorizzazione nella cache di Azure è ospitata in uno o più dei ruoli del progetto, alcune proprietà nella configurazione del servizio (file con estensione cscfg) e nella definizione del servizio (file con estensione csdef) vengono modificati quando si aggiorna un progetto. Se il progetto usa il pacchetto NuGet di memorizzazione nella cache di Azure, il progetto viene aggiornato alla versione più recente del pacchetto. È necessario aprire il file Web. config e verificare che la configurazione del client è stata gestita correttamente durante il processo di aggiornamento. Se si aggiungono riferimenti agli assembly client Caching di Azure senza usare il pacchetto NuGet, questi assembly non verrà aggiornati; è necessario aggiornare manualmente questi riferimenti alle nuove versioni.

> [!IMPORTANT]
> Per F# progetti, è necessario aggiornare manualmente i riferimenti agli assembly di Azure in modo che facciano riferimento le versioni più recenti degli assembly.
> 
> 

### <a name="how-to-upgrade-an-azure-project-to-the-current-release"></a>Come aggiornare un progetto Azure alla versione corrente
1. Installare la versione corrente degli strumenti di Azure nell'installazione di Visual Studio che si desidera utilizzare per il progetto aggiornato e quindi aprire il progetto che si desidera eseguire l'aggiornamento. Se il progetto è stato creato con una versione precedente alla 1.6 (novembre 2011), il progetto viene aggiornato automaticamente alla versione corrente. Se è stato creato il progetto con di novembre 2011 release e quella versione è ancora installata, il progetto viene aperto in tale versione.
2. In Esplora soluzioni aprire il menu di scelta rapida per il nodo del progetto, scegliere **proprietà**, quindi scegliere il **applicazione** scheda della finestra di dialogo visualizzata.
   
    Il **applicazione** scheda Mostra la versione degli strumenti che è associato al progetto. Se viene visualizzata la versione corrente degli strumenti di Azure, il progetto è già stato aggiornato. Se è stata installata una versione più recente degli strumenti rispetto a quella indicata nella scheda, un **aggiornare** viene visualizzato il pulsante.
3. Scegliere il **aggiornare** pulsante per aggiornare un progetto alla versione corrente degli strumenti.
4. Compilare il progetto e quindi risolvere gli eventuali errori risultanti dalle modifiche API. Per informazioni su come modificare il codice per la nuova versione, vedere la documentazione per l'API specifica.

