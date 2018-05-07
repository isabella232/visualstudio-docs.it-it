---
title: 'Procedura: Creare e rimuovere dipendenze di progetto'
ms.date: 06/21/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5b0948dab860431d9693e67489d958f00743fa17
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-and-remove-project-dependencies"></a>Procedura: Creare e rimuovere dipendenze di progetto

Quando si compila una soluzione che contiene più progetti, può essere necessario prima compilare alcuni progetti, per generare il codice usato da altri progetti. Quando un progetto usa codice eseguibile generato da un altro progetto, il progetto che genera il codice viene definito come dipendenza del progetto che usa il codice. Tali relazioni di dipendenza possono essere definite nella finestra di dialogo **Dipendenze progetto**.

## <a name="to-assign-dependencies-to-projects"></a>Per assegnare le dipendenze ai progetti

1.  Selezionare un progetto in **Esplora soluzioni**.

2.  Nel menu **Proprietà** scegliere **Dipendenze progetto**.

     Viene visualizzata la finestra di dialogo **Dipendenze progetto**.

    > [!NOTE]
    > L'opzione **Dipendenze progetto** è disponibile solo in una soluzione con più progetti.

3.  Nella scheda **Dipendenze** selezionare un progetto dal menu a discesa **Progetto**.

4.  Nel campo **Dipendente da** selezionare la casella di controllo di qualsiasi altro progetto da compilare prima del progetto specificato.

 La soluzione deve contenere più di un progetto per poter creare dipendenze di progetto.

## <a name="to-remove-dependencies-from-projects"></a>Per rimuovere dipendenze dai progetti

1.  Selezionare un progetto in **Esplora soluzioni**.

2.  Nel menu **Proprietà** scegliere **Dipendenze progetto**.

     Viene visualizzata la finestra di dialogo **Dipendenze progetto**.

    > [!NOTE]
    > L'opzione **Dipendenze progetto** è disponibile solo in una soluzione con più progetti.

3.  Nella scheda **Dipendenze** selezionare un progetto dal menu a discesa **Progetto**.

4.  Nel campo **Dipendente da** deselezionare le caselle di controllo accanto agli altri progetti che non sono più dipendenze del progetto specificato.

## <a name="see-also"></a>Vedere anche

- [Compilazione e pulizia di progetti e soluzioni in Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Compilare](../ide/compiling-and-building-in-visual-studio.md)
- [Informazioni sulle configurazioni della build](../ide/understanding-build-configurations.md)
- [Gestione delle proprietà di progetti e soluzioni](managing-project-and-solution-properties.md)