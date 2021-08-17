---
title: 'Procedura: creare un documento XML in base allo schema XSD'
description: Informazioni su come usare la funzionalità Genera XML di esempio per creare un documento XML basato su uno schema XSD.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 193b195f-e918-4c79-a1a1-8096a1433bde
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
ms.workload:
- multiple
ms.openlocfilehash: b057b4fa8670e1b7ed4c1f320a2e32b488fca172
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122025108"
---
# <a name="how-to-create-an-xml-document-based-on-an-xsd-schema"></a>Procedura: Creare un documento XML basato su uno schema XSD

La **funzionalità Genera XML** di esempio genera un file XML di esempio basato sul file XML Schema (XSD).

È possibile usare questa opzione per gli scenari seguenti:

- Per comprendere l'uso di diversi costrutti nello schema.

- Per confermare che lo schema funziona come previsto.

La **funzionalità Genera XML di** esempio è disponibile solo per gli elementi globali e richiede un set di XML Schema valido.

Questa funzionalità genera di norma documenti XML validi. Tuttavia, se lo schema contiene uno o più degli elementi seguenti, l'esempio potrebbe non essere valido:

- I vincoli di identità `xs:key`, `xs:keyref` e `xs:unique`.

- `xs:pattern` Sfaccettature.

- Enumerazioni di tipo `xs:QName`.

- `xs:ENTITY`Tipi `xs:ENTITIES` , `xs:NOTATION` e .

Si noti inoltre che il contenuto `xs:base64Binary` sarà generato solo se le enumerazioni si verificano nello schema per il tipo specificato.

## <a name="to-generate-an-xml-instance-document-based-on-the-xsd-file"></a>Per generare un documento di istanza XML basato sul file XSD

1. Seguire la procedura descritta in [Procedura: Creare e modificare un file di schema XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2. In XML [Schema Explorer fare](../xml-tools/xml-schema-explorer.md)clic con il pulsante destro del mouse `PurchaseOrder` sull'elemento globale e **quindi scegliere Genera XML di esempio.**

     Quando si seleziona questa opzione, PurchaseOrder. *Il* file xml con il contenuto XML di esempio seguente verrà generato e aperto nell'editor XML:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <PurchaseOrder OrderDate="1900-01-01" xmlns="http://tempuri.org/PurchaseOrderSchema.xsd">
      <ShipTo country="US">
        <name>name1</name>
        <street>street1</street>
        <city>city1</city>
        <state>state1</state>
        <zip>1</zip>
      </ShipTo>
      <ShipTo country="US">
        <name>name2</name>
        <street>street2</street>
        <city>city2</city>
        <state>state2</state>
        <zip>-79228162514264337593543950335</zip>
      </ShipTo>
      <BillTo country="US">
        <name>name1</name>
        <street>street1</street>
        <city>city1</city>
        <state>state1</state>
        <zip>1</zip>
      </BillTo>
    </PurchaseOrder>
    ```
