---
title: 'Finestra di progettazione del flusso di lavoro - procedura: creare applicazioni Console flusso di lavoro sequenziale (Legacy)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- workflows, console applications
- sequential workflows, console applications
- console applications, sequential workflow
ms.assetid: 9f7be7fa-551f-42c6-a9bb-f5ae8ab83625
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fb4e048fdf8eb8fee541f84656a29427b5a07a1d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
ms.locfileid: "31973219"
---
# <a name="how-to-create-sequential-workflow-console-applications-legacy"></a>Procedura: creare applicazioni console del flusso di lavoro sequenziale (legacy)

Seguire questi passaggi per creare un progetto di applicazione Console flusso di lavoro sequenziale usando la finestra di progettazione del flusso di lavoro Windows fornita da Visual Studio 2010. Utilizzare la finestra di progettazione del flusso di lavoro legacy quando è necessario avere come destinazione .NET Framework versione 3.5 o la WinFX.

## <a name="to-create-a-sequential-workflow-console-application"></a>Creazione delle Applicazioni console del flusso di lavoro sequenziale

1.  Avviare Visual Studio.

2.  Nel menu **File** scegliere **Nuovo** e quindi selezionare **Progetto**.

     Verrà visualizzata la finestra di dialogo **Nuovo progetto** .

3.  Selezionare il **.NET Framework 3.0** opzione o **.NET Framework 3.5** opzione nella casella di riepilogo nella parte superiore del **nuovo progetto** finestra per accedere alla finestra di progettazione legacy.

    > [!NOTE]
    > L'opzione predefinita in Visual Studio 2010 viene **.NET Framework 4**. Questa opzione viene utilizzata per creare applicazioni di Windows Workflow Foundation (WF) che hanno come destinazione di .NET Framework 4 e non utilizza la finestra di progettazione legacy.

4.  Nel **tipi di progetto** riquadro, selezionare progetti Visual c# o progetti di Visual Basic (sotto **altri linguaggi**), quindi selezionare **flusso di lavoro**.

5.  Nel **modelli** riquadro, selezionare **applicazione Console flusso di lavoro sequenziale**.

6.  Nel **nome** , immettere un nome descrittivo per il progetto per renderlo facilmente identificabile.

7.  Nel **percorso** , immettere la directory in cui si desidera salvare il progetto oppure fare clic su **Sfoglia** per passare a tale.

     Verrà aperta la finestra di progettazione Windows Forms nella quale verrà visualizzato il Form1 del progetto creato.

8.  Fare clic su **OK**.

     Verrà aperta la finestra di Progettazione flussi di lavoro e verrà visualizzata l'area di progettazione del flusso di lavoro sequenziale creato.

9. Trascinare un'attività dal **della casella degli strumenti** all'area di progettazione nel **rilasciare l'attività** area designata.

## <a name="see-also"></a>Vedere anche

- [Creazione di progetti flusso di lavoro legacy](../workflow-designer/creating-legacy-workflow-projects.md)
- [Sviluppo di flussi di lavoro](http://msdn.microsoft.com/en-us/557bcb1f-a7ab-49f6-8df7-2706b7001301)