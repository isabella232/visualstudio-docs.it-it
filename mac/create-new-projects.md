---
title: Creazione di nuovi progetti e soluzioni
description: Questo articolo descrive come creare progetti e soluzioni in Visual Studio per Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/23/2019
ms.assetid: 5880BB10-0A12-47E2-8A82-7A2D59C4D579
ms.openlocfilehash: dbfc0d951524bb9ffbbd4a2366679cfc6ae41925
ms.sourcegitcommit: 7fbfb2a1d43ce72545096c635df2b04496b0be71
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/09/2019
ms.locfileid: "67693056"
---
# <a name="creating-a-new-project"></a>Creazione di un nuovo progetto

## <a name="opening-the-project-creation-dialog"></a>Apertura della finestra di dialogo per la creazione del progetto

È possibile creare un nuovo progetto in Visual Studio per Mac in diversi modi. Quando si apre Visual Studio per Mac, viene visualizzata la schermata iniziale. Da qui è possibile scegliere **Nuovo** per passare alla schermata per la creazione del progetto.

> [!TIP]
> Dalla schermata iniziale è inoltre possibile aprire e cercare i progetti e le soluzioni recenti. Per aprire i progetti recenti si può anche scegliere **File > Soluzioni recenti** dalla barra dei menu

![Schermata iniziale con l'opzione per creare un nuovo progetto](media/first-run-project.png)

Se Visual Studio per Mac è già aperto con una soluzione caricata, è possibile creare una nuova soluzione scegliendo **File > Nuova soluzione** dalla barra dei menu. Se si crea una nuova soluzione in questo modo, la soluzione già caricata verrà chiusa.

## <a name="creating-a-new-project-from-a-template"></a>Creazione di un progetto da un modello

La finestra dialogo **Nuovo progetto** mostra, per impostazione predefinita, i modelli usati di recente, ordinati a partire da quelli *più recenti*.

Se non si vuole usare un modello recente, è possibile scegliere tra le categorie visualizzate sul lato sinistro della finestra di dialogo. Ogni categoria include più modelli di progetto disponibili per la selezione. Facendo clic su un tipo di progetto è possibile visualizzare la relativa descrizione sul lato destro della schermata.

![schermata di un nuovo progetto](media/project-creation-screen.png)

## <a name="configuring-your-new-project"></a>Configurazione del nuovo progetto

Dopo aver scelto un modello di progetto, è possibile usare le schermate successive per eseguire i passaggi necessari per configurare il progetto. La procedura può variare a seconda del tipo di progetto.

Per tutti i progetti è necessario specificare un nuovo progetto e un percorso in cui archiviare i file. Se il progetto fa parte di una nuova soluzione, anziché essere incluso in una soluzione esistente, è necessario specificare anche un nome di soluzione.

In questa fase è eventualmente possibile configurare anche le opzioni di controllo del codice sorgente Git. L'immagine seguente mostra un esempio dell'ultimo passaggio di configurazione per un progetto .NET Core:

![Configurazione di un nuovo progetto](media/configure-new-project.png)

## <a name="adding-additional-projects-to-a-solution"></a>Aggiunta di altri progetti a una soluzione

È possibile aggiungere altri progetti a una soluzione facendo clic con il pulsante destro del mouse sulla soluzione nel riquadro della soluzione e scegliendo **Aggiungi > Aggiungi nuovo progetto** oppure **Aggiungi > Aggiungi progetto esistente**.

Se si aggiunge un nuovo progetto, è necessario eseguire la procedura per la creazione del progetto, come illustrato in [Configurazione del nuovo progetto](#configuring-your-new-project).

Se si sceglie di aggiungere un progetto esistente, è possibile cercare un progetto esistente nel computer e aggiungerlo alla soluzione.

## <a name="see-also"></a>Vedere anche

- [Creare soluzioni e progetti (Visual Studio in Windows)](/visualstudio/ide/creating-solutions-and-projects)