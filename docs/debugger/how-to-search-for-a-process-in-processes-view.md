---
title: Cercare un processo nella visualizzazione Processi | Microsoft Docs
description: Cercare un processo specifico nella visualizzazione Processi dello strumento Spy++ usando l'ID processo o la stringa del modulo come criteri di ricerca durante il debug in Visual Studio.
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 9f5ff80257a3f3708d2de517e38fbc6abf6a77f9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122128169"
---
# <a name="how-to-search-for-a-process-in-processes-view"></a>Procedura: cercare un processo nella visualizzazione processi
È possibile cercare un processo specifico nella visualizzazione Processi usando l'ID processo o la stringa del modulo come criteri di ricerca. È anche possibile specificare la direzione iniziale della ricerca. I campi nella finestra di dialogo visualizzano gli attributi del processo selezionato nell'albero dei processi.

### <a name="to-search-for-a-process-in-processes-view"></a>Per cercare un processo nella visualizzazione Processi

1. Disporre le finestre in modo che Spy++ e una [finestra visualizzazione processi](../debugger/processes-view.md) attiva siano visibili.

2. Scegliere **Trova** processo dal menu **Cerca**

    Verrà [visualizzata la finestra di dialogo Process Search (Elabora](../debugger/process-search-dialog-box.md) ricerca).

3. Digitare l'ID processo o una stringa del modulo come criteri di ricerca.

4. Deselezionare tutti i campi per i quali non si desidera specificare valori.

   > [!TIP]
   > Per trovare tutti i processi di proprietà di un modulo, deselezionare **la casella Processo** e digitare il nome del modulo nella **casella** Modulo . Usare quindi **Trova successivo** per continuare a cercare i processi.

5. Scegliere **Su** **o Giù** per la direzione iniziale della ricerca.

6. Fare clic su **OK**.

   Se viene trovato un processo corrispondente, viene evidenziato nella **finestra di visualizzazione** Processo.