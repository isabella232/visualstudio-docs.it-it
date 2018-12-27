---
title: 'Finestra di progettazione del flusso di lavoro - procedura: Usare la finestra di progettazione variabili'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Presentation.View.DesignTimeVariable.UI
ms.assetid: 0318dfb0-bf8f-4f92-9b86-ae4c1b2161ad
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 19a5bcec8f3bde37f794f28a3b174376a935b9ac
ms.sourcegitcommit: 935e341a02dba1c2aa3b6e89469388aa6e626f7f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/20/2018
ms.locfileid: "53684288"
---
# <a name="how-to-use-the-variable-designer"></a>Procedura: Usare la finestra di progettazione variabili

La finestra di progettazione variabili consente di creare variabili da usare in scenari di data binding e istruzioni condizionali. Viene visualizzata la finestra di progettazione facendo il **variabili** pulsante nell'angolo inferiore sinistro dell'area di progettazione. La finestra di progettazione contiene un elenco di variabili che vengono visualizzati in un formato tabulare e possono essere ordinati per ognuna delle intestazioni di colonna, tranne per il **predefinito** colonna. Ogni variabile contiene un nome, un tipo di variabile, un ambito e un valore predefinito (se presente). Il nome e il valore predefinito sono campi di testo modificabili mentre il tipo e l'ambito sono elenchi a discesa. L'ambito è l'attività selezionata al momento del richiamo della finestra di progettazione variabili. Se non è possibile creare una variabile nell'ambito della selezione, l'ambito verrà impostato in modo predefinito sull'attività predecessore più vicina della selezione in modo da consentire la creazione di variabili nel relativo ambito. Per altre informazioni, vedere [variabili e argomenti (.NET)](/dotnet/framework/windows-workflow-foundation/variables-and-arguments).

 L'ordinamento non viene applicato fino a quando l'utente non usa in modo esplicito uno dei controlli di ordinamento, chiude e riapre la finestra di progettazione variabili o crea un'altra variabile.

## <a name="to-create-a-new-variable"></a>Per creare una nuova variabile

1.  Aprire una soluzione del flusso di lavoro o attività in Visual Studio.

2.  Nell'area di progettazione selezionare un'attività nel flusso di lavoro.

3.  Aprire la finestra di progettazione variabile facendo il **variabili** pulsante nell'angolo inferiore sinistro dell'area di progettazione. Verrà visualizzata la finestra di progettazione variabili.

4.  Fare clic sulla riga vuota denominata **Crea variabile**. Verrà aggiunta una nuova riga con una nuova variabile con i valori predefiniti seguenti: variablex per il **Name** dove x è di tipo integer e un valore iniziale pari a 1 che viene incrementato automaticamente per creare nomi di variabili univoci,  **Stringa** per il **tipo di variabile**, e **sequenza** per i **ambito**. Non vengono aggiunti valori per **predefinito**. Tali valori possono essere modificati in qualsiasi momento durante il processo di progettazione del flusso di lavoro.

    > [!NOTE]
    > Per eliminare una variabile, selezionare la variabile facendovi clic sopra e quindi premere il **eliminare** chiave.

## <a name="see-also"></a>Vedere anche

- [Uso di Progettazione flussi di lavoro](developing-applications-with-the-workflow-designer.md)
- [Variabili e argomenti](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)
- [Procedura: Utilizzare la finestra di progettazione argomenti](../workflow-designer/how-to-use-the-argument-designer.md)