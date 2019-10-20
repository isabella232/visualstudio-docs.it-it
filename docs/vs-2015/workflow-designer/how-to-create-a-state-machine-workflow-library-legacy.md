---
title: 'Procedura: creare una libreria del flusso di lavoro di una macchina a stati (legacy) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- projects, state machine workflow library
- state machine workflow libraries
- workflows, state machine workflow library
ms.assetid: 5bd68c6e-6a98-47d9-826d-9bb7a4fd72f8
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d3cff5d6aaa28915524b7699affdf41d3bebef4a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663371"
---
# <a name="how-to-create-a-state-machine-workflow-library-legacy"></a>Procedura: creare una libreria del flusso di lavoro di macchina a stati (legacy)
Seguire questi passaggi per creare un progetto libreria flusso di lavoro di una macchina a stati usando la [!INCLUDE[wfd1](../includes/wfd1-md.md)] legacy fornita da [!INCLUDE[vs2010](../includes/vs2010-md.md)]. Usare la [!INCLUDE[wfd2](../includes/wfd2-md.md)] legacy quando è necessario fare riferimento a [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

### <a name="to-create-a-state-machine-workflow-library-project"></a>Procedura: creazione di un progetto di libreria del flusso di lavoro di una macchina a stati

1. Avviare Visual Studio.

2. Nel menu **File** scegliere **Nuovo** e quindi selezionare **Progetto**.

     Verrà visualizzata la finestra di dialogo **Nuovo progetto** .

3. Selezionare l'opzione **.NET Framework 3,0** o l'opzione **.NET Framework 3,5** nell'elenco a discesa nella parte superiore della finestra **nuovo progetto** per accedere alla finestra di progettazione legacy.

    > [!NOTE]
    > L'opzione predefinita in [!INCLUDE[vs2010](../includes/vs2010-md.md)] è **.NET Framework 4**. Questa opzione viene usata per creare applicazioni [!INCLUDE[wf](../includes/wf-md.md)] che vengono destinate a [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] e non usa la finestra di progettazione legacy.

4. Nel riquadro **Tipi progetto** selezionare Visual C# o Visual Basic (in **altri linguaggi**), quindi selezionare flusso di **lavoro**.

5. Nel riquadro **modelli** selezionare **libreria flusso di lavoro macchina a stati**.

6. Nella casella **nome** immettere un nome descrittivo per il progetto per facilitarne l'identificazione.

7. Nella casella **percorso** immettere la directory in cui si desidera salvare il progetto oppure fare clic su **Sfoglia** per passare a tale directory.

     Se si vuole creare una directory della soluzione per il progetto, selezionare la casella **di controllo Crea directory per soluzione** e immettere un nome nella casella **Nome soluzione** .

8. Fare clic su **OK**.

## <a name="see-also"></a>Vedere anche
 Creazione di [flussi di lavoro di macchine a stati](https://msdn.microsoft.com/library/344caacd-bf3b-4716-bd5a-eca74fc5a61d) dei [progetti flusso di lavoro](../workflow-designer/creating-legacy-workflow-projects.md)