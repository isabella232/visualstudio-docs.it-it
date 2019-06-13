---
title: 'Procedura dettagliata: Creare un frammento di codice'
ms.date: 06/10/2019
ms.topic: conceptual
helpviewer_keywords:
- code snippets, creating
- code snippets, shortcut
- code snippets, template
- code snippets, replacements
- code snippets, references
- code snippets, imports
ms.assetid: 0dcaae11-39cf-4463-9c90-2494321251c2
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 6f58581a601da59e7ff66a3bae5ddcb7432bf8e3
ms.sourcegitcommit: cc5fd59e5dc99181601b7db8b28d7f8a83a36bab
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2019
ms.locfileid: "66836096"
---
# <a name="walkthrough-create-a-code-snippet"></a>Procedura dettagliata: Creare un frammento di codice

Per creare un frammento di codice sono necessari pochi passaggi. È sufficiente creare un file XML, inserire gli elementi appropriati e aggiungere il codice. È possibile apportare, facoltativamente, usare i parametri di sostituzione e i riferimenti al progetto. Importare il frammento di codice di installazione di Visual Studio usando il **importazione** pulsante il **Gestione frammenti di codice** (**strumenti** > **codice Gestione frammenti di**).

## <a name="snippet-template"></a>Modello di frammento

Il codice XML seguente è il modello di frammento di base:

```xml
<?xml version="1.0" encoding="utf-8"?>
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
    <CodeSnippet Format="1.0.0">
        <Header>
            <Title></Title>
        </Header>
        <Snippet>
            <Code Language="">
                <![CDATA[]]>
            </Code>
        </Snippet>
    </CodeSnippet>
</CodeSnippets>
```

## <a name="create-a-code-snippet"></a>Creare un frammento di codice

1. Creare un nuovo file XML in Visual Studio e aggiungere il modello come illustrato in precedenza.

2. Compilare il titolo del frammento di codice nel **titolo** elemento. Utilizzare il titolo **radice quadrata**.

3. Aggiungere il linguaggio del frammento nell'attributo **Language** dell'elemento **Code**. Per C#, usare **CSharp**e per Visual Basic, usare **VB**.

   > [!TIP]
   > Per visualizzare tutti i valori di lingua disponibile, passare il [sezione attributi dell'elemento di codice](code-snippets-schema-reference.md#attributes) nel [riferimenti allo schema dei frammenti di codice](code-snippets-schema-reference.md) pagina.

4. Aggiungere il frammento di codice nel **CDATA** sezione all'interno di **codice** elemento.

   Per C#:

   ```xml
   <Code Language="CSharp">
       <![CDATA[double root = Math.Sqrt(16);]]>
   </Code>
   ```

   O per Visual Basic:

   ```xml
   <Code Language="VB">
       <![CDATA[Dim root = Math.Sqrt(16)]]>
   </Code>
   ```

5. Salvare il frammento come *SquareRoot.snippet* (è possibile salvarlo ovunque).

## <a name="import-a-code-snippet"></a>Importare un frammento di codice

1. È possibile importare un frammento all'installazione di Visual Studio usando il **Gestione frammenti di codice**. Aprirlo scegliendone **degli strumenti** > **Gestione frammenti di codice**.

2. Fare clic sul pulsante **Importa**.

3. Scegliere il percorso in cui è stato salvato il frammento di codice nella procedura precedente, selezionarlo e fare clic su **Apri**.

4. Si aprirà la finestra di dialogo **Importa frammento di codice** in cui viene chiesto di scegliere il punto in cui aggiungere il frammento tra le opzioni nel riquadro di destra. Una delle opzioni possibili è **Frammenti di codice**. Selezionare l'opzione e fare clic su **Fine** e poi su **OK**.

5. Il frammento di codice viene copiato in uno dei percorsi seguenti, a seconda del linguaggio di codice:

   ::: moniker range="vs-2017"

   *%USERPROFILE%\Documents\Visual studio 2017\frammenti codice\visual C#\My Code Snippets*
    *%USERPROFILE%\Documents\Visual Studio 2017\frammenti codice\visual Basic\frammenti di codice*

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   *%USERPROFILE%\Documents\Visual studio 2019\Code codice\visual C#\My Code Snippets*
    *%USERPROFILE%\Documents\Visual Studio 2019\Code codice\visual Basic\frammenti di codice*

   ::: moniker-end

6. Testare il frammento aprendo un C# o un progetto di Visual Basic. Con un file di codice aperto nell'editor, scegliere **frammenti** > **Inserisci frammento di codice** dal menu di scelta rapida, quindi **frammenti di codice**. Verrà visualizzato un frammento denominato **radice quadrata**. Fare doppio clic.

   Il frammento di codice viene inserito nel file di codice.

## <a name="description-and-shortcut-fields"></a>Campi di descrizione e collegamento

::: moniker range="vs-2017"

1. I campi di descrizione contengono informazioni dettagliate sul frammento di codice quando viene visualizzato in Gestione frammenti di codice. Il collegamento è un tag che gli utenti possono digitare per inserire il frammento. Modificare il frammento aggiunto aprendo il file *%USERPROFILE%\Documents\Visual Studio 2017\frammenti frammenti\\[Visual C# o Visual Basic] \My Code Snippet\SquareRoot.snippet*.

::: moniker-end

::: moniker range=">=vs-2019"

1. I campi di descrizione contengono informazioni dettagliate sul frammento di codice quando viene visualizzato in Gestione frammenti di codice. Il collegamento è un tag che gli utenti possono digitare per inserire il frammento. Modificare il frammento aggiunto aprendo il file *%USERPROFILE%\Documents\Visual Studio 2019\Code frammenti\\[Visual C# o Visual Basic] \My Code Snippet\SquareRoot.snippet*.

::: moniker-end

   > [!TIP]
   > Poiché si sta modificando il file nella directory in cui Visual Studio inserito, non è necessario importarlo per Visual Studio.

2. Aggiungere gli elementi **Author** e **Description** all'elemento **Header** e compilarli.

3. L'elemento **Header** dovrebbe essere simile al seguente:

   ```xml
   <Header>
       <Title>Square Root</Title>
       <Author>Myself</Author>
       <Description>Calculates the square root of 16.</Description>
   </Header>
   ```

4. Aprire **Gestione frammenti di codice** e selezionare il frammento di codice. Nel riquadro di destra, si noti che il **Description** e **autore** campi vengono ora popolati.

   ![Descrizione di frammento di codice in Gestione frammenti di codice](media/code-snippet-description-author.png)

5. Per aggiungere un collegamento, aggiungere un **scelta rapida** elemento all'interno di **intestazione** elemento:

   ```xml
   <Header>
      <Title>Square Root</Title>
      <Author>Myself</Author>
      <Description>Calculates the square root of 16.</Description>
      <Shortcut>sqrt</Shortcut>
    </Header>
   ```

6. Salvare di nuovo il file del frammento.

7. Per testare il collegamento, aprire il progetto usato in precedenza, digitare **sqrt** nell'editor e premere **della scheda** (una volta per Visual Basic, due volte per C#).

   Il frammento viene inserito.

## <a name="replacement-parameters"></a>Parametri di sostituzione

È possibile che parti di un frammento di codice da sostituire con l'utente. Ad esempio, è possibile sostituire un nome di variabile con uno nel progetto corrente. È possibile specificare due tipi di sostituzioni, vale a dire valori letterali e oggetti. Usare la [elemento Literal](code-snippets-schema-reference.md#literal-element) per identificare una sostituzione per un frammento di codice che è interamente contenuto entro il frammento di codice ma verrà probabilmente personalizzata dopo che viene inserito nel codice (ad esempio, un valore stringa o numerica). Usare la [elemento oggetto](code-snippets-schema-reference.md#object-element) per identificare un elemento che viene richiesto dal frammento di codice, ma è probabilmente definito di fuori del frammento stesso (ad esempio, un'istanza dell'oggetto o un controllo).

1. Per consentire all'utente di sostituire facilmente il numero per calcolare la radice quadrata di, modificare il **frammento** elemento delle *SquareRoot.snippet* file come segue:

   ```xml
   <Snippet>
     <Code Language="CSharp">
       <![CDATA[double root = Math.Sqrt($Number$);]]>
     </Code>
     <Declarations>
       <Literal>
         <ID>Number</ID>
         <ToolTip>Choose the number you want the square root of.</ToolTip>
         <Default>16</Default>
       </Literal>
     </Declarations>
   </Snippet>
   ```

   Si noti che la sostituzione valore letterale sia assegnata un ID (`Number`). Che ID fa da entro il frammento di codice che lo delimita si con `$` caratteri:

   ```xml
   <![CDATA[double root = Math.Sqrt($Number$);]]>
   ```

2. Salvare il file di frammento di codice.

3. Aprire un progetto e inserire il frammento di codice.

   Viene inserito il frammento di codice e viene evidenziato il valore letterale modificabile per la sostituzione. Passare il mouse su parametro di sostituzione per visualizzare la descrizione comando per il valore.

   ![Descrizione comando parametro di sostituzione di frammento di codice in Visual Studio code](media/snippet-replacement-parameter-tooltip.png)

   > [!TIP]
   > Se è presente più di un parametro replacable in un frammento di codice, è possibile premere **scheda** per passare da uno a altro per modificare i valori.

## <a name="import-a-namespace"></a>Importa uno spazio dei nomi

È possibile usare un frammento di codice per aggiungere un `using` (direttiva) (C#) o `Imports` istruzione (Visual Basic), includendo il [elemento Imports](code-snippets-schema-reference.md#imports-element). Per i progetti .NET Framework, è anche possibile aggiungere un riferimento al progetto usando il [References (elemento)](code-snippets-schema-reference.md#references-element).

Il codice XML seguente viene illustrato un frammento di codice che usa il metodo `File.Exists` nello spazio dei nomi System.IO e, pertanto, vengono definiti i **importazioni** elemento per importare lo spazio dei nomi System.IO.

```xml
<?xml version="1.0" encoding="utf-8"?>
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
  <CodeSnippet Format="1.0.0">
    <Header>
      <Title>File Exists</Title>
      <Shortcut>exists</Shortcut>
    </Header>
    <Snippet>
      <Code Language="CSharp">
        <![CDATA[var exists = File.Exists("C:\\Temp\\Notes.txt");]]>
      </Code>
      <Imports>
        <Import>
          <Namespace>System.IO</Namespace>
        </Import>
      </Imports>
    </Snippet>
  </CodeSnippet>
</CodeSnippets>
```

## <a name="see-also"></a>Vedere anche

- [Informazioni di riferimento sullo schema dei frammenti di codice](../ide/code-snippets-schema-reference.md)