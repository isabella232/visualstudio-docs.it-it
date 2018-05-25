---
title: 'Procedura: creare un documento XML in base allo schema XSD'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 193b195f-e918-4c79-a1a1-8096a1433bde
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6d3da2e6b5b0c9ea2701524c0fb2fde1e1313687
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/25/2018
---
# <a name="how-to-create-an-xml-document-based-on-an-xsd-schema"></a>Procedura: creare un documento XML in base a uno schema XSD

Il **genera XML di esempio** funzionalità genera un file XML di esempio basato sul file XML Schema (XSD).

 È possibile usare questa opzione per gli scenari seguenti:

-   Per comprendere l'uso di diversi costrutti nello schema.

-   Per confermare che lo schema funziona come previsto.

Il **genera XML di esempio** funzionalità è disponibile solo in elementi globali e richiede un set di schemi XML valido.

Questa funzionalità genera di norma documenti XML validi. Tuttavia, se lo schema contiene uno o più degli elementi seguenti, l'esempio potrebbe non essere valido:

-   I vincoli di identità `xs:key`, `xs:keyref` e `xs:unique`.

-   Facet `xs:pattern`.

-   Enumerazioni di tipo `xs:QName`.

-   I tipi `xs:ENTITY`, `xs:ENTITIES` e `xs:NOTATION`.

Si noti inoltre che il contenuto `xs:base64Binary` sarà generato solo se le enumerazioni si verificano nello schema per il tipo specificato.

## <a name="to-generate-an-xml-instance-document-based-on-the-xsd-file"></a>Per generare un documento di istanza XML basato sul file XSD

1.  Seguire i passaggi descritti in [procedura: creare e modificare un file di schema XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2.  Nel [XML Schema Explorer](../xml-tools/xml-schema-explorer.md), fare doppio clic su di `PurchaseOrder` elemento globale. Selezionare **genera XML di esempio**.

     Quando si seleziona questa opzione, PurchaseOrder. *xml* file con il seguente contenuto XML di esempio verrà generato e aperto nell'Editor XML:

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

## <a name="see-also"></a>Vedere anche

- [Utilizzo di dati XML](../xml-tools/working-with-xml-data.md)