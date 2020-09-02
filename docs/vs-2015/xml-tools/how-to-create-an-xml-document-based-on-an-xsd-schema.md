---
title: 'Procedura: creare un documento XML in base a uno schema XSD | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 193b195f-e918-4c79-a1a1-8096a1433bde
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e9e48c48d6711a1eb21157122d13790e22688855
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670941"
---
# <a name="how-to-create-an-xml-document-based-on-an-xsd-schema"></a>Procedura: creare un documento XML in base allo schema XSD
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La funzionalità **genera XML di esempio** genera un file XML di esempio basato sul file XML Schema (XSD).

 È possibile usare questa opzione per gli scenari seguenti:

- Per comprendere l'uso di diversi costrutti nello schema.

- Per confermare che lo schema funziona come previsto.

  La funzionalità **genera XML di esempio** è disponibile solo sugli elementi globali e richiede un set di XML schema valido.

  Questa funzionalità genera di norma documenti XML validi. Tuttavia, se lo schema contiene uno o più degli elementi seguenti, l'esempio potrebbe non essere valido:

- I vincoli di identità `xs:key`, `xs:keyref` e `xs:unique`.

- `xs:pattern` facet.

- Enumerazioni di tipo `xs:QName`.

- `xs:ENTITY``xs:ENTITIES`tipi, e `xs:NOTATION` .

  Si noti inoltre che il contenuto `xs:base64Binary` sarà generato solo se le enumerazioni si verificano nello schema per il tipo specificato.

### <a name="to-generate-an-xml-instance-document-based-on-the-xsd-file"></a>Per generare un documento di istanza XML basato sul file XSD

1. Seguire i passaggi in [procedura: creare e modificare un file di schema XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2. In [XML Schema Explorer](../xml-tools/xml-schema-explorer.md)fare clic con il pulsante destro del mouse sull' `PurchaseOrder` elemento globale. Selezionare **genera XML di esempio**.

     Quando si seleziona questa opzione, il file PurchaseOrder.xml con il seguente contenuto XML di esempio sarà generato e aperto nell'editor XML:

    ```
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
 [Utilizzo di dati XML](../xml-tools/working-with-xml-data.md)
