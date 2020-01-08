---
title: XML Schema Explorer-ricerca nel set di schemi
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ec1395e0-d03c-4130-810d-f2db656937bd
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8378ebaccefaedfcc3d83f23bcab56f7417264dd
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592503"
---
# <a name="search-the-schema-set"></a>Eseguire ricerche nel set di schemi

**XML Schema Explorer** consente di eseguire ricerche nel set di schemi nei modi seguenti:

- Ricerca per parole chiave.

- Ricerca specifica dello schema.

## <a name="keyword-search"></a>Ricerca per parole chiave

Per eseguire ricerche di parole chiave, immettere una sottostringa nella casella di testo **Cerca SchemaSet** della barra degli strumenti di **XML Schema Explorer** .

![Ricerca di parole chiave in XML Schema Explorer](../xml-tools/media/schemaexplorersearch.gif)

In **XML Schema Explorer** viene eseguita la ricerca del set di schemi per gli attributi seguenti:

- Attributi `name` o `ref` che corrispondono alla parola chiave specificata. Per nome è possibile trovare elementi, attributi, tipi e così via.

- Attributi `schemaLocation` delle istruzioni include.

- Attributi `namespace` delle istruzioni import.

## <a name="schema-specific-search"></a>Ricerca specifica dello schema

In **XML Schema Explorer** sono inoltre incluse ricerche predefinite a cui è possibile accedere tramite il menu di scelta rapida (clic con il pulsante destro del mouse) di **XML Schema Explorer**. Per ulteriori informazioni sui menu di scelta rapida disponibili, vedere [menu di scelta rapida](../xml-tools/context-menus-xml-schema-explorer.md). È anche possibile eseguire una ricerca specifica dello schema dalla visualizzazione iniziale. Per ulteriori informazioni, vedere la sezione "Dettagli set di schemi" nell'argomento [visualizzazione iniziale](../xml-tools/start-view.md) .

## <a name="display-and-navigate-search-results"></a>Visualizzare ed esplorare i risultati della ricerca

Dopo aver terminato la ricerca, il riquadro dei risultati di riepilogo viene aggiunto alla barra degli strumenti con i risultati della ricerca. I risultati della ricerca sono evidenziati anche in **XML Schema Explorer** e contrassegnati con i segni di avanzamento sulla barra di scorrimento verticale. È possibile esplorare i risultati della ricerca usando i pulsanti **Vai al** risultato della ricerca successivo e **Vai ai risultati della ricerca precedente** nel riquadro dei risultati di riepilogo della barra degli strumenti di **XML Schema Explorer** . utilizzando i tasti **F3** e **MAIUSC**+**F3**; oppure facendo clic sui segni di graduazione nella barra di scorrimento.

È possibile aggiungere i risultati della ricerca all'area di lavoro facendo clic sul pulsante **Aggiungi nodi evidenziati all'area di lavoro** nel riquadro dei risultati di riepilogo.

![Risultato della ricerca in XML Schema Explorer](../xml-tools/media/schemaexplorersearchresult.gif)

## <a name="clear-search-results"></a>Cancella risultati della ricerca

Per cancellare i risultati della ricerca, fare clic sul pulsante **x** nel riquadro risultati riepilogo della barra degli strumenti di ricerca di **XML Schema Explorer** .

## <a name="see-also"></a>Vedere anche

- [XML Schema Explorer](../xml-tools/xml-schema-explorer.md)
