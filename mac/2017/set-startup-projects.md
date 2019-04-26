---
title: Impostare più progetti di avvio in Visual Studio per Mac
description: Questo articolo descrive come impostare più progetti di avvio durante l'esecuzione o il debug.
author: sayedihashimi
ms.author: sayedha
ms.date: 02/21/2019
ms.topic: conceptual
ms.prod: visual-studio-mac
ms.assetid: fd354fff-ce6b-4505-a815-84a2311e39ba
ms.openlocfilehash: a4a4f2f4fd4ce6cd88d11979a21e4e9184adfca8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62988509"
---
# <a name="how-to-set-multiple-startup-projects"></a>Procedura: Impostare più progetti di avvio

Visual Studio per Mac consente di specificare se avviare più di un progetto durante il debug o l'esecuzione della soluzione.

## <a name="to-set-multiple-startup-projects"></a>Per impostare più progetti di avvio

1. Nel **riquadro della soluzione** selezionare la soluzione (il primo nodo in alto).

2. Scegliere il menu di scelta rapida del nodo della soluzione facendo clic con il pulsante destro del mouse, quindi scegliere **Imposta progetti di avvio...**.

   ![Menu di scelta rapida Imposta progetti di avvio](media/startup-proj-ctx-menu.png)

3. Verrà visualizzata la finestra di dialogo **Crea configurazione di esecuzione della soluzione**. In questa finestra di dialogo si creerà una nuova configurazione di esecuzione della soluzione denominata per la soluzione. È possibile assegnare qualsiasi nome. Il nome predefinito è `Multiple Projects`.

   ![Finestra di dialogo Crea configurazione di esecuzione della soluzione](media/create-sln-run-config.png)

4. Fare clic su **Crea configurazione di esecuzione**. Si aprirà la finestra di dialogo **Opzioni soluzione** con la nuova configurazione di esecuzione della soluzione selezionata.

   ![Finestra di dialogo Opzioni soluzione](media/sln-options-run-config-multi-projects.png)

5. Selezionare i progetti che si vuole avviare durante il debug o l'esecuzione dell'applicazione da Visual Studio per Mac.

   ![Finestra di dialogo Opzioni soluzione con la configurazione di esecuzione configurata](media/sln-options-run-config-multi-projects-configured.png)

6. Fare clic su **OK**. La finestra di dialogo verrà chiusa e la nuova configurazione di esecuzione della soluzione viene impostata come configurazione di esecuzione attiva.

   ![Soluzione con più progetti configurati da avviare in fase di debug o esecuzione](media/startup-project-configured.png) Si può notare che sono stati configurati due progetti da avviare perché entrambi sono in **grassetto** nel **riquadro della soluzione**. Nella barra degli strumenti la nuova configurazione di esecuzione è configurata come configurazione di esecuzione della soluzione corrente.

## <a name="next-steps"></a>Passaggi successivi

- [Compilazione e creazione di build in Visual Studio per Mac](compiling-and-building.md)
- [Informazioni sulle configurazioni della build](configurations.md)