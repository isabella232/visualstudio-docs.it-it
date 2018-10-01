---
title: 'Procedura: creare un documento XML in base a uno Schema XSD | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 193b195f-e918-4c79-a1a1-8096a1433bde
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7ce870506097c820d5a6a8e981ffd63d64257780
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47518586"
---
# <a name="how-to-create-an-xml-document-based-on-an-xsd-schema"></a>Procedura: creare un documento XML in base allo schema XSD
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [procedura: creare un documento XML basato su uno Schema XSD](https://docs.microsoft.com/visualstudio/xml-tools/how-to-create-an-xml-document-based-on-an-xsd-schema).  
  
  
Il **genera XML di esempio** funzionalità genera un file XML di esempio basato su file di Schema XSD (XML).  
  
 È possibile usare questa opzione per gli scenari seguenti:  
  
-   Per comprendere l'uso di diversi costrutti nello schema.  
  
-   Per confermare che lo schema funziona come previsto.  
  
 Il **genera XML di esempio** funzionalità è disponibile solo per gli elementi globali e richiede un set di schemi XML valido.  
  
 Questa funzionalità genera di norma documenti XML validi. Tuttavia, se lo schema contiene uno o più degli elementi seguenti, l'esempio potrebbe non essere valido:  
  
-   I vincoli di identità `xs:key`, `xs:keyref` e `xs:unique`.  
  
-   Facet `xs:pattern`.  
  
-   Enumerazioni di tipo `xs:QName`.  
  
-   I tipi `xs:ENTITY`, `xs:ENTITIES` e `xs:NOTATION`.  
  
 Si noti inoltre che il contenuto `xs:base64Binary` sarà generato solo se le enumerazioni si verificano nello schema per il tipo specificato.  
  
### <a name="to-generate-an-xml-instance-document-based-on-the-xsd-file"></a>Per generare un documento di istanza XML basato sul file XSD  
  
1.  Seguire i passaggi descritti in [procedura: creare e modificare un File di Schema XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).  
  
2.  Nel [XML Schema Explorer](../xml-tools/xml-schema-explorer.md), fare doppio clic su di `PurchaseOrder` elemento globale. Selezionare **genera XML di esempio**.  
  
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



