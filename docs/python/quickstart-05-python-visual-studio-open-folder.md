---
title: Avvio rapido - Aprire una cartella di codice Python
description: In questa guida di avvio rapido viene illustrato come aprire ed eseguire codice Python da una cartella senza usare un progetto di Visual Studio (solo Visual Studio 2019).
ms.date: 03/12/2019
ms.topic: quickstart
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18
ms.workload:
- python
- data-science
monikerRange: '>= vs-2019'
ms.openlocfilehash: 2da3b76ee7a22e58431eafafa8600158a0ae9b18b12f3f4fc054f0aa0171ffea
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121245252"
---
# <a name="quickstart-open-and-run-python-code-in-a-folder"></a>Guida introduttiva: Aprire ed eseguire codice Python in una cartella

Dopo aver [installato il supporto Python in Visual Studio 2019](installing-python-support-in-visual-studio.md), è facile eseguire codice Python esistente in Visual Studio 2019 senza creare un progetto di Visual Studio.

> [!Note]
> In Visual Studio 2017 e versioni precedenti è necessario creare un progetto di Visual Studio per eseguire codice Python, operazione che è possibile eseguire facilmente usando un modello di progetto predefinito. Vedere [Avvio rapido: Creare un progetto Python da codice esistente](quickstart-01-python-in-visual-studio-project-from-existing-code.md)

1. Per questa procedura dettagliata, è possibile usare qualsiasi cartella con codice Python. Per seguire la procedura con l'esempio riportato di seguito, clonare il repository di GitHub gregmalcolm/python_koans nel computer locale usando il comando `git clone https://github.com/gregmalcolm/python_koans` in una cartella appropriata.

1. Avviare Visual Studio 2019 e nella schermata iniziale selezionare **Apri** nella parte inferiore della colonna **Per iniziare**. In alternativa, se è già in Visual Studio, selezionare invece il **comando Apri**  >    >   cartella.

    ![Schermata iniziale di Visual Studio](media/quickstart-open-folder/01-open-local-folder.png)

1. Passare alla cartella che contiene il codice Python e quindi scegliere **Seleziona cartella**. Se si usa il codice python_koans, assicurarsi di selezionare la cartella `python3` all'interno della cartella di clonazione.

    ![Finestra di dialogo Seleziona cartella dal comando Apri cartella](media/quickstart-open-folder/02-select-folder.png)

1. Visual Studio visualizza la cartella in **Esplora soluzioni** nella cosiddetta **visualizzazione cartelle**. È possibile espandere e comprimere le cartelle usando le frecce sui bordi a sinistra dei nomi delle cartelle:

    ![Controlli per espandere e comprimere le cartelle in Esplora soluzioni](media/quickstart-open-folder/03-expand-collapse-folders.png)

1. Quando si apre una cartella di Python, Visual Studio crea varie cartelle nascoste per gestire le impostazioni relative al progetto. Per visualizzare queste cartelle (ed eventuali altri file e cartelle nascosti, ad esempio la cartella *.git*), selezionare il pulsante della barra degli strumenti **Mostra tutti i file**:

    ![Visualizzazione delle cartelle nascoste in Esplora soluzioni](media/quickstart-open-folder/05-view-hidden-folders.png)

1. Per eseguire il codice, è prima necessario identificare il file di programma di avvio o principale. Nell'esempio qui illustrato, il file di avvio è *contemplate-koans.py*. Fare clic con il pulsante destro del mouse su tale file e scegliere **Imposta come file di avvio**.

    ![Impostazione di un elemento di avvio in Esplora soluzioni](media/quickstart-open-folder/06-set-as-startup-item-command.png)

    > [!Important]
    > Se l'elemento di avvio non si trova nella radice della cartella aperta, è necessario aggiungere anche una riga al file JSON di configurazione di avvio, come descritto nella sezione [Impostare una directory di lavoro](#set-a-working-directory).

1. Eseguire il codice premendo **CTRL** + **F5** o selezionando **Debug** Avvia senza  >  **eseguire debug.** È anche possibile selezionare il pulsante della barra degli strumenti che mostra l'elemento di avvio con un pulsante di riproduzione, che esegue il codice nel debugger di Visual Studio. In tutti i casi, Visual Studio rileva che l'elemento di avvio è un file di Python, quindi esegue automaticamente il codice nell'ambiente Python predefinito. (Tale ambiente viene visualizzato a destra dell'elemento di avvio sulla barra degli strumenti.)

    ![Pulsante della barra degli strumenti per avviare il debugger](media/quickstart-open-folder/07-start-debug-toolbar.png)

1. L'output del programma viene visualizzato in una finestra di comando separata:

    ![Finestra di output per l'esecuzione di codice Python](media/quickstart-open-folder/08-result-window.png)

1. Per eseguire il codice in un ambiente diverso, selezionare tale ambiente nell'elenco a discesa sulla barra degli strumenti e quindi avviare di nuovo l'elemento di avvio.

1. Per chiudere la cartella in Visual Studio, selezionare il **comando di** menu File Close  >  **folder (Chiudi** cartella).

## <a name="set-a-working-directory"></a>Impostare una directory di lavoro

Per impostazione predefinita, Visual Studio esegue un progetto Python aperto come cartella nella radice della stessa cartella. Il codice nel progetto, tuttavia, potrebbe presupporre che Python sia in esecuzione in una sottocartella. Ad esempio, si supponga di aprire la cartella radice del repository python_koans e quindi di impostare il file *python3/contemplate-koans.py* come elemento di avvio. Se poi si esegue il codice, viene visualizzato un errore di file *koans.txt* non trovato. Questo errore si verifica perché *contemplate-koans.py* presuppone che Python sia in esecuzione nella cartella *python3* anziché nella radice del repository.

In questi casi, è anche necessario aggiungere una riga al file JSON di configurazione di avvio per specificare la directory di lavoro:

1. Fare clic con il pulsante destro del mouse sul file di avvio Python (con estensione *py*) in **Esplora soluzioni** e scegliere **Impostazioni per debug e avvio**.

    ![Screenshot della visualizzazione Esplora soluzioni cartella con il file contemplate-koans.py selezionato e l'opzione Debug e Impostazioni selezionata nel menu di scelta rapida.](media/quickstart-open-folder/09-debug-launch-settings-menu-command.png)

1. Nella finestra di dialogo **Seleziona un debugger** visualizzata selezionare **Predefinito** e quindi scegliere **Seleziona**.

    ![Screenshot della finestra di dialogo Seleziona un debugger con il debugger predefinito selezionato e il pulsante Seleziona selezionato.](media/quickstart-open-folder/10-select-debugger.png)

    > [!Note]
    > Se l'opzione  Predefinita non è visualizzata, assicurarsi di aver scelto un file python con estensione *py* quando si selezionano i comandi **Debug e Impostazioni** avvio. Visual Studio usa il tipo di file per determinare le opzioni del debugger da visualizzare.

1. Visual Studio apre un file denominato *launch.vs.json*, che si trova nella cartella nascosta *.vs*. Questo file descrive il contesto di debug per il progetto. Per specificare una directory di lavoro, aggiungere un valore per `"workingDirectory"`, come in `"workingDirectory": "python3"` per l'esempio python koans:

    ```json
    {
      "version": "0.2.1",
      "defaults": {},
      "configurations": [
        {
          "type": "python",
          "interpreter": "(default)",
          "interpreterArguments": "",
          "scriptArguments": "",
          "env": {},
          "nativeDebug": false,
          "webBrowserUrl": "",
          "project": "python3\\contemplate_koans.py",
          "name": "contemplate_koans.py",
          "workingDirectory": "python3"
        }
      ]
    }
    ```

1. Salvare il file e avviare nuovamente il programma, che viene ora eseguito nella cartella specificata.

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Esercitazione: Usare Python in Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Vedi anche

- [Guida introduttiva: Creare un progetto Python a partire da un codice esistente](quickstart-01-python-in-visual-studio-project-from-existing-code.md)
- [Guida introduttiva: Creare un progetto Python da un repository](quickstart-03-python-in-visual-studio-project-from-repository.md)
- [Identificare manualmente un interprete Python esistente](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
