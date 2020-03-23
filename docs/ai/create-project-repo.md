---
title: Clonare un repository
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 73f1595e0e6c8f182f0bedcece51011390964ed2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "62539658"
---
# <a name="clone-a-repository-of-python-code-in-visual-studio"></a>Clonare un repository del codice Python in Visual Studio

Dopo aver [installato Visual Studio Tools for AI](installation.md), è possibile clonare facilmente un repository di codice Python e creare un progetto a partire da questo.

1. Per connettersi ai repository GitHub, eseguire il programma di installazione di Visual Studio, **Code tools** selezionare **Modifica**e selezionare la scheda **Modify** **Singoli componenti** . **GitHub extension for Visual Studio**

    ![Selezione dell'estensione GitHub nel programma di installazione di Visual Studio](media/create-project-repo/installation-github-extension.png)

2. Avviare Visual Studio.

3. Selezionare **Visualizza > Team Explorer** per aprire la finestra **Team Explorer**, in cui è possibile connettersi a GitHub o ad Azure DevOps oppure clonare un repository.

    ![Finestra Team Explorer con Azure DevOps, GitHub e la clonazione di un repository](media/create-project-repo/team-explorer-devops.png)

4. Nel campo URL in **Repository Git locali** immettere `https://github.com/Microsoft/samples-for-ai`, immettere una cartella per i file clonati e selezionare **Clona**.

    > [!Tip]
    > La cartella immessa in Team Explorer è specifica per ricevere i file clonati. A differenza del comando `git clone`, la creazione di un clone in Team Explorer non crea automaticamente una sottocartella con il nome del repository.

5. Al termine della clonazione, fare doppio clic sulla cartella del repository nella parte inferiore di Team Explorer per passare al dashboard del repository. In **Soluzioni** selezionare **Nuovo**.

    ![Finestra Team Explorer, creazione di un nuovo progetto da un clone](media/create-project-repo/team-explorer-new-project.png)

6. Nella finestra di dialogo **Nuovo progetto** visualizzata, selezionare " Dal codice**Python esistente**", specificare un nome per il progetto, impostare **Posizione** sulla stessa cartella del repository e selezionare **OK**. Nella procedura guidata visualizzata, selezionare **Fine**.

7. Selezionare **Visualizza > Esplora soluzioni** dal menu.

8. In Esplora soluzioni `TensorFlow Examples> MNIST` espandere il `convolutional.py`nodo , fare clic con il pulsante destro del mouse su e scegliere Imposta come file di **avvio**. Questo passaggio indica quale file deve essere usato da Visual Studio per l'esecuzione del progetto.

9. Premere **CTRL**+**F5** o selezionare **Debug > Avvia senza eseguire il debug** per eseguire il programma. Se viene visualizzato un errore, ricontrollare l'impostazione relativa alla directory di lavoro nel passaggio precedente.

10. Quando il programma viene eseguito correttamente, si noterà che viene avviato il download del set di dati per training e test, quindi viene eseguito il training del modello e viene infine restituita la frequenza degli errori. Si vuole ridurre la frequenza degli errori nel tempo

    ![Primo output del programma MNIST Python](media/create-project-repo/tensorflow-mnist-running.png)

   > [!NOTE]
   > Se si usa Anaconda e si riceve un errore di numpy mancante, può essere necessario [modificare l'ambiente Python in modo da usare Anaconda](../python/selecting-a-python-environment-for-a-project.md).

11. È possibile visualizzare lo stato con TensorBoard. Fare clic con il pulsante destro de mouse sul progetto e scegliere **Run TensorBoard** (Esegui TensorBoard) quindi selezionare la directory dei log di output di TensorBoard.

   ![eseguire tensorboard](media/create-project-repo/run-tensorboard.png)

12. Si noti che gli errori diminuiscono nel tempo e ciò indica un miglioramento della qualità.

   ![eseguire tensorboard](media/create-project-repo/tensorboard.png)
