---
title: Configurazione di iterazioni di test per il test di carico
description: Informazioni su come configurare le impostazioni di iterazione test, per configurare il numero massimo di iterazioni nello scenario e il tempo di pausa tra di esse.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, scenarios, iterations
- load test, iterations
- load tests, scenarios
ms.assetid: ac480fb7-f4f7-47dc-9ae5-98be3aca4fba
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: 0b6a32d49471b0adc3480bcb53455740204e1059b82bcb056f474b6df47c4cbc
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121395389"
---
# <a name="configure-test-iterations-in-a-load-test-scenario"></a>Configurare le iterazioni di test in uno scenario di test di carico

Per configurare le impostazioni delle iterazioni di test, modificare uno scenario di test di carico usando l'Editor test di carico e la finestra **Proprietà**. Per impostazione predefinita, un scenario di test di carico viene configurato senza specificare il numero massimo di iterazioni. Si ha l'opzione di configurare il numero massimo di iterazioni nello scenario e l'intervallo tra un'iterazione e l'altra.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="specify-the-maximum-test-iterations-for-a-scenario"></a>Specificare il numero massimo di iterazioni di test per uno scenario

È possibile specificare il numero massimo di volte che si vuole eseguire i test per uno scenario usando l'Editor test di carico per modificare la proprietà **Numero massimo di iterazioni test** nella finestra **Proprietà**.

La proprietà **Numero massimo di iterazioni test** controlla il numero massimo di iterazioni di test da eseguire per lo scenario. Analogamente alla proprietà **Iterazioni test** nelle impostazioni di esecuzione del test di carico, si tratta del numero massimo per tutti gli utenti in tutti gli agenti, non di un'impostazione per utente.

> [!NOTE]
> Per un elenco completo delle proprietà dello scenario di test di carico e delle relative descrizioni, vedere [Proprietà dello scenario di test di carico.](../test/load-test-scenario-properties.md)

Per una combinazione di test sequenziale, un'iterazione è un passaggio in tutti i test nella combinazione. Per tutte le altre combinazioni di test, ogni esecuzione del test rappresenta un'iterazione. Per altre informazioni, vedere [Informazioni sul controllo combinazione](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).

Se il test di carico è basato sulla durata e tale durata scade prima del completamento del conteggio delle iterazioni, il test si arresterà. Se il test è basato sull'iterazione e le iterazioni di test vengono soddisfatte prima di quelle dello scenario, il test si arresterà. La durata viene configurata usando la proprietà **Durata esecuzione** nella finestra **Proprietà** associata a un'impostazione di esecuzione in un test di carico.

Quando viene soddisfatto il conteggio delle iterazioni dello scenario, l'esecuzione dello scenario verrà arrestata ma qualsiasi altro scenario attivo continuerà a essere eseguito.

> [!NOTE]
> Una proprietà correlata è la proprietà **Unique** in un'origine dati di test Web, che si sposta in sequenza tra i dati, riga per riga, ma una sola volta per ogni record. Per altre informazioni, vedere [Aggiungere un'origine dati a un test prestazioni Web](../test/add-a-data-source-to-a-web-performance-test.md).

La proprietà **Numero massimo di iterazioni test** è utile in diverse situazioni. Alcuni tester che si occupano di test di carico preferiscono eseguire test basati sulle iterazioni, mentre altri preferiscono i test basati sulla durata.

![Specifica delle iterazioni di test in uno scenario](../test/media/loadtest_prop.png)

### <a name="to-specify-the-maximum-test-iterations"></a>Per specificare il numero massimo di iterazioni di test

1. Aprire un test di carico.

2. Verrà visualizzato l'Editor test di carico. Verrà visualizzata la struttura ad albero del test di carico.

3. Nella cartella **Scenari** dell'albero del test di carico scegliere il nodo dello scenario per il quale si vuole specificare il numero massimo di iterazioni di test.

4. Scegliere **Finestra Proprietà** dal menu **Visualizza**.

     Le categorie e le proprietà dello scenario vengono visualizzate nella finestra **Proprietà**.

5. Nella casella di testo per la proprietà **Numero massimo di iterazioni test** digitare un valore che indica il numero massimo di test da eseguire per lo scenario quando viene eseguito il test di carico.

    > [!NOTE]
    > L'uso di un valore 0 per la proprietà **Numero massimo di iterazioni test** consente di specificare che non è previsto un numero massimo di interazioni.

6. Terminata la modifica della proprietà, scegliere **Salva** dal menu **File**. Sarà quindi possibile eseguire il test di carico usando il nuovo valore dell'opzione **Numero massimo di iterazioni test**.

## <a name="specify-think-times-between-test-iterations-for-a-scenario"></a>Specificare il tempo di interazione utente tra iterazioni di test per uno scenario

La proprietà **Tempo interazione utente tra due iterazioni test** viene impostata usando la finestra **Proprietà** durante la modifica delle proprietà dello scenario di test di carico nell'Editor test di carico.

La proprietà **Tempo interazione utente tra due iterazioni test** viene usata per specificare il numero di secondi di attesa prima di avviare un'iterazione test.

> [!NOTE]
> Per un elenco completo delle proprietà dello scenario di test di carico e delle relative descrizioni, vedere [Proprietà dello scenario di test di carico.](../test/load-test-scenario-properties.md)

### <a name="to-specify-the-think-time-between-test-iterations"></a>Per specificare il tempo di interazione utente tra iterazioni di test

1. Aprire un test di carico.

     Viene visualizzato l'**Editor test di carico**. Verrà visualizzata la struttura ad albero del test di carico.

2. Nella cartella **Scenari** dell'albero del test di carico scegliere il nodo dello scenario per il quale si vuole specificare il tempo di interazione utente.

3. Scegliere **Finestra Proprietà** dal menu **Visualizza**.

     Le categorie e le proprietà dello scenario vengono visualizzate nella finestra **Proprietà**.

4. Per il valore della proprietà **Tempo interazione utente tra due iterazioni test**, immettere un numero che rappresenta il numero di secondi di attesa prima di avviare l'iterazione test successiva.

5. Terminata la modifica della proprietà, scegliere **Salva** dal menu **File**. Sarà quindi possibile eseguire il test di carico usando il nuovo valore dell'opzione **Tempo iterazione utente tra due iterazioni test**.

## <a name="see-also"></a>Vedi anche

- [Modificare gli scenari di test di carico](../test/edit-load-test-scenarios.md)
- [Configurare agenti di test e test controller per i test di carico](../test/configure-test-agents-and-controllers-for-load-tests.md)
- [Proprietà di uno scenario di test di carico](../test/load-test-scenario-properties.md)
- [Modificare i tempi interazione utente per simulare i ritardi di interazione umana con i siti Web](../test/edit-think-times-in-load-test-scenarios.md)
