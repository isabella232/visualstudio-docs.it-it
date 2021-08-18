---
title: Cercare una finestra in Windows visualizzazione | Microsoft Docs
description: Cercare una finestra specifica nella visualizzazione Windows dello strumento Spy++ usando il relativo handle, didascalia, classe o una combinazione della didascalia e della classe in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- windows, searching in Windows view
ms.assetid: 30306970-b861-4315-acf8-f86a43d4e73b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 7321a7ba358f47d02ba78769883765ebec555b4f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122097129"
---
# <a name="how-to-search-for-a-window-in-windows-view"></a>Procedura: cercare una finestra nella visualizzazione finestre
È possibile cercare una finestra specifica nella visualizzazione Windows usando il relativo handle, didascalia, classe o una combinazione della didascalia e della classe come criteri di ricerca. È anche possibile specificare la direzione iniziale della ricerca. I campi nella finestra di dialogo mostreranno gli attributi della finestra selezionata nell'albero della finestra.

 Iniziare con l'albero espanso al secondo livello (tutte le finestre figlio del desktop), in modo da poter identificare le finestre a livello di desktop in base al nome e al titolo della classe. Dopo aver scelto una finestra a livello di desktop, è possibile espandere tale livello per trovare una finestra figlio specifica.

### <a name="to-search-for-a-window-in-windows-view"></a>Per cercare una finestra nella Windows predefinita

1. Disporre le finestre in modo che Spy++, la [Windows visualizzazione](../debugger/windows-view.md) e la finestra di destinazione siano visibili.

2. Scegliere **Trova** finestra dal menu **Cerca.**

    Verrà [visualizzata la finestra di dialogo Ricerca](../debugger/window-search-dialog-box.md) finestra.

   > [!TIP]
   > Per ridurre il disordine dello schermo, selezionare **l'opzione Nascondi Spy.** Questa opzione nasconde la finestra principale di  Spy++ e lascia visibile solo la finestra di dialogo Ricerca finestre sopra le altre applicazioni. La finestra principale di Spy++ viene ripristinata quando si fa clic su **OK** o **Annulla** oppure quando si deseleziona l'opzione **Nascondi Spy++.**

3. Trascinare **lo strumento Finder** sulla finestra di destinazione. Quando si trascina lo strumento, nella **finestra di dialogo** Ricerca finestra vengono visualizzati i dettagli della finestra selezionata.

   - - oppure -

     Se si conosce l'handle della finestra desiderata , ad esempio dal debugger, è possibile digitarlo nella **casella Handle** .

   - - oppure -

     Se si conosce la didascalia e/o la classe della finestra  desiderata, è possibile digitarle nelle caselle di testo **Didascalia** e Classe e deselezionare la **casella di** testo Handle .

4. Scegliere **Su** **o Giù** per la direzione iniziale della ricerca.

5. Fare clic su **OK**.

    Se viene trovata una finestra corrispondente, viene evidenziata nella Windows [Visualizza.](../debugger/windows-view.md)