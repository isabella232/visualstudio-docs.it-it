---
title: Impostare più progetti di avvio
description: Questo articolo descrive come impostare più progetti di avvio durante l'esecuzione o il debug.
author: sayedihashimi
ms.author: sayedha
ms.date: 12/13/2019
ms.topic: how-to
ms.prod: visual-studio-mac
ms.assetid: fd354fff-ce6b-4505-a815-84a2311e39ba
ms.openlocfilehash: e0e1af97ec91af4105d1934a431f9aabc6562793
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85950111"
---
# <a name="set-multiple-startup-projects"></a>Impostare più progetti di avvio

Visual Studio per Mac consente di specificare se avviare più di un progetto durante il debug o l'esecuzione della soluzione.

## <a name="to-set-multiple-startup-projects"></a>Per impostare più progetti di avvio

1. Nel riquadro della soluzione selezionare la soluzione (il primo nodo in alto).

2. Fare clic con il pulsante destro del mouse sul nodo della soluzione e scegliere **Imposta progetti di avvio**:

   ![Selezionare Imposta progetti di avvio](media/startup-proj-ctx-menu.png)

3. Verrà visualizzata la finestra di dialogo **Crea configurazione di esecuzione della soluzione**. Questa finestra di dialogo consente di creare una nuova configurazione di esecuzione della soluzione denominata per la soluzione. È possibile usare qualsiasi nome. Il nome predefinito è `Multiple Projects`.

   ![Finestra di dialogo Crea configurazione di esecuzione della soluzione](media/create-sln-run-config.png)

4. Selezionare **Crea configurazione di esecuzione**. Verrà visualizzata la finestra di dialogo **Opzioni soluzione** con la nuova configurazione di esecuzione della soluzione selezionata.

   ![Finestra di dialogo Opzioni soluzione](media/sln-options-run-config-multi-projects.png)

5. Selezionare i progetti che si vuole avviare durante il debug o l'esecuzione dell'app da Visual Studio per Mac.

   ![Finestra di dialogo Opzioni soluzione con i progetti selezionati](media/sln-options-run-config-multi-projects-configured.png)

6. Selezionare **OK**. La nuova configurazione di esecuzione della soluzione viene impostata come configurazione di esecuzione attiva.

   ![Soluzione con più progetti configurati da avviare in fase di debug o esecuzione](media/startup-project-configured.png)

   Si può notare che sono stati configurati due progetti da avviare perché entrambi sono in **grassetto** nel riquadro della soluzione. Nella barra degli strumenti la nuova configurazione di esecuzione è impostata come configurazione di esecuzione della soluzione corrente.

## <a name="next-steps"></a>Passaggi successivi

- [Compilazione e creazione di build in Visual Studio per Mac](compiling-and-building.md)
- [Informazioni sulle configurazioni della build](configurations.md)
