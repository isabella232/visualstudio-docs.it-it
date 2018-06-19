---
title: "Finestra di progettazione del flusso di lavoro - procedura: creare un'applicazione Console flusso di lavoro"
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: 51a2eea7-921c-49f1-b358-68afc27f1ee9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6461a644bdedd3d391059cd8a3a17f887e77c6b3
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
ms.locfileid: "31970900"
---
# <a name="how-to-create-a-workflow-console-application"></a>Procedura: creare un'applicazione console flusso di lavoro

Windows Workflow Foundation (WF) consente di creare flussi di lavoro per l'esecuzione di processi di utenti o di sistema. La finestra di progettazione del flusso di lavoro di Windows fornisce la superficie di progettazione per la creazione di questi flussi di lavoro. La finestra di progettazione del flusso di lavoro può essere utilizzato per creare flussi di lavoro dall'interno di Visual Studio o può essere integrato in altre applicazioni che riallocano la finestra di progettazione.

In questo argomento viene descritto come utilizzare la finestra di progettazione del flusso di lavoro in Visual Studio 2010 per creare un flusso di lavoro in un'applicazione console.

## <a name="to-create-a-workflow-console-application"></a>Per creare un'applicazione console flusso di lavoro

1.  Avviare Visual Studio 2010.

2.  Nel menu **File** scegliere **Nuovo** e quindi selezionare **Progetto**.

     Verrà visualizzata la finestra di dialogo **Nuovo progetto** .

3.  Nel **modelli installati** riquadro, selezionare **flusso di lavoro** da uno di **Visual c#** o **Visual Basic** raggruppamenti, a seconda del lingua di preferenza.

4.  Nel riquadro centrale, selezionare **applicazione Console flusso di lavoro**.

5.  Nel **nome** , immettere un nome descrittivo per il progetto per renderlo facilmente identificabile.

6.  Nel **percorso** , immettere la directory in cui si desidera salvare il progetto oppure fare clic su **Sfoglia** per passare a tale.

7.  Nel **soluzione** , immettere il nome per la nuova soluzione. Fare clic su **OK** per creare l'applicazione.

    > [!NOTE]
    > Se si desidera aggiungere un'applicazione console flusso di lavoro a una soluzione esistente, aprire la soluzione in Visual Studio 2010, fare clic con il pulsante destro la soluzione in **Esplora soluzioni**e selezionare **Add**, quindi  **Nuovo progetto** per aprire la **nuovo progetto** finestra di dialogo. Procedere come descritto sopra in questa procedura.

8.  Il modello di progetto crea una definizione del flusso di lavoro in XAML mentre la definizione dell'applicazione console è in codice sorgente. La finestra di progettazione del flusso di lavoro aprirà e visualizzerà l'area di disegno del flusso di lavoro che è stato creato.

9. Per creare un flusso di lavoro, trascinare attività o altri elementi del flusso di lavoro dal **della casella degli strumenti** all'area di progettazione del flusso di lavoro.

## <a name="see-also"></a>Vedere anche

- [Creazione di un progetto flusso di lavoro](../workflow-designer/creating-a-workflow-project.md)