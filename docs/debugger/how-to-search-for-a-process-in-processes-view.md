---
title: 'Procedura: Cercare un processo nella visualizzazione processi | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Processes view
- processes, searching for
ms.assetid: 7cb97b37-4a95-4f1b-9eee-4910aa9c115b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2a6b57226b14963759bb4d78afff3beb5559a63e
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/12/2019
ms.locfileid: "64798985"
---
# <a name="how-to-search-for-a-process-in-processes-view"></a>Procedura: Cercare un processo nella visualizzazione processi
È possibile cercare un processo specifico nella visualizzazione processi usando la relativa stringa di ID o un modulo di processo come criterio di ricerca. È anche possibile specificare la direzione iniziale della ricerca. I campi nella finestra di dialogo mostrerà gli attributi del processo selezionato nell'albero del processo.

### <a name="to-search-for-a-process-in-processes-view"></a>Per cercare un processo nella visualizzazione processi

1. Disporre le finestre in modo tale Spy + + e un oggetto attivo [visualizzazione processi](../debugger/processes-view.md) finestra sono visibili.

2. Dal **ricerca** menu, scegliere **Trova processo**

    Il [dialogo Ricerca processi](../debugger/process-search-dialog-box.md) apre.

3. Digitare l'ID del processo o una stringa del modulo come criterio di ricerca.

4. Deselezionare tutti i campi per cui non si desidera specificare i valori.

   > [!TIP]
   > Per trovare tutti i processi appartenenti a un modulo, cancellare il **processo** e digitare il nome del modulo nel **modulo** casella. Quindi usare **Trova successivo** per continuare la ricerca dei processi.

5. Scegli **iscrizione** oppure **verso il basso** per la direzione iniziale della ricerca.

6. Fare clic su **OK**.

   Se viene trovato un processo di corrispondenza, è evidenziato nel **visualizzazione processo** finestra.