---
title: 'Procedura: Creare un documento XML in base a uno Schema XSD | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 193b195f-e918-4c79-a1a1-8096a1433bde
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 623da37807e0fd61041bfeb9ab411ce0cb96d4b5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68164483"
---
# <a name="how-to-create-an-xml-document-based-on-an-xsd-schema"></a>Procedura: Creare un documento XML in base a uno schema XSD
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il **genera XML di esempio** funzionalità genera un file XML di esempio basato su file di Schema XSD (XML).  
  
 È possibile usare questa opzione per gli scenari seguenti:  
  
- Per comprendere l'uso di diversi costrutti nello schema.  
  
- Per confermare che lo schema funziona come previsto.  
  
  Il **genera XML di esempio** funzionalità è disponibile solo per gli elementi globali e richiede un set di schemi XML valido.  
  
  Questa funzionalità genera di norma documenti XML validi. Tuttavia, se lo schema contiene uno o più degli elementi seguenti, l'esempio potrebbe non essere valido:  
  
- I vincoli di identità `xs:key`, `xs:keyref` e `xs:unique`.  
  
- Facet `xs:pattern`.  
  
- Enumerazioni di tipo `xs:QName`.  
  
- I tipi `xs:ENTITY`, `xs:ENTITIES` e `xs:NOTATION`.  
  
  Si noti inoltre che il contenuto `xs:base64Binary` sarà generato solo se le enumerazioni si verificano nello schema per il tipo specificato.  
  
### <a name="to-generate-an-xml-instance-document-based-on-the-xsd-file"></a>Per generare un documento di istanza XML basato sul file XSD  
  
1. Seguire i passaggi in [come: Creare e modificare un File di Schema XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).  
  
2. Nel [XML Schema Explorer](../xml-tools/xml-schema-explorer.md), fare doppio clic su di `PurchaseOrder` elemento globale. Selezionare **genera XML di esempio**.  
  
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
 [Uso dei dati XML](../xml-tools/working-with-xml-data.md)
