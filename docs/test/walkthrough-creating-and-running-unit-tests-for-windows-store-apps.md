---
title: Creazione ed esecuzione di unit test per app UWP
description: Informazioni sul supporto Visual Studio per unit test delle app universal Windows Platform. Visual Studio fornisce unit test modelli per C#, Visual Basic e C++.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- unit tests, creating
- unit tests
- unit tests, UWP apps
- unit tests, running
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- uwp
author: mikejo5000
ms.openlocfilehash: 91efcd80f1f805e4b841d5abf68082c718ef93cacc2bfb21ed323513b4044a7e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121424725"
---
# <a name="walkthrough-create-and-run-unit-tests-for-uwp-apps"></a>Procedura dettagliata: Creare ed eseguire unit test per app della piattaforma UWP

Visual Studio include il supporto per gli unit test delle app della piattaforma UWP (Universal Windows Platform). Visual Studio fornisce unit test di progetto per C#, Visual Basic e C++.

> [!TIP]
> Per altre informazioni sullo sviluppo di app per la piattaforma UWP, vedere [Introduzione alle app UWP](/windows/uwp/get-started/).

Le procedure seguenti descrivono i passaggi per creare, eseguire ed eseguire il debug di unit test per un'app UWP.

## <a name="create-a-unit-test-project-for-a-uwp-app"></a>Creare un progetto di unit test per un'app UWP

::: moniker range=">=vs-2019"

1. Aprire Visual Studio. Nella finestra iniziale scegliere **Crea un nuovo progetto**.

2. Nella casella di ricerca della pagina **Crea un nuovo progetto** immettere **unit test**.

   L'elenco di modelli filtra quelli per gli unit test.

3. Selezionare il **modello App unit test (universal Windows)** per C# o Visual Basic e quindi selezionare **Avanti.**

   ![Creare una nuova app unit test UWP in Visual Studio](media/vs-2019/new-uwp-unit-test-app.png)

4. Facoltativamente, modificare il nome e il percorso del progetto o della soluzione e quindi selezionare **Crea**.

5. Facoltativamente, modificare le versioni di piattaforma di destinazione e minima e quindi selezionare **OK.**

Dopo aver completato questi passaggi, il unit test viene creato e visualizzato in Esplora soluzioni.

![Progetto unit test UWP in Esplora soluzioni](media/vs-2019/uwp-unit-test-project-solution-explorer.png)

::: moniker-end

::: moniker range="vs-2017"

1. Scegliere **Nuovo progetto** dal menu **File**.

   Verrà **visualizzata la finestra Project** nuova finestra di dialogo.

2. In Modelli scegliere il linguaggio di programmazione con cui creare gli unit test e quindi scegliere la libreria di unit test per Windows Universal associata. Ad esempio, scegliere **Visual C#**, **Windows Universal** e quindi **Libreria unit test (Universal Windows)**.

3. (Facoltativo) Nella casella di testo **Nome** immettere il nome che si vuole usare per il progetto.

4. (Facoltativo) Modificare il percorso in cui si vuole creare il progetto immettendolo nella casella di testo **Percorso** oppure scegliendo il pulsante **Sfoglia**.

5. (Facoltativo) Nella casella di testo del nome **Soluzione** immettere il nome che si desidera usare per la soluzione.

6. Lasciare selezionata l'opzione **Crea directory per soluzione** e scegliere il pulsante **OK** .

   ![Libreria unit test personalizzata](../test/media/unit_test_win8_1.png)

   **Esplora soluzioni** viene popolato con il progetto unit test UWP e l'editor di codice visualizza il unit test con il titolo UnitTest1.

   ![Nuovo progetto di unit test personalizzato](../test/media/unit_test_win8_unittestexplorer_newprojectcreated.png)

::: moniker-end

## <a name="edit-the-unit-test-projects-uwp-application-manifest-file"></a>Modificare il file manifesto dell'applicazione UWP del progetto di unit test

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul file *Package.appxmanifest* e scegliere **Apri**.

2. In **Progettazione manifesto** scegliere la scheda **Funzionalità**.

3. Nell'elenco in **Funzionalità** selezionare le funzionalità necessarie per lo unit test e il codice per il test. Ad esempio, selezionare la casella di controllo **Internet** se lo unit test e il codice di cui si sta eseguendo il test necessitano della funzionalità di accesso a Internet.

   > [!NOTE]
   > Le funzionalità selezionate devono includere solo quelle necessarie affinché lo unit test funzioni correttamente.

   ![Manifesto unit test](../test/media/unit_test_win8_.png)

## <a name="code-the-unit-test-for-a-uwp-app"></a>Scrivere il codice per lo unit test di un'app UWP

Nell'editor di codice modificare il unit test e aggiungere le asserzioni e la logica necessarie per il test.

## <a name="run-unit-tests"></a>Eseguire unit test

Per compilare la soluzione ed eseguire il unit test usando Esplora test:

1. Dal menu **Test** scegliere **Finestre**, quindi scegliere **Esplora test**.

2. Scegliere **Compila** soluzione dal menu **Compila**.

   Il unit test ora viene visualizzato in Esplora test.

   > [!NOTE]
   > È necessario compilare la soluzione per aggiornare l'elenco degli unit test in Esplora test.

3. In **Esplora test** scegliere il unit test creato.

4. Scegliere **Esegui tutto**.

   ![Esplora unit test &#45; esegui unit test](../test/media/unit_test_win8_unittestexplorer_contextmenurun.png)

   > [!TIP]
   > È possibile selezionare uno o più unit test elencati in Esplora test, quindi fare clic con il pulsante destro del mouse e **scegliere Esegui test selezionati**.
   >
   > Inoltre, è possibile scegliere di **eseguire il debug dei test selezionati**, di **aprire il test** e di usare l'opzione **Proprietà** .
   >
   > ![Menu di scelta rapida &#45; unit test Esplora unit test](../test/media/unit_test_win8_unittestexplorer_contextmenu.png)

   Lo unit test viene eseguito. Al termine, Esplora test visualizza lo stato del test e il tempo trascorso e fornisce un collegamento all'origine.

   ![Esplora unit test &#45; test completato](../test/media/unit_test_win8_unittestexplorer_done.png)

## <a name="see-also"></a>Vedi anche

- [Test delle app UWP con Visual Studio](../test/unit-test-your-code.md)
- [Compilare e testare un'app UWP](/azure/devops/pipelines/apps/windows/universal?tabs=vsts)
