---
title: XML Schema Explorer - set di schemi di ricerca
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: ec1395e0-d03c-4130-810d-f2db656937bd
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8b3aa631ab673f7b6d679cbe39459ecb9a5fbbaf
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="searching-the-schema-set"></a>Ricerche nel set di schemi

XML Schema Explorer consente di eseguire ricerche nel set di schemi nei seguenti modi:

-   Ricerca per parole chiave.

-   Ricerca specifica dello schema.

## <a name="keyword-search"></a>Ricerca per parole chiave

 Eseguire ricerche di parole chiave immettendo una sottostringa nel **set di schemi di ricerca** casella di testo della barra degli strumenti di XML Schema Explorer.

 ![Ricerca di parola chiave XML Schema Explorer](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")

 XML Schema Explorer esegue la ricerca lo schema impostata per gli attributi seguenti:

-   Attributi `name` o `ref` che corrispondono alla parola chiave specificata. In questo modo è possibile trovare gli elementi, attributi, tipi e così via, in base al nome.

-   Attributi `schemaLocation` delle istruzioni include.

-   Attributi `namespace` delle istruzioni import.

## <a name="schema-specific-search"></a>Ricerca specifica dello schema

 XML Schema Explorer comprende inoltre ricerche predefinite cui è possibile accedere usando il menu di scelta rapida. Per ulteriori informazioni sui menu di contesto disponibili, vedere [menu di scelta rapida](../xml-tools/context-menus-xml-schema-explorer.md). È anche possibile eseguire una ricerca specifica dello schema dalla visualizzazione iniziale; Per ulteriori informazioni, vedere la sezione "Dettagli Set di schemi" nel [visualizzazione iniziale](../xml-tools/start-view.md) argomento.

## <a name="displaying-and-navigating-search-results"></a>Visualizzazione e spostamento all'interno dei risultati di ricerca

 Dopo aver terminato la ricerca, il riquadro dei risultati di riepilogo viene aggiunto alla barra degli strumenti con i risultati della ricerca. I risultati della ricerca sono anche evidenziati in XML Schema Explorer e contrassegnati con un segno di spunta sulla barra di scorrimento verticale. È possibile passare i risultati della ricerca mediante la **ricerca risultato successivo** e **ricerca risultato precedente** pulsanti nel riquadro dei risultati di riepilogo della barra degli strumenti di XML Schema Explorer; usando i tasti della tastiera F3 e MAIUSC + F3 oppure facendo clic sui segni di graduazione nella barra di scorrimento.

 È possibile aggiungere i risultati della ricerca all'area di lavoro facendo clic di **Aggiungi nodi evidenziati all'area di lavoro** pulsante del riquadro dei risultati di riepilogo.

 ![Risultato di ricerca XML Schema Explorer](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")

## <a name="clearing-search-results"></a>Eliminazione dei risultati di ricerca

 Per cancellare i risultati della ricerca, fare clic su di **x** pulsante del riquadro dei risultati di riepilogo della barra di ricerca di XML Schema Explorer.

## <a name="see-also"></a>Vedere anche

- [XML Schema Explorer](../xml-tools/xml-schema-explorer.md)