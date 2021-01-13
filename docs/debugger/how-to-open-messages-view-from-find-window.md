---
title: Aprire la visualizzazione messaggi dalla finestra trova | Microsoft Docs
description: Utilizzare la finestra di dialogo Trova finestra di Spy + + per selezionare una finestra di destinazione e quindi aprire una visualizzazione messaggi per tale finestra.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Messages View in Spy++, opening
- opening Messages View in Spy++
ms.assetid: 601a193e-432a-417b-9406-6fec9e401264
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0e66e3e1200e1e08776853f2ac8308537e4b4a17
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/13/2021
ms.locfileid: "98148910"
---
# <a name="how-to-open-messages-view-from-find-window"></a>Procedura: aprire la visualizzazione messaggi dalla finestra Trova
Potrebbe risultare utile utilizzare la finestra di dialogo **Trova finestra** per selezionare una finestra di destinazione e quindi aprire una visualizzazione messaggi di tale finestra.

### <a name="to-open-a-messages-view-window-using-the-find-window-dialog-box"></a>Per aprire una finestra di visualizzazione messaggi utilizzando la finestra di dialogo Trova finestra

1. Disporre le finestre in modo che siano visibili sia Spy + + che la finestra di destinazione.

2. Scegliere **Trova finestra** dal menu **Spy** .

    Verrà visualizzata la [finestra di dialogo Trova finestra](../debugger/find-window-dialog-box.md) .

3. Dalla scheda **Windows** trascinare lo strumento di **ricerca** sulla finestra di destinazione. Quando si trascina lo strumento, nella finestra di dialogo **Trova finestra** vengono visualizzati i dettagli della finestra selezionata.

   - - oppure -

     Se si dispone dell'handle della finestra che si desidera esaminare (ad esempio, copiato dal debugger), è possibile digitarlo nella casella di testo **handle** .

4. In **Mostra** selezionare **messaggi**.

5. Fare clic su **OK**.

    Viene visualizzata una finestra [visualizzazione messaggi](../debugger/messages-view.md) vuota e viene aggiunto un menu **messaggi** alla barra degli strumenti di Spy + +.

6. Dal menu **messaggi** scegliere Opzioni di **registrazione**.

    Verrà visualizzata la finestra di [dialogo Opzioni messaggio](../debugger/message-options-dialog-box.md) .

7. Selezionare le opzioni per i messaggi che si desidera visualizzare.

8. Premere **OK** per avviare la registrazione dei messaggi.

    A seconda delle opzioni selezionate, i messaggi iniziano a trasmettere nella finestra Visualizzazione messaggi attivi.

9. Quando si dispone di un numero sufficiente di messaggi, scegliere **Interrompi registrazione** dal menu **messaggi** .
