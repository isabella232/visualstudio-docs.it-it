---
title: Aggiungere contatori a insiemi di contatori per i test di carico
description: Quando si crea un test di carico utilizzando la Creazione guidata test di carico, è necessario aggiungere un insieme di contatori iniziale. Informazioni su come aggiungere contatori usando Editor test di carico.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- counters, counter sets
- counter sets
- load tests, counter sets
ms.assetid: e17d0e71-f982-4fc1-a2df-a1065d37473d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: b65fe48b0b912c3b26c4b16cb4d1269abad88f57
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122075879"
---
# <a name="how-to-add-counters-to-counter-sets-using-the-load-test-editor"></a>Procedura: Aggiungere contatori agli insiemi di contatori usando l'Editor test di carico

Quando si crea un test di carico usando la **Creazione guidata test di carico**, è necessario aggiungere un insieme di contatori iniziale. Ciò offre una serie di insiemi di contatori predefiniti per il test di carico. Per altre informazioni, vedere [Specificare gli insiemi di contatori e le regole di soglia per i computer in un test di carico](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Se i test di carico vengono distribuiti in computer remoti, viene eseguito il mapping dei contatori di controller e agenti ai relativi set. Per altre informazioni sull'uso dei computer remoti nel test di carico, vedere [Test controller e agenti di test](configure-test-agents-and-controllers-for-load-tests.md).

I contatori vengono gestiti nell'**Editor test di carico**. Gli insiemi di contatori già aggiunti al test sono visibili nel nodo **Insiemi di contatori** del test di carico. Dopo aver creato un test di carico, è possibile aggiungere i nuovi contatori agli insiemi di contatori esistenti.

## <a name="to-add-counters-to-a-counter-set"></a>Per aggiungere contatori a un insieme di contatori

1. Aprire un test di carico.

2. Espandere il nodo **Insiemi di contatori**. Verranno visualizzati tutti gli insiemi di contatori aggiunti al test di carico.

    > [!NOTE]
    > L'albero gerarchico del test di carico contiene anche il nodo **Impostazioni di esecuzione**, che contiene il nodo **Mapping insiemi di contatori** in cui sono indicati tutti i computer e gli insiemi di contatori mappati ai computer.

3. Fare clic con il pulsante destro del mouse sull'insieme di contatori esistente, quindi scegliere **Aggiungi contatori**.

     Viene visualizzata la finestra di dialogo **Seleziona contatori delle prestazioni**.

4. Nella casella combinata a discesa **Computer** digitare il nome del computer al quale eseguire il mapping. In alternativa, selezionare uno dei computer dall'elenco a discesa.

    > [!NOTE]
    > Poiché è necessario che gli insiemi di contatori siano mappati a un computer prima che vengano raccolti dati sulle prestazioni, specificare un computer in cui raccogliere i dati sulle prestazioni.

5. Selezionare una **Categoria contatori delle prestazioni** per filtrare le categorie di contatori di dati delle prestazioni. Verranno visualizzate due colonne di dati da cui selezionare i contatori delle prestazioni.

    > [!NOTE]
    > Alcune categorie di contatori richiedono di selezionare anche un'istanza. Se ad esempio si seleziona un contatore SQL, è necessario selezionare un'istanza SQL, in quanto nel computer di destinazione potrebbero essere installate più istanze di SQL.

6. Selezionare un contatore e un'istanza da aggiungere all'insieme di contatori personalizzati.

     \- - oppure -

     Selezionare il pulsante di opzione **Tutti i contatori** per selezionare tutti i contatori disponibili.

7. Scegliere **OK**.

    > [!NOTE]
    > È inoltre possibile aggiungere contatori a un insieme di contatori selezionando una categoria di contatori o un contatore esistente, scegliendo Copia, quindi incollandolo in un nodo di insiemi di contatori diverso. I contatori aggiuntivi che vengono copiati ma non sono necessari possono essere eliminati.

## <a name="see-also"></a>Vedi anche

- [Specifica degli insiemi di contatori e delle regole di soglia per i computer in un test di carico](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Configurare le impostazioni di esecuzione dei test di carico](../test/configure-load-test-run-settings.md)
