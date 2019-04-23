---
title: XML Schema Explorer - cercare nel set di schemi
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ec1395e0-d03c-4130-810d-f2db656937bd
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b73d5c8acac211db09926acf0ba8009aa04ac0a8
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60070899"
---
# <a name="search-the-schema-set"></a>Eseguire ricerche nel set di schemi

Il **XML Schema Explorer** consente di cercare lo schema impostato nei modi seguenti:

- Ricerca per parole chiave.

- Ricerca specifica dello schema.

## <a name="keyword-search"></a>Ricerca per parole chiave

 Eseguire ricerche per parole chiave immettendo una sottostringa nel **set di schemi di ricerca** casella di testo del **XML Schema Explorer** sulla barra degli strumenti.

 ![Ricerca di parole chiave in XML Schema Explorer](../xml-tools/media/schemaexplorersearch.gif)

 Il **XML Schema Explorer** Cerca lo schema impostato per gli attributi seguenti:

- Attributi `name` o `ref` che corrispondono alla parola chiave specificata. È possibile trovare gli elementi, attributi, tipi e così via, in base al nome.

- Attributi `schemaLocation` delle istruzioni include.

- Attributi `namespace` delle istruzioni import.

## <a name="schema-specific-search"></a>Ricerca specifica dello schema

 Il **XML Schema Explorer** comprende inoltre ricerche predefinite cui è possibile accedere tramite il menu di scelta rapida delle **XML Schema Explorer**. Per altre informazioni sui menu di scelta rapida disponibili, vedere [menu di scelta rapida](../xml-tools/context-menus-xml-schema-explorer.md). È anche possibile eseguire una ricerca specifica dello schema dalla visualizzazione iniziale; per altre informazioni, vedere la sezione "Dettagli Set di schemi" nel [visualizzazione iniziale](../xml-tools/start-view.md) argomento.

## <a name="display-and-navigate-search-results"></a>Visualizzare e passare i risultati della ricerca

 Dopo aver terminato la ricerca, il riquadro dei risultati di riepilogo viene aggiunto alla barra degli strumenti con i risultati della ricerca. I risultati della ricerca vengono evidenziate anche nella **XML Schema Explorer** e contrassegnato dal segno di spunta sulla barra di scorrimento verticale. È possibile passare i risultati della ricerca usando il **passare al risultato della ricerca successivo** e **ricerca risultato precedente** pulsanti nel riquadro dei risultati di riepilogo del **XML Schema Explorer**barra degli strumenti; usando i tasti **F3** e **MAIUSC**+**F3**; oppure facendo clic sul segni di graduazione nella barra di scorrimento.

 È possibile aggiungere i risultati della ricerca all'area di lavoro facendo il **Aggiungi nodi evidenziati all'area di lavoro** pulsante nel riquadro dei risultati di riepilogo.

 ![Risultati della ricerca in XML Schema Explorer](../xml-tools/media/schemaexplorersearchresult.gif)

## <a name="clear-search-results"></a>Risultati della ricerca non crittografato

 Per cancellare i risultati della ricerca, fare clic sui **x** pulsante nel riquadro dei risultati di riepilogo della **XML Schema Explorer** della barra degli strumenti.

## <a name="see-also"></a>Vedere anche

- [XML Schema Explorer](../xml-tools/xml-schema-explorer.md)