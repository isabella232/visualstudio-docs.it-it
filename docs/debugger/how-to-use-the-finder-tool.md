---
title: Usare lo strumento Finder | Microsoft Docs
description: Usare lo strumento Finder nella finestra di dialogo Trova finestra dello strumento Spy++ per visualizzare le proprietà o i messaggi della finestra durante una sessione di debug.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Window Finder Tool
ms.assetid: 5841926b-08c3-4e43-88bd-4223d04f9aef
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: dcb143c5a4afd1a88598127cd21e446fbfe5a414
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122065475"
---
# <a name="how-to-use-the-finder-tool"></a>Procedura: utilizzare lo strumento di ricerca
È possibile usare lo strumento Finder nella finestra **di dialogo Trova finestra** per visualizzare le proprietà o i messaggi della finestra. Lo strumento Finder può anche individuare le finestre figlio disabilitate e distinguere la finestra da evidenziare se le finestre figlio disabilitate si sovrappongono.

 ![Finestra&#43;&#43; trova di Spy](../debugger/media/icon_spy--_find.png "Icon_Spy++_Find") Strumento Finder nella finestra di dialogo Trova finestra

 La figura precedente mostra la finestra di dialogo Trova finestra dopo il passaggio 3 riportato di seguito.

### <a name="to-display-window-properties-or-messages"></a>Per visualizzare le proprietà o i messaggi della finestra

1. Disporre le finestre in modo che sia Spy++ che la finestra di destinazione siano visibili.

2. Scegliere **Trova finestra** dal menu **Spy.**

    Verrà [visualizzata la finestra di dialogo Trova](../debugger/find-window-dialog-box.md) finestra.

3. Trascinare **lo strumento Finder** sulla finestra di destinazione.

    Quando si trascina lo strumento, nella **finestra di dialogo Trova** finestra vengono visualizzati i dettagli sulla finestra selezionata.

   - - oppure -

     Se si dispone dell'handle della finestra che si vuole esaminare(ad esempio, copiato dal debugger), digitarlo nella **casella di testo Handle** .

   > [!TIP]
   > Per ridurre il disordine dello schermo, selezionare **l'opzione Nascondi Spy.** Questa opzione nasconde la finestra principale di  Spy++, lasciando visibile solo la finestra di dialogo Trova finestra sopra le altre applicazioni. La finestra principale di Spy++ viene ripristinata quando si fa clic su **OK** o **Annulla** oppure quando si deseleziona l'opzione **Nascondi Spy++.**

4. In **Mostra** selezionare **Proprietà** o **Messaggi.**

5. Fare clic su **OK**.

    Se è stata selezionata **l'opzione Proprietà**, [viene visualizzata la finestra di dialogo Proprietà](../debugger/window-properties-dialog-box.md) finestra . Se è stata selezionata **l'opzione Messaggi**, [viene visualizzata una](../debugger/messages-view.md) finestra Visualizzazione messaggi.

## <a name="see-also"></a>Vedi anche
- [Visualizzazioni di Spy++](../debugger/spy-increment-views.md)
- [Utilizzo di Spy++](../debugger/using-spy-increment.md)
- [Riferimenti per Spy++](../debugger/spy-increment-reference.md)