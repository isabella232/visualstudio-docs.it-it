---
title: 'Procedura dettagliata: Implementazione di frammenti di codice | Microsoft Docs'
description: È possibile creare frammenti di codice e includerli in un'estensione dell'editor. Informazioni su come creare/registrare frammenti di codice usando questa procedura dettagliata.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: adbc5382-d170-441c-9fd0-80faa1816478
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
dev_langs:
- CSharp
- VB
ms.workload:
- vssdk
ms.openlocfilehash: 106339c932b0339542fd184675448b8ec8354bf0618fbddc7e351ab11763a289
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121234759"
---
# <a name="walkthrough-implement-code-snippets"></a>Procedura dettagliata: Implementare frammenti di codice
È possibile creare frammenti di codice e includerli in un'estensione dell'editor in modo che gli utenti dell'estensione possano aggiungerli al proprio codice.

 Un frammento di codice è un frammento di codice o altro testo che può essere incorporato in un file. Per visualizzare tutti i frammenti registrati per linguaggi di programmazione specifici, scegliere Gestione frammenti di codice dal **menu** **Strumenti**. Per inserire un frammento di codice in un file, fare clic con il pulsante destro del mouse nel punto in cui si vuole inserire il frammento di codice, scegliere Inserisci frammento di codice o Surround **With**, individuare il frammento desiderato e quindi fare doppio clic su di esso. Premere **TAB** o **MAIUSC** TAB per modificare le parti rilevanti del frammento di codice e quindi premere +  **INVIO** o **ESC** per accettarlo. Per altre informazioni, vedere [Frammenti di codice](../ide/code-snippets.md).

 Un frammento di codice è contenuto in un file XML con estensione snippet*. Un frammento di codice può contenere campi evidenziati dopo l'inserimento del frammento in modo che l'utente possa trovarli e modificarli. Un file di frammento fornisce anche informazioni per **Gestione frammenti di codice** in modo che possa visualizzare il nome del frammento nella categoria corretta. Per informazioni sullo schema del frammento di codice, vedere [Informazioni di riferimento sullo schema dei frammenti di codice](../ide/code-snippets-schema-reference.md).

 Questa procedura dettagliata illustra come eseguire queste attività:

1. Creare e registrare frammenti di codice per un linguaggio specifico.

2. Aggiungere il **comando Inserisci frammento** di codice a un menu di scelta rapida.

3. Implementare l'espansione del frammento di codice.

   Questa procedura dettagliata è basata su [Procedura dettagliata: Visualizzare il completamento delle istruzioni](../extensibility/walkthrough-displaying-statement-completion.md).

## <a name="prerequisites"></a>Prerequisiti
 A partire Visual Studio 2015, non si installa Visual Studio SDK dall'Area download. È incluso come funzionalità facoltativa nella configurazione Visual Studio configurazione. È anche possibile installare VS SDK in un secondo momento. Per altre informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-and-register-code-snippets"></a>Creare e registrare frammenti di codice
 In genere, i frammenti di codice sono associati a un servizio di linguaggio registrato. Tuttavia, non è necessario implementare per registrare <xref:Microsoft.VisualStudio.Package.LanguageService> frammenti di codice. È sufficiente specificare un GUID nel file di indice del frammento di codice e quindi usare lo stesso GUID nell'oggetto <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> aggiunto al progetto.

 La procedura seguente illustra come creare frammenti di codice e associarli a un GUID specifico.

1. Creare la struttura di directory seguente:

    **%InstallDir%\TestSnippets\Snippets\1033\\**

    dove *%InstallDir%* è la Visual Studio di installazione. Anche se questo percorso viene in genere usato per installare frammenti di codice, è possibile specificare qualsiasi percorso.

2. Nella cartella \1033\ creare un file *.xml* e denomerlo **TestSnippets.xml**. Anche se questo nome viene in genere usato per un file di indice del frammento di codice, è possibile specificare qualsiasi nome purché abbia *un'estensione*.xmlfile. Aggiungere il testo seguente, quindi eliminare il GUID segnaposto e aggiungere il proprio.

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <SnippetCollection>
       <Language Lang="TestSnippets" Guid="{00000000-0000-0000-0000-000000000000}">
           <SnippetDir>
               <OnOff>On</OnOff>
               <Installed>true</Installed>
               <Locale>1033</Locale>
               <DirPath>%InstallRoot%\TestSnippets\Snippets\%LCID%\</DirPath>
               <LocalizedName>Snippets</LocalizedName>
           </SnippetDir>
       </Language>
   </SnippetCollection>
   ```

3. Creare un file nella cartella del frammento di codice, assegnargli il **nome test** e quindi aggiungere il `.snippet` testo seguente:

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <CodeSnippets  xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
       <CodeSnippet Format="1.0.0">
           <Header>
               <Title>Test replacement fields</Title>
               <Shortcut>test</Shortcut>
               <Description>Code snippet for testing replacement fields</Description>
               <Author>MSIT</Author>
               <SnippetTypes>
                   <SnippetType>Expansion</SnippetType>
               </SnippetTypes>
           </Header>
           <Snippet>
               <Declarations>
                   <Literal>
                     <ID>param1</ID>
                       <ToolTip>First field</ToolTip>
                       <Default>first</Default>
                   </Literal>
                   <Literal>
                       <ID>param2</ID>
                       <ToolTip>Second field</ToolTip>
                       <Default>second</Default>
                   </Literal>
               </Declarations>
               <References>
                  <Reference>
                      <Assembly>System.Windows.Forms.dll</Assembly>
                  </Reference>
               </References>
               <Code Language="TestSnippets">
                   <![CDATA[MessageBox.Show("$param1$");
        MessageBox.Show("$param2$");]]>
               </Code>
           </Snippet>
       </CodeSnippet>
   </CodeSnippets>
   ```

   La procedura seguente illustra come registrare i frammenti di codice.

### <a name="to-register-code-snippets-for-a-specific-guid"></a>Per registrare frammenti di codice per un GUID specifico

1. Aprire il **progetto CompletionTest.** Per informazioni su come creare questo progetto, vedere [Procedura dettagliata: Visualizzare il completamento delle istruzioni](../extensibility/walkthrough-displaying-statement-completion.md).

2. Nel progetto aggiungere riferimenti agli assembly seguenti:

    - Microsoft.VisualStudio.TextManager.Interop

    - Microsoft.VisualStudio.TextManager.Interop.8.0

    - microsoft.msxml

3. Nel progetto aprire il file **source.extension.vsixmanifest.**

4. Assicurarsi che la **scheda Asset contenga** un tipo di contenuto **VsPackage** **e** che Project sia impostato sul nome del progetto.

5. Selezionare il progetto CompletionTest e nella Finestra Proprietà **impostare Genera file Pkgdef** su **true.** Salvare il progetto.

6. Aggiungere una `SnippetUtilities` classe statica al progetto.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs" id="Snippet22":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb" id="Snippet22":::

7. Nella classe SnippetUtilities definire un GUID e assegnargli il valore usato nel file *SnippetsIndex.xml* file.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs" id="Snippet23":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb" id="Snippet23":::

8. Aggiungere alla <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> `TestCompletionHandler` classe . Questo attributo può essere aggiunto a qualsiasi classe pubblica o interna (non statica) nel progetto. Potrebbe essere necessario aggiungere una direttiva per lo spazio dei nomi `using` Microsoft.VisualStudio.Shell.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs" id="Snippet24":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb" id="Snippet24":::

9. Compilare ed eseguire il progetto. Nell'istanza sperimentale di Visual Studio che inizia quando viene eseguito il progetto, il frammento appena registrato deve essere visualizzato in **Gestione** frammenti di codice nel linguaggio **TestSnippets.**

## <a name="add-the-insert-snippet-command-to-the-shortcut-menu"></a>Aggiungere il comando Inserisci frammento di codice al menu di scelta rapida
 Il **comando Inserisci frammento** di codice non è incluso nel menu di scelta rapida per un file di testo. Pertanto, è necessario abilitare il comando .

#### <a name="to-add-the-insert-snippet-command-to-the-shortcut-menu"></a>Per aggiungere il comando Inserisci frammento di codice al menu di scelta rapida

1. Aprire il `TestCompletionCommandHandler` file di classe.

     Poiché questa classe implementa <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> , è possibile attivare il comando Inserisci **frammento** di codice nel <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodo . Prima di abilitare il comando, verificare che questo metodo non  venga chiamato all'interno di una funzione di automazione perché quando si fa clic sul comando Inserisci frammento di codice viene visualizzata l'interfaccia utente di selezione frammento.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs" id="Snippet25":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb" id="Snippet25":::

2. Compilare ed eseguire il progetto. Nell'istanza sperimentale aprire un file con estensione *zzz* e quindi fare clic con il pulsante destro del mouse in un punto qualsiasi. Il **comando Inserisci frammento** di codice dovrebbe essere visualizzato nel menu di scelta rapida.

## <a name="implement-snippet-expansion-in-the-snippet-picker-ui"></a>Implementare l'espansione dei frammenti nell'interfaccia utente di Selezione frammenti di codice
 Questa sezione illustra come implementare l'espansione del frammento  di codice in modo che l'interfaccia utente di selezione frammento di codice sia visualizzata quando si fa clic su Inserisci frammento di codice nel menu di scelta rapida. Un frammento di codice viene espanso anche quando un utente digitare il collegamento al frammento di codice e quindi premere **TAB.**

 Per visualizzare l'interfaccia utente della selezione frammento di codice e abilitare l'accettazione del frammento di navigazione e post-inserimento, usare il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metodo . L'inserimento stesso viene gestito dal <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> metodo .

 L'implementazione dell'espansione del frammento di codice usa <xref:Microsoft.VisualStudio.TextManager.Interop> interfacce legacy. Quando si esegue la conversione dalle classi dell'editor correnti al codice legacy, tenere presente che le interfacce legacy usano una combinazione di numeri di riga e numeri di colonna per specificare le posizioni in un buffer di testo, ma le classi correnti usano un indice. Pertanto, se un buffer ha tre righe ognuna con 10 caratteri (più una nuova riga, che conta come un carattere), il quarto carattere nella terza riga si trova alla posizione 27 nell'implementazione corrente, ma si trova alla riga 2, posizione 3 nell'implementazione precedente.

#### <a name="to-implement-snippet-expansion"></a>Per implementare l'espansione del frammento di codice

1. Aggiungere le direttive seguenti al file che contiene `TestCompletionCommandHandler` `using` la classe .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs" id="Snippet26":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb" id="Snippet26":::

2. Fare in `TestCompletionCommandHandler` modo che la classe implementi l'interfaccia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs" id="Snippet27":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb" id="Snippet27":::

3. Nella classe `TestCompletionCommandHandlerProvider` importare <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs" id="Snippet28":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb" id="Snippet28":::

4. Aggiungere alcuni campi privati per le interfacce di espansione del codice e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs" id="Snippet29":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb" id="Snippet29":::

5. Nel costruttore della `TestCompletionCommandHandler` classe impostare i campi seguenti.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs" id="Snippet30":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb" id="Snippet30":::

6. Per visualizzare la selezione frammento di codice quando l'utente fa clic sul **comando Inserisci frammento** di codice, aggiungere il codice seguente al <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metodo . Per rendere questa spiegazione più leggibile, il codice usato per il completamento dell'istruzione non viene visualizzato, ma vengono aggiunti blocchi di codice `Exec()` al metodo esistente. Aggiungere il blocco di codice seguente dopo il codice che controlla la presenza di un carattere.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs" id="Snippet31":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb" id="Snippet31":::

7. Se un frammento di codice include campi che è possibile esplorare, la sessione di espansione viene mantenuta aperta fino a quando l'espansione non viene accettata in modo esplicito. Se il frammento di codice non ha campi, la sessione viene chiusa e viene restituita `null` come dal <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.InvokeInsertionUI%2A> metodo . Nel metodo , dopo il codice dell'interfaccia utente di selezione frammento aggiunto nel passaggio precedente, aggiungere il codice seguente per gestire la navigazione dei frammenti (quando l'utente preme TAB o MAIUSC TAB dopo l'inserimento del <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>   +  frammento di codice).

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs" id="Snippet32":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb" id="Snippet32":::

8. Per inserire il frammento di codice quando l'utente digitare il collegamento corrispondente e quindi premere **TAB,** aggiungere codice al <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metodo . Il metodo privato che inserisce il frammento di codice verrà visualizzato in un passaggio successivo. Aggiungere il codice seguente dopo il codice di navigazione aggiunto nel passaggio precedente.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs" id="Snippet33":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb" id="Snippet33":::

9. Implementare i metodi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> dell'interfaccia . In questa implementazione gli unici metodi di interesse sono <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.EndExpansion%2A> e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> . Gli altri metodi devono restituire solo <xref:Microsoft.VisualStudio.VSConstants.S_OK> .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs" id="Snippet34":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb" id="Snippet34":::

10. Implementare il metodo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>. Il metodo helper che inserisce effettivamente le espansioni viene trattato in un passaggio successivo. Fornisce <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> informazioni su riga e colonna, che è possibile ottenere da <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs" id="Snippet35":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb" id="Snippet35":::

11. Il metodo privato seguente inserisce un frammento di codice, in base al collegamento o al titolo e al percorso. Chiama quindi il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansion.InsertNamedExpansion%2A> metodo con il frammento di codice.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs" id="Snippet36":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb" id="Snippet36":::

## <a name="build-and-test-code-snippet-expansion"></a>Espansione di frammenti di codice di compilazione e test
 È possibile verificare se l'espansione del frammento di codice funziona nel progetto.

1. Compilare la soluzione. Quando si esegue questo progetto nel debugger, viene avviata una seconda istanza di Visual Studio.

2. Aprire un file di testo e digitare del testo.

3. Fare clic con il pulsante destro del mouse in un punto qualsiasi del testo e quindi **scegliere Inserisci frammento di codice**.

4. L'interfaccia utente di selezione frammento dovrebbe essere visualizzata con un popup che indica **Test replacement fields (Campi di sostituzione test).** Fare doppio clic sul popup.

     È necessario inserire il frammento di codice seguente.

    ```
    MessageBox.Show("first");
    MessageBox.Show("second");
    ```

     Non premere **INVIO o** **ESC.**

5. Premere **TAB e** **MAIUSC** + **TAB** per alternare tra "first" e "second".

6. Accettare l'inserimento premendo **INVIO** o **ESC.**

7. In un'altra parte del testo digitare "test" e quindi premere **TAB.** Poiché "test" è il collegamento del frammento di codice, il frammento di codice deve essere inserito nuovamente.

## <a name="next-steps"></a>Passaggi successivi
