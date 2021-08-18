---
title: Usare Azure Pipelines per i test automatizzati
description: Informazioni su come implementare test automatizzati per l'automazione di compilazione-distribuzione-test usando Azure Pipelines e Team Foundation Server .
ms.custom: SEO-VS-2020
ms.date: 10/19/2018
ms.topic: how-to
helpviewer_keywords:
- automated testing, lab management, test lab
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 23991ee72e6ce108048a644371f33a13e529eaff
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122032978"
---
# <a name="use-azure-test-plans-instead-of-lab-management-for-automated-testing"></a>Usare Azure Test Plans anziché Lab Management per i test automatizzati

Se si usano Microsoft Test Manager e Lab Management per l'esecuzione di test automatizzati o per l'automazione delle operazioni di compilazione/distribuzione/test, questo argomento descrive come ottenere gli stessi risultati usando le funzionalità di [compilazione e versione](/azure/devops/pipelines/index?view=vsts&preserve-view=true) in Azure Pipelines e Team Foundation Server (TFS).

> [!NOTE]
> Microsoft Test Manager è deprecato in Visual Studio 2017 e rimosso in Visual Studio 2019.

## <a name="build-deploy-test-automation"></a>Automazione delle operazioni di compilazione/distribuzione/test

Per l'automazione della compilazione, della distribuzione e del test delle applicazioni, Microsoft Test Manager e Lab Management si basano su una definizione di compilazione XAML. Per raggiungere questo obiettivo, la compilazione XAML si basa su diversi costrutti creati in Microsoft Test Manager, ad esempio un ambiente lab e gruppi e impostazioni di test, e sui vari componenti di infrastruttura, ad esempio un controller di compilazione, agenti di compilazione, un controller di test e agenti di test. È possibile ottenere lo stesso risultato con meno passaggi usando Azure Pipelines o TFS.

| Passaggi | Con la compilazione XAML | In una compilazione o versione |
|-------|----------------------|-----------------|
| Identificare i computer in cui distribuire la compilazione ed eseguire i test. | Creare un ambiente lab standard in Microsoft Test Manager con questi computer. | n/d |
| Identificare i test da eseguire. | Creare un gruppo di test in Microsoft Test Manager, creare i test case e associare l'automazione a ogni test case. Creare le impostazioni di test in Microsoft Test Manager identificando il ruolo dei computer nell'ambiente lab in cui devono essere eseguiti i test. | Se si prevede di gestire l'esecuzione dei test usando i piani di test, creare un gruppo di test automatizzati in Microsoft Test Manager nello stesso modo. In alternativa, è possibile evitare questo passaggio se i test devono essere eseguiti direttamente da file binari di test generati dalle compilazioni. In entrambi i casi non è necessario creare impostazioni di test. |
| Automatizzare la distribuzione e l'esecuzione di test. | Creare una definizione di compilazione XAML tramite LabDefaultTemplate.*.xaml. Specificare la compilazione, i gruppi di test e l'ambiente lab nella definizione di compilazione. | Creare una [pipeline di compilazione o di versione](/azure/devops/pipelines/index?view=vsts&preserve-view=true) con un unico ambiente. Eseguire lo stesso script di distribuzione (dalla definizione di compilazione XAML) tramite l'attività Riga di comando ed eseguire test automatizzati tramite le attività Distribuzione agente di test ed Esegui test funzionali. Come input per queste attività, specificare l'elenco dei computer e le relative credenziali. |

Alcuni dei vantaggi offerti dall'uso di Azure Pipelines o TFS per questo scenario sono:

* Non è necessario alcun controller di compilazione o di test.
* L'agente di test viene installato tramite un'attività compresa nella compilazione o nella versione.
* È facile personalizzare i passaggi di distribuzione. È ora possibile usare più di uno script. È anche possibile usufruire delle numerose attività disponibili nel prodotto e in Visual Studio Marketplace.
* Non è necessario gestire gruppi di test. È possibile eseguire i test direttamente dai file binari.
* Per i test eseguiti all'interno di ogni compilazione o di ogni versione è possibile ottenere un'esperienza di report inline più esaustiva.
* È possibile tenere traccia delle risorse (versione, compilazione, elementi di lavoro, commit) distribuite e sottoposte a test in ogni ambiente.
* È possibile personalizzare ed estendere l'automazione per distribuire con facilità più ambienti di test e persino l'ambiente di produzione.
* È possibile pianificare l'automazione in modo che venga eseguita ogni volta che viene effettuata un'archiviazione o un commit oppure ogni giorno a un'ora specifica.

## <a name="self-service-management-of-scvmm-environments"></a>Gestione self-service di ambienti SCVMM

Il [Test Center in Microsoft Test Manager](/azure/devops/test/mtm/guidance-mtm-usage?view=vsts&preserve-view=true) supporta la possibilità di gestire una raccolta di modelli di ambiente, nonché di eseguire il provisioning di ambienti su richiesta tramite un [server SCVMM](/system-center/vmm/overview?view=sc-vmm-1801&preserve-view=true).

Le funzionalità di provisioning self-service di Centro lab hanno due obiettivi distinti:

* Fornire un modo più semplice per gestire l'infrastruttura. La gestione di modelli di macchine virtuali e di ambienti e la creazione automatica di reti private per isolare i cloni degli ambienti l'uno dall'altro sono esempi di gestione dell'infrastruttura.

* Consentire ai team di utilizzare macchine virtuali in modo più semplice per le attività di test e distribuzione. La possibilità di accedere agli ambienti lab con lo stesso modello di sicurezza dei progetti e l'uso integrato delle macchine virtuali negli scenari di test sono esempi di utilizzo semplificato.

Tuttavia, data l'evoluzione di sistemi più avanzati di gestione del cloud pubblico e privato, come esempio [Microsoft Azure](https://azure.microsoft.com/) e [Microsoft Azure Stack](https://azure.microsoft.com/overview/azure-stack/), per le funzionalità di gestione dell'infrastruttura di TFS 2017 e versioni successive non è prevista un'evoluzione. Viene invece ancora dedicata molta attenzione alla facilità di utilizzo delle risorse gestite tramite questo tipo di infrastrutture cloud.

La tabella seguente offre un riepilogo delle attività più comuni eseguite in Centro lab e del modo in cui è possibile eseguire queste attività tramite SCVMM o Azure (nel caso di attività di gestione dell'infrastruttura) o tramite TFS e Azure DevOps Services (nel caso di attività di test o distribuzione):

| Passaggi | Con Centro lab | In una compilazione o versione |
|-------|-----------------|-----------------------|
| Gestire una libreria di modelli di ambiente. | Creare un ambiente lab. Installare il software necessario nelle macchine virtuali. Eseguire Sysprep e archiviare l'ambiente come modello nella libreria. | Usare direttamente la console di amministrazione di SCVMM per creare e gestire modelli di macchine virtuali o modelli di servizi. Quando si usa Azure, selezionare uno dei [modelli di avvio rapido di Azure](https://azure.microsoft.com/resources/templates/). |
| Creare un ambiente lab. | Selezionare un modello di ambiente nella libreria e distribuirlo. Specificare i parametri necessari per personalizzare le configurazioni delle macchine virtuali. | Usare direttamente la console di amministrazione di SCVMM per creare macchine virtuali o istanze del servizio da modelli. Usare direttamente il portale di Azure per creare risorse. In alternativa, creare una definizione di versione con un ambiente. Usare una o più attività di Azure dall'[estensione SCVMM Integration](https://marketplace.visualstudio.com/items?itemname=ms-vscs-rm.scvmmapp) per creare nuove macchine virtuali. Creare una nuova versione di questa definizione equivale alla creazione di un nuovo ambiente in Centro lab. |
| Connettersi ai computer. | Aprire l'ambiente lab nel Visualizzatore dell'ambiente. | Usare direttamente la console di amministrazione di SCVMM per connettersi alle macchine virtuali. In alternativa, usare l'indirizzo IP o il nome DNS delle macchine virtuali per aprire sessioni di Desktop remoto. |
| Acquisire un checkpoint di un ambiente o ripristinare un checkpoint pulito per un ambiente. | Aprire l'ambiente lab nel Visualizzatore dell'ambiente. Selezionare l'opzione relativa all'acquisizione di un checkpoint o al ripristino di un checkpoint precedente. | Usare direttamente la console di amministrazione di SCVMM per eseguire queste operazioni all'interno di macchine virtuali. Oppure, per eseguire questi passaggi nell'ambito di un'automazione più ampia, includere le attività di checkpoint dell'[estensione SCVMM Integration](https://marketplace.visualstudio.com/items?itemname=ms-vscs-rm.scvmmapp) in una definizione di versione come parte dell'ambiente. |

## <a name="create-network-isolated-environments"></a>Creare ambienti di isolamento rete

Un ambiente lab con isolamento rete è un gruppo di macchine virtuali SCVMM che possono essere clonate in sicurezza senza creare conflitti di rete. Questa attività è stata eseguita in MTM in base a una serie di istruzioni che usavano un set di schede di interfaccia di rete per configurare le macchine virtuali in una rete privata e un altro set di schede di interfaccia di rete per configurare le macchine virtuali in una rete pubblica.

Tuttavia è possibile usare Azure Pipelines e Team Foundation Server, in combinazione con l'attività di compilazione e distribuzione di SCVMM, per gestire gli ambienti SCVMM, eseguire il provisioning di reti virtuali isolate e implementare scenari di compilazione-distribuzione-test. Ad esempio, è possibile usare l'attività per:

* Creare, ripristinare ed eliminare i checkpoint
* Creare nuove macchine virtuali con un modello
* Avviare e arrestare le macchine virtuali
* Eseguire script di PowerShell personalizzati per SCVMM

Per altre informazioni, vedere [Create a virtual network isolated environment for build-deploy-test scenarios](/azure/devops/pipelines/targets/create-virtual-network?view=vsts&preserve-view=true) (Creare un ambiente con isolamento di rete virtuale per scenari di compilazione-distribuzione-test).
