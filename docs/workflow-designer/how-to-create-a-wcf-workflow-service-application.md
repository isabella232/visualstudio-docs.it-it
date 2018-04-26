---
title: "Finestra di progettazione del flusso di lavoro - procedura: creare un'applicazione di servizio del flusso di lavoro WCF"
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: 12d675ac-27d8-4d86-ba16-6f7688f8c841
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 93fb69862c228a3b6e61467facba188dd20c67c7
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-a-wcf-workflow-service-application"></a>Procedura: creare un'applicazione del servizio flusso di lavoro WCF

Le applicazioni di servizio del flusso di lavoro di Windows Communication Foundation (WCF) sono servizi di comunicazioni distribuite che scambiano messaggi con i client e a se stessi limiti dei processi. L'implementazione del contratto di servizio sul lato del servizio viene eseguita in modo dichiarativo tramite le attività del flusso di lavoro in .NET Framework 4 in modo analogo ai servizi di flusso di lavoro legacy in .NET Framework 3.5.

## <a name="to-create-a-wcf-workflow-service-application"></a>Per creare un'applicazione di servizi flusso di lavoro WCF

1.  Avviare Visual Studio 2010.

2.  Nel menu **File** scegliere **Nuovo** e quindi selezionare **Progetto**.

     Verrà visualizzata la finestra di dialogo **Nuovo progetto** .

3.  Nel **modelli installati** riquadro, selezionare **WCF** o **flusso di lavoro** da uno di **Visual c#** o **diVisualBasic** a seconda del linguaggio scelto.

4.  Nel riquadro centrale, selezionare **applicazione del servizio del flusso di lavoro WCF**.

5.  Nel **nome** , immettere un nome descrittivo per il progetto per renderlo facilmente identificabile.

6.  Nel **percorso** , immettere la directory in cui si desidera salvare il progetto oppure fare clic su **Sfoglia** per passare a tale.

7.  Nel **soluzione** casella, selezionare questa opzione per creare una nuova soluzione e quindi fare clic su **OK**.

    > [!NOTE]
    > Se si desidera aggiungere un'applicazione console flusso di lavoro a una soluzione esistente, aprire la soluzione in Visual Studio 2010, fare clic con il pulsante destro la soluzione in **Esplora soluzioni**e selezionare **Add**, quindi  **Nuovo progetto** per aprire la **nuovo progetto** finestra di dialogo. Procedere come descritto sopra in questa procedura.

8.  Il modello di progetto crea una definizione di servizio come XAML. Verrà visualizzata la finestra di progettazione del flusso di lavoro di Windows per la visualizzazione di progettazione con un <xref:System.Activities.Statements.Sequence> attività che contiene un set di <xref:System.ServiceModel.Activities.Receive> e <xref:System.ServiceModel.Activities.SendReply> le attività.

## <a name="see-also"></a>Vedere anche

- [Procedura: Creare un'attività](/dotnet/framework/windows-workflow-foundation/how-to-create-an-activity)
- [Creazione di un progetto flusso di lavoro](../workflow-designer/creating-a-workflow-project.md)