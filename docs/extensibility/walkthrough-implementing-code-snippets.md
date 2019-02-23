---
title: 'Procedura dettagliata: Implementazione di frammenti di codice | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: adbc5382-d170-441c-9fd0-80faa1816478
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 377660b32f8edbb26e8a062d55ee152132f7f587
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56707081"
---
# <a name="walkthrough-implement-code-snippets"></a>Procedura dettagliata: Implementare i frammenti di codice
È possibile creare frammenti di codice e includerli in un'estensione dell'editor in modo che gli utenti dell'estensione possono aggiungere il proprio codice.

 Un frammento di codice è un frammento di codice o altro testo che può essere incorporato in un file. Per visualizzare tutti i frammenti di codice che sono stati registrati per determinati linguaggi di programmazione, sul **degli strumenti** menu, fare clic su **Gestione frammenti di codice**. Per inserire un frammento di codice in un file di scelta rapida in cui si desidera che il frammento di codice, fare clic su Inserisci frammento di codice, o **Racchiudi**, individuare il frammento di codice desiderato e quindi fare doppio clic. Premere **della scheda** oppure **MAIUSC**+**scheda** per modificare le parti pertinenti del frammento di codice e quindi premere **invio** o**Esc** ad accettarla. Per altre informazioni, vedere [frammenti di codice](../ide/code-snippets.md).

 Un frammento di codice è contenuto in un file XML con l'estensione del nome file con estensione snippet *. Un frammento di codice può contenere i campi evidenziati dopo l'inserimento del frammento in modo che l'utente può trovare e modificarle. Un file di frammento di codice fornisce anche informazioni per il **Gestione frammenti di codice** in modo che sia possibile visualizzare il nome del frammento di codice nella categoria corretta. Per informazioni sullo schema del frammento di codice, vedere [riferimenti allo schema dei frammenti di codice](../ide/code-snippets-schema-reference.md).

 Questa procedura dettagliata illustra come eseguire queste attività:

1. Creare e registrare i frammenti di codice per una lingua specifica.

2. Aggiungere il **Inserisci frammento di codice** comando a un menu di scelta rapida.

3. Implementare l'espansione del frammento.

   Questa procedura dettagliata è basata su [procedura dettagliata: Visualizzare il completamento delle istruzioni](../extensibility/walkthrough-displaying-statement-completion.md).

## <a name="prerequisites"></a>Prerequisiti
 A partire da Visual Studio 2015, Visual Studio SDK è non installare dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per altre informazioni, vedere [installare Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-and-register-code-snippets"></a>Creare e registrare i frammenti di codice
 In genere, i frammenti di codice sono associati a un servizio di linguaggio registrati. Tuttavia, non è necessario implementare un <xref:Microsoft.VisualStudio.Package.LanguageService> per registrare i frammenti di codice. Al contrario, specificare solo un GUID nel file di indice del frammento di codice e quindi usare lo stesso GUID nel <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> aggiunti al progetto.

 I passaggi seguenti illustrano come creare frammenti di codice e associarli a un GUID specifico.

1. Creare la struttura di directory seguente:

    **%InstallDir%\TestSnippets\Snippets\1033\\**

    in cui *% InstallDir %* è la cartella di installazione di Visual Studio. (Anche se questo percorso viene in genere usato per installare i frammenti di codice, è possibile specificare qualsiasi percorso.)

2. Nella cartella \1033\, creare un *. XML* del file e denominarlo **TestSnippets.xml**. (Anche se questo nome viene usato in genere per un file di indice del frammento di codice, è possibile specificare un nome qualsiasi, purché abbia un' *XML* estensione del nome file.) Aggiungere il testo seguente, quindi eliminare il GUID segnaposto e aggiungere la propria.

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

3. Creare un file nella cartella frammento di codice, denominarlo **testare**`.snippet`e quindi aggiungere il testo seguente:

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

### <a name="to-register-code-snippets-for-a-specific-guid"></a>Per registrare i frammenti di codice per un GUID specifico

1.  Aprire il **CompletionTest** progetto. Per informazioni su come creare il progetto, vedere [procedura dettagliata: Visualizzare il completamento delle istruzioni](../extensibility/walkthrough-displaying-statement-completion.md).

2.  Nel progetto, aggiungere riferimenti agli assembly seguenti:

    -   Microsoft.VisualStudio.TextManager.Interop

    -   Microsoft.VisualStudio.TextManager.Interop.8.0

    -   microsoft.msxml

3.  Nel progetto, aprire il **vsixmanifest** file.

4.  Assicurarsi che il **Assets** scheda contiene un **VsPackage** tipo e che il contenuto **progetto** è impostato sul nome del progetto.

5.  Selezionare il progetto CompletionTest e nella finestra Proprietà impostare **generare Pkgdef File** al **true**. Salvare il progetto.

6.  Aggiungere un valore statico `SnippetUtilities` classe al progetto.

     [!code-csharp[VSSDKCompletionTest#22](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_1.cs)]
     [!code-vb[VSSDKCompletionTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_1.vb)]

7.  Nella classe SnippetUtilities, definire un GUID e assegnargli il valore usato nel *SnippetsIndex.xml* file.

     [!code-csharp[VSSDKCompletionTest#23](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_2.cs)]
     [!code-vb[VSSDKCompletionTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_2.vb)]

8.  Aggiungere il <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> per il `TestCompletionHandler` classe. Questo attributo può essere aggiunto a qualsiasi classe (non statico) interni o pubblici nel progetto. (Potrebbe essere necessario aggiungere un `using` istruzione dello spazio dei nomi Microsoft.VisualStudio.Shell.)

     [!code-csharp[VSSDKCompletionTest#24](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_3.cs)]
     [!code-vb[VSSDKCompletionTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_3.vb)]

9. Compilare ed eseguire il progetto. Nell'istanza sperimentale di Visual Studio che viene avviato quando il progetto viene eseguito, il frammento di codice appena registrato deve essere visualizzato nei **Gestione frammenti di codice** sotto il **TestSnippets** language.

## <a name="add-the-insert-snippet-command-to-the-shortcut-menu"></a>Aggiungere il comando Inserisci frammento di codice al menu di scelta rapida
 Il **Inserisci frammento di codice** comando non è incluso nel menu di scelta rapida per un file di testo. Pertanto, è necessario abilitare il comando.

#### <a name="to-add-the-insert-snippet-command-to-the-shortcut-menu"></a>Per aggiungere il comando Inserisci frammento di codice per il menu di scelta rapida

1.  Aprire il `TestCompletionCommandHandler` file di classe.

     Poiché questa classe implementa <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>, è possibile attivare la **Inserisci frammento** comando il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> (metodo). Prima di abilitare il comando, verificare che questo metodo non è in corso chiamato all'interno di una funzione di automazione perché quando il **Inserisci frammento di codice** si fa clic sul comando, viene visualizzata l'interfaccia utente di selezione frammento di codice (UI).

     [!code-csharp[VSSDKCompletionTest#25](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_4.cs)]
     [!code-vb[VSSDKCompletionTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_4.vb)]

2.  Compilare ed eseguire il progetto. Nell'istanza sperimentale, aprire un file con il *zzz* estensione del nome file e quindi fare doppio clic su un punto qualsiasi in esso. Il **Inserisci frammento di codice** comando deve comparire nel menu di scelta rapida.

## <a name="implement-snippet-expansion-in-the-snippet-picker-ui"></a>Implementare l'espansione del frammento nell'interfaccia utente selezione frammento di codice
 In questa sezione viene illustrato come implementare l'espansione dei frammenti di codice in modo che la selezione frammento di codice dell'interfaccia utente è visualizzato quando **Inserisci frammento di codice** si fa clic sul menu di scelta rapida. Un frammento di codice viene espanso anche quando un utente digita il collegamento del frammento di codice e quindi preme **scheda**.

 Per visualizzare la selezione frammento di codice dell'interfaccia utente e per abilitare la navigazione e l'accettazione di post-inserimento frammento, utilizzare il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> (metodo). Dell'operazione di inserimento è gestito dal <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> (metodo).

 L'implementazione di espansione dei frammenti di codice utilizza legacy <xref:Microsoft.VisualStudio.TextManager.Interop> interfacce. Quando si traducono dalle classi editor corrente al codice legacy, tenere presente che le interfacce legacy usano una combinazione di numeri di riga e colonna per specificare i percorsi in un buffer di testo, ma le classi correnti usano un solo indice. Pertanto, se un buffer con tre righe, ognuna delle quali dispone di 10 caratteri (più di una nuova riga, che viene considerata come un carattere), non è il quarto carattere nella terza riga nella posizione 27 nell'implementazione corrente, ma è alla riga 2, posizione 3 nell'implementazione precedente.

#### <a name="to-implement-snippet-expansion"></a>Per implementare l'espansione del frammento

1.  Il file che contiene il `TestCompletionCommandHandler` classe, aggiungere il codice seguente `using` istruzioni.

     [!code-csharp[VSSDKCompletionTest#26](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_5.cs)]
     [!code-vb[VSSDKCompletionTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_5.vb)]

2.  Verificare i `TestCompletionCommandHandler` implementano il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> interfaccia.

     [!code-csharp[VSSDKCompletionTest#27](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_6.cs)]
     [!code-vb[VSSDKCompletionTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_6.vb)]

3.  Nel `TestCompletionCommandHandlerProvider` classe, importare il <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>.

     [!code-csharp[VSSDKCompletionTest#28](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_7.cs)]
     [!code-vb[VSSDKCompletionTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_7.vb)]

4.  Aggiungere alcuni campi privati per le interfacce di espansione di codice e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.

     [!code-csharp[VSSDKCompletionTest#29](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_8.cs)]
     [!code-vb[VSSDKCompletionTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_8.vb)]

5.  Nel costruttore del `TestCompletionCommandHandler` classe, impostare i campi seguenti.

     [!code-csharp[VSSDKCompletionTest#30](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_9.cs)]
     [!code-vb[VSSDKCompletionTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_9.vb)]

6.  Per visualizzare la selezione frammento di codice quando l'utente fa clic il **Inserisci frammento** comando, aggiungere il codice seguente al <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> (metodo). (Per rendere più leggibile, questa spiegazione di `Exec()`codice che viene usato per il completamento delle istruzioni non vengono visualizzati; in alternativa, i blocchi di codice vengono aggiunti al metodo esistente.) Aggiungere il blocco di codice seguente dopo il codice che verifica la presenza di un carattere.

     [!code-csharp[VSSDKCompletionTest#31](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_10.cs)]
     [!code-vb[VSSDKCompletionTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_10.vb)]

7.  Se un frammento di codice include campi che possono essere esplorati, la sessione di espansione è tenuta aperta fino a quando l'espansione è accettata in modo esplicito. Se il frammento di codice non dispone di alcun campo, la sessione viene chiusa e viene restituita come `null` dal <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.InvokeInsertionUI%2A> (metodo). Nel <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metodo, dopo la selezione frammento di codice dell'interfaccia utente che è stato aggiunto nel passaggio precedente, aggiungere il codice seguente per gestire la navigazione di frammento di codice (quando l'utente preme **scheda** oppure **MAIUSC** + **Scheda** dopo l'inserimento del frammento).

     [!code-csharp[VSSDKCompletionTest#32](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_11.cs)]
     [!code-vb[VSSDKCompletionTest#32](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_11.vb)]

8.  Per inserire il frammento di codice quando l'utente digita la scelta rapida corrispondente e quindi preme **della scheda**, aggiungere il codice per il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> (metodo). Il metodo privato che inserisce il frammento di codice verrà visualizzato in un passaggio successivo. Aggiungere il codice seguente dopo il codice di navigazione che è stato aggiunto nel passaggio precedente.

     [!code-csharp[VSSDKCompletionTest#33](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_12.cs)]
     [!code-vb[VSSDKCompletionTest#33](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_12.vb)]

9. Implementare i metodi del <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> interfaccia. In questa implementazione, sono gli unici metodi di interesse <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.EndExpansion%2A> e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>. Gli altri metodi devono restituire semplicemente <xref:Microsoft.VisualStudio.VSConstants.S_OK>.

     [!code-csharp[VSSDKCompletionTest#34](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_13.cs)]
     [!code-vb[VSSDKCompletionTest#34](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_13.vb)]

10. Implementare il metodo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>. Il metodo helper che effettivamente inserisce le espansioni viene trattato in un passaggio successivo. Il <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> vengono fornite informazioni di riga e colonna, che è possibile ottenere dal <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.

     [!code-csharp[VSSDKCompletionTest#35](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_14.cs)]
     [!code-vb[VSSDKCompletionTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_14.vb)]

11. Il metodo privato seguente consente di inserire un frammento di codice, in base sia lo scelta rapida o il titolo e il percorso. Chiama quindi il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansion.InsertNamedExpansion%2A> metodo con il frammento di codice.

     [!code-csharp[VSSDKCompletionTest#36](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_15.cs)]
     [!code-vb[VSSDKCompletionTest#36](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_15.vb)]

## <a name="build-and-test-code-snippet-expansion"></a>Compilare e testare l'espansione dei frammenti di codice
 È possibile verificare il funzionamento di espansione del frammento di codice nel progetto.

1.  Compilare la soluzione. Quando si esegue questo progetto nel debugger, viene avviata una seconda istanza di Visual Studio.

2.  Aprire un file di testo e digitare un testo.

3.  Fare doppio clic in una posizione nel testo e quindi fare clic su **Inserisci frammento di codice**.

4.  Selezione frammento di codice dell'interfaccia utente deve essere visualizzato con una finestra popup con la dicitura **testare i campi di sostituzione**. Fare doppio clic sulla finestra popup.

     Deve essere inserito il frammento di codice seguente.

    ```
    MessageBox.Show("first");
    MessageBox.Show("second");
    ```

     Non premere **invio** oppure **Esc**.

5.  Premere **della scheda** e **MAIUSC**+**scheda** alternare tra "first" e "secondo".

6.  Accettare l'inserimento premendo **invio** oppure **Esc**.

7.  In un'altra parte del testo, digitare "test" e quindi premere **scheda**. Poiché "test" è il collegamento del frammento di codice, il frammento di codice deve essere inserito nuovamente.

## <a name="next-steps"></a>Passaggi successivi