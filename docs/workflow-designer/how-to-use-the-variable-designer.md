---
title: 'Progettazione flussi di lavoro-procedura: usare la finestra di progettazione variabili'
description: Informazioni su come usare la finestra di progettazione variabili per creare variabili da usare in scenari di data binding e istruzioni condizionali.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- System.Activities.Presentation.View.DesignTimeVariable.UI
ms.assetid: 0318dfb0-bf8f-4f92-9b86-ae4c1b2161ad
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e8dc5e402fcf3bedabe2b0f7fe606dfe807525ab
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/10/2020
ms.locfileid: "94437827"
---
# <a name="how-to-use-the-variable-designer"></a>Procedura: utilizzare la finestra di progettazione variabili

La finestra di progettazione variabili consente di creare variabili da usare in scenari di data binding e istruzioni condizionali. Per accedere alla finestra di progettazione, fare clic sul pulsante **variabili** nell'angolo inferiore sinistro dell'area di disegno. La finestra di progettazione contiene un elenco di variabili che vengono visualizzate in un formato tabulare e possono essere ordinate in base a ognuna delle intestazioni di colonna, ad eccezione della colonna **predefinita** . Ogni variabile contiene un nome, un tipo di variabile, un ambito e un valore predefinito (se presente). Il nome e il valore predefinito sono campi di testo modificabili mentre il tipo e l'ambito sono elenchi a discesa. L'ambito è l'attività selezionata al momento del richiamo della finestra di progettazione variabili. Se non è possibile creare una variabile nell'ambito della selezione, l'ambito verrà impostato in modo predefinito sull'attività predecessore più vicina della selezione in modo da consentire la creazione di variabili nel relativo ambito. Per altre informazioni, vedere [variabili e argomenti (.NET)](/dotnet/framework/windows-workflow-foundation/variables-and-arguments).

 L'ordinamento non viene applicato fino a quando l'utente non usa in modo esplicito uno dei controlli di ordinamento, chiude e riapre la finestra di progettazione variabili o crea un'altra variabile.

## <a name="to-create-a-new-variable"></a>Per creare una nuova variabile

1. Aprire una soluzione flusso di lavoro o attività in Visual Studio.

2. Nell'area di progettazione selezionare un'attività nel flusso di lavoro.

3. Aprire la finestra di progettazione variabili facendo clic sul pulsante **variabili** nell'angolo inferiore sinistro dell'area di progettazione. Verrà visualizzata la finestra di progettazione variabili.

4. Fare clic sulla riga vuota con etichetta **Crea variabile**. Verrà aggiunta una nuova riga con una nuova variabile usando i valori predefiniti seguenti: VariableX per il **nome** dove x è un numero intero con un valore iniziale pari a 1 che viene incrementato automaticamente per creare nomi di variabile univoci, **stringa** per il **tipo di variabile** e **sequenza** per l' **ambito**. Per **impostazione predefinita** , non viene aggiunto alcun valore. Tali valori possono essere modificati in qualsiasi momento durante il processo di progettazione del flusso di lavoro.

    > [!NOTE]
    > Per eliminare una variabile, selezionarla facendo clic su di essa e quindi premere il tasto **Canc** .

## <a name="see-also"></a>Vedere anche

- [Uso di Progettazione flussi di lavoro](developing-applications-with-the-workflow-designer.md)
- [Variabili e argomenti](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)
- [Procedura: utilizzare la finestra di progettazione argomenti](../workflow-designer/how-to-use-the-argument-designer.md)
