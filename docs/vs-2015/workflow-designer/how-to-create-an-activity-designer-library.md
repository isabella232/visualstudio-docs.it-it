---
title: 'Procedura: creare una libreria ActivityDesigner | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 5b62e092-63b3-462d-9d77-fb112482f45d
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 63404d3d81c44ac4b8308d949cdb87df419f2e04
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662863"
---
# <a name="how-to-create-an-activity-designer-library"></a>Procedura: creare una libreria ActivityDesigner
Gli ActivityDesigner personalizzati consentono di creare un'interfaccia utente per un'attività personalizzata o standard. È possibile controllare la complessità dell'interfaccia utente e creare più ActivityDesigner per un'attività. Questo scenario consente di creare finestre di progettazione personalizzate per diversi destinatari.

### <a name="to-create-an-activity-designer-library"></a>Per creare una libreria ActivityDesigner

1. Avviare [!INCLUDE[vs2010](../includes/vs2010-md.md)].

2. Scegliere **nuovo**dal menu **file** , quindi selezionare **progetto...** per aprire la finestra di dialogo **nuovo progetto** .

3. Nel riquadro **Tipi progetto** selezionare flusso di **lavoro** da **Visual C#** o **Visual Basic** raggruppamenti a seconda del linguaggio preferito.

4. Nel riquadro **modelli** selezionare **libreria Activity Designer**.

5. Nella casella **nome** immettere un nome descrittivo per il progetto per facilitarne l'identificazione.

6. Nella casella **percorso** immettere la directory in cui si desidera salvare il progetto oppure fare clic su **Sfoglia** per passare a tale directory.

7. Nella casella **soluzione** Digitare un nome descrittivo per la soluzione, quindi fare clic su **OK**.

    > [!NOTE]
    > Se si desidera aggiungere un'applicazione console del flusso di lavoro a una soluzione esistente, aprire la soluzione in [!INCLUDE[vs2010](../includes/vs2010-md.md)] , fare clic con il pulsante destro del mouse sulla soluzione in **Esplora soluzioni**e selezionare **Aggiungi**, quindi **nuovo progetto.** per aprire la finestra di dialogo **nuovo progetto** . Procedere come descritto sopra in questa procedura.

8. Il modello di progetto crea una definizione dell'ActivityDesigner in XAML mentre il file di implementazione code-behind è in codice sorgente. [!INCLUDE[wfd1](../includes/wfd1-md.md)] verrà visualizzato con l'area di disegno per l'ActivityDesigner.

9. Trascinare [!INCLUDE[avalon1](../includes/avalon1-md.md)] i controlli dalla **casella degli strumenti** nell'area di progettazione per utilizzarli nell'ActivityDesigner personalizzato.  Per un esempio di come implementare un ActivityDesigner personalizzato, vedere [procedura: creare un ActivityDesigner personalizzato](https://msdn.microsoft.com/library/2f3aade6-facc-44ef-9657-a407ef8b9b31).

    > [!WARNING]
    > Gli ActivityDesigner personalizzati possono essere utilizzati per le attività personalizzate e per le [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] attività predefinite.

## <a name="see-also"></a>Vedere anche
 [Creazione di un progetto flusso di lavoro](../workflow-designer/creating-a-workflow-project.md)