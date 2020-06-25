---
title: Selezionare le impostazioni di esecuzione test di carico dalla riga di comando
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, command line
- load tests, run settings, selecting
ms.assetid: 175d1d58-f09a-4449-b132-a29a394a7c8e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 79f1cc833278a62e2871cdc725f5993b12bcdb60
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/23/2020
ms.locfileid: "85287558"
---
# <a name="how-to-select-a-load-test-run-setting-to-use-from-the-command-line"></a>Procedura: Selezionare un'impostazione di esecuzione test di carico dalla riga di comando

Un test di carico può includere *impostazioni di esecuzione* ovvero proprietà che determinano la modalità di esecuzione del test di carico. Sono organizzate in categorie nella finestra **Proprietà**. Quando si esegue un test di carico, viene utilizzata l'impostazione esecuzione test impostata correntemente come attiva.

Se nel test di carico è contenuta un'unica impostazione esecuzione test, si tratta sempre del nodo attivo. Se nel test di carico sono contenuti più nodi di impostazioni esecuzione test, è possibile selezionare quello da usare quando si esegue un test di carico dalla riga di comando. Vedere [procedura: aggiungere altre impostazioni esecuzione test a un test di carico](../test/how-to-add-additional-run-settings-to-a-load-test.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-change-the-run-setting-from-the-command-line"></a>Per modificare l'impostazione di esecuzione test dalla riga di comando

1. Se si vuole usare impostazioni esecuzione test diverse dalla riga di comando per sfruttare la strategia dei parametri di contesto, usare il comando seguente:

    `Set Test.UseRunSetting= CorporateStagingWebServer`

2. Eseguire il test di carico utilizzando mstest:

    `mstest /testcontainer:loadtest1.loadtest`

## <a name="see-also"></a>Vedi anche

- [Configurare le impostazioni di esecuzione dei test di carico](../test/configure-load-test-run-settings.md)
- [Specifica degli insiemi di contatori e delle regole di soglia per i computer in un test di carico](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Procedura: Aggiungere altre impostazioni esecuzione test a un test di carico](../test/how-to-add-additional-run-settings-to-a-load-test.md)
- [Procedura: Selezionare l'impostazione di esecuzione test attiva per un test di carico](../test/how-to-select-the-active-run-setting-for-a-load-test.md)
