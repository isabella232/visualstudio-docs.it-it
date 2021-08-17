---
title: Proprietà di uno scenario di test di carico
description: Informazioni su come modificare le impostazioni delle proprietà dello scenario di test di carico in Visual Studio a una delle varie proprietà dello scenario di test di carico in questo articolo.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: reference
helpviewer_keywords:
- load tests, properties
- load tests, scenarios
ms.assetid: 4414a638-1fa2-40ad-b1f4-b99f90b62e62
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: 9d27790915c545b7e3cd83538f8e0b41041244bd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122047374"
---
# <a name="load-test-scenario-properties"></a>Proprietà di uno scenario di test di carico

Modificare le impostazioni delle proprietà di uno scenario di test di carico in Visual Studio per soddisfare i requisiti del test di carico. In questo articolo vengono elencate le diverse proprietà di uno scenario di test di carico, suddivise per categoria.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="general"></a>Generale

|Proprietà|Definizione|
|-|----------------|
|**Nome**|Nome dello scenario.|

## <a name="mix"></a>Combinazione

|Proprietà|Definizione|
|-|----------------|
|**Combinazione di browser**|Specifica la combinazione di Web browser per il test di carico. È possibile specificare tipi di Web browser diversi e la relativa distribuzione del carico.<br /><br />Scegliere il pulsante con i puntini di sospensione **(…)** per aprire la finestra di dialogo **Modifica combinazioni di browser** e usare **Aggiungi** e **Rimuovi** per selezionare i tipi di Web browser nel test di carico.<br /><br />Per altre informazioni, vedere [Specificare i tipi di Web browser](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).|
|**Combinazione di reti**|Specifica la combinazione di reti per il test di carico. È possibile specificare quali tipi di rete includere e la relativa distribuzione del carico.<br /><br />Scegliere il pulsante con i puntini di sospensione **(…)** per aprire la finestra di dialogo **Modifica combinazione di reti** e usare **Aggiungi** e **Rimuovi** per selezionare i tipi di rete nel test di carico.<br /><br />Per altre informazioni, vedere [Specificare i tipi di rete virtuale](../test/specify-virtual-network-types-in-a-load-test-scenario.md).|
|**Combinazione di test**|Specifica le prestazioni Web e la combinazione di unit test per il test di carico. È possibile specificare quali test includere e la relativa distribuzione del carico.<br /><br />Scegliere il pulsante con i puntini di sospensione **(…)** per aprire la finestra di dialogo **Modifica combinazione di test** e usare **Aggiungi** e **Rimuovi** per selezionare i test nel test di carico.<br /><br />Per altre informazioni, vedere [Modificare la combinazione di test per uno scenario di test di carico](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).|
|**Tipo di combinazione di test**|Specifica il modello di combinazione di test da usare nel test di carico.<br /><br />Scegliere il pulsante con i puntini di sospensione **(…)** per aprire la finestra di dialogo **Modifica combinazione di test** e usare l'elenco a discesa in **Modello di combinazione di test** per selezionare il modello di combinazione di test da usare nel test di carico.<br /><br />Per altre informazioni, vedere [Modificare i modelli di combinazione di test](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).|

## <a name="options"></a>Opzioni

|Proprietà|Definizione|
|-|----------------|
|**Agenti da utilizzare**|Specifica gli agenti che lo scenario deve usare se il test di carico viene eseguito in remoto. È, ad esempio, possibile specificare un determinato set di agenti, in modo da garantire la coerenza quando si analizzano le tendenze delle prestazioni. Gli agenti possono inoltre essere distribuiti geograficamente, in modo che vi sia affinità tra gli script eseguiti e la posizione dell'agente.<br /><br />Gli agenti devono essere separati da virgole, ad esempio "**Agent1, Agent2, Agent3**". Se si lascia vuota la proprietà, significa che nello scenario dovranno essere utilizzati tutti gli agenti disponibili.<br /><br />Per altre informazioni, vedere [Procedura: Specificare agenti di test da usare](../test/how-to-specify-test-agents-to-use-in-load-test-scenarios.md).|
|**Applica distribuzione a ritardo velocità**|Valore booleano usato per specificare se si vogliono applicare ritardi di distribuzione tipici nel modello di combinazione di test di velocità dell'utente. Questa proprietà si applica solo se la proprietà **Tipo di combinazione di test** è impostata su **In base alla velocità dell'utente**.<br /><br />Per altre informazioni, vedere [Procedura: Applicare la distribuzione al ritardo velocità](../test/how-to-apply-distribution-to-pacing-delay-when-using-a-user-pace-test-mix-model.md)|
|**Commutazione IP**|Valore booleano usato per specificare se viene usata la commutazione IP.<br /><br />La commutazione IP consente a un agente di test di inviare richieste a un server usando un intervallo di indirizzi IP diversi. In questo modo si simulano le chiamate provenienti da computer client diversi. La commutazione IP è importante negli scenari di test di una Web farm con bilanciamento del carico. La maggior parte dei servizi di bilanciamento del carico stabilisce un'affinità tra un client e un determinato server Web usando l'indirizzo IP del client. Se tutte le richieste sembrano provenire da un singolo client, il servizio di bilanciamento del carico non bilancia il carico. Per ottenere un buon bilanciamento del carico nella Web farm, è importante che le richieste provengano da un intervallo di indirizzi IP.<br /><br />La commutazione IP è disponibile solo con l'agente di test.|
|**Numero massimo di iterazioni test**|Valore numerico utilizzato per specificare il numero massimo di test da eseguire nello scenario. Un valore 0 specifica che non viene impostato alcun valore massimo<br /><br />Per altre informazioni, vedere [Configurare iterazioni di test in uno scenario](../test/configure-test-iterations-in-a-load-test-scenario.md).|
|**Percentuale di nuovi utenti**|Valore numerico che specifica la percentuale di utenti nuovi o che visitano per la prima volta lo scenario.<br /><br />Per altre informazioni, vedere [Procedura: Specificare la percentuale di utenti virtuali che usano i dati della cache Web](../test/how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data.md).|
|**Profilo think**|Specifica se nello scenario verrà usata la **Distribuzione normale** o se il profilo interazione utente è **Attivato** o **Disattivato**.<br /><br />Per altre informazioni, vedere [Modificare i tempi interazione utente per simulare i ritardi di interazione umana con i siti Web](../test/edit-think-times-in-load-test-scenarios.md).|

## <a name="timing"></a>Intervallo

|Proprietà|Definizione|
|-|----------------|
|**Ritarda ora di inizio**|Valore che indica di quante ore, minuti e secondi ritardare l'avvio dello scenario dopo l'inizio del test di carico. Se la proprietà **Disabilita durante riscaldamento** viene impostata su **True**, la quantità di tempo di attesa viene applicata dopo il completamento del periodo di riscaldamento.<br /><br />Per altre informazioni, vedere [Configurare ritardi di avvio di uno scenario](../test/configure-scenario-start-delays.md).|
|**Disabilita durante riscaldamento**|Valore booleano usato per specificare se lo scenario deve essere o meno eseguito durante l'intervallo di tempo corrispondente al valore della proprietà **Durata riscaldamento** specificato nell'impostazione di esecuzione del test di carico.<br /><br />Per altre informazioni sulle proprietà delle impostazioni di esecuzione del test di carico, vedere [Proprietà delle impostazioni di esecuzione del test di carico](../test/load-test-run-settings-properties.md).<br /><br />Per altre informazioni, vedere [Configurare ritardi di avvio di uno scenario](../test/configure-scenario-start-delays.md).|
|**Tempo interazione utente tra due iterazioni test**|Valore numerico utilizzato per specificare il tempo di attesa, in secondi, tra iterazioni di test.<br /><br />Per altre informazioni, vedere [Modificare i tempi interazione utente per simulare i ritardi di interazione umana con i siti Web](../test/edit-think-times-in-load-test-scenarios.md).|

## <a name="see-also"></a>Vedi anche

- [Modificare gli scenari di test di carico](../test/edit-load-test-scenarios.md)
