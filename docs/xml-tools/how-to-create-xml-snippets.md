---
title: 'Procedura: creare frammenti XML'
description: Informazioni su come usare l'editor XML in Visual Studio creare frammenti XML che consentono di compilare file XML più rapidamente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d8556dd7-1382-4af7-ba80-3e873c9416be
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
ms.workload:
- multiple
ms.openlocfilehash: ee6dfe8990cf5e85a35a0d538c2bfbd50c3462e4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122045454"
---
# <a name="how-to-create-xml-snippets"></a>Procedura: Creare frammenti di codice XML

L'editor XML può essere usato per creare nuovi frammenti di codice XML. L'editor comprende un frammento di codice XML, denominato "Snippet", ovvero un frammento standard per la creazione di nuovi frammenti di codice XML.

## <a name="to-create-a-new-xml-snippet"></a>Per creare un nuovo frammento di codice XML

Per creare un nuovo frammento di codice XML, creare un nuovo file XML e usare la **funzionalità Inserisci frammento di** codice.

1. Scegliere **Nuovo** dal menu File **e** quindi fare clic su **File**.

2. Fare **clic su File XML** e quindi su **Apri**.

3. Fare clic con il pulsante destro del mouse nel riquadro dell'editor e **scegliere Inserisci frammento di codice**.

4. Selezionare **Frammento** di codice nell'elenco e premere **INVIO.**

5. Se necessario, apportare modifiche al nuovo frammento.

6. Scegliere **Salva** dal menu File **XMLFile.xml**.

     Verrà **visualizzata la finestra** di dialogo Salva file con nome .

7. Immettere il nome per il nuovo frammento di codice e selezionare **File di frammento** di codice nella **finestra** a discesa Salva con nome.

8. Usare  l'elenco a discesa Salva in per modificare il percorso del file nella cartella *Documenti\Visual Studio 2005\Code Snippets\XML\My XML Snippets* e quindi premere **Salva**.

## <a name="snippet-description"></a>Descrizione del frammento di codice

Contenuto della sezione vengono descritti alcuni elementi chiave del frammento di codice standard. Per altre informazioni sugli elementi dello schema utilizzati dai frammenti di codice XML, vedere [Informazioni di riferimento sullo schema dei frammenti di codice](../ide/code-snippets-schema-reference.md).

### <a name="snippettype-element"></a>SnippetType, elemento

L'editor supporta due tipi di frammento di codice:

```xml
<SnippetTypes>
  <SnippetType>SurroundsWith</SnippetType>
  <SnippetType>Expansion</SnippetType>
</SnippetTypes>
```

Il `Expansion` tipo determina se il frammento di codice viene visualizzato quando si richiama il comando Inserisci **frammento** di codice. Il `SurroundsWith` tipo determina se il frammento di codice viene visualizzato quando si richiama il comando **Surrounds With.**

### <a name="code-element"></a>Elemento del codice

L'elemento `Code` definisce il testo XML che verrà inserito quando viene richiamato il frammento di codice.

> [!NOTE]
> Il testo del frammento di codice XML deve essere racchiuso in una sezione `<![CDATA[...]]>`.

Di seguito viene riportato l'elemento `Code` creato dal frammento standard.

```xml
<Code Language="XML">
  <![CDATA[<test>
  <name>$name$</name>
  $selected$ $end$</test>]]>
</Code>
```

L'elemento `Code` comprende tre variabili.

- $name$ è la variabile definita dall'utente e consente di creare un elemento `name`, che presenta un valore modificabile il cui valore predefinito è "name". Le variabili definite dall'utente vengono definite usando l'elemento `Literal`.

- $selected$ è una variabile predefinita Rappresenta il testo selezionato nell'editor XML prima di richiamare il frammento di codice. La posizione di questa variabile determina la posizione del testo selezionato nel frammento di codice che racchiude la selezione.

- $end$ è una variabile predefinita. Quando l'utente preme **INVIO per** completare la modifica dei campi del frammento di codice, questa variabile determina dove viene spostato il punto di inserimento (^).

  L'elemento `Code` consente l'inserimento del testo XML seguente:

```xml
<test>
  <name>name</name>
</test>
```

Il valore dell'elemento nome viene contrassegnato come area modificabile.

### <a name="literal-element"></a>Literal, elemento

L'elemento `Literal` viene usato per identificare il testo di sostituzione che è possibile personalizzare dopo che è stato inserito nel file. Ad esempio, le stringhe letterali, i valori numerici e alcuni nomi di variabili possono essere dichiarati come letterali. È possibile definire un qualsiasi numero di valori formali nel frammento di codice XML e farvi riferimento più volte dall'interno del frammento. Di seguito viene riportato un esempio di elemento `Literal` che definisce una variabile $name$ il cui valore predefinito è "name."

```xml
<Literal>
  <ID>name</ID>
  <Default>name</Default>
</Literal
```

I valori formali possono anche fare riferimento a funzioni. L'editor XML include una funzione denominata **LookupPrefix**. La **funzione LookupPrefix** cerca l'URI dello spazio dei nomi specificato dal percorso nel documento XML da cui viene richiamato questo frammento di codice e restituisce il prefisso dello spazio dei nomi definito per tale spazio dei nomi, se presente, e include i due punti (:) in tale nome. Di seguito è riportato un esempio di `Literal` un elemento che usa la funzione **LookupPrefix.**

```xml
<Literal Editable="false">
   <ID>prefix</ID>
   <Function>LookupPrefix("namespaceURI")</Function>
</Literal>
```

La variabile $prefix$ può quindi essere usata in altri punti all'interno del frammento di codice XML.

## <a name="see-also"></a>Vedi anche

- [frammenti XML](../xml-tools/xml-snippets.md)
- [Procedura: Usare frammenti di codice XML](../xml-tools/how-to-use-xml-snippets.md)
- [Procedura: Generare un frammento di codice XML da uno schema XML](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md)
