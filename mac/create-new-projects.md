---
title: Creazione di nuovi progetti e soluzioni
description: Questo articolo descrive come creare progetti e soluzioni in Visual Studio per Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/06/2020
ms.assetid: 5880BB10-0A12-47E2-8A82-7A2D59C4D579
ms.openlocfilehash: c84fee5e4180caa59610fbcbcba85d3fc301341f7f77880f0a248f6bdde5fa06
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121266415"
---
# <a name="create-a-new-project"></a>Creazione di un nuovo progetto

## <a name="opening-the-project-creation-dialog"></a>Apertura della finestra di dialogo per la creazione del progetto

È possibile creare un nuovo progetto in Visual Studio per Mac in diversi modi. Quando si apre per la Visual Studio per Mac, viene visualizzata la finestra iniziale. Da qui è possibile scegliere **Nuovo** per visualizzare la schermata di creazione del progetto.

> [!TIP]
> Inoltre, dalla finestra iniziale è anche possibile aprire e cercare progetti e soluzioni recenti. Per aprire i progetti recenti si può anche scegliere **File > Soluzioni recenti** dalla barra dei menu

![Finestra iniziale con crea nuovo progetto](media/first-run-project.png)

Se Visual Studio per Mac è già aperto con una soluzione caricata, è possibile creare una nuova soluzione scegliendo **File > Nuova soluzione** dalla barra dei menu. La creazione di una nuova soluzione in questo modo chiude la soluzione già caricata.

## <a name="creating-a-new-project"></a>Creazione di un nuovo progetto

La finestra dialogo **Nuovo progetto** mostra, per impostazione predefinita, i modelli usati di recente, ordinati a partire da quelli *più recenti*.

Se non si vuole usare un modello recente, è possibile scegliere tra le categorie visualizzate sul lato sinistro della finestra di dialogo. Ogni categoria include più modelli di progetto disponibili per la selezione. Facendo clic su un tipo di progetto è possibile visualizzare la relativa descrizione sul lato destro della schermata.

![schermata di un nuovo progetto](media/project-creation-screen.png)

## <a name="configuring-your-new-project"></a>Configurazione del nuovo progetto

Dopo aver scelto un modello di progetto, è possibile usare le schermate successive per eseguire i passaggi necessari per configurare il progetto. La procedura può variare a seconda del tipo di progetto.

Per tutti i progetti è necessario specificare un nuovo progetto e un percorso in cui archiviare i file. Se il progetto fa parte di una nuova soluzione, anziché essere incluso in una soluzione esistente, è necessario specificare anche un nome di soluzione.

In questa fase è eventualmente possibile configurare anche le opzioni di controllo del codice sorgente Git. L'immagine seguente mostra un esempio dell'ultimo passaggio di configurazione per un progetto .NET Core:

![Configurazione di un nuovo progetto](media/configure-new-project.png)

## <a name="adding-additional-projects-to-a-solution"></a>Aggiunta di altri progetti a una soluzione

È possibile aggiungere altri progetti a una soluzione  facendo clic con il pulsante destro del mouse sulla soluzione nella finestra della soluzione e scegliendo Aggiungi > Aggiungi nuovo **Project** o Aggiungi > Aggiungi Project **.**

Se si aggiunge un nuovo progetto, è necessario eseguire la procedura per la creazione del progetto, come illustrato in [Configurazione del nuovo progetto](#configuring-your-new-project).

Se si sceglie di aggiungere un progetto esistente, è possibile cercare un progetto esistente nel computer e aggiungerlo alla soluzione.

## <a name="see-also"></a>Vedi anche

- [Creare soluzioni e progetti (Visual Studio in Windows)](/visualstudio/ide/creating-solutions-and-projects)
