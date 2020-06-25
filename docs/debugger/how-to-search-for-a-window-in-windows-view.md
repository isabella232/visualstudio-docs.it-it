---
title: 'Procedura: cercare una finestra nella visualizzazione Windows | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- windows, searching in Windows view
ms.assetid: 30306970-b861-4315-acf8-f86a43d4e73b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fb5fb871ebf03595c0baca0336e8449fe39029f3
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2020
ms.locfileid: "85349237"
---
# <a name="how-to-search-for-a-window-in-windows-view"></a>Procedura: cercare una finestra nella visualizzazione finestre
È possibile cercare una finestra specifica nella visualizzazione di Windows usando l'handle, la didascalia, la classe o una combinazione della didascalia e della classe come criterio di ricerca. È anche possibile specificare la direzione iniziale della ricerca. I campi nella finestra di dialogo mostreranno gli attributi della finestra selezionata nell'albero della finestra.

 Iniziare con l'albero espanso fino al secondo livello (tutte le finestre che sono elementi figlio del desktop), in modo che sia possibile identificare le finestre a livello di desktop in base al nome e al titolo della classe. Una volta scelta una finestra a livello di desktop, è possibile espandere tale livello per trovare una finestra figlio specifica.

### <a name="to-search-for-a-window-in-windows-view"></a>Per cercare una finestra nella visualizzazione di Windows

1. Disporre le finestre in modo che Spy + +, la finestra di [visualizzazione di Windows](../debugger/windows-view.md) e la finestra di destinazione siano visibili.

2. Dal menu **Cerca** scegliere **Trova finestra**.

    Verrà visualizzata la [finestra di dialogo ricerca finestra](../debugger/window-search-dialog-box.md) .

   > [!TIP]
   > Per ridurre il disordine dello schermo, selezionare l'opzione **Nascondi Spy** . Questa opzione consente di nascondere la finestra principale di Spy + +, lasciando visibile solo la finestra di dialogo di **ricerca della finestra** nella parte superiore delle altre applicazioni. La finestra principale di Spy + + viene ripristinata quando si fa clic su **OK** o **Annulla**oppure quando si deseleziona l'opzione **Nascondi Spy + +** .

3. Trascinare lo **strumento di ricerca** sulla finestra di destinazione. Quando si trascina lo strumento, nella finestra di dialogo **ricerca finestra** vengono visualizzati i dettagli della finestra selezionata.

   - - oppure -

     Se si conosce l'handle della finestra desiderata, ad esempio dal debugger, è possibile digitarlo nella casella **handle** .

   - - oppure -

     Se si conosce la didascalia e/o la classe della finestra desiderata, è possibile digitarle nelle caselle di testo **didascalia** e **classe** e deselezionare la casella di testo **handle** .

4. Scegliere **verso l'alto** o **verso il basso** la direzione iniziale della ricerca.

5. Fare clic su **OK**.

    Se viene trovata una finestra corrispondente, questa viene evidenziata nella finestra di [visualizzazione di Windows](../debugger/windows-view.md) .