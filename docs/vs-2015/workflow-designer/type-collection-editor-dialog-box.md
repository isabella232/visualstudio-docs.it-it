---
title: Finestra di dialogo Editor raccolta di tipi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- TypeCollectionEditor.UI
ms.assetid: 63cdea6b-bca2-4c06-b8b4-c8faabd40726
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: dae99166b8b811df75f2e2777d176e6778b60c7d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670153"
---
# <a name="type-collection-editor-dialog-box"></a>Finestra di dialogo Editor raccolta di tipi
La finestra di dialogo **Editor raccolta di tipi** viene utilizzata per aggiungere tipi noti alle attività di **trasmissione** e **ricezione** . Questa finestra di dialogo viene usata anche per aggiungere argomenti di tipo generico all'attività **InvokeMethod** . Se utilizzata per le attività **Send** e **Receive** per aggiungere tipi noti, nella finestra di dialogo Editor della **raccolta di tipi** è necessario che le aggiunte dei tipi siano univoche. Se viene aggiunto un tipo duplicato e viene eseguito il commit della modifica facendo clic su **OK**, viene restituito un messaggio di errore. Quando viene usato per l'attività **InvokeMethod** per aggiungere argomenti di tipo generico, la finestra di dialogo **Editor raccolta** di tipi consente l'aggiunta di tipi duplicati.

> [!NOTE]
> [!INCLUDE[crabout](../includes/crabout-md.md)] i tipi noti, vedere [Data Contract Known Types](https://msdn.microsoft.com/library/1a0baea1-27b7-470d-9136-5bbad86c4337).

 Nella tabella seguente vengono descritti gli elementi dell'interfaccia utente della finestra di dialogo **raccolta tipi** .

|Elemento dell'interfaccia utente|Descrizione|
|----------------|-----------------|
|**Type List**|Un elenco dei tipi che sono stati aggiunti o rimossi.|

## <a name="to-bring-up-the-type-collection-editor"></a>Per visualizzare Editor raccolta di tipi

#### <a name="to-bring-up-the-type-collection-editor-for-the-send-and-receive-activities"></a>Per visualizzare Editor raccolta di tipi per le attività Send e Receive

1. Selezionare l'attività **trasmissione** o **ricezione** nella visualizzazione progettazione.

2. Premere **F4** per visualizzare la finestra **Proprietà** .

3. Nella finestra **Proprietà** fare clic sul pulsante con i puntini di sospensione accanto alla proprietà **knownTypes** .

#### <a name="to-bring-up-the-type-collection-editor-for-the-invokemethod-activity"></a>Per visualizzare Editor raccolta di tipi per l'attività InvokeMethod

1. Selezionare l'attività **InvokeMethod** nella visualizzazione progettazione.

2. Premere **F4** per visualizzare la finestra **Proprietà** .

3. Nella finestra **Proprietà** fare clic sul pulsante con i puntini di sospensione accanto alla proprietà **genericTypeArguments** .