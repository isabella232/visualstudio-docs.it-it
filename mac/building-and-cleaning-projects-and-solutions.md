---
title: Compilazione e pulizia di progetti e soluzioni
description: Questo articolo descrive come compilare un progetto in Visual Studio per Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/19/2019
ms.assetid: E4B6CB42-9FE2-43B9-93B7-BD4BD50518B1
ms.topic: how-to
ms.openlocfilehash: de6be4b509eff8a013f7367614e0016f810b3657
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710481"
---
# <a name="building-and-cleaning-projects-and-solutions"></a>Compilazione e pulizia di progetti e soluzioni

Seguire i passaggi descritti in questo articolo per informazioni su come compilare, ricompilare o pulire tutti o alcuni progetti in una soluzione.

> [!NOTE]
> Questo argomento si applica a Visual Studio per Mac. Per Visual Studio su Windows, vedere [Compilare](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)e pulire progetti e soluzioni in Visual Studio .

## <a name="to-build-rebuild-or-clean-an-entire-solution"></a>Per compilare, ricompilare o pulire un'intera soluzione

1. Selezionare il nodo Soluzione nella **finestra della soluzione:**

    ![Selezione del nodo della soluzione](media/compiling-and-building-image1.png)

2. Selezionare **il** menu Compila nella barra dei menu e scegliere una delle opzioni seguenti:

    ![Selezione della voce di menu Compila tutto](media/compiling-and-building-image2.png)

    * Scegliere **Compila tutto** per compilare i file e i componenti all'interno del progetto modificati dopo la compilazione più recente.

    * Scegliere **Ricompila tutto** per "pulire" la soluzione e quindi compilare tutti i componenti e i file di progetto.

    * Scegliere **Pulisci tutto per** eliminare tutti i file intermedi e di output. Quando sono rimasti solo i file dei componenti e dei progetti, è possibile compilare nuove istanze di file intermedi e di output.

## <a name="to-build-or-rebuild-a-single-project"></a>Per compilare o ricompilare un progetto singolo

1. Selezionare il progetto nella **finestra della soluzione.**

2. Selezionare il menu **Compila** dalla barra dei menu.

3. Scegliere Build[ProjectName], Rebuild[ProjectName] o Clean[ProjectName].

## <a name="to-stop-a-build"></a>Per interrompere una compilazione

Per arrestare una compilazione, usare una delle opzioni seguenti:

* Premere il quadrato rosso nell'area di stato:

    ![Premere il quadrato rosso per interrompere la compilazione](media/compiling-and-building-image3.png)

* Usare la **voce** Arresta **nel** menu Compila.

* Premere **CMD+MAIUSC+INVIO.**

## <a name="see-also"></a>Vedi anche

- [Compilazione e pulizia di progetti e soluzioni (Visual Studio in Windows)](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)