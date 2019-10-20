---
title: 'Procedura: creare frammenti XML | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: d8556dd7-1382-4af7-ba80-3e873c9416be
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2e08821f1289927c4183a1639ae37136c220a88c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670903"
---
# <a name="how-to-create-xml-snippets"></a>Procedura: creare frammenti XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'editor XML può essere usato per creare nuovi frammenti di codice XML. L'editor comprende un frammento di codice XML, denominato "Snippet", ovvero un frammento standard per la creazione di nuovi frammenti di codice XML.

## <a name="to-create-a-new-xml-snippet"></a>Per creare un nuovo frammento di codice XML
 Per creare un nuovo frammento di codice XML, creare un nuovo file XML e usare la funzionalità **Inserisci frammento** .

1. Scegliere **nuovo** dal menu **file** e quindi fare clic su **file**.

2. Fare clic su **file XML** e quindi su **Apri**.

3. Fare clic con il pulsante destro del mouse nel riquadro dell'editor e scegliere **Inserisci frammento**.

4. Selezionare **snippet** dall'elenco e premere INVIO.

5. Se necessario, apportare modifiche al nuovo frammento.

6. Dal menu **file** selezionare **Salva XMLFile. XML**.

     Viene visualizzata la finestra **di dialogo Salva file con nome** .

7. Immettere il nome per il nuovo frammento e selezionare **file di frammento** nella finestra a discesa **Salva come** .

8. Utilizzare l'elenco a discesa **Salva in** per modificare il percorso del file nella cartella Documenti\Visual Studio 2005 \ Code Snippets\XML\My XML Snippets e quindi premere **Save**.

## <a name="snippet-description"></a>Descrizione del frammento di codice
 Contenuto della sezione vengono descritti alcuni elementi chiave del frammento di codice standard. Per ulteriori informazioni sugli elementi dello schema utilizzati dai frammenti di codice XML, vedere [riferimenti allo schema dei frammenti di codice](../ide/code-snippets-schema-reference.md).

### <a name="snippettype-element"></a>Elemento SnippetType
 L'editor supporta due tipi di frammento di codice:

```
<SnippetTypes>
  <SnippetType>SurroundsWith</SnippetType>
  <SnippetType>Expansion</SnippetType>
</SnippetTypes>
```

 Il tipo di `Expansion` determina se il frammento viene visualizzato quando si richiama il comando **Inserisci frammento** . Il tipo di `SurroundsWith` determina se il frammento viene visualizzato quando si richiama il comando **Racchiudi tra** .

### <a name="code-element"></a>Elemento Code
 L'elemento `Code` definisce il testo XML che verrà inserito quando viene richiamato il frammento di codice.

> [!NOTE]
> Il testo del frammento di codice XML deve essere racchiuso in una sezione `<![CDATA[...]]>`.

 Di seguito viene riportato l'elemento `Code` creato dal frammento standard.

```
<Code Language="XML">
  <![CDATA[<test>
  <name>$name$</name>
  $selected$ $end$</test>]]>
</Code>
```

 L'elemento `Code` comprende tre variabili.

- $name$ è la variabile definita dall'utente e consente di creare un elemento `name`, che presenta un valore modificabile il cui valore predefinito è "name". Le variabili definite dall'utente vengono definite usando l'elemento `Literal`.

- $selected$ è una variabile predefinita e rappresenta il testo che era stato selezionato nell'editor XML prima di richiamare il frammento di codice. La posizione di questa variabile determina la posizione del testo selezionato nel frammento di codice che racchiude la selezione.

- $end$ è una variabile predefinita. Quando l'utente preme INVIO per terminare la modifica dei campi del frammento di codice, la variabile determina la posizione in cui viene spostato l'accento circonflesso (^).

  L'elemento `Code` consente l'inserimento del testo XML seguente:

```
<test>
  <name>name</name>
</test>
```

 Il valore dell'elemento nome viene contrassegnato come area modificabile.

### <a name="literal-element"></a>Elemento Literal
 L'elemento `Literal` viene usato per identificare il testo di sostituzione che è possibile personalizzare dopo che è stato inserito nel file. Ad esempio, le stringhe letterali, i valori numerici e alcuni nomi di variabili possono essere dichiarati come letterali. È possibile definire un qualsiasi numero di valori formali nel frammento di codice XML e farvi riferimento più volte dall'interno del frammento. Di seguito viene riportato un esempio di elemento `Literal` che definisce una variabile $name$ il cui valore predefinito è "name."

```
<Literal>
  <ID>name</ID>
  <Default>name</Default>
</Literal
```

 I valori formali possono anche fare riferimento a funzioni. L'editor XML include una funzione denominata **LookupPrefix**. La funzione **LookupPrefix** cerca l'URI dello spazio dei nomi specificato dalla posizione nel documento XML da cui viene richiamato il frammento e restituisce il prefisso dello spazio dei nomi definito per lo spazio dei nomi, se presente, e include i due punti (:) con questo nome. Di seguito è riportato un esempio di un elemento `Literal` che utilizza la funzione **LookupPrefix** .

```
<Literal Editable="false">
   <ID>prefix</ID>
   <Function>LookupPrefix("namespaceURI")</Function>
</Literal>
```

 La variabile $prefix$ può quindi essere usata in altri punti all'interno del frammento di codice XML.

## <a name="see-also"></a>Vedere anche
 [Frammenti XML](../xml-tools/xml-snippets.md) [procedura: usare i frammenti XML](../xml-tools/how-to-use-xml-snippets.md) [procedura: generare un frammento XML da uno schema XML](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md)
