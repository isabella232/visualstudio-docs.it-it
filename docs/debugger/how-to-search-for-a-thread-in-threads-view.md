---
title: Cercare un thread nella visualizzazione Thread | Microsoft Docs
description: Cercare un thread specifico nella visualizzazione Thread dello strumento Spy++ usando l'ID thread o la stringa del modulo come criteri di ricerca durante il debug in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- threads, searching
ms.assetid: 5609a9b3-c279-4426-9e2e-dd87896a6d6f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 38db1aa0af80b8c2c1769c6acf864f577a1d7a2d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122052044"
---
# <a name="how-to-search-for-a-thread-in-threads-view"></a>Procedura: cercare un thread nella visualizzazione thread
È possibile cercare un thread specifico nella visualizzazione Thread usando l'ID thread o la stringa del modulo come criteri di ricerca. È anche possibile specificare la direzione iniziale della ricerca. I campi nella finestra di dialogo mostreranno gli attributi del thread selezionato nell'albero dei thread.

### <a name="to-search-for-a-thread-in-threads-view"></a>Per cercare un thread nella visualizzazione Thread

1. Disporre le finestre in modo che Spy++ e una finestra [di visualizzazione thread](../debugger/threads-view.md) attiva siano visibili.

2. Scegliere **Trova** thread dal menu **Cerca**.

    Verrà [visualizzata la finestra di dialogo Ricerca](../debugger/thread-search-dialog-box.md) thread .

3. Digitare l'ID thread o una stringa del modulo come criteri di ricerca.

4. Deselezionare tutti i campi per i quali non si desidera specificare valori.

   > [!TIP]
   > Per trovare tutti i thread di proprietà di un modulo, deselezionare la **casella di testo Thread** e digitare il nome del modulo nella **casella** Modulo. Usare quindi **Trova successivo per** continuare la ricerca di thread.

5. Scegliere **Su** **o Giù** per la direzione iniziale della ricerca.

6. Fare clic su **OK**.

   Se viene trovato un thread corrispondente, viene evidenziato nella finestra di visualizzazione Thread.