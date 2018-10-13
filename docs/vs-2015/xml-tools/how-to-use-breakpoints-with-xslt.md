---
title: 'Procedura: usare i punti di interruzione con XSLT | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bf7bbc2c-71dc-4cac-a6fc-add6b27d92ed
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b01553075115ce953b499f722a254b5a2b9f20ee
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49233454"
---
# <a name="how-to-use-breakpoints-with-xslt"></a>Procedura: utilizzare i punti di interruzione con XSLT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile impostare punti di interruzione in un foglio di stile XSLT o nel documento di origine XML. Se si imposta un punto di interruzione su un tag, all'avvio dell'esecuzione il punto di interruzione si sposterà all'istruzione successiva che dispone di informazioni sulla riga del codice sorgente.  
  
 Per altre informazioni, vedere [nozioni fondamentali di debug: punti di interruzione](http://msdn.microsoft.com/en-us/752a02c2-0ac7-4c8b-aa1b-4b2b3b21152e).  
  
## <a name="set-a-breakpoint-in-a-style-sheet"></a>Impostazione di un punto di interruzione in un foglio di stile  
 È possibile impostare punti di interruzione su tag di inizio e di fine e nodi di tipo text di un foglio di stile XSLT. È inoltre possibile impostare punti di interruzione in un blocco di script del codice.  
  
#### <a name="to-set-a-breakpoint-in-a-style-sheet"></a>Per impostare un punto di interruzione in un foglio di stile  
  
1.  Aprire un foglio di stile nell'editor XML.  
  
2.  Posizionare il cursore in corrispondenza della posizione del punto di interruzione, fare doppio clic su, scegliere **punto di interruzione**, fare clic su **Inserisci punto di interruzione**.  
  
3.  Fare clic sul pulsante Sfoglia (**...** ) sul **Input** campo della finestra delle proprietà del documento.  
  
4.  Individuare il documento di origine XML e fare clic su **aperto**.  
  
     In questo modo viene impostato il file del documento di origine usato per la trasformazione XSLT.  
  
5.  Scegliere il **Debug XSLT** pulsante sulla barra degli strumenti Editor XML.  
  
## <a name="set-a-breakpoint-in-an-xml-source-document"></a>Impostazione di un punto di interruzione nel documento di origine XML  
 È possibile impostare punti di interruzione su elementi, attributi, nodo dello spazio dei nomi, commenti, istruzioni di elaborazione e nodi di tipo text di un documento di origine XML. Non è possibile impostare un punto di interruzione sul nodo del documento o su un nodo di spazio dei nomi ereditato dall'elemento padre.  
  
#### <a name="to-set-a-breakpoint-in-an-xml-source-document"></a>Per impostare un punto di interruzione nel documento di origine XML  
  
1.  Aprire il documento XML nell'editor XML.  
  
2.  Posizionare il cursore in corrispondenza della posizione del punto di interruzione, fare doppio clic su, scegliere **punto di interruzione**, fare clic su **Inserisci punto di interruzione**.  
  
3.  Fare clic sul pulsante Sfoglia (**...** ) sul **Stylesheet** campo della finestra delle proprietà del documento.  
  
4.  Individuare il documento di origine XML e fare clic su **aperto**.  
  
     In questo modo viene impostato il file del documento di origine usato per la trasformazione XSLT.  
  
5.  Scegliere il **Debug XSLT** pulsante sulla barra degli strumenti Editor XML.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: eseguire il debug di un foglio di stile XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)

