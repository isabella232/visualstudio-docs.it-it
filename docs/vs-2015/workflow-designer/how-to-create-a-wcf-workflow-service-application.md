---
title: "Procedura: creare un'applicazione del servizio flusso di lavoro WCF | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 12d675ac-27d8-4d86-ba16-6f7688f8c841
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9bf941babd943c6856809a13de847b62745b2056
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72605007"
---
# <a name="how-to-create-a-wcf-workflow-service-application"></a>Procedura: creare un'applicazione del servizio flusso di lavoro WCF
Le applicazioni di servizi flusso di lavoro di [!INCLUDE[indigo1](../includes/indigo1-md.md)] sono servizi di comunicazioni distribuite che scambiano messaggi con i client oltre i limiti dei processi. L'implementazione del contratto di servizio sul lato servizio viene eseguita in modo dichiarativo tramite le attività del flusso di lavoro [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] in modo analogo ai servizi flusso di lavoro legacy di .NET Framework 3.5.

### <a name="to-create-a-wcf-workflow-service-application"></a>Per creare un'applicazione di servizi flusso di lavoro WCF

1. Avviare [!INCLUDE[vs2010](../includes/vs2010-md.md)].

2. Scegliere **nuovo**dal menu **file** , quindi selezionare **progetto.**

     Verrà visualizzata la finestra di dialogo **Nuovo progetto** .

3. Nel riquadro **modelli installati** selezionare **WCF** o flusso di **lavoro** dal raggruppamento **visuale C#**  o **Visual Basic** a seconda del linguaggio scelto.

4. Nel riquadro centrale selezionare **applicazione del servizio flusso di lavoro WCF**.

5. Nella casella **nome** immettere un nome descrittivo per il progetto per facilitarne l'identificazione.

6. Nella casella **percorso** immettere la directory in cui si desidera salvare il progetto oppure fare clic su **Sfoglia** per passare a tale directory.

7. Nella casella **soluzione** selezionare per creare una nuova soluzione e quindi fare clic su **OK**.

    > [!NOTE]
    > Se si desidera aggiungere un'applicazione console del flusso di lavoro a una soluzione esistente, aprire la soluzione in [!INCLUDE[vs2010](../includes/vs2010-md.md)], fare clic con il pulsante destro del mouse sulla soluzione in **Esplora soluzioni**e scegliere **Aggiungi**, quindi **nuovo progetto.** per aprire la finestra di dialogo **nuovo progetto** . Procedere come descritto sopra in questa procedura.

8. Il modello di progetto crea una definizione di servizio come XAML. [!INCLUDE[wfd1](../includes/wfd1-md.md)] viene aperto sulla visualizzazione Progettazione con un'attività <xref:System.Activities.Statements.Sequence> che contiene un set di attività <xref:System.ServiceModel.Activities.Receive> e <xref:System.ServiceModel.Activities.SendReply>.

## <a name="see-also"></a>Vedere anche
 [Procedura: creare un'attività](https://msdn.microsoft.com/library/c09b1e99-21b5-4d96-9c04-ec31db3f4436) [creazione di un progetto flusso di lavoro](../workflow-designer/creating-a-workflow-project.md)