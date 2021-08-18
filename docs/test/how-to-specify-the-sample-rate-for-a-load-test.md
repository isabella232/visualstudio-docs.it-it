---
title: Specificare la frequenza di campionamento per un'impostazione di esecuzione del test di carico
description: Informazioni su come modificare il valore dell'impostazione Frequenza di campionamento per un'esecuzione Finestra Proprietà usando il Editor test di carico.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, run settings
ms.assetid: 51cbe7d6-5dfd-4842-bca3-f7f8a665dc84
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: 2e397dec54a29f3a660c4cc91d21094a99986e5a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122135598"
---
# <a name="how-to-specify-the-sample-rate-for-a-load-test-run-setting"></a>Procedura: Specificare la frequenza di campionamento per un'impostazione di esecuzione dei test di carico

Dopo aver creato il test di carico usando la **Creazione guidata test di carico**, è possibile usare l'**Editor test di carico** per modificare le proprietà in modo da soddisfare le necessità e gli obiettivi di test.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Usando l'**Editor test di carico** è possibile modificare il valore della proprietà **Frequenza di campionamento** dell'impostazione di esecuzione test nella finestra **Proprietà**. Per un elenco completo delle proprietà delle impostazioni di esecuzione e delle relative descrizioni, vedere [Proprietà delle impostazioni esecuzione test di carico](../test/load-test-run-settings-properties.md).

Scegliere un valore appropriato per la proprietà **Frequenza di campionamento** per l'impostazione di esecuzione test di carico in base alla lunghezza del test di carico. Una frequenza di campionamento inferiore, ad esempio il valore predefinito di cinque secondi, richiede più spazio nel database dei risultati del test di carico. Per i test di carico più lunghi, l'aumento della frequenza di campionamento riduce la quantità di dati raccolti. Per altre informazioni, vedere Procedura: Specificare la frequenza di campionamento per [un'impostazione di esecuzione del test di carico](../test/how-to-specify-the-sample-rate-for-a-load-test.md).

Di seguito sono riportate alcune linee guida per le frequenze di campionamento:

|Durata test di carico|Frequenza di campionamento consigliata|
|-|-----------------------------|
|\< 1 ora|5 secondi|
|1 - 8 ore|5 secondi|
|8 - 24 ore|30 secondi|
|> 24 ore|60 secondi|

## <a name="to-specify-performance-counter-sampling-rate-in-a-run-setting"></a>Per specificare frequenza di campionamento del contatore delle prestazioni in un'impostazione esecuzione test

1. Aprire un test di carico.

     Viene visualizzato l'**Editor test di carico**. Verrà visualizzata la struttura ad albero del test di carico.

2. Nella cartella **Impostazioni esecuzione test** dell'albero del test di carico scegliere le impostazioni esecuzione test per cui si vuole specificare la frequenza di campionamento.

3. Scegliere **Finestra Proprietà** dal menu **Visualizza**.

     Le categorie e le proprietà delle impostazioni di esecuzione test di carico sono visualizzate nella finestra **Proprietà**.

4. Nella proprietà **Frequenza di campionamento** immettere un valore che indica la frequenza alla quale il test di carico raccoglierà dati del contatore delle prestazioni.

5. Terminata la modifica della proprietà, scegliere **Salva** dal menu **File**. Sarà quindi possibile eseguire il test di carico usando il nuovo valore dell'opzione **Frequenza di campionamento**.

## <a name="see-also"></a>Vedi anche

- [Configurare le impostazioni di esecuzione dei test di carico](../test/configure-load-test-run-settings.md)
- [Proprietà di uno scenario di test di carico](../test/load-test-scenario-properties.md)
