---
title: "Procedura: creare un'applicazione console del flusso di lavoro | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 51a2eea7-921c-49f1-b358-68afc27f1ee9
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f1334655f2a8b8587922628664e43784b54ce971
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72604923"
---
# <a name="how-to-create-a-workflow-console-application"></a>Procedura: creare un'applicazione console flusso di lavoro
[!INCLUDE[wf](../includes/wf-md.md)] consente di creare flussi di lavoro per l'esecuzione di processi di sistema o umane. [!INCLUDE[wfd1](../includes/wfd1-md.md)] fornisce l'area di progettazione per la creazione di tali flussi. La [!INCLUDE[wfd2](../includes/wfd2-md.md)] può essere usata per creare flussi di lavoro dall'interno di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] o può essere integrata in altre applicazioni che riallocano la finestra di progettazione.

 In questo argomento viene descritto come usare la [!INCLUDE[wfd2](../includes/wfd2-md.md)] in [!INCLUDE[vs2010](../includes/vs2010-md.md)] per creare un flusso di lavoro in un'applicazione console.

### <a name="to-create-a-workflow-console-application"></a>Per creare un'applicazione console flusso di lavoro

1. Avviare [!INCLUDE[vs2010](../includes/vs2010-md.md)].

2. Scegliere **nuovo**dal menu **file** , quindi selezionare **progetto.**

     Verrà visualizzata la finestra di dialogo **Nuovo progetto** .

3. Nel riquadro **modelli installati** selezionare flusso di **lavoro** da **Visual C#** o **Visual Basic** raggruppamenti, a seconda del linguaggio preferito.

4. Nel riquadro centrale selezionare **applicazione console flusso di lavoro**.

5. Nella casella **nome** immettere un nome descrittivo per il progetto per facilitarne l'identificazione.

6. Nella casella **percorso** immettere la directory in cui si desidera salvare il progetto oppure fare clic su **Sfoglia** per passare a tale directory.

7. Nella casella **soluzione** immettere il nome per la nuova soluzione. Fare clic su **OK** per creare l'applicazione.

    > [!NOTE]
    > Se si desidera aggiungere un'applicazione console del flusso di lavoro a una soluzione esistente, aprire la soluzione in [!INCLUDE[vs2010](../includes/vs2010-md.md)] , fare clic con il pulsante destro del mouse sulla soluzione in **Esplora soluzioni**e selezionare **Aggiungi**, quindi **nuovo progetto.** per aprire la finestra di dialogo **nuovo progetto** . Procedere come descritto sopra in questa procedura.

8. Il modello di progetto crea una definizione del flusso di lavoro in XAML mentre la definizione dell'applicazione console è in codice sorgente. In [!INCLUDE[wfd2](../includes/wfd2-md.md)] verrà visualizzata l'area di disegno per il flusso di lavoro creato.

9. Per comporre un flusso di lavoro, trascinare le attività o altri elementi del flusso di lavoro dalla **casella degli strumenti** nell'area di progettazione del flusso di lavoro.

## <a name="see-also"></a>Vedere anche
 [Creazione di un progetto flusso di lavoro](../workflow-designer/creating-a-workflow-project.md)