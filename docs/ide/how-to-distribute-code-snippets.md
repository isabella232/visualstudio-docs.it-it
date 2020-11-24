---
title: Distribuire frammenti di codice come estensione
description: Informazioni su come usare Gestione frammenti di codice per distribuire frammenti di codice ad altri sviluppatori.
ms.custom: SEO-VS-2020
ms.date: 03/21/2019
ms.topic: how-to
helpviewer_keywords:
- code snippets, distributing
ms.assetid: 5f717abd-e167-47ae-818c-6b0bae100ceb
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 17f477fe2d02a43cef77358e862cfdf80a079ba5
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/24/2020
ms.locfileid: "95597171"
---
# <a name="how-to-distribute-code-snippets"></a>Procedura: Distribuire frammenti di codice

È sufficiente distribuire i frammenti di codice ad altri utenti, che dovranno installarli nei computer con **Gestione frammenti di codice**. Se si hanno diversi frammenti da distribuire o si vuole distribuirli più ampiamente, tuttavia, è possibile includere il file di frammento in un'estensione di Visual Studio. Gli utenti di Visual Studio possono quindi installare l'estensione per ottenere i frammenti di codice.

## <a name="prerequisites"></a>Prerequisiti

Installare il carico di lavoro **Sviluppo di estensioni di Visual Studio** per ottenere l'accesso ai modelli del **progetto VSIX**.

![Carico di lavoro Sviluppo di estensioni di Visual Studio](media/vs-2019/extension-development-workload.png)

## <a name="set-up-the-extension"></a>Configurazione dell'estensione

In questa procedura si userà lo stesso frammento di codice Hello World creato in [procedura dettagliata: creazione di un frammento di codice](../ide/walkthrough-creating-a-code-snippet.md). Questo articolo specifica il frammento di codice XML, quindi non è necessario tornare indietro e creare un frammento di codice.

1. Creare un nuovo progetto dal modello di **progetto VSIX vuoto** e assegnare al progetto il nome **TestSnippet**.

2. Nel progetto **TestSnippet** aggiungere un nuovo file XML e denominarlo *VBCodeSnippet.snippet*. Sostituire il contenuto con il codice XML riportato di seguito:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <CodeSnippets
        xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
      <CodeSnippet Format="1.0.0">
        <Header>
          <Title>Hello World VB</Title>
          <Shortcut>HelloWorld</Shortcut>
          <Description>Inserts code</Description>
          <Author>MSIT</Author>
          <SnippetTypes>
            <SnippetType>Expansion</SnippetType>
            <SnippetType>SurroundsWith</SnippetType>
          </SnippetTypes>
        </Header>
        <Snippet>
          <Code Language="VB">
            <![CDATA[Console.WriteLine("Hello, World!")]]>
          </Code>
        </Snippet>
      </CodeSnippet>
    </CodeSnippets>
    ```

### <a name="set-up-the-directory-structure"></a>Configurazione della struttura di directory

1. In **Esplora soluzioni** selezionare il nodo del progetto e aggiungere una cartella contenente il nome che si vuole assegnare al frammento di codice in **Gestione frammenti di codice**. In questo caso, dovrebbe essere **HelloWorldVB**.

2. Spostare il file con estensione *snippet* nella cartella *HelloWorldVB*.

3. Selezionare il file *SNIPPET* in **Esplora soluzioni** e nella finestra **Proprietà** verificare che **Azione di compilazione** sia impostato su **Contenuto**, **Copia nella directory di output** sia impostato su **Copia sempre** e **Includi in VSIX** sia impostato su **true**.

### <a name="add-the-pkgdef-file"></a>Aggiunta del file con estensione pkgdef

::: moniker range="vs-2017"

1. Aggiungere un file di testo alla cartella *HelloWorldVB* e denominarlo *HelloWorldVB.pkgdef*. Questo file consente di aggiungere alcune chiavi nel Registro di sistema. In questo caso, aggiunge una nuova sottochiave alla chiave **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Languages\CodeExpansions\Basic**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Aggiungere un file di testo alla cartella *HelloWorldVB* e denominarlo *HelloWorldVB.pkgdef*. Questo file consente di aggiungere alcune chiavi nel Registro di sistema. In questo caso, aggiunge una nuova sottochiave alla chiave **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\16.0\Languages\CodeExpansions\Basic**.

::: moniker-end

2. Aggiungere al file il codice seguente:

    ```txt
    // Visual Basic
    [$RootKey$\Languages\CodeExpansions\Basic\Paths]
    "HelloWorldVB"="$PackageFolder$"
    ```

    Se si esamina questa chiave, è possibile visualizzare come specificare diverse lingue.

3. Selezionare il file *PKGDEF* in **Esplora soluzioni** e nella finestra **Proprietà** verificare che:

   - L'**azione di compilazione** sia impostata su **Contenuto**
   - L'opzione **Copia nella directory di output** sia impostata su **Copia sempre**
   - L'opzione **Includi in VSIX** sia impostata su **true**

4. Aggiungere il file con estensione *pkgdef* come una risorsa nel manifesto VSIX. Nel file *source.extension.vsixmanifest* passare alla scheda **Asset** e fare clic su **Nuovo**.

5. Nella finestra di dialogo **Aggiungi nuovo asset** impostare **Tipo** su **Microsoft.VisualStudio.VsPackage**, **Origine** su **File in filesystem** e **Percorso** su **HelloWorldVB.pkgdef** (che dovrebbe essere visualizzato nell'elenco a discesa).

### <a name="test-the-snippet"></a>Test del frammento di codice

1. A questo punto è possibile assicurarsi che il frammento di codice funzioni nell'istanza sperimentale di Visual Studio. L'istanza sperimentale è una seconda copia di Visual Studio, separata da quella usata per scrivere codice. Consente di lavorare su un'estensione senza impatto sull'ambiente di sviluppo.

2. Compilare il progetto e avviare il debug.

   Verrà visualizzata una seconda istanza di Visual Studio.

3. Nell'istanza sperimentale, passare a **strumenti**  >  **Gestione frammenti di codice** e impostare il **linguaggio** su **Basic**. *HelloWorldVB* verrà visualizzato come una delle cartelle e dovrebbe essere possibile espandere la cartella per visualizzare il frammento *HelloWorldVB*.

4. Eseguire il test del frammento di codice. Nell'istanza sperimentale aprire un progetto Visual Basic e uno dei file di codice. Posizionare il cursore in un punto nel codice, fare clic con il pulsante destro del mouse e nel menu di scelta rapida selezionare **Inserisci frammento di codice**.

5. *HelloWorldVB* dovrebbe essere visualizzato come una delle cartelle. Fare doppio clic. Verrà visualizzato un menu a comparsa **Inserisci frammento di codice: HellowWorldVB >** con un elenco a discesa **HelloWorldVB**. Fare clic sull'elenco a discesa **HelloWorldVB**.

   La riga seguente viene aggiunta al file di codice:

    ```vb
    Console.WriteLine("Hello, World!")
    ```

## <a name="see-also"></a>Vedere anche

- [Frammenti di codice](../ide/code-snippets.md)
