---
title: 'Procedura: generare un frammento XML da un XML Schema | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2c128d2a-aaa6-4814-aa95-e07056afe338
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6eb03fba400e20227155a2528b8aaf0b28f7761a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49951470"
---
# <a name="how-to-generate-an-xml-snippet-from-an-xml-schema"></a>Procedura: generare un frammento XML da XML Schema
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
L'editor XML è in grado di generare frammenti XML da uno schema XSD (XML Schema Definition Language). Ad esempio, quando si crea un file XML, mentre si è posizionati accanto al nome dell'elemento, premere TAB per inserire nell'elemento i dati XML generati dalle informazioni sullo schema per quel determinato elemento.  
  
 Questa funzionalità è disponibile solo per gli elementi. È inoltre necessario rispettare le seguenti regole:  
  
- All'elemento deve essere associato un tipo di schema, ovvero l'elemento deve essere valido in base a uno schema associato. Il tipo di schema non può essere astratto e il tipo deve contenere gli attributi e/o gli elementi figlio obbligatori.  
  
- L'elemento corrente nell'editor deve essere vuoto e senza attributi. Gli elementi seguenti, ad esempio, sono tutti validi:  
  
  -   `<Account`  
  
  -   `<Account>`  
  
  -   `<Account></Account>`  
  
- Il cursore deve trovarsi immediatamente a destra del nome dell'elemento.  
  
  Il frammento generato contiene tutti gli attributi e gli elementi obbligatori. Se `minOccurs` è maggiore di uno, il numero minimo richiesto di istanze di tale elemento è incluso nel frammento, fino a un massimo di 100 istanze.  Qualsiasi valore fisso trovato nello schema comporta valori fissi nel frammento. Gli elementi `xsd:any` e `xsd:anyAttribute` vengono ignorati e non comportano costrutti di frammenti aggiuntivi.  
  
  I valori predefiniti vengono generati e specificati come valori modificabili. Se nello schema viene specificato un valore predefinito, verrà usato tale valore. Tuttavia, se il valore predefinito dello schema è una striga vuota, l'editor genera i valori predefiniti nel modo seguente:  
  
- Se il tipo di schema contiene facet di enumerazione, direttamente o indirettamente tramite un qualsiasi membro di tipo unione, il primo valore enumerato rilevato nel modello a oggetti dello schema viene usato come valore predefinito.  
  
- Se il tipo di schema è un tipo atomic, l'editor ottiene il tipo atomic e ne inserisce il nome. Per un tipo semplice derivato viene usato il tipo base semplice. Per un tipo di elenco, il tipo atomic è l'attributo `itemType`. Per un tipo unione, il tipo atomic è il tipo atomic del primo `memberType`.  
  
## <a name="example"></a>Esempio  
 Nei passaggi di questa sezione viene illustrato come usare la funzionalità dei frammenti XML generati dallo schema dell'editor XML.  
  
> [!NOTE]
>  Prima di avviare tali procedure, salvare il file di schema nel computer locale.  
  
#### <a name="to-create-a-new-xml-file-and-associate-it-with-an-xml-schema"></a>Per creare un nuovo file XML e associarlo a uno schema XML  
  
1.  Nel **File** dal menu **New**, fare clic su **File**.  
  
2.  Selezionare **File XML** nel **modelli** riquadro e fare clic su **Open**.  
  
     Viene aperto un nuovo file nell'editor. Il file contiene una dichiarazione XML predefinita, `<?xml version="1.0" encoding="utf-8">`.  
  
3.  Nella finestra delle proprietà del documento, fare clic sul pulsante Sfoglia (**...** ) sul **schemi** campo.  
  
     Il **schemi XSD** verrà visualizzata la finestra di dialogo.  
  
4.  Fare clic su **Aggiungi**.  
  
     Il **Apri Schema XSD** verrà visualizzata la finestra di dialogo.  
  
5.  Selezionare il file di schema e fare clic su **aperto**.  
  
6.  Fare clic su **OK**.  
  
     Lo schema XML è ora associato al documento XML.  
  
#### <a name="to-generate-an-xml-snippet"></a>Per generare un frammento XML  
  
1.  Digitare `<` nel riquadro dell'editor.  
  
2.  Nell'elenco dei membri vengono visualizzati gli elementi possibili:  
  
     **!-** per aggiungere un commento.  
  
     **! Tipo di documento** per aggiungere un tipo di documento.  
  
     **?** per aggiungere un'istruzione di elaborazione.  
  
     **Contatto** per aggiungere l'elemento radice.  
  
3.  Selezionare **contatto** nell'elenco dei membri e premere INVIO.  
  
     L'editor aggiunge il tag di inizio `<Contact` e posiziona il cursore dopo il nome dell'elemento.  
  
4.  Premere TAB per generare i dati XML dell'elemento `Contact` in base alle informazioni sullo schema.  
  
### <a name="input"></a>Input  
 nella procedura dettagliata viene usato il seguente file di schema.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<xs:schema elementFormDefault="qualified"  
           xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:simpleType name="phoneType">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="Voice"/>  
      <xs:enumeration value="Fax"/>  
      <xs:enumeration value="Pager"/>  
    </xs:restriction>  
  </xs:simpleType>  
  <xs:element name="Contact">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="Name">  
          <xs:simpleType>  
            <xs:restriction base="xs:string"></xs:restriction>  
          </xs:simpleType>  
        </xs:element>  
        <xs:element name="Title"  
                    type="xs:string" />  
        <xs:element name="Phone"  
                    minOccurs="1"  
                    maxOccurs="unbounded">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="Number"  
                          minOccurs="1">  
                <xs:simpleType>  
                  <xs:restriction base="xs:string"></xs:restriction>  
                </xs:simpleType>  
              </xs:element>  
              <xs:element name="Type"  
                          default="Voice"  
                          minOccurs="1"  
                          type="phoneType"/>  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
      </xs:sequence>  
    </xs:complexType>  
  </xs:element>  
</xs:schema>  
```  
  
### <a name="output"></a>Output  
 Di seguito sono riportati i dati XML generati in base alle informazioni sullo schema associate all'elemento `Contact`. Gli elementi contrassegnati come `bold` indicano i campi modificabili nel frammento di codice XML.  
  
```  
<Contact>  
  <Name>name</Name>  
  <Title>title</Title>  
  <Phone>  
    <Number>number</Number>  
    <Type>Voice</Type>  
  </Phone>  
</Contact>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Frammenti di codice XML](../xml-tools/xml-snippets.md)   
 [Procedura: Usare frammenti XML](../xml-tools/how-to-use-xml-snippets.md)



