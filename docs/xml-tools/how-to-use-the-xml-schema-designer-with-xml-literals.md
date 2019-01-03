---
title: 'Procedura: Usare Progettazione XML Schema con i valori letterali XML'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: d11803e7-f81a-41a2-a145-ba494a45cc93
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 1483077142d1c60d3309458aedbe1abd7e2e2b00
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53863394"
---
# <a name="how-to-use-the-xml-schema-designer-with-xml-literals"></a>Procedura: Usare Progettazione XML Schema con i valori letterali XML

In questo argomento viene descritto come visualizzare uno schema associato a un valore letterale XML in un progetto di Visual Basic.

## <a name="to-create-a-new-visual-basic-console-application-project"></a>Per creare un nuovo progetto di applicazione console di Visual Basic

1.  Avviare Visual Studio.

2.  Dal **File** dal menu **New**, quindi selezionare **progetto**. Verrà visualizzata la finestra di dialogo **Nuovo progetto** . Per la **tipi di progetto**, selezionare **altri linguaggi** e quindi selezionare **Visual Basic**. Per la **modelli**, selezionare applicazione Console. Quindi digitare `XMLLiterals` nella **Name** campo e un percorso di progetto nel **percorso** campo. Fare clic su **OK**.

     Il nuovo progetto è creato. Il progetto XMLLiterals contiene un file di origine Visual Basic, *Module1.vb*.

## <a name="to-add-an-existing-xsd-file-to-the-project"></a>Per aggiungere un file XSD esistente al progetto

1.  Aprire un nuovo file di testo nel blocco note. Copiare il codice di esempio di XML Schema da [schema di ordine di acquisto](../xml-tools/sample-xsd-file-simple-schema.md) e incollarlo nel file.

2.  Salvare il file in un percorso con il nome *Purchaseorderschema*.

3.  Nelle **Esplora soluzioni**, fare clic sul nome del progetto, selezionare **Add**, quindi selezionare **elemento esistente**. Il **Aggiungi elemento esistente** verrà visualizzata la finestra di dialogo. Selezionare il *Purchaseorderschema* del file, selezionarlo e quindi fare clic su **Add**.

     Il progetto XMLLiterals contiene ora due file: *Module1.vb* e *Purchaseorderschema*.

## <a name="to-add-visual-basic-code-with-an-xml-literal-based-on-the-xsd-file-included-in-the-project"></a>Per aggiungere codice Visual Basic con un valore letterale XML, in base al file XSD incluso nel progetto

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