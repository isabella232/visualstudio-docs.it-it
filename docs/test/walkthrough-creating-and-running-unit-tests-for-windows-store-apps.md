---
title: Creazione ed esecuzione di unit test per app UWP
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- unit tests, creating
- unit tests
- unit tests, UWP apps
- unit tests, running
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
author: mikejo5000
ms.openlocfilehash: 4109f743caf7c62450591f78e90b92113fc4107e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "75568880"
---
# <a name="walkthrough-create-and-run-unit-tests-for-uwp-apps"></a>Procedura dettagliata: Creare ed eseguire unit test per app della piattaforma UWP

Visual Studio include il supporto per gli unit test delle app della piattaforma UWP (Universal Windows Platform). Visual Studio offre modelli di progetto unit test per C#, Visual Basic e C++.

> [!TIP]
> Per altre informazioni sullo sviluppo di app per la piattaforma UWP, vedere [Introduzione alle app UWP](/windows/uwp/get-started/).

Le procedure seguenti descrivono i passaggi per creare, eseguire ed eseguire il debug di unit test per un'app UWP.

## <a name="create-a-unit-test-project-for-a-uwp-app"></a>Creare un progetto di unit test per un'app UWP

::: moniker range=">=vs-2019"

1. Aprire Visual Studio. Nella finestra Start scegliere **Crea un nuovo progetto**.

2. Nella casella di ricerca della pagina **Crea un nuovo progetto** immettere **unit test**.

   L'elenco di modelli filtra quelli per gli unit test.

3. Selezionare il modello **app unit test (Windows universale)** per C# o Visual Basic e quindi fare clic su **Avanti**.

   ![Creare una nuova app unit test UWP in Visual Studio](media/vs-2019/new-uwp-unit-test-app.png)

4. Facoltativamente, modificare il nome del progetto o della soluzione e il percorso, quindi selezionare **Crea**.

5. Facoltativamente, modificare la destinazione e le versioni minime della piattaforma, quindi selezionare **OK**.

Dopo aver completato questi passaggi, il progetto unit test viene creato e visualizzato in Esplora soluzioni.

![Progetto unit test UWP in Esplora soluzioni](media/vs-2019/uwp-unit-test-project-solution-explorer.png)

::: moniker-end

::: moniker range="vs-2017"

1. Scegliere **Nuovo progetto** dal menu **File**.

   Verrà visualizzata la finestra di dialogo **nuovo progetto** .

2. In Modelli scegliere il linguaggio di programmazione con cui creare gli unit test e quindi scegliere la libreria di unit test per Windows Universal associata. Ad esempio, scegliere **Visual C#**, **Windows Universal** e quindi **Libreria unit test (Universal Windows)**.

3. (Facoltativo) Nella casella di testo **Nome** immettere il nome che si vuole usare per il progetto.

4. (Facoltativo) Modificare il percorso in cui si vuole creare il progetto immettendolo nella casella di testo **Percorso** oppure scegliendo il pulsante **Sfoglia**.

5. (Facoltativo) Nella casella di testo del nome **Soluzione** immettere il nome che si desidera usare per la soluzione.

6. Lasciare selezionata l'opzione **Crea directory per soluzione** e scegliere il pulsante **OK** .

   ![Libreria unit test personalizzata](../test/media/unit_test_win8_1.png)

   **Esplora soluzioni** viene popolato con il progetto di unit test UWP e l'editor di codice visualizza il unit test predefinito denominato UnitTest1.

   ![Nuovo progetto di unit test personalizzato](../test/media/unit_test_win8_unittestexplorer_newprojectcreated.png)

::: moniker-end

## <a name="edit-the-unit-test-projects-uwp-application-manifest-file"></a>Modificare il file manifesto dell'applicazione UWP del progetto di unit test

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul file *Package. appxmanifest* e scegliere **Apri**.

2. In **Progettazione manifesto** scegliere la scheda **Funzionalità**.

3. Nell'elenco in **Funzionalità**selezionare le funzionalità necessarie per lo unit test e il codice per il test. Ad esempio, selezionare la casella di controllo **Internet** se lo unit test e il codice di cui si sta eseguendo il test necessitano della funzionalità di accesso a Internet.

   > [!NOTE]
   > Le funzionalità selezionate devono includere solo quelle necessarie affinché lo unit test funzioni correttamente.

   ![Manifesto unit test](../test/media/unit_test_win8_.png)

## <a name="code-the-unit-test-for-a-uwp-app"></a>Scrivere il codice per lo unit test di un'app UWP

Nell'Editor di codice modificare il unit test e aggiungere le asserzioni e la logica necessarie per il test.

## <a name="run-unit-tests"></a>Eseguire unit test

Per compilare la soluzione ed eseguire il unit test usando Esplora test:

1. Dal menu **Test** scegliere **Finestre**, quindi scegliere **Esplora test**.

2. Scegliere **Compila soluzione**dal menu **Compila** .

   Il unit test viene ora visualizzato in Esplora test.

   > [!NOTE]
   > È necessario compilare la soluzione per aggiornare l'elenco degli unit test in Esplora test.

3. In **Esplora test**scegliere il unit test creato.

4. Scegliere **Esegui tutto**.

   ![Esplora unit test &#45; esegui unit test](../test/media/unit_test_win8_unittestexplorer_contextmenurun.png)

   > [!TIP]
   > È possibile selezionare uno o più unit test elencati in Esplora test, quindi fare clic con il pulsante destro del mouse e scegliere **Esegui test selezionati**.
   >
   > Inoltre, è possibile scegliere di **eseguire il debug dei test selezionati**, di **aprire il test**e di usare l'opzione **Proprietà** .
   >
   > ![Esplora unit test &#45; unit test menu di scelta rapida](../test/media/unit_test_win8_unittestexplorer_contextmenu.png)

   Lo unit test viene eseguito. Al termine, in Esplora test vengono visualizzati lo stato del test e il tempo trascorso e viene fornito un collegamento all'origine.

   ![Esplora unit test &#45; test completato](../test/media/unit_test_win8_unittestexplorer_done.png)

## <a name="see-also"></a>Vedere anche

- [Test delle app UWP con Visual Studio](../test/unit-test-your-code.md)
- [Compilare e testare un'app UWP](/azure/devops/pipelines/apps/windows/universal?tabs=vsts)
