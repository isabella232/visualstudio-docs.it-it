---
title: Aggiungere impostazioni esecuzione test a un test di carico
description: Informazioni su come usare impostazioni aggiuntive per un test di carico, tra cui la durata del test, il livello di dettaglio della raccolta dei risultati e gli insiemi di contatori raccolti.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, run settings, adding
- load tests, run settings
ms.assetid: 257d2a24-d582-4cfe-8b2b-51f51ba9cc84
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: f52eb09c35d54c37303147ea9698ce5fd2b9b744
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122092631"
---
# <a name="how-to-add-additional-run-settings-to-a-load-test"></a>Procedura: Aggiungere altre impostazioni esecuzione test a un test di carico

Le impostazioni esecuzione test di un test di carico determinano una varietà di altre impostazioni, tra cui la durata del test, il livello di dettaglio dell'insieme dei risultati e gli insiemi di contatori raccolti durante le esecuzioni dei test. È possibile creare e archiviare più impostazioni di esecuzione per ogni test di carico e selezionare una determinata impostazioni da usare durante l'esecuzione del test. Quando si crea un test di carico usando la **Creazione guidata test di carico**, al test viene aggiunta un'impostazione esecuzione test iniziale.

È possibile aggiungere altre impostazioni di esecuzione al test di carico con impostazioni di proprietà differenti, per poter eseguire il test di carico con condizioni diverse. Ad esempio, è possibile aggiungere una nuova impostazione test e usare una frequenza di campionamento diversa o specificare una durata dell'esecuzione più lunga. È possibile utilizzare una sola impostazione esecuzione test per volta ed è necessario specificare quale impostazione esecuzione test utilizzare contrassegnandola come attiva.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-add-another-run-setting"></a>Per aggiungere un'ulteriore impostazione di esecuzione

1. Aprire un test di carico.

2. (Facoltativo) Espandere la cartella **Impostazioni di esecuzione**.

3. Fare clic con il pulsante destro del mouse sulla cartella **Impostazioni di esecuzione** e scegliere **Aggiungi impostazione di esecuzione**.

     Viene aggiunta una nuova impostazione di esecuzione alla cartella **Impostazioni di esecuzione**.

4. Scegliere **Finestra Proprietà** dal menu **Visualizza**.

     Verrà visualizzata la **Finestra Proprietà** con le proprietà relative all'impostazione di esecuzione selezionata.

5. Nella finestra **Proprietà** usare la casella di testo per la proprietà **Nome** per assegnare alla nuova impostazione di esecuzione un nome che descriva la finalità dell'impostazione di esecuzione , ad esempio **Run Setting: Five minute run**.

6. Usare la **finestra Proprietà** per modificare le impostazioni di esecuzione. Modificare, ad esempio, la durata dell'esecuzione in **00:05:00** per eseguire il test per cinque minuti.

    > [!NOTE]
    > Per un elenco completo delle proprietà delle impostazioni di esecuzione e delle relative descrizioni, vedere [Proprietà delle impostazioni esecuzione test di carico](../test/load-test-run-settings-properties.md).

     A questo punto è possibile specificare che si desidera utilizzare l'impostazione esecuzione test aggiunta impostandola su attiva. Per altre informazioni, vedere [Procedura: Selezionare l'impostazione di esecuzione attiva per un test di carico.](../test/how-to-select-the-active-run-setting-for-a-load-test.md)

## <a name="see-also"></a>Vedi anche

- [Configurare le impostazioni di esecuzione dei test di carico](../test/configure-load-test-run-settings.md)
- [Specifica degli insiemi di contatori e delle regole di soglia per i computer in un test di carico](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
