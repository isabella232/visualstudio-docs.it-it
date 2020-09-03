---
title: 'Procedura: cercare un processo nella visualizzazione processi | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Processes view
- processes, searching for
ms.assetid: 7cb97b37-4a95-4f1b-9eee-4910aa9c115b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e823ecb1f7523c1a6f094d5669f4a37a72e84f60
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85349289"
---
# <a name="how-to-search-for-a-process-in-processes-view"></a>Procedura: cercare un processo nella visualizzazione processi
È possibile cercare un processo specifico nella visualizzazione processi usando la relativa ID processo o stringa del modulo come criterio di ricerca. È anche possibile specificare la direzione iniziale della ricerca. Nei campi della finestra di dialogo vengono visualizzati gli attributi del processo selezionato nell'albero dei processi.

### <a name="to-search-for-a-process-in-processes-view"></a>Per cercare un processo nella visualizzazione processi

1. Disporre le finestre in modo che Spy + + e una finestra di [visualizzazione processi](../debugger/processes-view.md) attivi siano visibili.

2. Dal menu **Cerca** scegliere **trova processo**

    Verrà visualizzata la finestra di [dialogo ricerca processi](../debugger/process-search-dialog-box.md) .

3. Digitare l'ID del processo o una stringa del modulo come criterio di ricerca.

4. Cancellare i campi per cui non si desidera specificare i valori.

   > [!TIP]
   > Per trovare tutti i processi di proprietà di un modulo, deselezionare la casella **processo** e digitare il nome del modulo nella casella **modulo** . Quindi usare **Trova successivo** per continuare la ricerca di processi.

5. Scegliere **verso l'alto** o **verso il basso** la direzione iniziale della ricerca.

6. Fare clic su **OK**.

   Se viene individuato un processo di corrispondenza, questo viene evidenziato nella finestra **visualizzazione processo** .