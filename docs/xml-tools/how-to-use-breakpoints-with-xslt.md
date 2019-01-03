---
title: 'Procedura: dei punti di interruzione con XSLT'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 72a22937792cc06bcac18f70a2bd4c53be98f7fe
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53894889"
---
# <a name="how-to-use-breakpoints-with-xslt"></a>Procedura: Usare i punti di interruzione con XSLT

È possibile impostare punti di interruzione in un foglio di stile XSLT o nel documento di origine XML. Se si imposta un punto di interruzione su un tag, all'avvio dell'esecuzione il punto di interruzione si sposterà all'istruzione successiva che dispone di informazioni sulla riga del codice sorgente.

Per altre informazioni, vedere [nozioni fondamentali di debug: I punti di interruzione](../debugger/using-breakpoints.md).

## <a name="set-a-breakpoint-in-a-style-sheet"></a>Impostare un punto di interruzione in un foglio di stile

È possibile impostare punti di interruzione su tag di inizio e di fine e nodi di tipo text di un foglio di stile XSLT. È inoltre possibile impostare punti di interruzione in un blocco di script del codice.

### <a name="to-set-a-breakpoint-in-a-style-sheet"></a>Per impostare un punto di interruzione in un foglio di stile

1.  Aprire un foglio di stile nell'editor XML.

2.  Posizionare il cursore in corrispondenza della posizione del punto di interruzione, fare doppio clic su, scegliere **punto di interruzione**, fare clic su **Inserisci punto di interruzione**.

3.  Fare clic sul pulsante Sfoglia (**...** ) sul **Input** campo della finestra delle proprietà del documento.

4.  Individuare il documento di origine XML e fare clic su **aperto**.

     In questo modo viene impostato il file del documento di origine usato per la trasformazione XSLT.

5.  Scegliere il **Debug XSLT** pulsante sulla barra degli strumenti Editor XML.

## <a name="set-a-breakpoint-in-an-xml-source-document"></a>Impostare un punto di interruzione in un documento di origine XML

È possibile impostare punti di interruzione su elementi, attributi, nodo dello spazio dei nomi, commenti, istruzioni di elaborazione e nodi di tipo text di un documento di origine XML. Non è possibile impostare un punto di interruzione sul nodo del documento o su un nodo di spazio dei nomi ereditato dall'elemento padre.

### <a name="to-set-a-breakpoint-in-an-xml-source-document"></a>Per impostare un punto di interruzione nel documento di origine XML

1.  Aprire il documento XML nell'editor XML.

2.  Posizionare il cursore in corrispondenza della posizione del punto di interruzione, fare doppio clic su, scegliere **punto di interruzione**, fare clic su **Inserisci punto di interruzione**.

3.  Fare clic sul pulsante Sfoglia (**...** ) sul **Stylesheet** campo della finestra delle proprietà del documento.

4.  Individuare il documento di origine XML e fare clic su **aperto**.

     In questo modo viene impostato il file del documento di origine usato per la trasformazione XSLT.

5.  Scegliere il **Debug XSLT** pulsante sulla barra degli strumenti Editor XML.

## <a name="see-also"></a>Vedere anche

- [Procedura dettagliata: Eseguire il debug di un foglio di stile XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)