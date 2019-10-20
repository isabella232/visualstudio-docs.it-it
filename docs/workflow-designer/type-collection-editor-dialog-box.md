---
title: Finestra di dialogo Editor della raccolta di tipi Progettazione flussi di lavoro
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TypeCollectionEditor.UI
ms.assetid: 63cdea6b-bca2-4c06-b8b4-c8faabd40726
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a0a9bf604749524d76b8046d60de75d4b5844cc4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649785"
---
# <a name="type-collection-editor-dialog-box"></a>Finestra di dialogo Editor raccolta di tipi

La finestra di dialogo **Editor raccolta di tipi** viene utilizzata per aggiungere tipi noti alle attività di **trasmissione** e **ricezione** . Questa finestra di dialogo viene usata anche per aggiungere argomenti di tipo generico all'attività **InvokeMethod** . Se utilizzata per le attività **Send** e **Receive** per aggiungere tipi noti, nella finestra di dialogo Editor della **raccolta di tipi** è necessario che le aggiunte dei tipi siano univoche. Se viene aggiunto un tipo duplicato e viene eseguito il commit della modifica facendo clic su **OK**, viene restituito un messaggio di errore. Quando viene usato per l'attività **InvokeMethod** per aggiungere argomenti di tipo generico, la finestra di dialogo **Editor raccolta** di tipi consente l'aggiunta di tipi duplicati.

Per ulteriori informazioni, vedere [tipi noti del contratto dati](/dotnet/framework/wcf/feature-details/data-contract-known-types).

Nella tabella seguente vengono descritti gli elementi dell'interfaccia utente della finestra di dialogo **raccolta tipi** .

|Elemento dell'interfaccia utente|Descrizione|
|-|-----------------|
|**Elenco dei tipi**|Un elenco dei tipi che sono stati aggiunti o rimossi.|

## <a name="to-bring-up-the-type-collection-editor-for-the-send-and-receive-activities"></a>Per visualizzare Editor raccolta di tipi per le attività Send e Receive

1. Selezionare l'attività **trasmissione** o **ricezione** nella visualizzazione progettazione.

2. Premere **F4** per visualizzare la finestra **Proprietà** .

3. Nella finestra **Proprietà** fare clic sul pulsante con i puntini di sospensione accanto alla proprietà **knownTypes** .

## <a name="to-bring-up-the-type-collection-editor-for-the-invokemethod-activity"></a>Per visualizzare Editor raccolta di tipi per l'attività InvokeMethod

1. Selezionare l'attività **InvokeMethod** nella visualizzazione progettazione.

2. Premere **F4** per visualizzare la finestra **Proprietà** .

3. Nella finestra **Proprietà** fare clic sul pulsante con i puntini di sospensione accanto alla proprietà **genericTypeArguments** .