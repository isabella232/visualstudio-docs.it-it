---
title: 'Guida rapida: Clonare un repository di codice Python'
description: In questa guida introduttiva viene creato un progetto Python in Visual Studio tramite la clonazione del repository koans Python con Visual Studio Team Explorer.
ms.date: 12/06/2018
ms.topic: quickstart
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 6ec913b78094ac9ad6649e019548e3785b939ba8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122076178"
---
# <a name="quickstart-clone-a-repository-of-python-code-in-visual-studio"></a>Guida introduttiva: Clonare un repository di codice Python in Visual Studio

Dopo aver [installato il supporto di Python in Visual Studio](installing-python-support-in-visual-studio.md), è possibile aggiungere l'estensione GitHub per Visual Studio. L'estensione consente di clonare facilmente un repository di codice Python e di creare un progetto da quest'ultimo dall'interno dell'IDE. Rimane comunque possibile clonare i repository dalla riga di comando e utilizzarli in Visual Studio.

## <a name="install-the-github-extension-for-visual-studio"></a>Installare l'estensione GitHub per Visual Studio

[!INCLUDE[install-github-extension](includes/install-github-extension.md)]

## <a name="work-with-github-in-visual-studio"></a>Usare GitHub in Visual Studio

1. Avviare Visual Studio.

1. Selezionare **Visualizza** Team Explorer per aprire la finestra Team Explorer in cui è possibile connettersi a GitHub o Azure Repos o  >   clonare un repository.  Se la pagina **Connetti** illustrata di seguito non viene visualizzata, selezionare l'icona della spina sulla barra degli strumenti superiore.

    ![Finestra Team Explorer con Azure Repos, GitHub e la clonazione di un repository](media/team-explorer.png)

1. In **Repository Git locali** selezionare il comando **Clona** e quindi immettere `https://github.com/gregmalcolm/python_koans` nel campo URL, immettere una cartella per i file clonati e selezionare il pulsante **Clona**.

    > [!Tip]
    > La cartella specificata **in** Team Explorer è la cartella esatta per ricevere i file clonati. A differenza del comando `git clone`, la creazione di un clone in **Team Explorer** non crea automaticamente una sottocartella con il nome del repository.

1. Al termine della clonazione, viene visualizzato il nome del repository nell'elenco **Repository Git locali**. Fare doppio clic su questo nome per passare al dashboard del repository in **Team Explorer**.

1. In **Soluzioni** selezionare **Nuovo**.

    ![Finestra Team Explorer, creazione di un nuovo progetto da un clone](media/team-explorer-new-project.png)

1. Nella finestra di dialogo Nuovo **Project** visualizzata passare al linguaggio **Python** (o cercare in "Python"), selezionare From Existing Python Code (Da codice **Python** esistente), specificare un nome per il progetto, impostare **Location** (Percorso) sulla stessa cartella del repository e selezionare **OK**. Nella procedura guidata visualizzata, selezionare **Fine**.

1. Selezionare   >  **Visualizza Esplora soluzioni** dal menu.

1. In **Esplora soluzioni** espandere il nodo **python3**, fare clic con il pulsante destro del mouse su **contemplate_koans.py** e scegliere **Imposta come file di avvio**. Questo passaggio indica quale file deve essere usato da Visual Studio per l'esecuzione del progetto.

1. Selezionare **Project** Proprietà Koans dal menu, selezionare la scheda Generale e impostare Directory di lavoro  >   su "python3".   Questo passaggio è necessario perché, per impostazione predefinita, Visual Studio imposta la directory di lavoro sulla radice del progetto anziché sul percorso del file di avvio (*python3\contemplate_koans.py*, che è possibile visualizzare nelle proprietà del progetto). Il codice del programma cerca un file *koans.txt* nella cartella di lavoro, di conseguenza, se non si modifica questo valore viene visualizzato un errore di runtime.

    ![Impostazione della cartella di lavoro per un progetto di Python](media/projects-set-working-directory.png)

1. Premere **CTRL** + **F5 o** selezionare Avvia **debug** senza eseguire  >  **debug** per eseguire il programma. Se viene visualizzato un errore **FileNotFoundError** per il file *koans.txt*, controllare l'impostazione della directory di lavoro come descritto nel passaggio precedente.

1. Quando il programma viene eseguito correttamente, viene visualizzato un errore di asserzione alla riga 17 del file *python3/koans/about_asserts.py*. È intenzionale: il programma è progettato per fare in modo che gli errori intenzionali siano corretti. (Per altri dettagli, vedere [Ruby Koans](https://rubykoans.com/) da cui è stato ideato Python Koans.)

    ![Primo output del programma di Python koans](media/koans-output.png)

1. Aprire *python3/koans/about_asserts.py* da **Esplora soluzioni** e fare doppio clic sul file. Si noti che i numeri di riga non vengono visualizzati nell'editor per impostazione predefinita. Per modificare questa impostazione, selezionare Opzioni strumenti, selezionare Mostra tutte le impostazioni nella parte inferiore della finestra di dialogo, quindi passare a Editor di testo  >      >  **Python**  >  **Generale** e selezionare **Numeri di riga:**

    ![Accensione del numero di riga per i file di Python](media/options-general-line-numbers.png)

1. Correggere l'errore modificando l'argomento `False` nella riga di 17 con `True`. La riga deve essere letta come segue:

    ```python
    self.assertTrue(True) # This should be True
    ```

1. Eseguire di nuovo il programma. Se Visual Studio segnala errori, rispondere con **Sì** per continuare a eseguire il codice. Si può quindi vedere che il primo controllo viene superato e che programma si arresta in corrispondenza del koan successivo. Continuare a correggere gli errori e a eseguire il programma in base alle esigenze.

> [!Important]
> In questa guida introduttiva è stato creato un clone diretto del repository *python_koans* in GitHub. Un repository di questo tipo è protetto dall'autore da modifiche dirette, pertanto il tentativo di eseguire il commit delle modifiche nel repository ha esito negativo. In pratica gli sviluppatori creano invece una copia del repository tramite fork nei propri account GitHub, apportano le modifiche all'interno della copia e quindi creano richieste pull per inviare tali modifiche al repository originale. Quando si ha una copia fork personale, usare l'URL corrispondente anziché l'URL del repository originale usato in precedenza.

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Esercitazione: Usare Python in Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Vedi anche

- [Identificare manualmente un interprete Python esistente](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
- [Come installare il supporto di Python in Visual Studio in Windows](installing-python-support-in-visual-studio.md)
- [Percorsi di installazione](installing-python-support-in-visual-studio.md#install-locations)
