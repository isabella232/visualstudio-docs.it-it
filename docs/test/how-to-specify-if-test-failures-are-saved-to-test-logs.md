---
title: Salvare il log di test di carico per i test non superati
description: Informazioni su come specificare se si vuole salvare il log di test se un test ha esito negativo in un test di carico modificando la proprietà Salva log in errore test.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, scenarios
- load tests, logging
ms.assetid: 08a7fe98-a7f7-4b8d-94a3-ec82b65a2aaf
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: b29d78b81d5684203dd37b6e12c24235672bd2b4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122135611"
---
# <a name="how-to-specify-if-test-failures-are-saved-to-test-logs-using-the-load-test-editor"></a>Procedura: Specificare se i test non superati vengono salvati in log di test usando l'Editor test di carico

Dopo aver creato il test di carico usando la **Creazione guidata test di carico**, è possibile usare l'**Editor test di carico** per modificare le proprietà del test di carico in modo da soddisfare le necessità e gli obiettivi di test. Vedere [Procedura dettagliata: Creare ed eseguire un test di carico](../test/walkthrough-create-and-run-a-load-test.md). È possibile specificare se si vuole salvare il log di test nel caso in cui un test non venga superato in un test di carico modificando la proprietà **Salva log su test non superati**.

> [!NOTE]
> Per un elenco completo delle proprietà delle impostazioni esecuzione test e delle relative descrizioni, vedere Proprietà [delle impostazioni esecuzione test di carico.](../test/load-test-run-settings-properties.md)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-specify-if-the-test-log-is-saved-when-a-test-fails-in-a-scenario"></a>Per specificare se il log di test viene salvato quando un test in uno scenario non viene superato

1. Aprire un test di carico.

     Viene visualizzato l'**Editor test di carico**. Verrà visualizzata la struttura ad albero del test di carico.

2. Nella cartella **Impostazioni esecuzione test** dell'albero del test di carico scegliere il nodo delle impostazioni esecuzione test per le quali si vuole specificare il numero massimo di iterazioni di test.

3. Scegliere **Finestra Proprietà** dal menu **Visualizza**.

     Le categorie e le proprietà delle impostazioni di esecuzione verranno visualizzate nella finestra **Proprietà**.

4. Nella proprietà **Salva log su test non superati** selezionare **True** o **False** per specificare se si vuole salvare il log di test nel caso in cui un test non venga superato nello scenario.

     Terminata la modifica della proprietà, scegliere **Salva** dal menu **File**.

     È possibile visualizzare i dati salvati nel log utilizzando la visualizzazione Tabelle dell'analizzatore test di carico. Per altre informazioni, vedere [Analizzare i risultati e gli errori dei test di carico nella visualizzazione Tabelle](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

## <a name="see-also"></a>Vedi anche

- [Modificare gli scenari di test di carico](../test/edit-load-test-scenarios.md)
- [Procedura dettagliata: Creare ed eseguire un test di carico](../test/walkthrough-create-and-run-a-load-test.md)
