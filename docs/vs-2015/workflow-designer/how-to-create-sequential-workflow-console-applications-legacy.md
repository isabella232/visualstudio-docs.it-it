---
title: 'Procedura: creare applicazioni console del flusso di lavoro sequenziale (legacy) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, console applications
- sequential workflows, console applications
- console applications, sequential workflow
ms.assetid: 9f7be7fa-551f-42c6-a9bb-f5ae8ab83625
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c9e3f97021e742db7b22a400dee0682669b07e4c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662723"
---
# <a name="how-to-create-sequential-workflow-console-applications-legacy"></a>Procedura: creare applicazioni console del flusso di lavoro sequenziale (legacy)
Seguire questi passaggi per creare un progetto Applicazione console flusso di lavoro sequenziale usando la [!INCLUDE[wfd1](../includes/wfd1-md.md)] legacy fornita da [!INCLUDE[vs2010](../includes/vs2010-md.md)]. Usare la [!INCLUDE[wfd2](../includes/wfd2-md.md)] legacy quando è necessario fare riferimento a [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

### <a name="to-create-a-sequential-workflow-console-application"></a>Creazione delle Applicazioni console del flusso di lavoro sequenziale

1. Avviare Visual Studio.

2. Scegliere **Nuovo** dal menu **File**e quindi selezionare **Progetto**.

     Verrà visualizzata la finestra di dialogo **Nuovo progetto** .

3. Selezionare l'opzione **.NET Framework 3,0** o l'opzione **.NET Framework 3,5** nell'elenco a discesa nella parte superiore della finestra **nuovo progetto** per accedere alla finestra di progettazione legacy.

    > [!NOTE]
    > L'opzione predefinita in [!INCLUDE[vs2010](../includes/vs2010-md.md)] è **.NET Framework 4**. Questa opzione viene usata per creare applicazioni [!INCLUDE[wf](../includes/wf-md.md)] che vengono destinate a [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] e non usa la finestra di progettazione legacy.

4. Nel riquadro **Tipi progetto** selezionare progetti Visual C# o progetti Visual Basic (in **altri linguaggi**), quindi selezionare **flusso di lavoro**.

5. Nel riquadro **modelli** selezionare **applicazione console flusso di lavoro sequenziale**.

6. Nella casella **nome** immettere un nome descrittivo per il progetto per facilitarne l'identificazione.

7. Nella casella **percorso** immettere la directory in cui si desidera salvare il progetto oppure fare clic su **Sfoglia** per passare a tale directory.

     Verrà aperta la finestra di progettazione Windows Forms nella quale verrà visualizzato il Form1 del progetto creato.

8. Fare clic su **OK**.

     Verrà aperta la finestra di Progettazione flussi di lavoro e verrà visualizzata l'area di progettazione del flusso di lavoro sequenziale creato.

9. Trascinare un'attività dalla **casella degli strumenti** all'area di progettazione nell'area designata **attività di rilascio** .

## <a name="see-also"></a>Vedere anche
 [Creazione di progetti flusso di lavoro legacy](../workflow-designer/creating-legacy-workflow-projects.md) [sviluppo di flussi di lavoro](https://msdn.microsoft.com/557bcb1f-a7ab-49f6-8df7-2706b7001301)