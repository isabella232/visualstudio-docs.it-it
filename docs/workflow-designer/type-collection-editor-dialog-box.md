---
title: Finestra di progettazione del flusso di lavoro - finestra di dialogo Editor raccolta di tipi
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TypeCollectionEditor.UI
ms.assetid: 63cdea6b-bca2-4c06-b8b4-c8faabd40726
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 191635364c445bc3959ee2f5f63c7c72c71f171d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62433929"
---
# <a name="type-collection-editor-dialog-box"></a>Finestra di dialogo Editor raccolta di tipi

Il **Editor raccolta di tipi** finestra di dialogo consente di aggiungere tipi noti per il **inviare** e **ricezione** attività. Questa finestra di dialogo viene usato anche per aggiungere argomenti tipo generico per il **InvokeMethod** attività. Quando viene utilizzato per il **inviare** e **ricezione** attività per aggiungere tipi noti, il **Editor raccolta di tipi** nella finestra di dialogo richiede tali aggiunte siano univoche. Se viene aggiunto un tipo duplicato e viene eseguito il commit della modifica facendo **OK**, viene restituito un messaggio di errore. Quando viene utilizzato per il **InvokeMethod** attività per aggiungere argomenti tipo generico, il **Editor raccolta di tipi** nella finestra di dialogo consente l'aggiunta di tipi duplicati.

Per altre informazioni, vedere [tipi conosciuti di contratto dati](/dotnet/framework/wcf/feature-details/data-contract-known-types).

La tabella seguente descrive gli elementi dell'interfaccia utente di **raccolta di tipi** nella finestra di dialogo.

|Elemento dell'interfaccia utente|Descrizione|
|-|-----------------|
|**Elenco dei tipi**|Un elenco dei tipi che sono stati aggiunti o rimossi.|

## <a name="to-bring-up-the-type-collection-editor-for-the-send-and-receive-activities"></a>Per visualizzare Editor raccolta di tipi per le attività Send e Receive

1. Selezionare il **inviare** oppure **ricezione** attività nella visualizzazione progettazione.

2. Premere **F4** per visualizzare i **proprietà** finestra.

3. Nel **delle proprietà** finestra, fare clic sul pulsante dei puntini di sospensione accanto alle **KnownTypes** proprietà.

## <a name="to-bring-up-the-type-collection-editor-for-the-invokemethod-activity"></a>Per visualizzare Editor raccolta di tipi per l'attività InvokeMethod

1. Selezionare il **InvokeMethod** attività nella visualizzazione progettazione.

2. Premere **F4** per visualizzare i **proprietà** finestra.

3. Nel **delle proprietà** finestra, fare clic sul pulsante dei puntini di sospensione accanto alle **GenericTypeArguments** proprietà.