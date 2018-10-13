---
title: 'Procedura: usare Progettazione XML Schema con i valori letterali XML | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d11803e7-f81a-41a2-a145-ba494a45cc93
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 592886a1cfe9d0ffc9c7165729cede3340bc65c8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49218374"
---
# <a name="how-to-use-the-xml-schema-designer-with-xml-literals"></a>Procedura: utilizzare Progettazione XML Schema con i valori letterali XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
In questo argomento viene descritto come visualizzare uno schema associato a un valore letterale XML in un progetto di Visual Basic.  
  
### <a name="to-create-a-new-visual-basic-console-application-project"></a>Per creare un nuovo progetto di applicazione console di Visual Basic  
  
1.  Avviare Visual Studio 2010.  
  
2.  Dal **File** dal menu **New**, quindi selezionare **progetto**. Verrà visualizzata la finestra di dialogo **Nuovo progetto** . Per la **tipi di progetto**, selezionare **altri linguaggi** e quindi selezionare **Visual Basic**. Per la **modelli**, selezionare applicazione Console. Quindi digitare `XMLLiterals` nella **Name** campo e un percorso di progetto nel **percorso** campo. Fare clic su **OK**.  
  
     Il nuovo progetto è creato. Il progetto XMLLiterals contiene un file di origine di Visual Basic, Module1.vb.  
  
### <a name="to-add-an-existing-xsd-file-to-the-project"></a>Per aggiungere un file XSD esistente al progetto  
  
1.  Apri nuovi file di testo in Notepad.Copy il codice di esempio di XML Schema da [Schema di ordine di acquisto](../xml-tools/sample-xsd-file-simple-schema.md) e incollarlo nel file.  
  
2.  Salvare il file in un percorso con il nome PurchaseOrderSchema.xsd.  
  
3.  In Esplora soluzioni, fare clic sul nome del progetto, selezionare **Add**, quindi selezionare **elemento esistente...** . Il **Aggiungi elemento esistente** verrà visualizzata la finestra di dialogo. Individuare il file Purchaseorderschema XSD, selezionarlo e quindi fare clic su **Add**.  
  
     Il progetto XMLLiterals contiene ora due file: Module1.vb e PurchaseOrderSchema.xsd.  
  
### <a name="to-add-visual-basic-code-with-an-xml-literal-based-on-the-xsd-file-included-in-the-project"></a>Per aggiungere codice Visual Basic con un valore letterale XML, in base al file XSD incluso nel progetto  
  
1.  Sostituire il codice nel file Module1.vb con il codice seguente:  
  
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
  
2.  Fare doppio clic su qualsiasi nodo XML in un valore letterale XML o un'importazione di spazi dei nomi XML e selezionare **Mostra in Schema Explorer**.  
  
     XML Schema Explorer viene visualizzato accanto a un file di Visual Basic che dispone di un valore letterale XML associato al set di schemi XML.



