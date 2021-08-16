---
title: Progettazione flussi di lavoro finestra di dialogo Editor raccolta tipi
description: Informazioni su come usare la finestra di dialogo Editor raccolta tipi per aggiungere tipi noti alle attività Send e Receive.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TypeCollectionEditor.UI
ms.assetid: 63cdea6b-bca2-4c06-b8b4-c8faabd40726
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 9178601dad13630f0e830fe14766ec91d08fb380d7006214a60f79fef1014379
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121365822"
---
# <a name="type-collection-editor-dialog-box"></a>Finestra di dialogo Editor raccolta di tipi

La **finestra di dialogo Editor** raccolta tipi consente di aggiungere tipi noti alle attività **Send** **e Receive.** Questa finestra di dialogo viene usata anche per aggiungere argomenti di tipo generico **all'attività InvokeMethod.** Se usata per le **attività Send** e **Receive** per aggiungere tipi noti, la finestra di dialogo **Editor** raccolta tipi richiede che le aggiunte di tipo siano univoche. Se viene aggiunto un tipo duplicato e viene eseguito il commit della modifica facendo clic su **OK,** viene restituito un messaggio di errore. Se usata per **l'attività InvokeMethod** per aggiungere argomenti di tipo generico, la finestra di dialogo **Editor raccolta** tipi consente l'aggiunta di tipi duplicati.

Per altre informazioni, vedere [Tipi noti del contratto dati](/dotnet/framework/wcf/feature-details/data-contract-known-types).

Nella tabella seguente vengono descritti gli elementi dell'interfaccia utente della finestra **di dialogo Raccolta** tipi .

|Elemento dell'interfaccia utente|Descrizione|
|-|-----------------|
|**Type List**|Un elenco dei tipi che sono stati aggiunti o rimossi.|

## <a name="to-bring-up-the-type-collection-editor-for-the-send-and-receive-activities"></a>Per visualizzare Editor raccolta di tipi per le attività Send e Receive

1. Selezionare **l'attività** **Invia o Ricevi** nella visualizzazione Progettazione.

2. Premere **F4** per visualizzare la **finestra** Proprietà.

3. Nella finestra **Proprietà** fare clic sul pulsante con i puntini di sospensione accanto alla **proprietà KnownTypes.**

## <a name="to-bring-up-the-type-collection-editor-for-the-invokemethod-activity"></a>Per visualizzare Editor raccolta di tipi per l'attività InvokeMethod

1. Selezionare **l'attività InvokeMethod** nella visualizzazione progettazione.

2. Premere **F4** per visualizzare la **finestra** Proprietà.

3. Nella finestra **Proprietà** fare clic sul pulsante con i puntini di sospensione accanto alla **proprietà GenericTypeArguments.**
