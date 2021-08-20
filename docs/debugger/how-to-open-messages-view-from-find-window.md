---
title: Aprire la visualizzazione Messaggi dalla finestra Trova | Microsoft Docs
description: Usare la finestra di dialogo Trova finestra in Spy++ per selezionare una finestra di destinazione e quindi aprire una visualizzazione Messaggi per tale finestra.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Messages View in Spy++, opening
- opening Messages View in Spy++
ms.assetid: 601a193e-432a-417b-9406-6fec9e401264
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 852769189cf7294696f562d4d7ed6e89ce962cbd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122128234"
---
# <a name="how-to-open-messages-view-from-find-window"></a>Procedura: aprire la visualizzazione messaggi dalla finestra Trova
Può risultare utile usare la **finestra** di dialogo Trova finestra per selezionare una finestra di destinazione e quindi aprire una visualizzazione Messaggi di tale finestra.

### <a name="to-open-a-messages-view-window-using-the-find-window-dialog-box"></a>Per aprire una finestra di visualizzazione Messaggi usando la finestra di dialogo Trova finestra

1. Disporre le finestre in modo che sia Spy++ che la finestra di destinazione siano visibili.

2. Scegliere **Trova finestra** dal menu **Spy.**

    Verrà [visualizzata la finestra di dialogo Trova](../debugger/find-window-dialog-box.md) finestra .

3. Dalla scheda **Windows,** trascinare lo strumento **Di ricerca** sulla finestra di destinazione. Quando si trascina lo strumento, nella **finestra di dialogo Trova** finestra vengono visualizzati i dettagli sulla finestra selezionata.

   - - oppure -

     Se si dispone dell'handle della finestra che si vuole esaminare , ad esempio copiato dal debugger, è possibile digitarlo nella **casella di** testo Handle .

4. In **Mostra** selezionare **Messaggi**.

5. Fare clic su **OK**.

    Viene visualizzata [una finestra vuota Di](../debugger/messages-view.md) visualizzazione messaggi e viene aggiunto **un** menu Messaggi alla barra degli strumenti di Spy++.

6. Scegliere **Opzioni di** registrazione dal menu **Messaggi**.

    Verrà [visualizzata la finestra di dialogo Opzioni](../debugger/message-options-dialog-box.md) messaggio .

7. Selezionare le opzioni per i messaggi da visualizzare.

8. Premere **OK per** avviare la registrazione dei messaggi.

    A seconda delle opzioni selezionate, i messaggi iniziano a trasmettere nella finestra di visualizzazione messaggi attiva.

9. Quando i messaggi sono sufficienti, scegliere **Arresta** registrazione **dal** menu Messaggi.
