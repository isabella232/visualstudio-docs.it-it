---
title: 'Procedura: utilizzare i punti di interruzione con XSLT | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: bf7bbc2c-71dc-4cac-a6fc-add6b27d92ed
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0519c3ab19e7d36aa26ea2f462c8a4571b9f8b32
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656299"
---
# <a name="how-to-use-breakpoints-with-xslt"></a>Procedura: utilizzare i punti di interruzione con XSLT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile impostare punti di interruzione in un foglio di stile XSLT o nel documento di origine XML. Se si imposta un punto di interruzione su un tag, all'avvio dell'esecuzione il punto di interruzione si sposterà all'istruzione successiva che dispone di informazioni sulla riga del codice sorgente.

 Per altre informazioni, vedere [nozioni fondamentali sul debug:](https://msdn.microsoft.com/752a02c2-0ac7-4c8b-aa1b-4b2b3b21152e)punti di interruzione.

## <a name="set-a-breakpoint-in-a-style-sheet"></a>Impostazione di un punto di interruzione in un foglio di stile
 È possibile impostare punti di interruzione su tag di inizio e di fine e nodi di tipo text di un foglio di stile XSLT. È inoltre possibile impostare punti di interruzione in un blocco di script del codice.

#### <a name="to-set-a-breakpoint-in-a-style-sheet"></a>Per impostare un punto di interruzione in un foglio di stile

1. Aprire un foglio di stile nell'editor XML.

2. Posizionare il cursore nella posizione del punto di interruzione, fare clic con il pulsante destro del mouse, scegliere punto di **interruzione**, quindi scegliere Inserisci punto di **interruzione**.

3. Fare clic sul pulsante Sfoglia (**...**) nel campo di **input** della finestra proprietà del documento.

4. Individuare il documento di origine XML e fare clic su **Apri**.

     In questo modo viene impostato il file del documento di origine usato per la trasformazione XSLT.

5. Fare clic sul pulsante **debug XSL** sulla barra degli strumenti dell'editor XML.

## <a name="set-a-breakpoint-in-an-xml-source-document"></a>Impostazione di un punto di interruzione nel documento di origine XML
 È possibile impostare punti di interruzione su elementi, attributi, nodo dello spazio dei nomi, commenti, istruzioni di elaborazione e nodi di tipo text di un documento di origine XML. Non è possibile impostare un punto di interruzione sul nodo del documento o su un nodo di spazio dei nomi ereditato dall'elemento padre.

#### <a name="to-set-a-breakpoint-in-an-xml-source-document"></a>Per impostare un punto di interruzione nel documento di origine XML

1. Aprire il documento XML nell'editor XML.

2. Posizionare il cursore nella posizione del punto di interruzione, fare clic con il pulsante destro del mouse, scegliere punto di **interruzione**, quindi scegliere Inserisci punto di **interruzione**.

3. Fare clic sul pulsante Sfoglia (**...**) nel campo **foglio di stile** della finestra proprietà del documento.

4. Individuare il documento di origine XML e fare clic su **Apri**.

     In questo modo viene impostato il file del documento di origine usato per la trasformazione XSLT.

5. Fare clic sul pulsante **debug XSL** sulla barra degli strumenti dell'editor XML.

## <a name="see-also"></a>Vedere anche
 [Procedura dettagliata: eseguire il debug di un foglio di stile XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)
