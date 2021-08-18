---
title: 'Procedura dettagliata: Creare un frammento di codice'
description: 'Informazioni su come creare un frammento di codice in tre passaggi: creare un file XML, compilare gli elementi appropriati e aggiungerne il codice.'
ms.custom: SEO-VS-2020
ms.date: 03/31/2020
ms.topic: how-to
helpviewer_keywords:
- code snippets, creating
- code snippets, shortcut
- code snippets, template
- code snippets, replacements
- code snippets, references
- code snippets, imports
ms.assetid: 0dcaae11-39cf-4463-9c90-2494321251c2
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 866f4880caf90977e3da809e63def40932c8f024
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122116643"
---
# <a name="walkthrough-create-a-code-snippet"></a>Procedura dettagliata: Creare un frammento di codice

Per creare un frammento di codice sono necessari pochi passaggi. È sufficiente creare un file XML, inserire gli elementi appropriati e aggiungere il codice. È eventualmente possibile usare parametri di sostituzione e riferimenti al progetto. Importare il frammento nell'installazione di Visual Studio usando il pulsante **Importa** in **Gestione frammenti di codice** (**Strumenti** > **Gestione frammenti di codice**).

## <a name="snippet-template"></a>Modello di frammento

Il codice XML seguente illustra il modello di frammento di base:

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

2. Specificare il titolo del frammento nell'elemento **Title**. Usare il titolo **Square Root**.

3. Aggiungere il linguaggio del frammento nell'attributo **Language** dell'elemento **Code**. Per C#, usare **CSharp**, per Visual Basic, usare **VB** e per C++, usare **CPP**.

   > [!TIP]
   > Per tutti i valori di lingua disponibili, vedere la [sezione Attributi dell'elemento Code](code-snippets-schema-reference.md#attributes) nella pagina [Riferimento dello schema dei frammenti di codice](code-snippets-schema-reference.md).

4. Aggiungere il frammento di codice nella sezione **CDATA** all'interno dell'elemento **Code**.

   Per C#:

   ```xml
   <Code Language="CSharp">
       <![CDATA[double root = Math.Sqrt(16);]]>
   </Code>
   ```

   Oppure per Visual Basic:

   ```xml
   <Code Language="VB">
       <![CDATA[Dim root = Math.Sqrt(16)]]>
   </Code>
   ```

   > [!NOTE]
   > Non è possibile specificare come impostare un rientro o formattare le righe di codice nella sezione **CDATA** di un frammento di codice. Al momento dell'inserimento, il servizio di linguaggio formatta automaticamente il codice inserito.

5. Salvare il frammento come *SquareRoot.snippet* in un percorso qualsiasi.

## <a name="import-a-code-snippet"></a>Importare un frammento di codice

1. È possibile importare un frammento nell'installazione di Visual Studio tramite **Gestione frammenti di codice**. Aprirlo scegliendo **Strumenti**  >  **Gestione frammenti di codice**.

2. Fare clic sul pulsante **Import** (Importa).

3. Scegliere il percorso in cui è stato salvato il frammento di codice nella procedura precedente, selezionarlo e fare clic su **Apri**.

4. Si aprirà la finestra di dialogo **Importa frammento di codice** in cui viene chiesto di scegliere il punto in cui aggiungere il frammento tra le opzioni nel riquadro di destra. Una delle opzioni possibili è **Frammenti di codice**. Selezionare l'opzione e fare clic su **Fine** e poi su **OK**.

5. Il frammento viene copiato in uno dei percorsi seguenti, a seconda del linguaggio del codice:

   ::: moniker range="vs-2017"

   *%USERPROFILE%\Documents\Visual Studio 2017\Code Snippets\Visual C#\My Code Snippets*  
   *%USERPROFILE%\Documenti\Visual Studio 2017\Frammenti di codice\Visual Basic\Frammenti di codice*

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   *%USERPROFILE%\Documents\Visual Studio 2019\Code Snippets\Visual C#\My Code Snippets*  
   *%USERPROFILE%\Documenti\Visual Studio 2019\Frammenti di codice\Visual Basic\Frammenti di codice*

   ::: moniker-end

6. Testare il frammento aprendo un progetto C# o Visual Basic. Con un file di codice aperto nell'editor, scegliere Frammenti di codice Inserisci frammento di codice dal menu di scelta  >   rapida, quindi **Frammenti di codice.** Verrà visualizzato un frammento denominato **Square Root**. Fare doppio clic.

   Il frammento viene inserito nel file di codice.

## <a name="description-and-shortcut-fields"></a>Campi di descrizione e collegamento

::: moniker range="vs-2017"

1. I campi di descrizione contengono informazioni dettagliate sul frammento di codice quando viene visualizzato in Gestione frammenti di codice. Il collegamento è un tag che gli utenti possono digitare per inserire il frammento. Modificare il frammento aggiunto aprendo il file *%USERPROFILE%\Documenti\Visual Studio 2017\Frammenti di codice\\[Visual C# o Visual Basic]\Frammenti di codice\SquareRoot.snippet*.

::: moniker-end

::: moniker range=">=vs-2019"

1. I campi di descrizione contengono informazioni dettagliate sul frammento di codice quando viene visualizzato in Gestione frammenti di codice. Il collegamento è un tag che gli utenti possono digitare per inserire il frammento. Modificare il frammento aggiunto aprendo il file *%USERPROFILE%\Documenti\Visual Studio 2019\Frammenti di codice\\[Visual C# o Visual Basic]\Frammenti di codice\SquareRoot.snippet*.

::: moniker-end

   > [!TIP]
   > Poiché si sta modificando il file nella directory in cui è stato inserito da Visual Studio, non è necessario importarlo di nuovo in Visual Studio.

2. Aggiungere gli elementi **Author** e **Description** all'elemento **Header** e compilarli.

3. L'elemento **Header** dovrebbe essere simile al seguente:

   ```xml
   <Header>
       <Title>Square Root</Title>
       <Author>Myself</Author>
       <Description>Calculates the square root of 16.</Description>
   </Header>
   ```

4. Aprire **Gestione frammenti di codice** e selezionare il frammento di codice. Nel riquadro a destra i campi **Descrizione** e **Autore** includono ora valori.

   ![Descrizione del frammento di codice in Gestione frammenti di codice](media/code-snippet-description-author.png)

5. Per aggiungere un collegamento, includere un elemento **Shortcut** all'interno dell'elemento **Header**:

   ```xml
   <Header>
      <Title>Square Root</Title>
      <Author>Myself</Author>
      <Description>Calculates the square root of 16.</Description>
      <Shortcut>sqrt</Shortcut>
    </Header>
   ```

6. Salvare di nuovo il file del frammento.

7. Per testare il collegamento, aprire il progetto usato in precedenza, digitare **sqrt** nell'editor e premere **TAB** (una volta per Visual Basic, due volte per C#).

   Il frammento viene inserito.

## <a name="replacement-parameters"></a>Parametri di sostituzione

Può essere opportuno consentire all'utente di sostituire parti di un frammento di codice, ad esempio sostituire il nome di una variabile con uno nel progetto corrente. È possibile specificare due tipi di sostituzioni, vale a dire valori letterali e oggetti. Usare l'[elemento Literal](code-snippets-schema-reference.md#literal-element) per identificare una sostituzione per una parte di codice che è interamente contenuta nel frammento, ma che verrà probabilmente personalizzata dopo l'inserimento nel codice, ad esempio una stringa o un valore numerico. Usare l'[elemento Object](code-snippets-schema-reference.md#object-element) per identificare un elemento che è richiesto dal frammento di codice, ma che probabilmente è definito al di fuori del frammento stesso, ad esempio un'istanza di un oggetto o un controllo.

1. Per consentire all'utente di sostituire facilmente il numero per calcolarne la radice quadrata, modificare l'elemento **Snippet** del file *SquareRoot.snippet* nel modo seguente:

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

   Si noti che al sostituto del valore letterale è assegnato un ID (`Number`). Per fare riferimento a tale ID all'interno del frammento di codice viene usato `$` come carattere di delimitazione:

   ```xml
   <![CDATA[double root = Math.Sqrt($Number$);]]>
   ```

2. Salvare il file del frammento.

3. Aprire un progetto e inserire il frammento.

   Viene inserito il frammento di codice e viene evidenziato il valore letterale modificabile per la sostituzione. Passare il puntatore sul parametro di sostituzione per visualizzare la descrizione comando relativa al valore.

   ![Descrizione comando del parametro di sostituzione del frammento di codice in Visual Studio](media/snippet-replacement-parameter-tooltip.png)

   > [!TIP]
   > Se in un frammento di codice sono presenti più parametri sostituibili, è possibile premere **TAB** per passare da uno all'altro per modificare i valori.

## <a name="import-a-namespace"></a>Importare uno spazio dei nomi

È possibile usare un frammento di codice per aggiungere una direttiva `using` (C#) o un'istruzione `Imports` (Visual Basic) includendo l'[elemento Imports](code-snippets-schema-reference.md#imports-element). Per i progetti .NET Framework, è anche possibile aggiungere un riferimento al progetto usando l'[elemento References](code-snippets-schema-reference.md#references-element).

Il codice XML seguente illustra un frammento di codice che usa il metodo `File.Exists` nello spazio dei nomi System.IO e, pertanto, definisce l'elemento **Imports** per importare lo spazio dei nomi System.IO.

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

## <a name="see-also"></a>Vedi anche

- [Riferimento dello schema dei frammenti di codice](../ide/code-snippets-schema-reference.md)
