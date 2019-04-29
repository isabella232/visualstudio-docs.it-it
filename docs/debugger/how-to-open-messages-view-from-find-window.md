---
title: 'Procedura: Aprire la visualizzazione messaggi dalla finestra Trova | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Messages View in Spy++, opening
- opening Messages View in Spy++
ms.assetid: 601a193e-432a-417b-9406-6fec9e401264
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f5fef9288a662b6726c185b50a79c8007b586b42
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62906580"
---
# <a name="how-to-open-messages-view-from-find-window"></a>Procedura: Aprire la visualizzazione messaggi dalla finestra Trova
Può risultare comodo usare la **Trova finestra** finestra di dialogo per selezionare una finestra di destinazione e quindi aprire una visualizzazione di messaggi di tale finestra.

### <a name="to-open-a-messages-view-window-using-the-find-window-dialog-box"></a>Per aprire una finestra di visualizzazione dei messaggi tramite la finestra di dialogo Trova finestra

1. Disporre le finestre in modo che sia Spy + + e la finestra di destinazione sono visibili.

2. Dal **Spy** menu, scegliere **Trova finestra**.

    Il [finestra di dialogo Trova](../debugger/find-window-dialog-box.md) apre.

3. Dal **Windows** scheda, trascinare le **strumento di ricerca** nell'intervallo di destinazione. Quando si trascina lo strumento, il **Trova finestra** nella finestra di dialogo vengono visualizzati i dettagli sulla finestra selezionata.

   - oppure -

     Se hai l'handle della finestra di cui si vuole esaminare (ad esempio, copiato dal debugger), è possibile digitare nel **gestire** casella di testo.

4. Sotto **mostrare**, selezionare **messaggi**.

5. Fare clic su **OK**.

    Uno spazio vuoto [visualizzazione messaggi](../debugger/messages-view.md) viene visualizzata una finestra e un **messaggi** menu viene aggiunto alla barra degli strumenti di Spy + +.

6. Dal **messaggi** menu, scegliere **opzioni di registrazione**.

    Il [finestra di dialogo Opzioni messaggio](../debugger/message-options-dialog-box.md) apre.

7. Selezionare le opzioni per i messaggi che si desidera visualizzare.

8. Premere **OK** per avviare la registrazione messaggi.

    A seconda delle opzioni selezionate, i messaggi di avviare lo streaming nella finestra di visualizzazione di messaggi attiva.

9. Quando si dispone di messaggi sufficiente, scegliere **Arresta registrazione** dalle **messaggi** menu.
