---
title: 'Progettazione flussi di lavoro-procedura: usare la finestra di progettazione degli argomenti'
description: Informazioni su progettazione argomenti e su come usare la finestra di progettazione degli argomenti per consentire il flusso dei dati all'interno e all'esterno di un'attività.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- System.Activities.Presentation.View.ArgumentDesigner.UI
- System.Activities.Presentation.View.DesignTimeArgument.UI
ms.assetid: 64813fd5-1ea1-499a-98b4-ab2a44b7ee5e
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9b97368a942747046aa7641771f84a9f2ed41e11
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894101"
---
# <a name="how-to-use-the-argument-designer"></a>Procedura: utilizzare la finestra di progettazione argomenti

La finestra di progettazione degli argomenti semplifica l'accesso ai dati in entrata e in uscita da un'attività. Per accedere alla finestra di progettazione, fare clic sul pulsante **argomenti** nell'angolo inferiore sinistro dell'area di progettazione. La finestra di progettazione contiene un elenco di argomenti che vengono visualizzati in un formato tabulare e possono essere ordinati in base a ognuna delle intestazioni di colonna, ad eccezione della colonna **valore predefinito** . Ogni argomento include un nome, una direzione per la proprietà in/out/in-out, un tipo e un valore di espressione predefinito (se presente). Il nome e il valore di espressione predefinito sono campi di testo modificabili, mentre il tipo e la direzione sono elenchi a discesa. Per altre informazioni, vedere [variabili e argomenti (.NET)](/dotnet/framework/windows-workflow-foundation/variables-and-arguments).

## <a name="to-create-a-new-argument"></a>Per creare un nuovo argomento

1. Aprire una soluzione flusso di lavoro o attività in Visual Studio.

2. Aprire la finestra di progettazione degli argomenti facendo clic sul pulsante **argomenti** nell'angolo inferiore sinistro dell'area di progettazione. Verrà visualizzata la finestra di progettazione argomenti.

3. Fare clic sulla riga vuota con etichetta **Crea argomento**. Verrà aggiunta una nuova riga con un nuovo argomento usando i valori predefiniti seguenti: argomentox per il **nome** dove x è un numero intero con un valore iniziale pari a 1 che viene incrementato automaticamente per creare nomi di argomento univoci, **in** per la **direzione** e **stringa** per il **tipo di argomento**. Per il **valore predefinito** non viene aggiunto alcun valore. Tali valori possono essere modificati in qualsiasi momento durante il processo di progettazione del flusso di lavoro.

    > [!NOTE]
    > Per eliminare un argomento, selezionarlo facendo clic su di esso e quindi premere il tasto **Canc** .

## <a name="see-also"></a>Vedi anche

- [Uso di Progettazione flussi di lavoro](developing-applications-with-the-workflow-designer.md)
- [Variabili e argomenti](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)
