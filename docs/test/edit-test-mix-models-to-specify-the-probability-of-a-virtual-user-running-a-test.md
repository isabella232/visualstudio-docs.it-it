---
title: Modifica di modelli di combinazione di test
description: Informazioni sul modo in cui il modello di combinazione di test consente di avere diversi flussi di lavoro, che si avvicinano più da vicino al modo in cui gli utenti finali interagiscono con le applicazioni.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, scenarios
- load tests, virtual users
ms.assetid: e3b7d952-9012-400a-8131-3444390a6066
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: 6bf9001d07a56d521283bcd5e9c6b7774437df48
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122140011"
---
# <a name="edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test"></a>Modificare i modelli di combinazione di test per specificare la probabilità che un utente virtuale esegua un test

Il *modello di combinazione di test* specifica la probabilità che un utente virtuale esegua un determinato test in uno scenario di test di carico. In questo modo, è possibile simulare un carico in maniera più realistica. Anziché avere un unico flusso di lavoro nelle applicazioni, è possibile avere più flussi di lavoro in modo da ottenere una migliore approssimazione della modalità di interazione degli utenti finali con le applicazioni.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="test-mix-model-options"></a>Opzioni del modello di combinazione di test

È possibile specificare una delle seguenti opzioni relative al modello di combinazione di test per lo scenario di test di carico:

- **In base al numero totale di test:** determina quale test delle prestazioni Web o unit test viene eseguito quando un utente virtuale inizia un'iterazione di test. Alla fine del test di carico, il numero di volte in cui un determinato test è stato eseguito corrisponde alla distribuzione di test assegnata. Usare questo modello di combinazione di test quando si basa la combinazione di test sulle percentuali di transazioni in un log IIS o nei dati di produzione.

- **In base al numero di utenti virtuali:** Determina la percentuale di utenti virtuali che eseguiranno determinate prestazioni Web o unit test. Durante il test di carico, il numero di utenti che stanno eseguendo un determinato test corrisponde alla distribuzione assegnata. Usare questo modello di combinazione di test quando si basa la combinazione di test sulla percentuale di utenti che sta eseguendo un determinato test.

- **In base al ritmo dell'utente:** Nel corso del test di carico, ogni test delle prestazioni Web o unit test viene eseguito un numero specificato di volte per ogni utente, all'ora. Usare questo modello di combinazione di test quando si vuole che gli utenti virtuali eseguano il test a un ritmo determinato durante il test di carico.

- **In base all'ordine sequenziale:** Ogni utente virtuale esegue le prestazioni Web o gli unit test nell'ordine in cui i test sono definiti nello scenario. L'utente virtuale continua a eseguire ciclicamente i test in questo ordine fino al completamento del test di carico.

## <a name="tasks"></a>Attività

|Attività|Argomenti correlati|
|-|-----------------------|
|**Specifica della combinazione di test per il test di carico:** quando si crea un test di carico è possibile specificarne le impostazioni nella **Creazione guidata test di carico**. La **Creazione guidata test di carico** consente anche di scegliere test Web e unit test esistenti da aggiungere allo scenario iniziale. Dopo aver aggiunto test allo scenario, si specifica la combinazione di test per lo scenario.<br /><br /> È possibile usare le opzioni di modellazione del carico per prevedere più accuratamente l'uso reale di un sito Web o un'applicazione sottoposti a test di carico. Tale procedura è importante perché un test di carico che non si basa su un modello di carico accurato può generare risultati fuorvianti.|-   [Emulazione dell'uso reale previsto di un'applicazione o un sito Web](../test/emulate-real-world-usage-of-a-web-site-in-a-load-test-using-test-mix-models.md)|
|**Modificare il modello di combinazione di test:** È possibile modificare uno scenario di test di carico per usare uno dei modelli di combinazione di test **usando** l'Editor test di carico .||
|**Configurazione del ritardo velocità per un modello di combinazione di test basato sulla velocità utente:** se lo scenario del test di carico è configurato in modo da usare il **modello di combinazione di test in base alla velocità dell'utente**, è possibile specificare la modalità di configurazione del ritardo velocità della distribuzione.|-   [Procedura: Applicare la distribuzione al ritardo di velocità quando si usa un modello di combinazione di test del ritmo utente](../test/how-to-apply-distribution-to-pacing-delay-when-using-a-user-pace-test-mix-model.md)|

## <a name="change-the-test-mix-model-in-a-scenario"></a>Modificare il modello di combinazione di test in uno scenario

Dopo aver creato il test di carico mediante la **Creazione guidata test di carico**, è possibile usare l'**Editor test di carico** per modificare le proprietà degli scenari in modo da soddisfare le necessità e gli obiettivi di test specifici.

> [!NOTE]
> Per un elenco completo delle proprietà delle impostazioni di carico e delle relative descrizioni, vedere [Proprietà dello scenario di test di carico](../test/load-test-scenario-properties.md).

Usando il **Editor test di carico**, è possibile modificare il modello di combinazione di test in uno scenario di test di carico modificando la proprietà **Tipo combinazione** di test nella **finestra** Proprietà.

### <a name="to-change-the-test-mix-model"></a>Per modificare il modello di combinazione di test

1. Aprire un test di carico.

     Viene visualizzato l'**Editor test di carico**. Verrà visualizzata la struttura ad albero del test di carico.

2. Nella cartella *Scenari* dell'albero del test di carico scegliere il nodo dello scenario per il quale si vuole specificare il numero massimo di iterazioni test.

3. Scegliere **Finestra Proprietà** dal menu **Visualizza**.

     Verranno visualizzate le categorie e le proprietà dello scenario.

4. Nella proprietà **Tipo di combinazione di test** scegliere il pulsante con i puntini di sospensione (**…**).

     Verrà visualizzata la finestra di dialogo **Modifica combinazione di test**.

5. Scegliere l'elenco a discesa in **Modello di combinazione di test** e selezionare il modello di combinazione di test che si vuole usare per lo scenario.

6. (Facoltativo) Modificare la combinazione di test usando i pulsanti **Aggiungi**, **Rimuovi** e **Distribuisci** e i dispositivi di scorrimento di distribuzione. Per altre informazioni, vedere [Modificare la combinazione di test per specificare quali test includere in uno scenario di test di carico](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).

7. (Facoltativo) Specificare un test delle prestazioni Web e uno unit test da inizializzare o terminare usando le caselle di controllo e selezionando i test desiderati. Per altre informazioni, vedere [Emulazione dell'uso reale previsto di un'applicazione o un sito Web](../test/emulate-real-world-usage-of-a-web-site-in-a-load-test-using-test-mix-models.md).

8. Scegliere **OK**.

     Nella finestra **Proprietà** viene visualizzato il nuovo modello di combinazione di test per la proprietà **Tipo di combinazione di test**.

9. Dopo aver modificato la proprietà, scegliere **Salva** dal menu **File**. Sarà quindi possibile eseguire il test di carico usando il nuovo valore dell'opzione **Tipo di combinazione di test**.

## <a name="see-also"></a>Vedi anche

- [Modificare gli scenari di test di carico](../test/edit-load-test-scenarios.md)
- [Proprietà di uno scenario di test di carico](../test/load-test-scenario-properties.md)
