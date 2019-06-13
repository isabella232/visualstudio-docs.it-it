---
title: Creazione di nuovi progetti e soluzioni
description: Questo articolo descrive come creare progetti e soluzioni in Visual Studio per Mac
author: conceptdev
ms.author: crdun
ms.date: 05/23/2019
ms.assetid: 5880BB10-0A12-47E2-8A82-7A2D59C4D579
ms.openlocfilehash: 045d92365501b888e56ce4ae397331e597b5b33a
ms.sourcegitcommit: 51dad3e11d7580567673e0d426ab3b0a17584319
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/10/2019
ms.locfileid: "66820737"
---
# <a name="creating-a-new-project"></a>Creazione di un nuovo progetto

## <a name="opening-the-project-creation-dialog"></a>Aprire la finestra di dialogo di creazione progetto

Esistono alcuni modi per creare un nuovo progetto in Visual Studio per Mac. Quando si apre innanzitutto Visual Studio per Mac, verrà visualizzata la schermata iniziale. Da qui è possibile scegliere **New** che verrà visualizzata la schermata di creazione del progetto.

> [!TIP]
> Inoltre, dalla schermata iniziale, è possibile anche aprire e cercare, progetti e soluzioni recenti. È anche possibile aprire progetti recenti accedendo alla barra dei menu e scegliendo **File > soluzioni recenti**

![Schermata iniziale con Crea nuovo progetto](media/first-run-project.png)

Se Visual Studio per Mac è già aperto con una soluzione caricata, è possibile creare una nuova soluzione accedendo alla barra dei menu e scegliendo **File > nuova soluzione**. Creare una nuova soluzione in questo modo verrà chiusa la soluzione che è già stata caricata.

## <a name="creating-a-new-project-from-a-template"></a>Crea un nuovo progetto da un modello

Il **nuovo progetto** finestra di dialogo, per impostazione predefinita, Mostra i modelli usati di recente vengono ordinati *usati più di recente*.

Se non vuoi usare un modello di recente, è possibile scegliere tra le categorie a sinistra della finestra di dialogo. Ogni categoria include diversi modelli di progetto per cui scegliere. Facendo clic su un tipo di progetto consente di visualizzare una descrizione sul lato destro dello schermo.

![Schermata Nuovo progetto](media/project-creation-screen.png)

## <a name="configuring-your-new-project"></a>Configurazione del nuovo progetto

Dopo aver scelto un modello di progetto, schermate riportate di seguito illustra in dettaglio eventuali passaggi di configurazione necessari per configurare il progetto. Questo può variare ogni tipo di progetto.

Tutti i progetti richiedono un nuovo progetto, insieme a un percorso per archiviare i file. Se il progetto fa parte di una nuova soluzione, anziché aggiungerlo a una soluzione esistente, un nome di soluzione sarà anche necessario.

Facoltativamente, in questa fase è anche possibile configurare le opzioni di controllo codice sorgente di Git. L'immagine seguente è riportato un esempio dell'ultimo passaggio di configurazione per un progetto .NET Core:

![Configurazione di un nuovo progetto](media/configure-new-project.png)

## <a name="adding-additional-projects-to-a-solution"></a>Aggiunta di ulteriori progetti a una soluzione

È possibile aggiungere ulteriori progetti a una soluzione facendo clic la soluzione nel riquadro della soluzione e scegliendo uno **Aggiungi > Aggiungi nuovo progetto** oppure **Aggiungi > Aggiungi progetto esistente**.

Aggiunge un nuovo progetto illustra in dettaglio la creazione del progetto, come illustrato nella [configurazione del nuovo progetto](#configuring-your-new-project).

Scegliere di aggiungere un progetto esistente verrà consentono a ricerca di un progetto esistente nel computer e aggiungerlo alla soluzione.

## <a name="see-also"></a>Vedere anche

- [Creare soluzioni e progetti (Visual Studio in Windows)](/visualstudio/ide/creating-solutions-and-projects)