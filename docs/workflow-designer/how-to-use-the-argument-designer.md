---
title: 'Progettazione flussi di lavoro - Procedura: Usare la finestra di progettazione argomenti'
description: Informazioni sulla finestra di progettazione argomenti e su come usare la finestra di progettazione degli argomenti per consentire il flusso dei dati da e verso un'attività.
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
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 52f7d9bb06d60782e67664cf648ce03a2f7437fa
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122099061"
---
# <a name="how-to-use-the-argument-designer"></a>Procedura: utilizzare la finestra di progettazione argomenti

La finestra di progettazione argomenti semplifica il flusso dei dati da e verso un'attività. Accedere alla finestra di progettazione facendo clic sul **pulsante Argomenti** nell'angolo inferiore sinistro dell'area di progettazione. La finestra di progettazione contiene un elenco di argomenti visualizzati in formato tabulare e che possono essere ordinati in base a ogni intestazione di colonna, ad eccezione della **colonna Valore** predefinito . Ogni argomento include un nome, una direzione per la proprietà in/out/in-out, un tipo e un valore di espressione predefinito (se presente). Il nome e il valore di espressione predefinito sono campi di testo modificabili, mentre il tipo e la direzione sono elenchi a discesa. Per altre informazioni, vedere [Variabili e argomenti (.NET).](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)

## <a name="to-create-a-new-argument"></a>Per creare un nuovo argomento

1. Aprire una soluzione flusso di lavoro o attività in Visual Studio.

2. Aprire la finestra di progettazione degli argomenti facendo clic **sul pulsante Argomenti** nell'angolo inferiore sinistro dell'area di progettazione. Verrà visualizzata la finestra di progettazione argomenti.

3. Fare clic sulla riga vuota con **l'etichetta Crea argomento**. Verrà aggiunta una nuova riga con un nuovo argomento usando i valori predefiniti seguenti: argumentx per **Name** dove x è un numero intero con valore iniziale 1 che viene incrementato automaticamente per creare nomi di argomento univoci, **In** per **Direction** e **String** per il tipo **di argomento**. Non viene aggiunto alcun valore per **il valore predefinito**. Tali valori possono essere modificati in qualsiasi momento durante il processo di progettazione del flusso di lavoro.

    > [!NOTE]
    > Per eliminare un argomento, selezionarlo facendo clic su di esso e quindi premere **CANC.**

## <a name="see-also"></a>Vedi anche

- [Uso di Progettazione flussi di lavoro](developing-applications-with-the-workflow-designer.md)
- [Variabili e argomenti](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)
