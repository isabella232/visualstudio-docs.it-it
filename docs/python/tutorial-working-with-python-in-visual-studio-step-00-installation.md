---
title: Esercitazione sull'uso di Python in Visual Studio, passaggio 0, installazione
titleSuffix: ''
description: Passaggio 0 (prerequisiti di installazione) della procedura dettagliata di base per l'utilizzo di Python in Visual Studio.
ms.date: 09/14/2021
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: vs-acquisition
ms.workload:
- python
- data-science
ms.openlocfilehash: 1e712d5df44dd87f07b50b243e8e63ed9e1ad0bf
ms.sourcegitcommit: 811e4ee80311433fefbe6d6223bf72c431008403
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2021
ms.locfileid: "127890435"
---
# <a name="install-python-support-in-visual-studio"></a>Installare il supporto Python in Visual Studio

> [!Note]
> Il supporto di Python è attualmente disponibile solo in Visual Studio per Windows. In Mac e Linux il supporto python è disponibile [tramite Visual Studio Code](https://code.visualstudio.com/docs/python/python-tutorial).

1. Scaricare ed eseguire il programma di Visual Studio più recente per Windows. Il supporto di Python è presente nella versione 15.2 e successive. Se è già Visual Studio installato, aprire Visual Studio ed eseguire il programma di installazione selezionando Strumenti  >  **Aggiungi strumenti e funzionalità**.

    > [!div class="nextstepaction"]
    > [Installa Visual Studio Community](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted)

    >[!Tip]
    > L'edizione Community è per singoli sviluppatori, per la formazione in classe, la ricerca accademica e per lo sviluppo open source. Per altri usi, installare [Visual Studio Professional](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Professional&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted) oppure [Visual Studio Enterprise](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Enterprise&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted).

1. Il programma di installazione offre un elenco di carichi di lavoro, che sono gruppi di opzioni correlate per aree di sviluppo specifico. Per Python, selezionare il carico di lavoro **Sviluppo Python** e selezionare **Installa**:

    ![Screenshot del carico di lavoro sviluppo Python selezionato nel programma di Visual Studio di installazione.](media/installation-python-workload.png)

1. Per testare rapidamente il supporto python, avviare Visual Studio, premere **ALT** I per aprire +  la finestra **Python Interactive** e immettere `2+2` . Se non viene visualizzato l'output **4**, eseguire nuovamente la procedura.

    ::: moniker range="<=vs-2019"
    ![Screenshot del test di Python tramite la finestra interattiva.](media/installation-interactive-test.png)
    ::: moniker-end

    ::: moniker range=">=vs-2022"
    ![Screenshot del test di Python tramite la finestra interattiva Visual Studio 2022.](media/vs-2022/python-interactive.png)
    ::: moniker-end

## <a name="next-step"></a>Passaggio successivo

> [!div class="nextstepaction"]
> [Passaggio 1: Creare un progetto Python](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Vedi anche

- [Identificare manualmente un interprete Python esistente](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
- [Installare il supporto di Python in Visual Studio 2015 e versioni precedenti](installing-python-support-in-visual-studio.md)
- [Percorsi di installazione](installing-python-support-in-visual-studio.md#install-locations)
