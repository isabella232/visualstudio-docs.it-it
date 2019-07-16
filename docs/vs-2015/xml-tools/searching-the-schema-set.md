---
title: La ricerca nel Set di schemi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: ec1395e0-d03c-4130-810d-f2db656937bd
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1d388db50ae935ef85b720177bd31c832a353d31
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68145175"
---
# <a name="searching-the-schema-set"></a>Ricerche nel set di schemi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

XML Schema Explorer consente di eseguire ricerche nel set di schemi nei seguenti modi:  
  
- Ricerca per parole chiave.  
  
- Ricerca specifica dello schema.  
  
## <a name="keyword-search"></a>Ricerca per parole chiave  
 Eseguire ricerche per parole chiave immettendo una sottostringa nel **set di schemi di ricerca** casella di testo della barra degli strumenti XML Schema Explorer.  
  
 ![Ricerca per parole chiave XML Schema Explorer](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")  
  
 XML Schema Explorer esegue ricerche dei seguenti elementi nel set di schemi:  
  
- Attributi `name` o `ref` che corrispondono alla parola chiave specificata. In questo modo è possibile individuare elementi, attributi, tipi e così via in base al nome.  
  
- Attributi `schemaLocation` delle istruzioni include.  
  
- Attributi `namespace` delle istruzioni import.  
  
## <a name="schema-specific-search"></a>Ricerca specifica dello schema  
 XML Schema Explorer comprende inoltre ricerche predefinite cui è possibile accedere usando il menu di scelta rapida. Per altre informazioni sui menu di scelta rapida disponibili, vedere [menu di scelta rapida](../xml-tools/context-menus-xml-schema-explorer.md). È anche possibile eseguire una ricerca specifica dello schema dalla visualizzazione iniziale; per altre informazioni, vedere la sezione "Dettagli Set di schemi" nel [visualizzazione iniziale](../xml-tools/start-view.md) argomento.  
  
## <a name="displaying-and-navigating-search-results"></a>Visualizzazione e spostamento all'interno dei risultati di ricerca  
 Dopo aver terminato la ricerca, il riquadro dei risultati di riepilogo viene aggiunto alla barra degli strumenti con i risultati della ricerca. I risultati della ricerca sono anche evidenziati in XML Schema Explorer e contrassegnati con un segno di spunta sulla barra di scorrimento verticale. È possibile passare i risultati della ricerca usando il **passare al risultato della ricerca successivo** e **ricerca risultato precedente** pulsanti nel riquadro dei risultati di riepilogo della barra degli strumenti XML Schema Explorer; usando i tasti della tastiera F3 e MAIUSC+F3; oppure fare clic sul segni di graduazione nella barra di scorrimento.  
  
 È possibile aggiungere i risultati della ricerca all'area di lavoro facendo il **Aggiungi nodi evidenziati all'area di lavoro** pulsante nel riquadro dei risultati di riepilogo.  
  
 ![Risultato di ricerca XML Schema Explorer](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")  
  
## <a name="clearing-search-results"></a>Eliminazione dei risultati di ricerca  
 Per cancellare i risultati della ricerca, scegliere il **x** pulsante nel riquadro dei risultati di riepilogo della barra degli strumenti di ricerca di XML Schema Explorer.  
  
## <a name="see-also"></a>Vedere anche  
 [XML Schema Explorer](../xml-tools/xml-schema-explorer.md)
