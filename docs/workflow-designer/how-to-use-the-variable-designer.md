---
title: 'Progettazione flussi di lavoro - Procedura: Usare Progettazione variabili'
description: Informazioni su come usare Progettazione variabili per creare variabili da usare in scenari di data binding e istruzioni condizionali.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- System.Activities.Presentation.View.DesignTimeVariable.UI
ms.assetid: 0318dfb0-bf8f-4f92-9b86-ae4c1b2161ad
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 2391694c44c5494fb9410acd7247c59e95a1b9bf
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122099035"
---
# <a name="how-to-use-the-variable-designer"></a>Procedura: utilizzare la finestra di progettazione variabili

La finestra di progettazione variabili consente di creare variabili da usare in scenari di data binding e istruzioni condizionali. Per accedere alla finestra di progettazione, fare clic **sul pulsante** Variabili nell'angolo inferiore sinistro dell'area di disegno. La finestra di progettazione contiene un elenco di variabili visualizzate in formato tabulare e che possono essere ordinate in base a ognuna delle intestazioni di colonna, ad eccezione della **colonna** Default. Ogni variabile contiene un nome, un tipo di variabile, un ambito e un valore predefinito (se presente). Il nome e il valore predefinito sono campi di testo modificabili mentre il tipo e l'ambito sono elenchi a discesa. L'ambito è l'attività selezionata al momento del richiamo della finestra di progettazione variabili. Se non è possibile creare una variabile nell'ambito della selezione, l'ambito verrà impostato in modo predefinito sull'attività predecessore più vicina della selezione in modo da consentire la creazione di variabili nel relativo ambito. Per altre informazioni, vedere [Variabili e argomenti (.NET)](/dotnet/framework/windows-workflow-foundation/variables-and-arguments).

 L'ordinamento non viene applicato fino a quando l'utente non usa in modo esplicito uno dei controlli di ordinamento, chiude e riapre la finestra di progettazione variabili o crea un'altra variabile.

## <a name="to-create-a-new-variable"></a>Per creare una nuova variabile

1. Aprire una soluzione di flusso di lavoro o attività in Visual Studio.

2. Nell'area di progettazione selezionare un'attività nel flusso di lavoro.

3. Aprire la finestra di progettazione delle variabili facendo clic sul **pulsante** Variabili nell'angolo inferiore sinistro dell'area di disegno. Verrà visualizzata la finestra di progettazione variabili.

4. Fare clic sulla riga vuota con **l'etichetta Crea variabile**. Verrà aggiunta una nuova riga con una nuova variabile usando i valori predefiniti seguenti: variablex per **Name,** dove x è un numero intero con valore iniziale 1 che viene incrementato automaticamente per creare nomi di variabili univoci, **String** per il tipo **Di** variabile e **Sequenza** per **l'ambito**. Non viene aggiunto alcun valore per **Default**. Tali valori possono essere modificati in qualsiasi momento durante il processo di progettazione del flusso di lavoro.

    > [!NOTE]
    > Per eliminare una variabile, selezionarla facendo clic su di essa e quindi premere **CANC.**

## <a name="see-also"></a>Vedi anche

- [Uso di Progettazione flussi di lavoro](developing-applications-with-the-workflow-designer.md)
- [Variabili e argomenti](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)
- [Procedura: utilizzare la finestra di progettazione argomenti](../workflow-designer/how-to-use-the-argument-designer.md)
