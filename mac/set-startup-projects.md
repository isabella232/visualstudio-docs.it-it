---
title: Impostare più progetti di avvio
description: Questo articolo descrive come impostare più progetti di avvio durante l'esecuzione o il debug.
author: jmatthiesen
ms.author: jomatthi
ms.date: 11/09/2020
ms.topic: how-to
ms.prod: visual-studio-mac
ms.assetid: fd354fff-ce6b-4505-a815-84a2311e39ba
ms.openlocfilehash: df1e088a5e2d0f65d8b72dad0895f1edb1740f1f
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2021
ms.locfileid: "123964661"
---
# <a name="set-multiple-startup-projects"></a>Impostare più progetti di avvio

Visual Studio per Mac consente di specificare se avviare più di un progetto durante il debug o l'esecuzione della soluzione.

## <a name="to-set-multiple-startup-projects"></a>Per impostare più progetti di avvio

1. Nella finestra della soluzione selezionare la soluzione (il nodo principale).

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

   Ora i due progetti sono configurati per l'avvio, rappresentato da entrambi i progetti visualizzati in **grassetto** nella finestra della soluzione. Nella barra degli strumenti la nuova configurazione di esecuzione è impostata come configurazione di esecuzione della soluzione corrente.

## <a name="next-steps"></a>Passaggi successivi

- [Compilazione e creazione di build in Visual Studio per Mac](compiling-and-building.md)
- [Informazioni sulle configurazioni della build](configurations.md)
