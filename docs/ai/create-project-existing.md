---
title: Creare un progetto AI da codice esistente
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: 8c0909259291bc5d2db2c4a9c8b87b1a0321d362
ms.sourcegitcommit: 48e93538f1e352fc1f972b642bb5fcce2f6834a2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2020
ms.locfileid: "85371716"
---
# <a name="create-an-ai-project-from-existing-code"></a>Creare un progetto AI da codice esistente

Dopo aver [installato Visual Studio Tools for AI](installation.md) è facile aggiungere codice Python esistente in un progetto di Visual Studio.

> [!Important]
> Il processo descritto non sposta o copia i file di origine. Se si vuole usare una copia, per prima cosa duplicare la cartella.

1. Avviare Visual Studio e selezionare **File > Nuovo > Progetto**.

2. Nella finestra di dialogo **Nuovo progetto** cercare "**AI Tools**" (Strumenti AI), selezionare il modello "**Da codice Python esistente**", assegnare al progetto un nome e una posizione e selezionare **OK**.

   ![Nuovo progetto da codice esistente, passaggio 1](media/create-project-existing/new-ai-project.png)

3. Nella procedura guidata visualizzata impostare il percorso del codice esistente, un filtro per i tipi di file ed eventuali percorsi di ricerca richiesti dal progetto, quindi selezionare **OK**. Se non si sa quali sono i percorsi di ricerca, lasciare vuoto il campo.

   ![Nuovo progetto da codice esistente, passaggio 2](media/create-project-existing/azurebatch-newproject.png)

   Se il codice esistente fa parte di un progetto di Azure Machine Learning, selezionare **Is Azure Machine Learning folder** (Cartella di Azure Machine Learning) per assicurarsi che vengano convertiti correttamente dettagli di configurazione di Azure Machine Learning importanti, come l'account di sperimentazione, l'area di lavoro, i contesti di calcolo da usare e altro ancora.

4. Per impostare un file di avvio, individuare il file in **Esplora soluzioni**, fare clic con il pulsante destro del mouse e scegliere **Imposta come file di avvio**.

5. Eseguire il programma premendo **CTRL** + **F5** o selezionando **debug > avvia senza eseguire debug**.

> [!div class="nextstepaction"]
> [Esercitazione: uso di Python in Visual Studio](../python/tutorial-working-with-python-in-visual-studio-step-00-installation.md)

## <a name="see-also"></a>Vedi anche

- [Identificazione manuale di un ambiente Phyton esistente](../python/managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
