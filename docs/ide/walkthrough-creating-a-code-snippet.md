---
title: 'Procedura dettagliata: Creare un frammento di codice'
ms.date: 10/27/2017
ms.prod: visual-studio-dev15
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
manager: douge
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 66d618999fc2ae3e94316f64e20a82516efbeb38
ms.sourcegitcommit: 38db86369af19e174b0aba59ba1918a5c4fe4a61
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/14/2019
ms.locfileid: "54269800"
---
# <a name="walkthrough-create-a-code-snippet"></a>Procedura dettagliata: Creare un frammento di codice
Per creare un frammento di codice sono necessari pochi passaggi. È sufficiente creare un file XML, inserire gli elementi appropriati e aggiungere il codice. È anche possibile aggiungere al codice riferimenti e parametri sostitutivi. È possibile aggiungere il frammento all'installazione di Visual Studio usando il pulsante **Importa** in **Gestione frammenti di codice** (**Strumenti** > **Gestione frammenti di codice**).

## <a name="snippet-template"></a>Modello di frammento
 Di seguito è illustrato il modello di frammento di base:

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

### <a name="create-a-code-snippet"></a>Creare un frammento di codice

1.  Creare un nuovo file XML in Visual Studio e aggiungere il modello come illustrato in precedenza.

2.  Compilare il titolo del frammento, ad esempio "Hello World VB", nell'elemento **Title**.

3.  Aggiungere il linguaggio del frammento nell'attributo **Language** dell'elemento **Code**. In questo esempio usare "VB".

4.  Aggiungere codice nella sezione **CDATA** all'interno dell'elemento **Code**, ad esempio:

    ```xml
    <Code Language="VB">
        <![CDATA[Console.WriteLine("Hello, World!")]]>
    </Code>
    ```

5.  Salvare il frammento come *VBCodeSnippet.snippet*.

### <a name="add-a-code-snippet-to-visual-studio"></a>Aggiungere un frammento di codice a Visual Studio

1.  È possibile aggiungere frammenti di codice personalizzati all'installazione di Visual Studio tramite Gestione frammenti di codice. Aprire **Gestione frammenti di codice** (**Strumenti** > **Gestione frammenti di codice**).

2.  Fare clic sul pulsante **Importa**.

3.  Scegliere il percorso in cui è stato salvato il frammento di codice nella procedura precedente, selezionarlo e fare clic su **Apri**.

4.  Si aprirà la finestra di dialogo **Importa frammento di codice** in cui viene chiesto di scegliere il punto in cui aggiungere il frammento tra le opzioni nel riquadro di destra. Una delle opzioni possibili è **Frammenti di codice**. Selezionare l'opzione e fare clic su **Fine** e poi su **OK**.

5.  Il frammento viene copiato nel percorso seguente:

     *%USERPROFILE%\Documenti\Visual Studio 2017\Frammenti di codice\Visual Basic\Frammenti di codice*

6.  Testare il frammento aprendo un progetto di Visual Basic e un file di codice. Nel file scegliere **Frammenti** > **Inserisci frammento** dal menu di scelta rapida e quindi **Frammenti di codice**. Verrà visualizzato un frammento denominato **My Visual Basic Code Snippet** (Frammento di codice Visual Basic). Fare doppio clic.

    `Console.WriteLine("Hello, World!")` viene inserito nel file di codice.

### <a name="add-description-and-shortcut-fields"></a>Aggiungere campi di descrizione e collegamento

1.  I campi di descrizione contengono informazioni dettagliate sul frammento di codice quando viene visualizzato in Gestione frammenti di codice. Il collegamento è un tag che gli utenti possono digitare per inserire il frammento. Modificare il frammento aggiunto aprendo il file *%USERPROFILE%\Documenti\Visual Studio 2017\Frammenti di codice\Visual Basic\Frammenti di codice\VBCodeSnippet.snippet*.

2.  Aggiungere gli elementi **Author** e **Description** all'elemento **Header** e compilarli.

3.  L'elemento **Header** dovrebbe essere simile al seguente:

    ```xml
    <Header>
        <Title>Hello World VB</Title>
        <Author>Myself</Author>
        <Description>Says Hello to the world.</Description>
    </Header>
    ```

4.  Aprire **Gestione frammenti di codice** e selezionare il frammento di codice. Nel riquadro a destra i campi **Descrizione** e **Autore** saranno ora popolati.

5.  Per aggiungere un collegamento, aggiungere un elemento **Shortcut** insieme agli elementi **Author** e **Description**:

    ```xml
    <Header>
        <Title>Hello World VB</Title>
        <Author>Myself</Author>
        <Description>Says Hello to the world.</Description>
        <Shortcut>hello</Shortcut>
    </Header>
    ```

6.  Salvare di nuovo il file del frammento.

7.  Per testare il collegamento, aprire un progetto Visual Basic e aprire un file di codice. Digitare `hello` nel file e premere **TAB** due volte.

    Il frammento viene inserito.

### <a name="add-references-and-imports"></a>Aggiungere riferimenti e importazioni

1.  È possibile aggiungere un riferimento a un progetto usando l'elemento **References** e aggiungere una dichiarazione di importazione usando l'elemento **Imports**. Questa procedura è valida anche per C#. Se ad esempio si modifica `Console.WriteLine` nell'esempio di codice in `MessageBox.Show`, può essere necessario aggiungere l'assembly *System.Windows.Forms.dll* al progetto.

2.  Aprire il frammento.

3.  Aggiungere l'elemento **References** sotto l'elemento **Snippet**:

    ```xml
    <References>
        <Reference>
            <Assembly>System.Windows.Forms.dll</Assembly>
        </Reference>
    </References>
    ```

4.  Aggiungere l'elemento **Imports** sotto l'elemento **Snippet**:

    ```xml
    <Imports>
        <Import>
           <Namespace>System.Windows.Forms</Namespace>
        </Import>
    </Imports>
    ```

5.  Modificare la sezione **CDATA** nel modo seguente:

    ```xml
    <![CDATA[MessageBox.Show("Hello, World!")]]>
    ```

6.  Salvare il frammento.

7.  Aprire un progetto Visual Basic e aggiungere il frammento.

8.  Viene visualizzata un'istruzione `Imports` nella parte superiore del file di codice:

    ```vb
    Imports System.Windows.Forms
    ```

9. Considerare le proprietà del progetto. La scheda **Riferimenti** contiene un riferimento a *System.Windows.Forms.dll*.

### <a name="add-replacements"></a>Aggiungere sostituzioni

1.  È possibile che si vogliano sostituire alcune parti dei frammenti di codice, ad esempio nel caso in cui venga aggiunta una variabile e la si voglia sostituire con una del progetto corrente. È possibile specificare due tipi di sostituzioni, vale a dire valori letterali e oggetti. I valori letterali sono stringhe di un certo tipo, ad esempio valori letterali stringa, nomi di variabile o rappresentazioni di stringa di valori numerici. Gli oggetti sono istanze di un certo tipo diverso da una stringa. Questa procedura consente di dichiarare la sostituzione di un valore letterale o di un oggetto e modificare il codice in modo che faccia riferimento a queste sostituzioni.

2.  Aprire il frammento.

3.  In questo esempio viene usata una stringa di connessione SQL. Di conseguenza è necessario modificare gli elementi **Imports** e **References** per aggiungere i riferimenti appropriati:

    ```xml
    <References>
        <Reference>
            <Assembly>System.Data.dll</Assembly>
        </Reference>
        <Reference>
            <Assembly>System.Xml.dll</Assembly>
        </Reference>
    </References>
    <Imports>
        <Import>
            <Namespace>System.Data</Namespace>
        </Import>
        <Import>
            <Namespace>System.Data.SqlClient</Namespace>
        </Import>
    </Imports>
    ```

4.  Per dichiarare la sostituzione di un valore letterale della stringa di connessione SQL, aggiungere un elemento **Declarations** sotto l'elemento **Snippet** e qui aggiungere un elemento **Literal** con sottoelementi per l'ID, la descrizione comando e il valore predefinito per la sostituzione:

    ```xml
    <Declarations>
        <Literal>
            <ID>SqlConnString</ID>
            <ToolTip>Replace with a SQL connection string.</ToolTip>
            <Default>"SQL connection string"</Default>
        </Literal>
    </Declarations>
    ```

5.  Per dichiarare la sostituzione di un oggetto per la connessione SQL, aggiungere un elemento **Object** all'interno dell'elemento **Declarations** e aggiungere sottoelementi per l'ID, il tipo di oggetto, la descrizione comando e il valore predefinito. L'elemento **Declarations** risultante sarà simile al seguente:

    ```xml
    <Declarations>
        <Literal>
            <ID>SqlConnString</ID>
            <ToolTip>Replace with a SQL connection string.</ToolTip>
            <Default>"SQL connection string"</Default>
        </Literal>
        <Object>
            <ID>SqlConnection</ID>
            <Type>System.Data.SqlClient.SqlConnection</Type>
            <ToolTip>Replace with a connection object in your application.</ToolTip>
            <Default>dcConnection</Default>
        </Object>
    </Declarations>
    ```

6.  Nella sezione di codice si fa riferimento alle sostituzioni delimitandole con i segni $, ad esempio `$replacement$`:

    ```xml
    <Code Language="VB" Kind="method body">
        <![CDATA[Dim daCustomers As SqlDataAdapter
            Dim selectCommand As SqlCommand

            daCustomers = New SqlClient.SqlDataAdapter()
            selectCommand = new SqlClient.SqlCommand($SqlConnString$)
            daCustomers.SelectCommand = selectCommand
            daCustomers.SelectCommand.Connection = $SqlConnection$]]>
    </Code>
    ```

7.  Salvare il frammento.

8.  Aprire un progetto Visual Basic e aggiungere il frammento.

9. Il codice sarà essere simile al seguente, dove le sostituzioni `SQL connection string` e `dcConnection` sono evidenziate in arancione chiaro. Scegliere **TAB** per passare da una sostituzione all'altra.

    ```vb
    Dim daCustomers As SqlDataAdapter
    Dim selectCommand As SqlCommand

    daCustomers = New SqlClient.SqlDataAdapter()
    selectCommand = New SqlClient.SqlCommand("SQL connection string")
    daCustomers.SelectCommand = selectCommand
    daCustomers.SelectCommand.Connection = dcConnection
    ```

## <a name="see-also"></a>Vedere anche

- [Informazioni di riferimento sullo schema dei frammenti di codice](../ide/code-snippets-schema-reference.md)