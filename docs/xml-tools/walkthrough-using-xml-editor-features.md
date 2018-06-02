---
title: "Procedura dettagliata: utilizzo delle funzionalità dell'editor XML"
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: ea8dc357-2e66-455a-aec2-7ccaccfc9adf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: afda2968ece2a18b7abdc2c4c35e4353206cbe42
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/01/2018
ms.locfileid: "34693825"
---
# <a name="walkthrough-use-xml-editor-features"></a>Questa procedura dettagliata: Utilizzare funzionalità dell'editor XML

Nei passaggi della procedura dettagliata viene illustrato come creare un nuovo documento XML. Nella procedura dettagliata vengono inoltre usate alcune delle funzionalità dell'editor XML che lo rendono particolarmente utile per la creazione di codice XML.

> [!NOTE]
> Prima di avviare la procedura dettagliata, salvare il *HireDate* file (incluso di seguito in questo argomento) nel computer locale.

## <a name="to-create-a-new-xml-file-and-associate-it-with-an-xml-schema"></a>Per creare un nuovo file XML e associarlo a uno schema XML

1.  Nel **File** dal menu **New**, fare clic su **File**.

2.  Selezionare **File XML** nel **modelli** riquadro e fare clic su **aprire**.

     Viene aperto un nuovo file nell'editor. Il file contiene una dichiarazione XML predefinita, `<?xml version="1.0" encoding="utf-8">`.

3.  Nella finestra delle proprietà del documento, fare clic sul pulsante Sfoglia (**...** ) nei **schemi** campo.

     Il **schemi XSD** viene visualizzata la finestra di dialogo.

4.  Fare clic su **Aggiungi**.

     Il **Apri Schema XSD** viene visualizzata la finestra di dialogo.

5.  Selezionare il *HireDate* del file e fare clic su **Apri**.

6.  Fare clic su **OK**.

     Lo schema XML è ora associato al documento XML. Lo schema XML viene usato per convalidare il documento. Viene anche usato da IntelliSense per inserire elementi validi nell'elenco dei membri.

## <a name="to-add-data"></a>Per aggiungere dati

1.  Digitare `<` nel riquadro dell'editor.

     Nell'elenco dei membri vengono visualizzati gli elementi possibili:

    -   **!-** per aggiungere un commento.

    -   **! DOCTYPE** per aggiungere un tipo di documento.

    -   **?** per aggiungere un'istruzione di elaborazione.

    -   **dipendente** per aggiungere l'elemento radice.

2.  Selezionare **<!-** per aggiungere un nodo di tipo comment e premere **invio**.

     L'editor inserisce un tag di fine comment e colloca il cursore tra i tag comment di inizio e di fine.

3.  Digitare **file XML di Test**.

4.  In una nuova riga digitare `<`e selezionare **dipendente** dall'elenco dei membri.

     L'editor aggiunge l'inizio di un elemento XML, `<employee`. A questo punto è possibile aggiungere attributi all'elemento o chiudere il tag di inizio digitando `>`.

5.  Digitare `>` per chiudere il tag.

6.  L'editor aggiunge il tag di fine. Il tag di fine viene aggiunto con una sottolineatura ondulata che indica un errore di convalida. Il **ToolTip** viene visualizzato il messaggio: **dell'elemento 'employee' dispone di contenuto non completo. Previsto 'ID'**.

7.  Tipo `<` e selezionare **ID** dall'elenco dei membri. Digitare quindi `>`.

     L'editor aggiunge l'elemento XML, `<ID></ID>`, e posiziona il cursore dopo il tag di inizio identificatore.

8.  Tipo **abc**.

     Il **abc** testo ha una sottolineatura ondulata. Il **ToolTip** viene visualizzato il messaggio: **l'elemento 'ID' ha un valore non valido in base al relativo tipo di dati**.

9. Fare clic sull'elemento ID e selezionare **Vai a definizione**.

     Verrà aperto l'editor di *HireDate* file in una nuova finestra del documento e posiziona il cursore nella definizione dell'elemento dello schema di ID.

10. Tornare al file XML e sostituire il **abc** testo con **123**.

     La sottolineatura ondulata e **ToolTip** sotto il valore ID dell'elemento vengono cancellati. Il **ToolTip** per l'entità finale dipendente tag viene ora visualizzato il messaggio: **dell'elemento 'employee' dispone di contenuto non completo. Previsto 'la data di assunzione'**.

11. Posizionare il cursore dopo il tag di fine identificatore, digitare `<`, selezionare **la data di assunzione** dall'elenco dei membri e quindi digitare `>`.

     L'editor aggiunge l'elemento XML, `<hire-date></hire-date>`, e posiziona il cursore dopo il tag di inizio data assunzione.

12. Digitare **2003-01-10** per il valore di data di assunzione.

## <a name="to-format-the-xml-document"></a>Per formattare il documento XML

- Selezionare il **Formatta documento** pulsante nella barra degli strumenti dell'Editor XML.

    Il documento XML viene riformattato.

## <a name="to-save-the-xml-document"></a>Per salvare il documento XML

1.  Dal **File** dal menu **Salva con nome**.

     Il **Salva File con nome** viene visualizzata la finestra di dialogo. Il nome file predefinito è *"XMLFile1"*.

2.  Immettere il nome del file e il percorso per il documento XML e fare clic su **salvare**.

## <a name="hiredatexsd-file"></a>file hireDate. xsd
 nella procedura dettagliata viene usato il seguente file di schema.

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

## <a name="see-also"></a>Vedere anche

- [Editor XML](../xml-tools/xml-editor.md)