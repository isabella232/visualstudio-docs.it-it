---
title: 'Finestra di progettazione del flusso di lavoro - procedura: creare progetti flusso di lavoro (Legacy)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- workflow projects, creating
- projects, workflow
ms.assetid: 32299555-662c-469d-a90d-89f4700dc78c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bb5d58c6d450a5e68d804e33785ec76349bfb6d8
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-workflow-projects-legacy"></a>Procedura: creare progetti di flusso di lavoro (legacy)

Seguire questi passaggi per creare un progetto di Windows Workflow Foundation (WF) destinato a .NET Framework versione 3.5 o la WinFX. Questa procedura utilizza la finestra di progettazione del flusso di lavoro Windows legacy fornita da Visual Studio 2010.

## <a name="to-create-a-workflow-project"></a>Creazione di un Progetto di flusso di lavoro 

1.  Avviare Visual Studio.

2.  Nel menu **File** scegliere **Nuovo** e quindi selezionare **Progetto**.

     Verrà visualizzata la finestra di dialogo **Nuovo progetto** .

3.  Selezionare il **.NET Framework 3.0** opzione o **.NET Framework 3.5** opzione nella casella di riepilogo nella parte superiore del **nuovo progetto** finestra per accedere alla finestra di progettazione legacy.

    > [!NOTE]
    > L'opzione predefinita in Visual Studio 2010 viene **.NET Framework 4**. Questa opzione viene utilizzata per creare applicazioni di Windows Workflow Foundation (WF) che hanno come destinazione di .NET Framework 4 e non utilizza la finestra di progettazione legacy.

4.  Nel **tipi di progetto** riquadro, selezionare progetti Visual c# o Visual Basic (progetti), quindi **flusso di lavoro**.

5.  Nel **modelli** riquadro, selezionare uno dei modelli di progetto installati:

    -   Applicazione console del flusso di lavoro sequenziale

    -   Libreria del flusso di lavoro sequenziale

    -   Libreria delle attività del flusso di lavoro

    -   Applicazione console del flusso di lavoro della macchina a stati

    -   Libreria del flusso di lavoro di una macchina a stati

    -   Progetto del flusso di lavoro vuoto

6.  Nel **nome** , immettere un nome descrittivo per il progetto per renderlo facilmente identificabile.

7.  Nel **percorso** , immettere la directory in cui si desidera salvare il progetto oppure fare clic su **Sfoglia** per passare alla directory.

     Se si desidera una directory della soluzione creata per il progetto, selezionare il **Crea directory per soluzione** casella di controllo e immettere un nome per il **Nome soluzione** casella.

8.  Fare clic su **OK**.

## <a name="see-also"></a>Vedere anche

- [Creazione di progetti flusso di lavoro legacy](../workflow-designer/creating-legacy-workflow-projects.md)