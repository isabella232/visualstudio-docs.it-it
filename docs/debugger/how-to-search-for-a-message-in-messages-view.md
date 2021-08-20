---
title: Cercare un messaggio nella visualizzazione Messaggi | Microsoft Docs
description: Cercare un messaggio specifico nella visualizzazione Messaggi dello strumento Spy++ usando il relativo handle, tipo o ID messaggio come criteri di ricerca durante il debug in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Message Search dialog box
- Messages view
- messages, searching for
ms.assetid: 732b7ccc-54ea-41db-823b-2b96e3e4083e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: e58274235eca23e9358a47a0711ebf46568ab1ff
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122161115"
---
# <a name="how-to-search-for-a-message-in-messages-view"></a>Procedura: cercare un thread nella visualizzazione messaggi
È possibile cercare un messaggio specifico nella visualizzazione Messaggi usando il relativo handle, tipo o ID messaggio come criteri di ricerca. Uno di questi criteri, o una combinazione, sarà un criterio di ricerca valido. È anche possibile specificare la direzione iniziale della ricerca. I campi nella finestra di dialogo vengono precaricati con gli attributi del messaggio attualmente selezionato.

### <a name="to-search-for-a-message-in-messages-view"></a>Per cercare un messaggio nella visualizzazione Messaggi

1. Disporre le finestre in modo che Spy++ e una finestra [visualizzazione messaggi](../debugger/messages-view.md) attiva siano visibili.

2. Scegliere **Trova** messaggio dal menu **Cerca**.

    Verrà [visualizzata la finestra di dialogo Ricerca](../debugger/message-search-dialog-box.md) messaggi .

3. Trascinare **lo strumento Finder** sulla finestra desiderata. Quando si trascina lo strumento, nella **finestra di dialogo** Ricerca messaggi vengono visualizzati i dettagli nella finestra selezionata.

   - - oppure -

     Se si dispone dell'handle della finestra di cui si desidera esaminare i messaggi, digitarlo nella **casella di testo Handle** .

   - - oppure -

     Se si conosce il tipo di messaggio e/o  l'ID messaggio desiderato, selezionarli dai menu a discesa Tipo e Messaggio e deselezionare la **casella di** testo Handle . 

4. Deselezionare tutti i campi per i quali non si desidera specificare valori.

   > [!TIP]
   > Per ridurre il disordine dello schermo, selezionare **l'opzione Nascondi Spy.** Questa opzione nasconde la finestra principale di  Spy++, lasciando visibile solo la finestra di dialogo Trova finestra sopra le altre applicazioni. La finestra principale di Spy++ viene ripristinata quando si fa clic su **OK** o Annulla **oppure** quando si deseleziona l'opzione Nascondi **Spy++.**

5. Scegliere **Su** **o Giù** per la direzione iniziale della ricerca.

6. Fare clic su **OK**.

   Se viene trovato un messaggio corrispondente, viene evidenziato nella finestra di visualizzazione Messaggi. Vedere [Visualizzazione messaggi](../debugger/messages-view.md).