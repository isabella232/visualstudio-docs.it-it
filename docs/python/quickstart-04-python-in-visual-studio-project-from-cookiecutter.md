---
title: Guida introduttiva- Creare progetti Python con Cookiecutter
description: In questa guida introduttiva viene creato un progetto Visual Studio per Python tramite un modello Cookiecutter.
ms.date: 02/25/2019
ms.topic: quickstart
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18, SEO-VS-2020
ms.workload:
- python
- data-science
ms.openlocfilehash: 26e65a7aeee0d24b3c75b7251d6e4072103500f8
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126711479"
---
# <a name="quickstart-create-a-project-from-a-cookiecutter-template"></a>Guida introduttiva: Creare un progetto da un modello di Cookiecutter

Dopo aver [installato il supporto di Python in Visual Studio](installing-python-support-in-visual-studio.md), è facile creare un nuovo progetto da un modello Cookiecutter, inclusi quelli che vengono pubblicati in GitHub. [Cookiecutter](https://cookiecutter.readthedocs.io/en/latest/) offre un'interfaccia utente grafica per individuare modelli, opzioni del modello di input e creare progetti e file. Questa estensione è inclusa in Visual Studio 2017 e versioni successive e può essere installata separatamente nelle versioni precedenti di Visual Studio.

1. Per questa Guida rapida, è necessario installare prima la distribuzione di Python Anaconda3, che include i pacchetti Python necessari per il modello Cookiecutter illustrato di seguito. Eseguire il programma di installazione di Visual Studio, selezionare **Modifica**, espandere le opzioni per **Sviluppo Python** sul lato destro e selezionare **Anaconda3** (32 bit o 64 bit). Si noti che l'installazione potrebbe richiedere alcuni minuti a seconda della velocità di Internet, tuttavia questo è il modo più semplice per installare i pacchetti necessari.

1. Avviare Visual Studio.

1. Selezionare **File**  >  **Nuovo**  >  **da Cookiecutter.** Questo comando apre una finestra in Visual Studio in cui è possibile esplorare i modelli.

    ![Nuovo progetto da un modello di Cookiecutter](media/projects-from-cookiecutter1.png)

1. Selezionare il modello **Microsoft/python-sklearn-classifier-cookiecutter**, quindi selezionare **Avanti**. La prima volta che si usa un modello specifico, il processo può richiedere alcuni minuti, dato che Visual Studio deve installare i pacchetti Python necessari.

1. Nel passaggio successivo impostare un percorso per il nuovo progetto nel campo **Crea in** e quindi selezionare **Crea e apri progetto**.

    ![Secondo passaggio usando Cookiecutter, impostazione delle proprietà del progetto](media/projects-from-cookiecutter2.png)

1. Al termine del processo, viene visualizzato il messaggio **Successfully created files using template... (Creazione di file con modello completata con il modello...**). Il progetto viene aperto in Esplora soluzioni automatico.

1. Premere **CTRL** + **F5 o** selezionare **Debug** Avvia senza  >  **eseguire debug** per eseguire il programma.

    ![Output del progetto del modello python-sklearn-classifier-cookiecutter](media/projects-from-cookiecutter4.png)

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Esercitazione: Usare Python in Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Vedi anche

- [Usare l'estensione Cookiecutter](using-python-cookiecutter-templates.md)
- [Identificare manualmente un interprete Python esistente](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
- [Installare il supporto di Python in Visual Studio 2015 e versioni precedenti](installing-python-support-in-visual-studio.md)
- [Percorsi di installazione](installing-python-support-in-visual-studio.md#install-locations)
