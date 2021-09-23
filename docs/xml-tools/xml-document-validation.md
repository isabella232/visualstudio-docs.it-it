---
title: Convalida di documenti XML nell'editor XML
description: Informazioni sulla convalida dei documenti XML nell'editor XML e su come controlla la sintassi XML 1.0 ed esegue la convalida dei dati durante la digitazione.
ms.custom: SEO-VS-2020
ms.date: 09/16/2021
ms.topic: conceptual
ms.assetid: abb353bd-6c4a-4978-b03b-a8c245bbfb55
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
ms.workload:
- multiple
ms.openlocfilehash: 1dc2fcbbac33fe19cd50b44675609f7121c1be69
ms.sourcegitcommit: da5efd7698e357c59ba9b7dbbcaaceb5d1cfade2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/23/2021
ms.locfileid: "128307051"
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

## <a name="entity-reference-limit"></a>Limite dei riferimenti alle entità
Per impostazione predefinita, l'elaborazione DTD limita il numero di riferimenti a entità a 10.000 riferimenti e può contenere la maggior parte degli schemi XML.  Il messaggio di errore in Visual Studio può essere "Superato il limite di riferimenti alle entità per filename".

Se si verifica questa limitazione nell'elaborazione di un documento XML e si vuole estendere il validator a uno schema più grande, è possibile modificare questa impostazione con la chiave Visual Studio `MaxNumberOfDtdEntityReferences` registro di sistema. Per [altre informazioni su come apportare questa modifica, Visual Studio modifica](../install/tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance) del Registro di sistema per un'istanza di . Si noti che questo vale per tutti i documenti XML aperti dall'utente in tale computer.

## <a name="see-also"></a>Vedi anche

- [Editor XML](../xml-tools/xml-editor.md)
