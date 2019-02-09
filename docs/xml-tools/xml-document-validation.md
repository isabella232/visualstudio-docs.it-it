---
title: Convalida di documenti XML nell'Editor XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: abb353bd-6c4a-4978-b03b-a8c245bbfb55
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 74c8f327f17e6d2e05d0748195cb139f3a05a6f4
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55931195"
---
# <a name="xml-document-validation"></a>Convalida di documenti XML

L'editor XML verifica la sintassi XML 1.0 ed esegue inoltre la convalida dei dati durante la digitazione. L'editor può eseguire la convalida tramite una DTD (Document Type Definition) o uno schema. Le sottolineature ondulate di colore rosso evidenziano gli errori di formato del codice XML 1.0. Le sottolineature ondulate di colore blu mostrano gli errori di semantica rilevati sulla base della DTD o della convalida dello schema. A ciascun errore è associata una voce nell'elenco degli errori. È possibile inoltre visualizzare il messaggio di errore posizionando per qualche istante il puntatore del mouse sulla sottolineatura ondulata.

 Gli schemi usati nella convalida vengono individuati confrontando il `targetNamespace` di uno schema compilato con la dichiarazione xmlns dell'elemento. Gli schemi compilati vengono caricati da una delle seguenti posizioni, elencate in ordine di priorità:

-   Dal nome del file specificato nella **schemi** campo del documento **proprietà** finestra.

-   Schema inline o DTD.

-   Una DTD esterna o un attributo `xsd:schemaLocation` e `xsd:noNamespaceSchemaLocation`

-   Un URI dello spazio dei nomi dello schema XDR "x-schema".

Gli schemi possono essere rilevati anche nelle seguenti posizioni aggiuntive quando lo schema dispone di uno spazio dei nomi di destinazione non vuoto:

-   Un'altra finestra dell'editor contenente lo schema.

-   Uno schema nella soluzione corrente.

-   Uno schema dalla directory della cache degli schemi.

## <a name="xslt-files"></a>File XSLT
 Quando si modifica un file XSLT, il *XSLT* file che si trova nella cache dello schema viene usato per la convalida. Gli errori di convalida vengono visualizzati con una sottolineatura ondulata di colore blu. Gli errori del compilatore XSLT vengono visualizzati con una sottolineatura ondulata di colore rosso.

## <a name="xml-schema-xsd-files"></a>File XML schema (XSD)
 Quando si modifica un file di XML Schema, il *XSDSchema* file che si trova nella cache dello schema viene usato per la convalida. Gli errori di convalida vengono visualizzati con una sottolineatura ondulata di colore blu. Anche gli errori di compilazione vengono visualizzati con una sottolineatura ondulata di colore rosso.

## <a name="see-also"></a>Vedere anche

- [Editor XML](../xml-tools/xml-editor.md)