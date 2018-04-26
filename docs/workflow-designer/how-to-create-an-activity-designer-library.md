---
title: 'Finestra di progettazione del flusso di lavoro - procedura: creare una libreria ActivityDesigner'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: 5b62e092-63b3-462d-9d77-fb112482f45d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d05ddb48e88627f4b7ab4112c164b5129ddba910
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-an-activity-designer-library"></a>Procedura: creare una libreria ActivityDesigner
Gli ActivityDesigner personalizzati consentono di creare un'interfaccia utente per un'attività personalizzata o standard. È possibile controllare la complessità dell'interfaccia utente e creare più ActivityDesigner per un'attività. Questo scenario consente di creare finestre di progettazione personalizzate per diversi destinatari.

## <a name="to-create-an-activity-designer-library"></a>Per creare una libreria ActivityDesigner

1.  Avviare Visual Studio 2010.

2.  Nel **File** dal menu **New**e quindi selezionare **progetto** per aprire il **nuovo progetto** finestra di dialogo.

3.  Nel **tipi di progetto** riquadro, selezionare **flusso di lavoro** da uno di **Visual c#** o **Visual Basic** a seconda del preferito lingua.

4.  Nel **modelli** riquadro, selezionare **libreria ActivityDesigner**.

5.  Nel **nome** , immettere un nome descrittivo per il progetto per renderlo facilmente identificabile.

6.  Nel **percorso** , immettere la directory in cui si desidera salvare il progetto oppure fare clic su **Sfoglia** per passare a tale.

7.  Nel **soluzione** casella, digitare un nome descrittivo per la soluzione, quindi fare clic su **OK**.

    > [!NOTE]
    > Se si desidera aggiungere un'applicazione console flusso di lavoro a una soluzione esistente, aprire la soluzione in Visual Studio 2010, fare clic con il pulsante destro sulla soluzione in **Esplora soluzioni**e selezionare **Add**, quindi **Nuovo progetto** per aprire la **nuovo progetto** finestra di dialogo. Procedere come descritto sopra in questa procedura.

8.  Il modello di progetto crea una definizione dell'ActivityDesigner in XAML mentre il file di implementazione code-behind è in codice sorgente. La finestra di progettazione del flusso di lavoro di Windows verrà visualizzato nell'area di lavoro per l'ActivityDesigner.

9. Trascinare Windows Presentation Foundation (WPF) dei controlli di **casella degli strumenti** all'area di progettazione per usarli nell'ActivityDesigner personalizzato.  Per un esempio di come implementare un ActivityDesigner personalizzato, vedere [procedura: creare un ActivityDesigner personalizzato](/dotnet/framework/windows-workflow-foundation/how-to-create-a-custom-activity-designer).

    > [!WARNING]
    > Gli ActivityDesigner personalizzati è utilizzabile per le attività personalizzate nonché per 4activities di .NET Framework predefiniti.

## <a name="see-also"></a>Vedere anche

- [Creazione di un progetto flusso di lavoro](../workflow-designer/creating-a-workflow-project.md)