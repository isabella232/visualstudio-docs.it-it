---
title: Insiemi di contatori di test di carico
description: Informazioni su come usare il Editor test di carico gestione per gestire gli insiemi di contatori scegliendo i computer e assegnando insiemi di contatori da raccogliere da ogni computer.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
f1_keywords:
- vs.test.load.dialog.countersetmapping
helpviewer_keywords:
- counters, counter sets
- performance counters
- counter sets
- load tests, counter sets
ms.assetid: 64315c2f-a0b2-4378-be16-0774b99beef5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: fd18acc2f5ca22cfa70c9a28042f460cb0e7f8bc
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122148545"
---
# <a name="how-to-manage-counter-sets-using-the-load-test-editor"></a>Procedura: Gestire insiemi di contatori usando l'Editor test di carico

Quando si crea un test di carico usando la **Creazione guidata test di carico**, è necessario aggiungere un insieme di contatori iniziale. Ciò offre una serie di insiemi di contatori predefiniti per il test di carico.

> [!NOTE]
> Se i test di carico vengono distribuiti in computer remoti, viene eseguito il mapping dei contatori di controller e agenti ai relativi set. Per altre informazioni sull'uso dei computer remoti nel test di carico, vedere [Test controller e agenti di test](configure-test-agents-and-controllers-for-load-tests.md).

La gestione degli insiemi di contatori implica la scelta del gruppo di computer da cui raccogliere i dati sulle prestazioni e l'assegnazione di una serie di insiemi di contatori da raccogliere da ogni singolo computer. I contatori vengono gestiti nell'**Editor test di carico**.

![Gestione degli insiemi di contatori](../test/media/loadtestmanagecountersets.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-manage-counter-sets"></a>Per gestire gli insiemi di contatori

1. Aprire un test di carico.

2. Scegliere il pulsante **Gestisci insiemi di contatori**.

     - oppure -

     Fare clic con il pulsante destro del mouse sulla cartella **Insiemi di contatori** nell'albero del test di carico e scegliere **Gestisci insiemi di contatori**.

     Viene visualizzata la finestra di dialogo **Gestisci insiemi di contatori**.

3. (Facoltativo) Nella casella di riepilogo **I computer e gli insiemi di contatori selezionati saranno aggiunti alla seguente impostazione di esecuzione** selezionare un'impostazione di esecuzione diversa.

    > [!NOTE]
    > Ciò vale solo se nel test di carico sono incluse più impostazioni di esecuzione.

4. (Facoltativo) Scegliere **Aggiungi computer** per aggiungere un nuovo computer da monitorare. Verrà richiesto di indicare un nome. Digitare il nome di un computer per visualizzare i nodi sotto la nuova voce, ad esempio **ASP.NET**, **IIS**, **SQL** e altri. Selezionare le caselle di controllo accanto ai nodi da selezionare. I nuovi contatori vengono visualizzati nel riquadro **Anteprima selezioni**.

5. (Facoltativo) Nella casella di testo **Tag computer** digitare un tag da associare al computer. Ad esempio, "TestMachine12 in lab3."

     I tag computer consentono di identificare un computer con un nome facile da riconoscere

     e vengono visualizzati nel nodo **Mapping insiemi di contatori** nell'albero nell'Editor test di carico. Inoltre, i tag vengono visualizzati nei rapporti di Excel che consentono alle parti interessate di identificare il ruolo del computer nel test di carico. Ad esempio, "Web Server1 in lab2" o "SQL Server2 in Phoenix office". Per altre informazioni, vedere [Creare report sui risultati dei test di carico per confronti tra test o analisi delle tendenze](../test/compare-load-test-results.md).

6. Scegliere **OK**.

## <a name="see-also"></a>Vedi anche

- [Test controller e agenti di test](configure-test-agents-and-controllers-for-load-tests.md)
- [Specifica degli insiemi di contatori e delle regole di soglia per i computer in un test di carico](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Configurare le impostazioni di esecuzione dei test di carico](../test/configure-load-test-run-settings.md)
