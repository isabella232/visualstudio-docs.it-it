---
title: Convalida di documenti XML nell'editor XML
description: Informazioni sulla convalida dei documenti XML nell'editor XML e su come controlla la sintassi XML 1.0 ed esegue la convalida dei dati durante la digitazione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: abb353bd-6c4a-4978-b03b-a8c245bbfb55
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
ms.workload:
- multiple
ms.openlocfilehash: 19585e36094868cedad279f0f7b4d982647da1d7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122091825"
---
# <a name="xml-document-validation"></a>Convalida di documenti XML

L'editor XML controlla la sintassi XML 1.0 ed esegue anche la convalida dei dati durante la digitazione. L'editor può eseguire la convalida tramite una DTD (Document Type Definition) o uno schema. Le sottolineature ondulate di colore rosso evidenziano gli errori di formato del codice XML 1.0. Le sottolineature ondulate di colore blu mostrano gli errori di semantica rilevati sulla base della DTD o della convalida dello schema. A ciascun errore è associata una voce nell'elenco degli errori. È possibile inoltre visualizzare il messaggio di errore posizionando per qualche istante il puntatore del mouse sulla sottolineatura ondulata.

Gli schemi usati nella convalida vengono individuati confrontando il `targetNamespace` di uno schema compilato con la dichiarazione xmlns dell'elemento. Gli schemi compilati vengono caricati da una delle seguenti posizioni, elencate in ordine di priorità:

- Dal nome file specificato nel **campo Schemi** della finestra **Proprietà del** documento.

- Schema inline o DTD.

- Una DTD esterna o un attributo `xsd:schemaLocation` e `xsd:noNamespaceSchemaLocation`

- Un URI dello spazio dei nomi dello schema XDR "x-schema".

Gli schemi possono essere rilevati anche nelle seguenti posizioni aggiuntive quando lo schema dispone di uno spazio dei nomi di destinazione non vuoto:

- Un'altra finestra dell'editor contenente lo schema.

- Uno schema nella soluzione corrente.

- Uno schema dalla directory della cache degli schemi.

## <a name="xslt-files"></a>File XSLT
Quando si modifica un file XSLT, il file *xslt.xsd* che si trova nella cache dello schema viene utilizzato per la convalida. Gli errori di convalida vengono visualizzati con una sottolineatura ondulata di colore blu. Gli errori del compilatore XSLT vengono visualizzati con una sottolineatura ondulata di colore rosso.

## <a name="xml-schema-xsd-files"></a>File XML Schema (XSD)
Quando si modifica un file XML Schema, per la convalida viene utilizzato il file *xsdschema.xsd* che si trova nella cache dello schema. Gli errori di convalida vengono visualizzati con una sottolineatura ondulata di colore blu. Anche gli errori di compilazione vengono visualizzati con una sottolineatura ondulata di colore rosso.

## <a name="see-also"></a>Vedi anche

- [Editor XML](../xml-tools/xml-editor.md)
