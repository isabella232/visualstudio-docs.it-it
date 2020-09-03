---
title: 'Procedura: creare progetti di flusso di lavoro (legacy) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflow projects, creating
- projects, workflow
ms.assetid: 32299555-662c-469d-a90d-89f4700dc78c
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3cf68c1a28f662bfa4e271d3c402ef1c8946b6f1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668672"
---
# <a name="how-to-create-workflow-projects-legacy"></a>Procedura: creare progetti di flusso di lavoro (legacy)
Seguire questi passaggi per creare un progetto [!INCLUDE[wf](../includes/wf-md.md)] che viene destinato a [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o a [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]. In questa procedura viene usata la [!INCLUDE[wfd1](../includes/wfd1-md.md)] legacy fornita da [!INCLUDE[vs2010](../includes/vs2010-md.md)].

### <a name="to-create-a-workflow-project"></a>Creazione di un Progetto di flusso di lavoro 

1. Avviare [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)].

2. Scegliere **Nuovo** dal menu **File**e quindi selezionare **Progetto**.

     Verrà visualizzata la finestra di dialogo **Nuovo progetto** .

3. Selezionare l'opzione **.NET Framework 3,0** o l'opzione **.NET Framework 3,5** nell'elenco a discesa nella parte superiore della finestra **nuovo progetto** per accedere alla finestra di progettazione legacy.

    > [!NOTE]
    > L'opzione predefinita in [!INCLUDE[vs2010](../includes/vs2010-md.md)] è **.NET Framework 4**. Questa opzione viene usata per creare applicazioni [!INCLUDE[wf](../includes/wf-md.md)] che vengono destinate a [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] e non usa la finestra di progettazione legacy.

4. Nel riquadro **Tipi progetto** selezionare progetti Visual C# o progetti Visual Basic, quindi selezionare **flusso di lavoro**.

5. Nel riquadro **modelli** selezionare uno dei modelli di progetto installati:

    - Applicazione console del flusso di lavoro sequenziale

    - Libreria del flusso di lavoro sequenziale

    - Libreria delle attività del flusso di lavoro

    - Applicazione console del flusso di lavoro della macchina a stati

    - Libreria del flusso di lavoro di una macchina a stati

    - Progetto del flusso di lavoro vuoto

6. Nella casella **nome** immettere un nome descrittivo per il progetto per facilitarne l'identificazione.

7. Nella casella **percorso** immettere la directory in cui si desidera salvare il progetto oppure fare clic su **Sfoglia** per passare alla directory.

     Se si vuole creare una directory della soluzione per il progetto, selezionare la casella **di controllo Crea directory per soluzione** e immettere un nome nella casella **Nome soluzione** .

8. Fare clic su **OK**.

## <a name="see-also"></a>Vedere anche
 [Creazione di progetti flusso di lavoro legacy](../workflow-designer/creating-legacy-workflow-projects.md)