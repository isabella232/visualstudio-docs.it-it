---
title: 'Procedura: utilizzare lo strumento di ricerca | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Window Finder Tool
ms.assetid: 5841926b-08c3-4e43-88bd-4223d04f9aef
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7833502c1f36adb654ecc4cc4d3b4dfb742a85b8
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2020
ms.locfileid: "85348730"
---
# <a name="how-to-use-the-finder-tool"></a>Procedura: utilizzare lo strumento di ricerca
È possibile utilizzare lo strumento di ricerca nella **finestra di dialogo Trova finestra** per visualizzare le proprietà o i messaggi della finestra. Lo strumento di ricerca può anche individuare le finestre figlio disabilitate e distinguere la finestra da evidenziare se le finestre figlio disabilitate si sovrappongono.

 ![Spy&#43;&#43; trova finestra di dialogo](../debugger/media/icon_spy--_find.png "Icon_Spy + + _Find") Strumento di ricerca nella finestra di dialogo Trova finestra

 La figura precedente Mostra la finestra di dialogo Trova finestra dopo il passaggio 3 riportato di seguito.

### <a name="to-display-window-properties-or-messages"></a>Per visualizzare le proprietà o i messaggi della finestra

1. Disporre le finestre in modo che siano visibili sia Spy + + che la finestra di destinazione.

2. Scegliere **Trova finestra**dal menu **Spy** .

    Verrà visualizzata la [finestra di dialogo Trova finestra](../debugger/find-window-dialog-box.md) .

3. Trascinare lo **strumento di ricerca** sulla finestra di destinazione.

    Quando si trascina lo strumento, nella finestra di dialogo **Trova finestra** vengono visualizzati i dettagli della finestra selezionata.

   - - oppure -

     Se si dispone dell'handle della finestra che si desidera esaminare (ad esempio, copiato dal debugger), digitarlo nella casella di testo **handle** .

   > [!TIP]
   > Per ridurre il disordine dello schermo, selezionare l'opzione **Nascondi Spy** . Questa opzione consente di nascondere la finestra principale di Spy + +, lasciando visibile solo la finestra di dialogo **Trova finestra** nella parte superiore delle altre applicazioni. La finestra principale di Spy + + viene ripristinata quando si fa clic su **OK** o **Annulla**oppure quando si deseleziona l'opzione **Nascondi Spy + +** .

4. In **Mostra**selezionare **Proprietà** o **messaggi**.

5. Fare clic su **OK**.

    Se si seleziona **Proprietà**, viene visualizzata la [finestra di dialogo Proprietà finestra](../debugger/window-properties-dialog-box.md) . Se sono stati selezionati **messaggi**, viene visualizzata una finestra [visualizzazione messaggi](../debugger/messages-view.md) .

## <a name="see-also"></a>Vedi anche
- [Visualizzazioni di Spy++](../debugger/spy-increment-views.md)
- [Utilizzo di Spy++](../debugger/using-spy-increment.md)
- [Riferimenti per Spy++](../debugger/spy-increment-reference.md)