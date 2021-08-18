---
title: Configurare ritardi di avvio di uno scenario per test di carico
description: Informazioni su come specificare un ritardo prima dell'avvio di uno scenario in un test di carico usando il Editor test di carico e il Finestra Proprietà.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, scenarios, start delays
ms.assetid: 2f634fba-8dfa-4c7a-a8b9-be867b78d16a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: c918d2479c27b068fd155ddaea78241019f22ca6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122092683"
---
# <a name="configure-scenario-start-delays-in-load-tests"></a>Configurare ritardi di avvio di uno scenario nei test di carico

Specificare un ritardo prima dell'avvio di uno scenario in un test di carico usando l'Editor test di carico e la finestra **Proprietà**.

La proprietà **Ritarda ora di inizio** può ad esempio essere utile quando è necessario che uno scenario inizi a produrre elementi usati da un altro scenario. È possibile ritardare il secondo scenario per consentire al primo di popolare i dati.

Un altro esempio è costituito da uno scenario eseguito solo a una determinata ora del giorno. È quindi possibile ritardare l'avvio dello scenario per simulare questa situazione.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="specify-the-delay-start-time-of-a-scenario"></a>Specificare il ritardo dell'ora di inizio di uno scenario

È possibile specificare un ritardo prima dell'avvio di uno scenario in un test di carico usando l'Editor test di carico per modificare la proprietà **Ritarda ora di inizio** nella finestra **Proprietà**.

> [!NOTE]
> Per un elenco completo delle proprietà dello scenario di test di carico e delle relative descrizioni, vedere [Proprietà dello scenario di test di carico](../test/load-test-scenario-properties.md).

La proprietà **Ritarda ora di inizio** può ad esempio essere utile quando è necessario che uno scenario inizi a produrre elementi usati da un altro scenario. È possibile ritardare il secondo scenario per consentire al primo di popolare i dati.

Un altro esempio è costituito da uno scenario eseguito solo a una determinata ora del giorno. È pertanto possibile ritardare l'avvio dello scenario per simulare questa situazione.

> [!NOTE]
> Per un elenco completo delle proprietà delle impostazioni esecuzione test con le relative descrizioni, vedere [Proprietà di uno scenario di test di carico](../test/load-test-scenario-properties.md).

### <a name="to-specify-the-delay-start-time-for-a-scenario"></a>Per specificare il ritardo dell'ora di inizio per uno scenario

1. Aprire un test di carico.

     Verrà visualizzato l'Editor test di carico. Verrà visualizzata la struttura ad albero del test di carico.

2. Nella cartella **Scenari** dell'albero del test di carico scegliere il nodo dello scenario per il quale si desidera specificare il ritardo per l'ora di inizio.

3. Scegliere **Finestra Proprietà** dal menu **Visualizza**.

     Le categorie e le proprietà dello scenario vengono visualizzate nella finestra **Proprietà**.

4. Nella casella di testo per la proprietà **Ritarda ora di inizio** digitare un valore per indicare il tempo di attesa dall'avvio del test di carico all'avvio dello scenario quando viene eseguito il test di carico.

    > [!NOTE]
    > Se il valore della proprietà **Disabilita durante riscaldamento** per lo scenario è impostato su **True**, il valore della proprietà **Ritarda ora di inizio** viene applicato dopo il periodo di riscaldamento. È possibile stabilire quali scenari includere nella fase di riscaldamento usando la proprietà dello scenario **Disabilita durante riscaldamento**.

5. Dopo aver modificato la proprietà, scegliere **Salva** dal menu **File**. Sarà quindi possibile eseguire il test di carico usando il nuovo valore di **Ritarda ora di inizio**.

## <a name="enable-and-disable-whether-a-scenario-runs-during-the-warm-up-period"></a>Abilitare e disabilitare l'esecuzione di uno scenario durante il periodo di riscaldamento

La proprietà **Disabilita durante riscaldamento** viene impostata usando la finestra **Proprietà**. Le proprietà degli scenari dei test di carico vengono modificate tramite l'Editor test di carico.

La proprietà **Disabilita durante riscaldamento** viene usata per indicare se eseguire o meno lo scenario durante il periodo di riscaldamento specificato nella proprietà **Ritarda ora di inizio**. Per altre informazioni, consultare la procedura precedente, [Specificare il ritardo dell'ora di inizio di uno scenario](#specify-the-delay-start-time-of-a-scenario).

> [!NOTE]
> Per un elenco completo delle proprietà delle impostazioni esecuzione test con le relative descrizioni, vedere [Proprietà di uno scenario di test di carico](../test/load-test-scenario-properties.md).

### <a name="to-enable-or-disable-the-warm-up-period-for-a-scenario"></a>Per abilitare o disabilitare il periodo di riscaldamento per un scenario

1. Aprire un test di carico.

     Viene visualizzato l'**Editor test di carico**. Verrà visualizzata la struttura ad albero del test di carico.

2. Nella cartella **Scenari** dell'albero del test di carico scegliere il nodo dello scenario per cui si vuole modificare il comportamento di riscaldamento.

3. Scegliere **Finestra Proprietà** dal menu **Visualizza**.

     Le categorie e le proprietà dello scenario vengono visualizzate nella finestra **Proprietà**.

     Nella proprietà **Disabilita durante riscaldamento** selezionare **True** o **False.**

4. Terminata la modifica della proprietà, scegliere **Salva** dal menu **File**. Sarà quindi possibile eseguire il test di carico usando il nuovo valore dell'opzione **Disabilita durante riscaldamento**.

## <a name="see-also"></a>Vedi anche

- [Modificare gli scenari di test di carico](../test/edit-load-test-scenarios.md)
- [Configurare agenti di test e test controller per i test di carico](../test/configure-test-agents-and-controllers-for-load-tests.md)
- [Proprietà di uno scenario di test di carico](../test/load-test-scenario-properties.md)
