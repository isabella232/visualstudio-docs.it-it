---
title: Ricerca nel set di schemi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: ec1395e0-d03c-4130-810d-f2db656937bd
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0e3a8563d5e2cd29c9c521761498d7ef87b7cbab
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656164"
---
# <a name="searching-the-schema-set"></a>Ricerche nel set di schemi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

XML Schema Explorer consente di eseguire ricerche nel set di schemi nei seguenti modi:

- Ricerca per parole chiave.

- Ricerca specifica dello schema.

## <a name="keyword-search"></a>Ricerca per parole chiave
 Per eseguire ricerche di parole chiave, immettere una sottostringa nella casella di testo **Cerca SchemaSet** della barra degli strumenti di XML Schema Explorer.

 ![Ricerca parole chiave di XML Schema Explorer](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")

 XML Schema Explorer esegue ricerche dei seguenti elementi nel set di schemi:

- Attributi `name` o `ref` che corrispondono alla parola chiave specificata. In questo modo è possibile individuare elementi, attributi, tipi e così via in base al nome.

- Attributi `schemaLocation` delle istruzioni include.

- Attributi `namespace` delle istruzioni import.

## <a name="schema-specific-search"></a>Ricerca specifica dello schema
 XML Schema Explorer comprende inoltre ricerche predefinite cui è possibile accedere usando il menu di scelta rapida. Per ulteriori informazioni sui menu di scelta rapida disponibili, vedere [menu di scelta rapida](../xml-tools/context-menus-xml-schema-explorer.md). È anche possibile eseguire una ricerca specifica dello schema dalla visualizzazione iniziale. Per ulteriori informazioni, vedere la sezione "Dettagli set di schemi" nell'argomento [visualizzazione iniziale](../xml-tools/start-view.md) .

## <a name="displaying-and-navigating-search-results"></a>Visualizzazione e spostamento all'interno dei risultati di ricerca
 Dopo aver terminato la ricerca, il riquadro dei risultati di riepilogo viene aggiunto alla barra degli strumenti con i risultati della ricerca. I risultati della ricerca sono anche evidenziati in XML Schema Explorer e contrassegnati con un segno di spunta sulla barra di scorrimento verticale. È possibile esplorare i risultati della ricerca usando i pulsanti **Vai al** risultato della ricerca successivo e **Vai ai risultati della ricerca precedente** nel riquadro dei risultati di riepilogo della barra degli strumenti di XML Schema Explorer. utilizzando i tasti F3 e MAIUSC + F3; oppure facendo clic sui segni di graduazione nella barra di scorrimento.

 È possibile aggiungere i risultati della ricerca all'area di lavoro facendo clic sul pulsante **Aggiungi nodi evidenziati all'area di lavoro** nel riquadro dei risultati di riepilogo.

 ![Risultato della ricerca in XML Schema Explorer](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")

## <a name="clearing-search-results"></a>Eliminazione dei risultati di ricerca
 Per cancellare i risultati della ricerca, fare clic sul pulsante **x** nel riquadro risultati riepilogo della barra degli strumenti di ricerca di XML Schema Explorer.

## <a name="see-also"></a>Vedere anche
 [XML Schema Explorer](../xml-tools/xml-schema-explorer.md)
