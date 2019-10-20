---
title: "Procedura dettagliata: utilizzo delle funzionalità dell'editor XML | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: ea8dc357-2e66-455a-aec2-7ccaccfc9adf
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fa954cfb356593a4f22a44faddd69acdcfc93e37
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669572"
---
# <a name="walkthrough-using-xml-editor-features"></a>Procedura dettagliata: utilizzo delle funzionalità dell'editor XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nei passaggi della procedura dettagliata viene illustrato come creare un nuovo documento XML. Nella procedura dettagliata vengono inoltre usate alcune delle funzionalità dell'editor XML che lo rendono particolarmente utile per la creazione di codice XML.

> [!NOTE]
> Prima di avviare la procedura dettagliata, salvare il file hireDate.xsd (incluso di seguito in questo argomento) sul computer locale.

### <a name="to-create-a-new-xml-file-and-associate-it-with-an-xml-schema"></a>Per creare un nuovo file XML e associarlo a uno schema XML

1. Scegliere **nuovo**dal menu **file** e quindi fare clic su **file**.

2. Selezionare **file XML** nel riquadro **modelli** e fare clic su **Apri**.

     Viene aperto un nuovo file nell'editor. Il file contiene una dichiarazione XML predefinita, `<?xml version="1.0" encoding="utf-8">`.

3. Nella finestra proprietà del documento fare clic sul pulsante Sfoglia ( **...** ) nel campo **schemi** .

     Verrà visualizzata la finestra di dialogo **schemi XSD** .

4. Fare clic su **Aggiungi**.

     Verrà visualizzata la finestra di dialogo **Apri schema XSD** .

5. Selezionare il file hiree. xsd e fare clic su **Apri**.

6. Fare clic su **OK**.

     Lo schema XML è ora associato al documento XML. Lo schema XML viene usato per convalidare il documento. Viene anche usato da IntelliSense per inserire elementi validi nell'elenco dei membri.

### <a name="to-add-data"></a>Per aggiungere dati

1. Digitare `<` nel riquadro dell'editor.

     Nell'elenco dei membri vengono visualizzati gli elementi possibili:

    - **!--** aggiungere un commento.

    - **! DOCTYPE** per aggiungere un tipo di documento.

    - **?** per aggiungere un'istruzione di elaborazione.

    - **dipendente** per aggiungere l'elemento radice.

2. Selezionare **\<!--** per aggiungere un nodo di commento e premere INVIO.

     L'editor inserisce un tag di fine comment e colloca il cursore tra i tag comment di inizio e di fine.

3. Digitare il **file XML di test**.

4. In una nuova riga digitare `<` e selezionare **Employee** dall'elenco dei membri.

     L'editor aggiunge l'inizio di un elemento XML, `<employee`. A questo punto è possibile aggiungere attributi all'elemento o chiudere il tag di inizio digitando `>`.

5. Digitare `>` per chiudere il tag.

6. L'editor aggiunge il tag di fine. Il tag di fine viene aggiunto con una sottolineatura ondulata che indica un errore di convalida. La descrizione comando visualizza il messaggio: contenuto dell'elemento 'employee' incompleto. Previsto "Identificatore".

7. Digitare `<` e selezionare **ID** nell'elenco dei membri. Digitare quindi `>`.

     L'editor aggiunge l'elemento XML, `<ID></ID>`, e posiziona il cursore dopo il tag di inizio identificatore.

8. Digitare **ABC**.

     Il testo **ABC** presenta una sottolineatura ondulata. La descrizione comando visualizza il messaggio: l'elemento 'identificatore' non ha un valore valido per il relativo tipo di dati.

9. Fare clic con il pulsante destro del mouse sull'elemento ID e scegliere **Vai a definizione**.

     Nell'editor viene aperto il file hireDate.xsd in una nuova finestra del documento e il cursore viene posizionato sulla definizione dell'elemento dello schema identificatore.

10. Tornare al file XML e sostituire il testo **ABC** con **123**.

     La sottolineatura ondulata e la descrizione comando sotto il valore identificatore dell'elemento vengono cancellati. La descrizione comando del tag di fine del dipendente visualizza il messaggio: contenuto dell'elemento 'employee' incompleto. Previsto 'hire-date'.

11. Posizionare il cursore dopo il tag di fine identificatore, digitare `<`, scegliere la data di assunzione dall'elenco dei membri, quindi digitare `>`.

     L'editor aggiunge l'elemento XML, `<hire-date></hire-date>`, e posiziona il cursore dopo il tag di inizio data assunzione.

12. Digitare **2003-01-10** per il valore data di assunzione.

### <a name="to-format-the-xml-document"></a>Per formattare il documento XML

1. Selezionare il pulsante **Formatta documento** sulla barra degli strumenti dell'editor XML.

     Il documento XML viene riformattato.

### <a name="to-save-the-xml-document"></a>Per salvare il documento XML

1. Scegliere **Salva con nome**dal menu **file** .

     Viene visualizzata la finestra **di dialogo Salva file con nome** . Il nome file predefinito è "XMLFile1".

2. Immettere il nome del file e il percorso del documento XML, quindi fare clic su **Salva**.

## <a name="hiredatexsd-file"></a>File hireDate.xsd
 nella procedura dettagliata viene usato il seguente file di schema.

```
<?xml version="1.0"?>
<xs:schema attributeFormDefault="unqualified"
     elementFormDefault="qualified" targetNamespace="urn:empl-hire"
     xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="employee">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="ID" type="xs:unsignedShort" />
        <xs:element name="hire-date" type="xs:date" />
      </xs:sequence>
    </xs:complexType>
  </xs:element>
</xs:schema>
```

## <a name="see-also"></a>Vedere anche
 [Editor XML](../xml-tools/xml-editor.md)
