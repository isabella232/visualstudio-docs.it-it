---
title: Cerca un messaggio nella visualizzazione messaggi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Message Search dialog box
- Messages view
- messages, searching for
ms.assetid: 732b7ccc-54ea-41db-823b-2b96e3e4083e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7c4b597870d7a87b396b4c6e828da814c49f9bfb
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852009"
---
# <a name="how-to-search-for-a-message-in-messages-view"></a>Procedura: cercare un thread nella visualizzazione messaggi
È possibile cercare un messaggio specifico nella visualizzazione messaggi utilizzando il relativo handle, tipo o ID messaggio come criterio di ricerca. Uno qualsiasi di questi, o una combinazione, sarà un criterio di ricerca valido. È possibile specificare anche la direzione iniziale della ricerca. I campi della finestra di dialogo vengono precaricati con gli attributi del messaggio attualmente selezionato.

### <a name="to-search-for-a-message-in-messages-view"></a>Per cercare un messaggio nella visualizzazione messaggi

1. Disporre le finestre in modo che Spy + + e una finestra di [visualizzazione dei messaggi](../debugger/messages-view.md) attivi siano visibili.

2. Dal menu **Cerca** scegliere **Trova messaggio**.

    Verrà visualizzata la finestra di [dialogo Ricerca messaggi](../debugger/message-search-dialog-box.md) .

3. Trascinare lo **strumento di ricerca** sulla finestra desiderata. Quando si trascina lo strumento, nella finestra di dialogo **Ricerca messaggi** vengono visualizzati i dettagli della finestra selezionata.

   - - oppure -

     Se si dispone dell'handle della finestra di cui si desidera esaminare i messaggi, digitarlo nella casella di testo **handle** .

   - - oppure -

     Se si conosce il tipo di messaggio e/o l'ID del messaggio desiderato, selezionarli nei menu a discesa **tipo** e **messaggio** e deselezionare la casella di testo **handle** .

4. Cancellare i campi per cui non si desidera specificare i valori.

   > [!TIP]
   > Per ridurre il disordine dello schermo, selezionare l'opzione **Nascondi Spy** . Questa opzione consente di nascondere la finestra principale di Spy + +, lasciando visibile solo la finestra di dialogo **Trova finestra** nella parte superiore delle altre applicazioni. La finestra principale di Spy + + viene ripristinata quando si fa clic su **OK** o **Annulla**oppure quando si deseleziona l'opzione **Nascondi Spy + +** .

5. Scegliere **verso l'alto** o **verso il basso** la direzione iniziale della ricerca.

6. Fare clic su **OK**.

   Se viene trovato un messaggio corrispondente, questo viene evidenziato nella finestra Visualizzazione messaggi. Vedere [visualizzazione messaggi](../debugger/messages-view.md).