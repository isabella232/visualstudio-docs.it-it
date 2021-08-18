---
title: "Passaggio 2: Eseguire l'app visualizzatore di immagini"
description: Informazioni su come eseguire l'app visualizzatore di immagini.
ms.custom: SEO-VS-2020
ms.date: 09/06/2019
ms.assetid: 9a8fe90e-c97b-4e98-b6c8-0c6b3962c49d
ms.topic: tutorial
author: j-martens
ms.author: jmartens
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 808b5635764a49f67788825f5524662145ac5d77
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122116890"
---
# <a name="step-2-run-your-picture-viewer-app"></a>Passaggio 2: Eseguire l'app visualizzatore di immagini

Quando si crea un progetto Windows'app Forms, si compila effettivamente un programma che viene eseguito. In questa esercitazione l'app visualizzatore di immagini non fa ancora &mdash; molto, anche se lo farà. Per il momento, viene visualizzata una finestra vuota che mostra **Form1** nella barra del titolo.

Ecco come eseguire l'app. 

1. Scegliere una delle seguenti modalità:

    - Premere **F5**.

    - Sulla barra dei menu scegliere **Debug**  >  **Avvia debug**.

    - Sulla barra degli strumenti scegliere il **pulsante** Avvia debug, che viene visualizzato come segue:

      ![Pulsante della barra degli strumenti Avvia debug](../ide/media/express_icondebug.png)<br>
      ***Avviare il debug** _ _toolbar pulsante*

1. Visual Studio l'app e viene visualizzata una finestra denominata **Form1.** Lo screenshot seguente mostra l'app appena creata. L'app è in esecuzione e verrà aggiunta a breve.

     ![Windows App Forms in esecuzione](../ide/media/express_firstrun.png)<br>
***Windows Forms App** _, _running*

1. Tornare all'ambiente Visual Studio di sviluppo integrato (IDE) e quindi esaminare la nuova barra degli strumenti. Quando si esegue un'applicazione, sulla barra degli strumenti vengono visualizzati altri pulsanti. Questi pulsanti consentono di eseguire operazioni come arrestare e avviare l'app e di rilevare eventuali errori (bug) che potrebbero verificarsi. Per questo esempio viene utilizzato per avviare e arrestare l'app.

     ![Barra degli strumenti di debug](../ide/media/express_debugtoolbar.png)<br>
***Debug** di _ _toolbar*

1. Usare uno dei metodi seguenti per arrestare l'app:

    - Sulla barra degli strumenti scegliere il pulsante **Termina debug**.

    - Sulla barra dei menu scegliere **Debug**  >  **Arresta debug**.

    - Usare la tastiera e premere **MAIUSC** + **F5.**

    - Scegliere il **pulsante X** nell'angolo superiore della **finestra form1.**

    > [!NOTE]
    > Quando si esegue l'app dall'interno dell'IDE, si chiama debug perché in genere si esegue questa operazione per individuare e correggere bug (errori) nell'applicazione. Anche se questa app è piccola e non fa ancora molto, è comunque un programma reale. Per l'esecuzione e il debug di altri programmi si applica la stessa procedura. Per altre informazioni sul debug, vedere [Presentazione del debugger](../debugger/debugger-feature-tour.md).

## <a name="next-steps"></a>Passaggi successivi

* Per andare al passaggio successivo dell'esercitazione, vedere **[Passaggio 3: Impostare le proprietà del modulo.](../ide/step-3-set-your-form-properties.md)**

* Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 1: Creare un progetto app Windows Forms](../ide/step-1-create-a-windows-forms-application-project.md).

## <a name="see-also"></a>Vedi anche

* [Esercitazione 2: Creare un quiz matematico a tempo](tutorial-2-create-a-timed-math-quiz.md)
* [Esercitazione 3: Creare un gioco corrispondente](tutorial-3-create-a-matching-game.md)
