---
title: 'Finestra di progettazione del flusso di lavoro - procedura: creare applicazioni di Console del flusso di lavoro macchina a stati (Legacy)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- console applications, state machine workflows
- state machine workflow console applications
- state machine workflows, console applicationa
ms.assetid: d6170b5d-5d4f-48e1-8257-c78604f27eac
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 805b048a9e30f7a637e178d223b962259dadd926
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
ms.locfileid: "31971349"
---
# <a name="how-to-create-state-machine-workflow-console-applications-legacy"></a>Procedura: creare applicazioni console flusso di lavoro di una macchina a stati (legacy)

Seguire questi passaggi per creare un progetto di applicazione Console flusso di lavoro macchina a stati usando la finestra di progettazione del flusso di lavoro Windows fornita da Visual Studio 2010. Utilizzare la finestra di progettazione del flusso di lavoro legacy quando è necessario avere come destinazione .NET Framework versione 3.5 o la WinFX.

## <a name="to-create-a-state-machine-application-project"></a>Per creare un progetto di applicazione della macchina a stati

1.  Avviare Visual Studio.

2.  Nel menu **File** scegliere **Nuovo** e quindi selezionare **Progetto**.

     Verrà visualizzata la finestra di dialogo **Nuovo progetto** .

3.  Selezionare il **.NET Framework 3.0** opzione o **.NET Framework 3.5** opzione nella casella di riepilogo nella parte superiore del **nuovo progetto** finestra per accedere alla finestra di progettazione legacy.

    > [!NOTE]
    > L'opzione predefinita in Visual Studio 2010 viene **.NET Framework 4**. Questa opzione viene utilizzata per creare applicazioni di Windows Workflow Foundation (WF) che hanno come destinazione di .NET Framework 4 e non utilizza la finestra di progettazione legacy.

4.  Nel **tipi di progetto** riquadro, selezionare Visual c# o Visual Basic (sotto **altri linguaggi**) e quindi selezionare **flusso di lavoro**.

5.  Nel **modelli** riquadro, selezionare **applicazione Console flusso di lavoro macchina a stati**.

6.  Nel **nome** , immettere un nome descrittivo per il progetto per renderlo facilmente identificabile.

7.  Nel **percorso** , immettere la directory in cui si desidera salvare il progetto oppure fare clic su **Sfoglia** per passare a tale.

     Se si desidera una directory della soluzione creata per il progetto, selezionare il **Crea directory per soluzione** casella di controllo e immettere un nome per il **Nome soluzione** casella.

8.  Fare clic su **OK**.

## <a name="see-also"></a>Vedere anche

- [Creazione di progetti flusso di lavoro legacy](../workflow-designer/creating-legacy-workflow-projects.md)
- [Procedura: Creare una libreria del flusso di lavoro di macchina a stati (legacy)](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md)