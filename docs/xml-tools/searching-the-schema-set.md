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
ms.openlocfilehash: c110344499281243628d633d005506af5cd801d0
ms.sourcegitcommit: d1824ab926ebbc4a8057163e0edeaf35cec57433
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/24/2018
---
# <a name="search-the-schema-set"></a>Cercare il set di schemi

Il **XML Schema Explorer** consente di cercare lo schema impostato nei modi seguenti:

-   Ricerca per parole chiave.

-   Ricerca specifica dello schema.

## <a name="keyword-search"></a>Ricerca per parole chiave

 Eseguire ricerche per parole chiave immettendo una sottostringa nel **set di schemi di ricerca** casella di testo del **XML Schema Explorer** sulla barra degli strumenti.

 ![Ricerca di parola chiave XML Schema Explorer](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")

 Il **XML Schema Explorer** Cerca lo schema impostata per gli attributi seguenti:

-   Attributi `name` o `ref` che corrispondono alla parola chiave specificata. È possibile trovare gli elementi, attributi, tipi e così via, in base al nome.

-   Attributi `schemaLocation` delle istruzioni include.

-   Attributi `namespace` delle istruzioni import.

## <a name="schema-specific-search"></a>Ricerca specifica dello schema

 Il **XML Schema Explorer** comprende inoltre ricerche predefinite cui è possibile accedere tramite il menu di scelta rapida del **XML Schema Explorer**. Per ulteriori informazioni sui menu di scelta rapida disponibili, vedere [menu di scelta rapida](../xml-tools/context-menus-xml-schema-explorer.md). È anche possibile eseguire una ricerca specifica dello schema dalla visualizzazione iniziale; Per ulteriori informazioni, vedere la sezione "Dettagli Set di schemi" nel [visualizzazione iniziale](../xml-tools/start-view.md) argomento.

## <a name="display-and-navigate-search-results"></a>Visualizzare e passare i risultati della ricerca

 Dopo aver terminato la ricerca, il riquadro dei risultati di riepilogo viene aggiunto alla barra degli strumenti con i risultati della ricerca. I risultati della ricerca vengono evidenziati le **XML Schema Explorer** e contrassegnato dal segno di spunta sulla barra di scorrimento verticale. È possibile passare i risultati della ricerca mediante la **ricerca risultato successivo** e **Vai al risultato di ricerca precedente** pulsanti nel riquadro dei risultati di riepilogo del **XML Schema Explorer**barra degli strumenti; tramite i tasti **F3** e **MAIUSC**+**F3**; o facendo clic sui segni di graduazione nella barra di scorrimento.

 È possibile aggiungere i risultati della ricerca all'area di lavoro facendo clic di **Aggiungi nodi evidenziati all'area di lavoro** pulsante del riquadro dei risultati di riepilogo.

 ![Risultato di ricerca XML Schema Explorer](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")

## <a name="clear-search-results"></a>Cancella risultati

 Per cancellare i risultati della ricerca, fare clic sui **x** pulsante nel riquadro dei risultati di riepilogo del **XML Schema Explorer** della barra degli strumenti.

## <a name="see-also"></a>Vedere anche

- [XML Schema Explorer](../xml-tools/xml-schema-explorer.md)