---
title: 'Procedura: creare una libreria del flusso di lavoro sequenziale (legacy) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- sequential workflows, creating library
- workflows, sequential workflow library
- projects, sequential workflow library
- sequential workflow libraries
ms.assetid: 9433ccf3-1eab-4d53-90ff-2e7b2341676c
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: adc2e71678e6892d12640a3153f24bfb90dfa429
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663404"
---
# <a name="how-to-create-a-sequential-workflow-library-legacy"></a>Procedura: creare una libreria del flusso di lavoro sequenziale (legacy)
Seguire questi passaggi per creare un progetto libreria flusso di lavoro sequenziale usando la [!INCLUDE[wfd1](../includes/wfd1-md.md)] legacy fornita da [!INCLUDE[vs2010](../includes/vs2010-md.md)]. Usare la [!INCLUDE[wfd2](../includes/wfd2-md.md)] legacy quando è necessario fare riferimento a [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

### <a name="to-create-a-sequential-workflow-library-project"></a>Per creare un progetto di libreria del flusso di lavoro sequenziale

1. Avviare Visual Studio.

2. Scegliere **Nuovo** dal menu **File**e quindi selezionare **Progetto**.

     Verrà visualizzata la finestra di dialogo **Nuovo progetto** .

3. Selezionare l'opzione **.NET Framework 3,0** o l'opzione **.NET Framework 3,5** nell'elenco a discesa nella parte superiore della finestra **nuovo progetto** per accedere alla finestra di progettazione legacy.

    > [!NOTE]
    > L'opzione predefinita in [!INCLUDE[vs2010](../includes/vs2010-md.md)] è **.NET Framework 4**. Questa opzione viene usata per creare applicazioni [!INCLUDE[wf](../includes/wf-md.md)] che vengono destinate a [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] e non usa la finestra di progettazione legacy.

4. Nel riquadro **Tipi progetto** selezionare Visual C# o Visual Basic (in **altri linguaggi**), quindi selezionare **flusso di lavoro**.

5. Nel riquadro **modelli** selezionare **libreria flusso di lavoro sequenziale**.

6. Nella casella **nome** immettere un nome descrittivo per il progetto per facilitarne l'identificazione.

7. Nella casella **percorso** immettere la directory in cui si desidera salvare il progetto oppure fare clic su **Sfoglia** per passare a tale directory.

     Se si vuole creare una directory della soluzione per il progetto, selezionare la casella **di controllo Crea directory per soluzione** e immettere un nome nella casella **Nome soluzione** .

8. Fare clic su **OK**.

## <a name="see-also"></a>Vedere anche
 Creazione di stili di creazione [flussi](https://msdn.microsoft.com/aacf4ec6-da05-4974-958a-974769dda739) di lavoro [legacy di progetti flussi](../workflow-designer/creating-legacy-workflow-projects.md) di lavoro