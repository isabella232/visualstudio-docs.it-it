---
title: 'Procedura: Creare e rimuovere dipendenze di progetto'
description: Informazioni su come usare Visual Studio creare e rimuovere la dipendenza del progetto dal codice da altri progetti.
ms.custom: SEO-VS-2020
ms.date: 06/21/2017
ms.topic: how-to
f1_keywords:
- VS.ProjectDependenciesDlg
helpviewer_keywords:
- vs.build.projectdependencies
- project dependencies
- builds [Visual Studio], setting up
- project build configurations, dependencies
- dependencies, project
- projects [Visual Studio], dependencies
ms.assetid: e2a0a8ff-dae7-40a8-b774-b88aa5235183
ms.technology: vs-ide-compile
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0e2a29e655d562dcd70f6af8089d37a500e3277494b812d74ba7e19772a3ec02
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121357869"
---
# <a name="how-to-create-and-remove-project-dependencies"></a>Procedura: Creare e rimuovere dipendenze di progetto

Quando si compila una soluzione che contiene più progetti, può essere necessario prima compilare alcuni progetti, per generare il codice usato da altri progetti. Quando un progetto usa codice eseguibile generato da un altro progetto, il progetto che genera il codice viene definito come dipendenza del progetto che usa il codice. Tali relazioni di dipendenza possono essere definite nella finestra di dialogo **Dipendenze progetto**.

## <a name="to-assign-dependencies-to-projects"></a>Per assegnare le dipendenze ai progetti

1. In **Esplora soluzioni** selezionare un progetto.

2. Nel menu **Proprietà** scegliere **Dipendenze progetto**.

    Viene visualizzata la finestra di dialogo **Dipendenze progetto**.

   > [!NOTE]
   > L'opzione **Dipendenze progetto** è disponibile solo in una soluzione con più progetti.

3. Nella scheda **Dipendenze** selezionare un progetto dal menu a discesa **Progetto**.

4. Nel campo **Dipendente da** selezionare la casella di controllo di qualsiasi altro progetto da compilare prima del progetto specificato.

   La soluzione deve contenere più di un progetto per poter creare dipendenze di progetto.

## <a name="to-remove-dependencies-from-projects"></a>Per rimuovere dipendenze dai progetti

1. In **Esplora soluzioni** selezionare un progetto.

2. Nel menu **Proprietà** scegliere **Dipendenze progetto**.

     Viene visualizzata la finestra di dialogo **Dipendenze progetto**.

    > [!NOTE]
    > L'opzione **Dipendenze progetto** è disponibile solo in una soluzione con più progetti.

3. Nella scheda **Dipendenze** selezionare un progetto dal menu a discesa **Progetto**.

4. Nel campo **Dipendente da** deselezionare le caselle di controllo accanto agli altri progetti che non sono più dipendenze del progetto specificato.

## <a name="see-also"></a>Vedi anche

- [Compilazione e pulizia di progetti e soluzioni in Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Compilare](../ide/compiling-and-building-in-visual-studio.md)
- [Informazioni sulle configurazioni della build](../ide/understanding-build-configurations.md)
- [Gestire le proprietà di progetti e soluzioni](managing-project-and-solution-properties.md)
