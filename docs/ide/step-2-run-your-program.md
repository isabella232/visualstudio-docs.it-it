---
title: "Passaggio 2: eseguire l'app visualizzatore immagini"
ms.date: 09/06/2019
ms.assetid: 9a8fe90e-c97b-4e98-b6c8-0c6b3962c49d
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8204f2a32a1bb29203c75af55aa383141f17853f
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579409"
---
# <a name="step-2-run-your-picture-viewer-app"></a>Passaggio 2: eseguire l'app visualizzatore immagini

Quando si crea un progetto di app Windows Forms, si compila effettivamente un programma che esegue. In questa esercitazione, l'app visualizzatore immagini non è ancora&mdash;anche se verrà eseguita. Per il momento, viene visualizzata una finestra vuota che mostra **Form1** nella barra del titolo.

Ecco come eseguire l'app. 

1. Scegliere uno dei metodi seguenti:

    - Premere **F5**.

    - Sulla barra dei menu scegliere **Debug** > **Avvia debug**.

    - Sulla barra degli strumenti scegliere il pulsante **Avvia debug** , che viene visualizzato come segue:

      ![pulsante della barra degli strumenti Avvia debug](../ide/media/express_icondebug.png)<br>
      *Pulsante della barra degli strumenti* ***Avvia debug***

1. Visual Studio esegue l'app e viene visualizzata una finestra denominata **Form1** . Lo screenshot seguente mostra l'app appena compilata. L'app è in esecuzione e a breve verrà aggiunta.

     ![Windows Forms app che esegue](../ide/media/express_firstrun.png)<br>
***App Windows Forms***, *in esecuzione*

1. Tornare all'Integrated Development Environment di Visual Studio (IDE), quindi osservare la nuova barra degli strumenti. Quando si esegue un'applicazione, vengono visualizzati pulsanti aggiuntivi sulla barra degli strumenti. Questi pulsanti consentono di eseguire operazioni quali l'arresto e l'avvio dell'applicazione e consentono di rilevare eventuali errori (bug). Per questo esempio viene usato per avviare e arrestare l'app.

     barra degli strumenti debug ![](../ide/media/express_debugtoolbar.png)<br>
*Barra degli strumenti* debug

1. Per arrestare l'app, usare uno dei metodi seguenti:

    - Sulla barra degli strumenti scegliere il pulsante **Termina debug**.

    - Sulla barra dei menu scegliere **Debug** > **Termina debug**.

    - Usare la tastiera e premere **maiusc**+**F5**.

    - Fare clic su **X** nell'angolo in alto a destra della finestra **Form1**.

    > [!NOTE]
    > Quando si esegue l'app dall'interno dell'IDE, viene chiamato debug perché in genere si esegue questa operazione per individuare e correggere i bug (errori) nell'applicazione. Anche se questa app è di piccole dimensioni e non è ancora molto, è ancora un vero programma. Per l'esecuzione e il debug di altri programmi si applica la stessa procedura. Per altre informazioni sul debug, vedere [Presentazione del debugger](../debugger/debugger-feature-tour.md).

## <a name="next-steps"></a>Passaggi successivi

* Per andare al passaggio successivo dell'esercitazione, vedere **[passaggio 3: impostare le proprietà del form](../ide/step-3-set-your-form-properties.md)** .

* Per tornare al passaggio precedente dell'esercitazione, vedere [passaggio 1: creare un progetto di App Windows Forms](../ide/step-1-create-a-windows-forms-application-project.md).

## <a name="see-also"></a>Vedere anche

* [Esercitazione 2: creare un quiz matematico a tempo](tutorial-2-create-a-timed-math-quiz.md)
* [Esercitazione 3: creare un gioco di abbinamenti](tutorial-3-create-a-matching-game.md)
