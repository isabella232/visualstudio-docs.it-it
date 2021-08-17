---
title: Configurare agenti di test/controller di test per i test di carico
description: Informazioni su Visual Studio possibile creare un carico simulato usando macchine virtuali o fisiche per generare un carico maggiore di quello che un singolo computer può generare da solo.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, test agents and controllers
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: 1f789b8e5816b072b815cb59bae6c1cd377e0d055db53b8a663f6b4d5c2f7266
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121425049"
---
# <a name="overview-of-test-agents-and-test-controllers-for-running-load-tests"></a>Panoramica di agenti di test e test controller per i test di carico

Visual Studio è in grado di generare un carico simulato per l'app usando macchine virtuali o fisiche. Questi computer devono essere configurati in modo da avere un solo controller di test e uno o più agenti di test. È possibile usare il controller di test e gli agenti di test per generare un carico maggiore rispetto a quello che può essere generato da un singolo computer.

> [!NOTE]
> È anche possibile usare il test di carico basato su cloud per specificare le macchine virtuali che generano il caricamento di molti utenti che accedono al sito Web contemporaneamente. Tuttavia, l'uso test controller/installazione dell'agente di test nelle macchine virtuali ospitate nel cloud non è supportato. Altre informazioni sui test di carico basati su cloud sono disponibili nell'articolo relativo all'[esecuzione di test di carico con Azure Test Plans](/azure/devops/test/load-test/get-started-simple-cloud-load-test?view=vsts&preserve-view=true).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="load-simulation-architecture"></a>Architettura di simulazione di carico

L'architettura di simulazione di carico è costituita da un client di Visual Studio, un controller di test e agenti di test.

- Il client viene usato per sviluppare i test, eseguire i test e visualizzare i risultati dei test.

- Il controller di test viene usato per gestire gli agenti di test e raccogliere i risultati dei test.

- Gli agenti di test vengono usati per eseguire i test e raccogliere i dati, comprese le informazioni di sistema e i dati di profilatura di ASP.NET definiti nell'impostazione di test.

Questa architettura offre i vantaggi seguenti:

- La possibilità di scalare in orizzontale la generazione del carico aggiungendo altri agenti di test a un controller di test.

- La flessibilità di installare il software del client, del controller di test e degli agenti di test nello stesso computer o in computer diversi. Esempio:

   **Configurazione locale:**

  - Computer1: Visual Studio, controller, agente.

    ![Computer locale che utilizza controller e agente](./media/load-test-configa.png)

    **Configurazione remota tipica:**

  - Computer1 e 2: Visual Studio (più tester possono usare lo stesso controller).

  - Computer3: controller (in cui possono essere anche presenti agenti installati).

  - Computer4-n: agente o agenti tutti associati al controller in Computer3.

    ![Computer remoti che utilizzano controller e agenti](./media/load-test-configb.png)

Anche se un controller di test gestisce in genere diversi agenti di test, un agente può essere associato solo a un unico controller. Ogni agente di test può essere condiviso da un team di sviluppatori. Questa architettura consente di aumentare il numero di agenti di test, generando così carichi maggiori.

## <a name="test-agent-and-test-controller-interaction"></a>Interazione tra controller di test e agenti di test

Il controller di test gestisce un set di agenti di test per eseguire i test. Il controller di test comunica con gli agenti di test per avviare e interrompere i test, per registrare lo stato dell'agente e per raccogliere i risultati dei test.

### <a name="test-controller"></a>Controller di test

Il controller di test fornisce un'architettura generale per l'esecuzione di test e include funzionalità speciali per l'esecuzione di test di carico. Il controller di test invia il test di carico a tutti gli agenti di test e attende fino a quando tutti gli agenti di test non hanno inizializzato il test. Quando tutti gli agenti di test sono pronti, il controller di test invia un messaggio agli agenti di test per avviare il test.

### <a name="test-agent"></a>Agente di test

L'agente di test viene eseguito come servizio in attesa delle richieste del controller di test per avviare un nuovo test. Quando l'agente di test riceve una richiesta, il relativo servizio avvia un processo su cui eseguire i test. Ogni agente di test esegue lo stesso test di carico.

Agli agenti di test viene assegnato un peso dall'amministratore e il carico viene distribuito in base al peso di un agente di test. Ad esempio, se l'agente di test 1 ha un peso pari a 30 e l'agente di test 2 ha un peso di 70 e il carico è impostato su 1000 utenti, l'agente di test 1 simula 300 utenti virtuali mentre l'agente di test 2 ne simula 700. Vedere [Gestire i test controller e gli agenti di test con Visual Studio](../test/manage-test-controllers-and-test-agents.md).

L'agente di test accetta come input un set di test e un set di parametri di simulazione. Un concetto essenziale riguarda l'indipendenza dei test dal computer in cui vengono eseguiti.

## <a name="test-controller-and-test-agent-connection-points"></a>Punti di connessione tra test controller e agenti di test

La figura seguente mostra i punti di connessione tra il controller di test, l'agente di test e il client. Sono inoltre illustrate le porte che vengono usate per le connessioni in ingresso e in uscita e le restrizioni di sicurezza applicate a tali porte.

![Porte e sicurezza del controller e dell'agente di test](./media/test-controller-agent-firewall.png)

Per altre informazioni, vedere [Configurare le porte per test controller e agenti di test](../test/configure-ports-for-test-controllers-and-test-agents.md).

## <a name="test-controller-and-agent-installation-information"></a>Informazioni sull'installazione di test controller e agenti di test

Per informazioni importanti sui requisiti hardware e software per i test controller e gli agenti di test, sulle procedure per l'installazione e sulla configurazione dell'ambiente per ottenere prestazioni ottimali, vedere [Installare e configurare agenti di test](../test/lab-management/install-configure-test-agents.md).

## <a name="use-the-test-controller-and-test-agent-with-unit-tests"></a>Uso del test controller e dell'agente di test con unit test

Dopo aver installato un controller di test e uno o più agenti, è possibile specificare se usare un'esecuzione remota con il controller di test nell'impostazione di test per i test di carico. Inoltre, è possibile specificare i dati e gli adattatori diagnostici da usare con il ruolo associato agli agenti nell'impostazione di test.

## <a name="see-also"></a>Vedi anche

- [Installare e configurare agenti di test](../test/lab-management/install-configure-test-agents.md)
