---
title: Cercare un processo nella visualizzazione processi | Microsoft Docs
description: Cercare un processo specifico nella visualizzazione processi dello strumento Spy + + usando la relativa ID processo o stringa del modulo come criterio di ricerca durante il debug in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Processes view
- processes, searching for
ms.assetid: 7cb97b37-4a95-4f1b-9eee-4910aa9c115b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 85b2c2bab29316846620c7dbec935b41eec1d9df
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99845074"
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