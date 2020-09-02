---
title: "Procedura dettagliata: utilizzo delle funzionalità dell'editor XML"
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: ea8dc357-2e66-455a-aec2-7ccaccfc9adf
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1cebf6f7621fb5fada37b8e4592efd429bdc85e6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85817398"
---
# <a name="walkthrough-use-xml-editor-features"></a>Procedura dettagliata: usare le funzionalità dell'editor XML

Nei passaggi della procedura dettagliata viene illustrato come creare un nuovo documento XML. Nella procedura dettagliata vengono inoltre utilizzate alcune delle funzionalità dell'editor XML che lo rendono utile per la creazione di XML.

> [!NOTE]
> Prima di avviare la procedura dettagliata, salvare il file *hiree. xsd* (incluso di seguito in questo argomento) nel computer locale.

## <a name="to-create-a-new-xml-file-and-associate-it-with-an-xml-schema"></a>Per creare un nuovo file XML e associarlo a un XML Schema

1. Scegliere **nuovo**dal menu **file** e quindi fare clic su **file**.

2. Selezionare **file XML** nel riquadro **modelli** e fare clic su **Apri**.

     Viene aperto un nuovo file nell'editor. Il file contiene una dichiarazione XML predefinita, `<?xml version="1.0" encoding="utf-8">`.

3. Nella finestra proprietà del documento fare clic sul pulsante Sfoglia (**...**) nel campo **schemi** .

     Verrà visualizzata la finestra di dialogo **schemi XSD** .

4. Scegliere **Aggiungi**.

     Verrà visualizzata la finestra di dialogo **Apri schema XSD** .

5. Selezionare il file *hiree. xsd* e fare clic su **Apri**.

6. Fare clic su **OK**.

     Lo schema XML è ora associato al documento XML. Lo schema XML viene usato per convalidare il documento. Viene anche usato da IntelliSense per inserire elementi validi nell'elenco dei membri.

## <a name="to-add-data"></a>Per aggiungere dati

1. Digitare `<` nel riquadro dell'editor.

     Nell'elenco dei membri vengono visualizzati gli elementi possibili:

    - **!--** aggiungere un commento.

    - **! DOCTYPE** per aggiungere un tipo di documento.

    - **?** per aggiungere un'istruzione di elaborazione.

    - **dipendente** per aggiungere l'elemento radice.

2. Selezionare ** &lt; !--** per aggiungere un nodo di commento e premere **invio**.

     L'editor inserisce un tag di fine comment e colloca il cursore tra i tag comment di inizio e di fine.

3. Digitare il **file XML di test**.

4. In una nuova riga digitare `<` e selezionare **Employee** dall'elenco dei membri.

     L'editor aggiunge l'inizio di un elemento XML, `<employee`. A questo punto è possibile aggiungere attributi all'elemento o chiudere il tag di inizio digitando `>`.

5. Digitare `>` per chiudere il tag.

6. L'editor aggiunge il tag di fine. Il tag di fine viene aggiunto con una sottolineatura ondulata che indica un errore di convalida. La **Descrizione comando** Visualizza il messaggio: **l'elemento "Employee" contiene contenuto incompleto. Previsto ' ID '**.

7. Digitare `<` e selezionare **ID** nell'elenco dei membri. Digitare quindi `>`.

     L'editor aggiunge l'elemento XML, `<ID></ID>`, e posiziona il cursore dopo il tag di inizio identificatore.

8. Digitare **ABC**.

     Il testo **ABC** presenta una sottolineatura ondulata. La **Descrizione comando** Visualizza il messaggio: **l'elemento ' ID ' ha un valore non valido in base al relativo tipo di dati**.

9. Fare clic con il pulsante destro del mouse sull'elemento ID e scegliere **Vai a definizione**.

     L'editor apre il file *hiree. xsd* in una nuova finestra del documento e posiziona il cursore sulla definizione dell'elemento dello schema dell'ID.

10. Tornare al file XML e sostituire il testo **ABC** con **123**.

     La sottolineatura ondulata e la **Descrizione comando** vengono cancellate sotto il valore dell'elemento ID. La **Descrizione comando** per il tag di fine Employee ora Visualizza il messaggio: **l'elemento "Employee" contiene contenuto incompleto. Previsto ' hire-date '**.

11. Posizionare il cursore dopo il tag di fine ID, digitare `<` , selezionare **hire-date** nell'elenco dei membri, quindi digitare `>` .

     L'editor aggiunge l'elemento XML, `<hire-date></hire-date>`, e posiziona il cursore dopo il tag di inizio data assunzione.

12. Digitare **2003-01-10** per il valore data di assunzione.

## <a name="to-format-the-xml-document"></a>Per formattare il documento XML

- Selezionare il pulsante **Formatta documento** sulla barra degli strumenti dell'editor XML oppure premere **CTRL** + **E**,**D**.

   ![Pulsante Formatta documento XML in Visual Studio](media/format-xml-document.png)

   Il documento XML viene riformattato.

## <a name="to-save-the-xml-document"></a>Per salvare il documento XML

1. Dal menu **File** selezionare **Salva con nome**.

     Viene visualizzata la finestra **di dialogo Salva file con nome** . Il nome file predefinito è *"XMLFile1"*.

2. Immettere il nome del file e il percorso del documento XML, quindi fare clic su **Salva**.

## <a name="hiredatexsd-file"></a>il file con estensione XSD viene assunto

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

## <a name="see-also"></a>Vedere anche

- [Editor XML](../xml-tools/xml-editor.md)
