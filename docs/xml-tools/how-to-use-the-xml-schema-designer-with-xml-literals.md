---
title: 'Procedura: utilizzare Progettazione XML Schema con i valori letterali XML'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d11803e7-f81a-41a2-a145-ba494a45cc93
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: b515092087ab213db5d3002f00c56753c2e3de14
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "85814642"
---
# <a name="how-to-use-the-xml-schema-designer-with-xml-literals"></a>Procedura: utilizzare Progettazione XML Schema con valori letterali XML

In questo argomento viene descritto come visualizzare uno schema associato a un valore letterale XML in un progetto di Visual Basic.

## <a name="create-a-new-visual-basic-project"></a>Creare un nuovo progetto di Visual Basic

1. Aprire Visual Studio.

2. Creare un nuovo progetto di **app Console** Visual Basic denominato **XMLLiterals**.

     Il nuovo progetto contiene un file di origine Visual Basic, *Module1. vb*.

## <a name="add-an-existing-xsd-file"></a>Aggiungere un file XSD esistente

1. Aprire un nuovo file di testo nel blocco note. Copiare il codice di esempio XML schema dallo [schema di ordine di acquisto](../xml-tools/sample-xsd-file-simple-schema.md) e incollarlo nel file.

2. Salvare il file in un percorso con il nome *PurchaseOrderSchema. xsd*.

3. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul nome del progetto, scegliere **Aggiungi**, quindi selezionare **elemento esistente**. Verrà visualizzata la finestra di dialogo **elemento Aggiungi** . Individuare il file *PurchaseOrderSchema. xsd* , selezionarlo e quindi fare clic su **Aggiungi**.

     Il progetto XMLLiterals contiene ora due file: *Module1. vb* e *PurchaseOrderSchema. xsd*.

## <a name="add-code"></a>Aggiungere codice

Per aggiungere Visual Basic codice con un valore letterale XML, in base al file XSD incluso nel progetto:

1. Sostituire il codice nel file *Module1. vb* con il codice seguente:

   ```vb
   Imports <xmlns:ns="http://tempuri.org/PurchaseOrderSchema.xsd">

   Module Module1
      Sub Main()

          Dim XMLLiteral = <ns:PurchaseOrder OrderDate="1900-01-01">
                               <ns:ShipTo country="US">
                                   <ns:name>name1</ns:name>
                                   <ns:street>street1</ns:street>
                                   <ns:city>city1</ns:city>
                                   <ns:state>state1</ns:state>
                                   <ns:zip>1</ns:zip>
                               </ns:ShipTo>
                               <ns:BillTo country="US">
                                   <ns:name>name1</ns:name>
                                   <ns:street>street1</ns:street>
                                   <ns:city>city1</ns:city>
                                   <ns:state>state1</ns:state>
                                   <ns:zip>1</ns:zip>
                               </ns:BillTo>
                           </ns:PurchaseOrder>

      End Sub
   End Module
   ```

2. Fare clic con il pulsante destro del mouse su qualsiasi nodo XML in un valore letterale XML o un'importazione di spazi dei nomi XML e selezionare **Mostra in Esplora schema**

   **XML Schema Explorer** viene visualizzato side-by-side con un file di Visual Basic con il valore letterale XML associato al set di XML Schema.
