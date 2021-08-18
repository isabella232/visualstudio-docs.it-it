---
title: "Procedura dettagliata: Uso delle funzionalità dell'editor XML"
description: Informazioni su come creare un nuovo documento XML seguendo i passaggi di questa procedura dettagliata che illustra le funzionalità dell'editor XML.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: ea8dc357-2e66-455a-aec2-7ccaccfc9adf
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
ms.workload:
- multiple
ms.openlocfilehash: 563f629ed21d524eb302d55af2550c86a89922e5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122045502"
---
# <a name="walkthrough-use-xml-editor-features"></a>Procedura dettagliata: Usare le funzionalità dell'editor XML

Nei passaggi della procedura dettagliata viene illustrato come creare un nuovo documento XML. La procedura dettagliata usa anche alcune delle funzionalità dell'editor XML che lo rendono utile per la creazione XML.

> [!NOTE]
> Prima di iniziare la procedura dettagliata, salvare il file *hireDate.xsd* (incluso di seguito in questo argomento) nel computer locale.

## <a name="to-create-a-new-xml-file-and-associate-it-with-an-xml-schema"></a>Per creare un nuovo file XML e associarlo a uno schema XML

1. Scegliere **Nuovo** dal menu File **e** fare clic su **File**.

2. Selezionare **File XML nel** riquadro Modelli **e** fare clic su **Apri.**

     Viene aperto un nuovo file nell'editor. Il file contiene una dichiarazione XML predefinita, `<?xml version="1.0" encoding="utf-8">`.

3. Nella finestra delle proprietà del documento fare clic sul pulsante Sfoglia (**...**) nel **campo** Schemi.

     Verrà **visualizzata la finestra di** dialogo Schemi XSD .

4. Fare clic su **Aggiungi**.

     Verrà **visualizzata la finestra** di dialogo Apri schema XSD .

5. Selezionare il file *hireDate.xsd* e fare clic su **Apri**.

6. Fare clic su **OK**.

     Lo schema XML è ora associato al documento XML. Lo schema XML viene usato per convalidare il documento. Viene anche usato da IntelliSense per inserire elementi validi nell'elenco dei membri.

## <a name="to-add-data"></a>Per aggiungere dati

1. Digitare `<` nel riquadro dell'editor.

     Nell'elenco dei membri vengono visualizzati gli elementi possibili:

    - **!--** aggiungere un commento.

    - **! DOCTYPE per** aggiungere un tipo di documento.

    - **?** per aggiungere un'istruzione di elaborazione.

    - **employee** per aggiungere l'elemento radice.

2. Selezionare **&lt; !--** per aggiungere un nodo di commento e premere **INVIO.**

     L'editor inserisce un tag di fine comment e colloca il cursore tra i tag comment di inizio e di fine.

3. Digitare nel **file XML di test**.

4. In una nuova riga digitare `<` e selezionare **employee dall'elenco** dei membri.

     L'editor aggiunge l'inizio di un elemento XML, `<employee`. A questo punto è possibile aggiungere attributi all'elemento o chiudere il tag di inizio digitando `>`.

5. Digitare `>` per chiudere il tag.

6. L'editor aggiunge il tag di fine. Il tag di fine viene aggiunto con una sottolineatura ondulata che indica un errore di convalida. La **descrizione comando** visualizza il messaggio: **L'elemento 'employee' ha contenuto incompleto. Previsto 'ID'.**

7. Digitare `<` e selezionare ID **dall'elenco** dei membri. Digitare quindi `>`.

     L'editor aggiunge l'elemento XML, `<ID></ID>`, e posiziona il cursore dopo il tag di inizio identificatore.

8. Digitare **abc**.

     Il **testo abc** ha una sottolineatura ondulata. La **descrizione comando** visualizza il messaggio: **L'elemento 'ID' ha un valore non valido in base al tipo di dati**.

9. Fare clic con il pulsante destro del mouse sull'elemento ID e **scegliere Vai a definizione.**

     L'editor apre il file *hireDate.xsd* in una nuova finestra del documento e posiziona il cursore sulla definizione dell'elemento dello schema ID.

10. Tornare al file XML e sostituire il testo **abc** con **123**.

     La sottolineatura ondulata e **la descrizione comando** vengono cancellate sotto il valore dell'elemento ID. La **descrizione comando** per il tag di fine del dipendente visualizza ora il messaggio: **L'elemento 'employee' ha contenuto incompleto. Previsto 'hire-date'.**

11. Posizionare il cursore dopo il tag di fine ID, `<` digitare , **selezionare hire-date** nell'elenco dei membri e quindi digitare `>` .

     L'editor aggiunge l'elemento XML, `<hire-date></hire-date>`, e posiziona il cursore dopo il tag di inizio data assunzione.

12. Digitare **2003-01-10** come valore della data di assunzione.

## <a name="to-format-the-xml-document"></a>Per formattare il documento XML

- Selezionare il **pulsante Formatta** documento sulla barra degli strumenti dell'editor XML oppure premere **CTRL** + **E**,**D**.

   ![Pulsante Formatta documento XML in Visual Studio](media/format-xml-document.png)

   Il documento XML viene riformattato.

## <a name="to-save-the-xml-document"></a>Per salvare il documento XML

1. Dal menu **File** selezionare **Salva con nome**.

     Verrà **visualizzata la finestra di** dialogo Salva file con nome . Il nome file predefinito è *'XMLFile1'.*

2. Immettere il nome file e il percorso per il documento XML e fare clic su **Salva**.

## <a name="hiredatexsd-file"></a>File hireDate.xsd

In questa procedura dettagliata viene usato il file di schema seguente:

```xml
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

## <a name="see-also"></a>Vedi anche

- [Editor XML](../xml-tools/xml-editor.md)
