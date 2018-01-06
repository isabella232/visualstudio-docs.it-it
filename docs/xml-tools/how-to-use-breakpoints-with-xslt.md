---
title: 'Procedura: utilizzare i punti di interruzione con XSLT | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bf7bbc2c-71dc-4cac-a6fc-add6b27d92ed
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 1407d34bc833c5c8a911adc87c8fa7cfec933256
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-breakpoints-with-xslt"></a>Procedura: utilizzare i punti di interruzione con XSLT
È possibile impostare punti di interruzione in un foglio di stile XSLT o nel documento di origine XML. Se si imposta un punto di interruzione su un tag, all'avvio dell'esecuzione il punto di interruzione si sposterà all'istruzione successiva che dispone di informazioni sulla riga del codice sorgente.  
  
 Per ulteriori informazioni, vedere [nozioni fondamentali di debug: i punti di interruzione](http://msdn.microsoft.com/en-us/752a02c2-0ac7-4c8b-aa1b-4b2b3b21152e).  
  
## <a name="set-a-breakpoint-in-a-style-sheet"></a>Impostazione di un punto di interruzione in un foglio di stile  
 È possibile impostare punti di interruzione su tag di inizio e di fine e nodi di tipo text di un foglio di stile XSLT. È inoltre possibile impostare punti di interruzione in un blocco di script del codice.  
  
#### <a name="to-set-a-breakpoint-in-a-style-sheet"></a>Per impostare un punto di interruzione in un foglio di stile  
  
1.  Aprire un foglio di stile nell'editor XML.  
  
2.  Posizionare il cursore sulla posizione del punto di interruzione, fare doppio clic su, scegliere **punto di interruzione**, fare clic su **Inserisci punto di interruzione**.  
  
3.  Fare clic sul pulsante Sfoglia (**...** ) nei **Input** campo della finestra delle proprietà del documento.  
  
4.  Individuare il documento di origine XML e fare clic su **aprire**.  
  
     In questo modo viene impostato il file del documento di origine usato per la trasformazione XSLT.  
  
5.  Fare clic su di **Debug XSLT** pulsante sulla barra degli strumenti Editor XML.  
  
## <a name="set-a-breakpoint-in-an-xml-source-document"></a>Impostazione di un punto di interruzione nel documento di origine XML  
 È possibile impostare punti di interruzione su elementi, attributi, nodo dello spazio dei nomi, commenti, istruzioni di elaborazione e nodi di tipo text di un documento di origine XML. Non è possibile impostare un punto di interruzione sul nodo del documento o su un nodo di spazio dei nomi ereditato dall'elemento padre.  
  
#### <a name="to-set-a-breakpoint-in-an-xml-source-document"></a>Per impostare un punto di interruzione nel documento di origine XML  
  
1.  Aprire il documento XML nell'editor XML.  
  
2.  Posizionare il cursore sulla posizione del punto di interruzione, fare doppio clic su, scegliere **punto di interruzione**, fare clic su **Inserisci punto di interruzione**.  
  
3.  Fare clic sul pulsante Sfoglia (**...** ) nei **Stylesheet** campo della finestra delle proprietà del documento.  
  
4.  Individuare il documento di origine XML e fare clic su **aprire**.  
  
     In questo modo viene impostato il file del documento di origine usato per la trasformazione XSLT.  
  
5.  Fare clic su di **Debug XSLT** pulsante sulla barra degli strumenti Editor XML.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: eseguire il debug di un foglio di stile XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)