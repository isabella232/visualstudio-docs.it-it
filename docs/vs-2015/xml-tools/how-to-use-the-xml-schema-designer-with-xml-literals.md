---
title: 'Procedura: utilizzare Progettazione XML Schema con valori letterali XML | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: d11803e7-f81a-41a2-a145-ba494a45cc93
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a9e82cf8387756cb4a4abe8b4c41d082485cdcdc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656289"
---
# <a name="how-to-use-the-xml-schema-designer-with-xml-literals"></a>Procedura: utilizzare Progettazione XML Schema con i valori letterali XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In questo argomento viene descritto come visualizzare uno schema associato a un valore letterale XML in un progetto di Visual Basic.

### <a name="to-create-a-new-visual-basic-console-application-project"></a>Per creare un nuovo progetto di applicazione console di Visual Basic

1. Avviare Visual Studio 2010.

2. Scegliere **Nuovo** dal menu **File**, quindi selezionare **Progetto**. Verrà visualizzata la finestra di dialogo **Nuovo progetto** . Per i **tipi di progetto**, selezionare **altri linguaggi,** quindi selezionare **Visual Basic**. Per i **modelli**, selezionare applicazione console. Digitare quindi `XMLLiterals` il campo **nome** e il percorso del progetto nel campo **percorso** . Fare clic su **OK**.

     Il nuovo progetto è creato. Il progetto XMLLiterals contiene un file di origine di Visual Basic, Module1.vb.

### <a name="to-add-an-existing-xsd-file-to-the-project"></a>Per aggiungere un file XSD esistente al progetto

1. Aprire un nuovo file di testo nel blocco note. copiare il codice di esempio XML schema dallo [schema di ordine di acquisto](../xml-tools/sample-xsd-file-simple-schema.md) e incollarlo nel file.

2. Salvare il file in un percorso con il nome PurchaseOrderSchema.xsd.

3. Nella Esplora soluzioni fare clic con il pulsante destro del mouse sul nome del progetto, scegliere **Aggiungi**, quindi selezionare **elemento esistente.** Verrà visualizzata la finestra di dialogo **elemento Aggiungi** . Individuare il file PurchaseOrderSchema. xsd, selezionarlo e quindi fare clic su **Aggiungi**.

     Il progetto XMLLiterals contiene ora due file: Module1.vb e PurchaseOrderSchema.xsd.

### <a name="to-add-visual-basic-code-with-an-xml-literal-based-on-the-xsd-file-included-in-the-project"></a>Per aggiungere codice Visual Basic con un valore letterale XML, in base al file XSD incluso nel progetto

1. Sostituire il codice nel file Module1.vb con il codice seguente:

    ```
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

     XML Schema Explorer viene visualizzato accanto a un file di Visual Basic che dispone di un valore letterale XML associato al set di schemi XML.
