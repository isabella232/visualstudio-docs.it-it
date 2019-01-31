---
title: 'Procedura: Cercare un thread nella visualizzazione messaggi | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 59fc1d6936822bb3a5ffad3bcdcbe9bc9976f293
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54940349"
---
# <a name="how-to-search-for-a-message-in-messages-view"></a>Procedura: Cercare un messaggio nella visualizzazione messaggi
È possibile cercare un messaggio specifico nella visualizzazione dei messaggi tramite relativo handle, tipo o ID del messaggio come criterio di ricerca. Una di queste, o una combinazione, ovvero saranno i criteri di ricerca valida. La direzione iniziale della ricerca può anche essere specificata. I campi nella finestra di dialogo sono precaricati con gli attributi del messaggio attualmente selezionato.  
  
### <a name="to-search-for-a-message-in-messages-view"></a>Per cercare un messaggio nella visualizzazione messaggi  
  
1. Disporre le finestre in modo tale Spy + + e un oggetto attivo [visualizzazione messaggi](../debugger/messages-view.md) finestra sono visibili.  
  
2. Dal **ricerca** menu, scegliere **Trova messaggio**.  
  
    Il [finestra di dialogo Ricerca messaggi](../debugger/message-search-dialog-box.md) apre.  
  
3. Trascinare il **strumento di ricerca** rispetto alla finestra desiderata. Quando si trascina lo strumento, il **ricerca messaggi** nella finestra di dialogo vengono visualizzati i dettagli sulla finestra selezionata.  
  
   - oppure -  
  
     Se hai l'handle della finestra di cui si desidera esaminare i messaggi, digitarla nella **gestire** casella di testo.  
  
   - oppure -  
  
     Se si conosce il tipo di messaggio e/o ID del messaggio desiderati, selezionarli dal **tipo** e **messaggio** menu a discesa e deselezionare il **gestire** casella di testo.  
  
4. Deselezionare tutti i campi per cui non si desidera specificare i valori.  
  
   > [!TIP]
   >  Per ridurre il disordine schermata, selezionare la **Nascondi Spy + +** opzione. Questa opzione consente di nascondere la finestra principale di Spy + + e di mantenere solo le **Trova finestra** nella finestra di dialogo visibile nella parte superiore alle altre applicazioni. La finestra principale di Spy + + è ripristinata quando si fa clic **OK** oppure **Cancel**, o quando si cancella il **Nascondi Spy + +** opzione.  
  
5. Scegli **iscrizione** oppure **verso il basso** per la direzione iniziale della ricerca.  
  
6. Fare clic su **OK**.  
  
   Se viene trovato un messaggio corrisponda, evidenziarlo nella finestra di visualizzazione dei messaggi. Visualizzare [la visualizzazione messaggi](../debugger/messages-view.md).