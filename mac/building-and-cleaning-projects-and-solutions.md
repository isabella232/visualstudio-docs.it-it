---
title: Compilazione e pulizia di progetti e soluzioni
description: Questo articolo descrive come compilare un progetto in Visual Studio per Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/19/2019
ms.assetid: E4B6CB42-9FE2-43B9-93B7-BD4BD50518B1
ms.openlocfilehash: 924bdb08154ecb3caad04cabf7e860bed9204e98
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/20/2020
ms.locfileid: "71128449"
---
# <a name="building-and-cleaning-projects-and-solutions"></a>Compilazione e pulizia di progetti e soluzioni

Seguire i passaggi descritti in questo articolo per informazioni su come compilare, ricompilare o pulire tutti o alcuni progetti in una soluzione.

> [!NOTE]
> Questo argomento si applica a Visual Studio per Mac. Per Visual Studio in Windows, vedere [Compilare e pulire progetti e soluzioni in Visual Studio.](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)

## <a name="to-build-rebuild-or-clean-an-entire-solution"></a>Per compilare, ricompilare o pulire un'intera soluzione

1. Selezionare il nodo Soluzione nel **riquadro Della soluzione:**

    ![Selezione del nodo della soluzione](media/compiling-and-building-image1.png)

2. Selezionate il menu **Compila** nella barra dei menu e scegliete una delle seguenti opzioni:

    ![Selezione della voce di menu Compila tutto](media/compiling-and-building-image2.png)

    * Scegliere **Compila tutto** per compilare i file e i componenti all'interno del progetto che sono stati modificati dopo la compilazione più recente.

    * Scegliere **Ricompila tutto** per "pulire" la soluzione, quindi compilare tutti i file e i componenti di progetto.

    * Scegliere **Pulisci tutto** per eliminare tutti i file intermedi e di output. Quando sono rimasti solo i file dei componenti e dei progetti, è possibile compilare nuove istanze di file intermedi e di output.

## <a name="to-build-or-rebuild-a-single-project"></a>Per compilare o ricompilare un progetto singolo

1. Selezionare il progetto nel **riquadro della soluzione**.

2. Selezionare il menu **Compila** dalla barra dei menu.

3. Scegliere Compila [NomeProgetto], Ricompila[NomeProgetto] o Pulisci[NomeProgetto].

## <a name="to-stop-a-build"></a>Per interrompere una compilazione

Per interrompere una compilazione, utilizzare una delle opzioni seguenti:

* Premere il quadrato rosso nell'area di stato:

    ![Premere il quadrato rosso per interrompere la compilazione](media/compiling-and-building-image3.png)

* Utilizzare la voce **Stop** nel menu **Compila** .

* Premete **Comando (Mac OS) e Premete Maiusc (Windows) o Comando (Mac**OS

## <a name="see-also"></a>Vedere anche

- [Compilazione e pulizia di progetti e soluzioni (Visual Studio in Windows)](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)