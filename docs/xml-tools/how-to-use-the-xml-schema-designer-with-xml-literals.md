---
title: 'Procedura: Usare Progettazione XML Schema con i valori letterali XML'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d11803e7-f81a-41a2-a145-ba494a45cc93
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 9e92cbdca3ac2c5c366ec054ba79f2e7324986c1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63001813"
---
# <a name="how-to-use-the-xml-schema-designer-with-xml-literals"></a>Procedura: Usare Progettazione XML Schema con i valori letterali XML

In questo argomento viene descritto come visualizzare uno schema associato a un valore letterale XML in un progetto di Visual Basic.

## <a name="create-a-new-visual-basic-project"></a>Creare un nuovo progetto di Visual Basic

1. Aprire Visual Studio.

2. Creare una nuova di Visual Basic **applicazione Console** progetto denominato **XMLLiterals**.

     Il nuovo progetto contiene un file di origine Visual Basic, *Module1.vb*.

## <a name="add-an-existing-xsd-file"></a>Aggiungere un file XSD esistente

1. Aprire un nuovo file di testo nel blocco note. Copiare il codice di esempio di XML Schema da [schema di ordine di acquisto](../xml-tools/sample-xsd-file-simple-schema.md) e incollarlo nel file.

2. Salvare il file in un percorso con il nome *Purchaseorderschema*.

3. Nelle **Esplora soluzioni**, fare clic sul nome del progetto, selezionare **Add**, quindi selezionare **elemento esistente**. Il **Aggiungi elemento esistente** verrà visualizzata la finestra di dialogo. Selezionare il *Purchaseorderschema* del file, selezionarlo e quindi fare clic su **Add**.

     Il progetto XMLLiterals contiene ora due file: *Module1.vb* e *Purchaseorderschema*.

## <a name="add-code"></a>Aggiungere il codice

Per aggiungere il codice Visual Basic con un valore letterale XML, in base al file XSD incluso nel progetto:

1. Sostituire il codice nel *Module1.vb* file con il codice seguente:

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

2. Fare doppio clic su qualsiasi nodo XML in un valore letterale XML o un'importazione di spazi dei nomi XML e selezionare **Mostra in Schema Explorer**.

   Il **XML Schema Explorer** viene visualizzato accanto a un file di Visual Basic che contiene il valore letterale XML associato al set XML schema.