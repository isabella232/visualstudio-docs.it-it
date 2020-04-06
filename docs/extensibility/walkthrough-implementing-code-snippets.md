---
title: 'Procedura dettagliata: implementazione di frammenti di codice WalkthroughWalkthrough: Implementing Code Snippets Documenti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: adbc5382-d170-441c-9fd0-80faa1816478
author: acangialosi
ms.author: anthc
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- vssdk
ms.openlocfilehash: ba1b6e0852c1ec1b306938b791eed78e79d211ce
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697104"
---
# <a name="walkthrough-implement-code-snippets"></a>Procedura dettagliata: Implementare frammenti di codiceWalkthrough: Implement code snippets
È possibile creare frammenti di codice e includerli in un'estensione dell'editor in modo che gli utenti dell'estensione possano aggiungerli al proprio codice.

 Un frammento di codice è un frammento di codice o altro testo che può essere incorporato in un file. Per visualizzare tutti i frammenti registrati per particolari linguaggi di programmazione, scegliere **Gestione frammenti di codice**dal menu **Strumenti** . Per inserire un frammento di codice in un file, fare clic con il pulsante destro del mouse nel punto in cui si desidera inserire il frammento, scegliere Inserisci frammento di codice o **Circonda con**, individuare il frammento desiderato e quindi fare doppio clic su di esso. Premere **TAB** o **MAIUSC**+**Tab** per modificare le parti rilevanti dello snippet, quindi premere **INVIO** o **ESC** per accettarlo. Per ulteriori informazioni, consultate [Frammenti di](../ide/code-snippets.md)codice.

 Un frammento di codice è contenuto in un file XML con estensione .snippet. Un frammento può contenere campi evidenziati dopo l'inserimento del frammento di codice in modo che l'utente possa trovarli e modificarli. Un file di frammento fornisce inoltre informazioni per **Gestione frammenti di codice** in modo che possa visualizzare il nome del frammento nella categoria corretta. Per informazioni sullo schema dei frammenti di codice, vedere Informazioni di [riferimento sullo schema dei frammenti](../ide/code-snippets-schema-reference.md)di codice .

 In questa procedura dettagliata viene illustrato come eseguire queste attività:This walkthrough teaches how to accomplish these tasks:

1. Creare e registrare frammenti di codice per un linguaggio specifico.

2. Aggiungere il comando **Inserisci frammento** di codice a un menu di scelta rapida.

3. Implementare l'espansione dei frammenti.

   Questa procedura dettagliata è basata su [Procedura dettagliata: completamento dell'istruzione Display](../extensibility/walkthrough-displaying-statement-completion.md).

## <a name="prerequisites"></a>Prerequisiti
 A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio.It's included as an optional feature in Visual Studio setup. È anche possibile installare l'SDK di VISUAL SMI in un secondo momento. Per ulteriori informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-and-register-code-snippets"></a>Creare e registrare frammenti di codiceCreate and register code snippets
 In genere, i frammenti di codice sono associati a un servizio di linguaggio registrato. Tuttavia, non è necessario <xref:Microsoft.VisualStudio.Package.LanguageService> implementare un per registrare i frammenti di codice. Al contrario, è sufficiente specificare un GUID nel <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> file di indice del frammento e quindi utilizzare lo stesso GUID nel file che si aggiunge al progetto.

 I passaggi seguenti illustrano come creare frammenti di codice e associarli a un GUID specifico.

1. Creare la struttura di directory seguente:

    **%InstallDir% , TestSnippets , Frammenti di codice , 1033\\**

    dove *%InstallDir%* è la cartella di installazione di Visual Studio. Sebbene questo percorso venga in genere utilizzato per installare frammenti di codice, è possibile specificare qualsiasi percorso.

2. Creare un file *XML* e denominarlo **TestSnippets.xml**. Anche se questo nome viene in genere utilizzato per un file di indice dei frammenti, è possibile specificare qualsiasi nome purché abbia estensione *xml.* Aggiungere il testo seguente, quindi eliminare il GUID segnaposto e aggiungerne uno personalizzato.

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

3. Creare un file nella cartella del frammento di codice, denominarlo **test**`.snippet`, quindi aggiungere il testo seguente:

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

   I passaggi seguenti illustrano come registrare i frammenti di codice.

### <a name="to-register-code-snippets-for-a-specific-guid"></a>Per registrare frammenti di codice per un GUID specificoTo register code snippets for a specific GUID

1. Aprire il progetto **CompletionTest.** Per informazioni su come creare questo progetto, vedere [Procedura dettagliata: completamento delle istruzioni display](../extensibility/walkthrough-displaying-statement-completion.md).

2. Nel progetto, aggiungere riferimenti ai seguenti assembly:

    - Microsoft.VisualStudio.TextManager.Interop

    - Microsoft.VisualStudio.TextManager.Interop.8.0

    - microsoft.msxml (informazioni in due: informazioni in base alle informazioni

3. Nel progetto aprire il file **source.extension.vsixmanifest.**

4. Assicurarsi che la scheda **Asset** contenga un tipo di contenuto **VsPackage** e che **Project** sia impostato sul nome del progetto.

5. Selezionare il progetto CompletionTest e nella finestra Proprietà impostare **Genera file Pkgdef** su **true**. Salvare il progetto.

6. Aggiungere una `SnippetUtilities` classe statica al progetto.

     [!code-csharp[VSSDKCompletionTest#22](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_1.cs)]
     [!code-vb[VSSDKCompletionTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_1.vb)]

7. Nella classe SnippetUtilities definire un GUID e assegnargli il valore utilizzato nel file *SnippetsIndex.xml.*

     [!code-csharp[VSSDKCompletionTest#23](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_2.cs)]
     [!code-vb[VSSDKCompletionTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_2.vb)]

8. Aggiungere <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> l'oggetto alla `TestCompletionHandler` classe. Questo attributo può essere aggiunto a qualsiasi classe pubblica o interna (non statica) nel progetto. Potrebbe essere necessario aggiungere `using` una direttiva per lo spazio dei nomi Microsoft.VisualStudio.Shell.

     [!code-csharp[VSSDKCompletionTest#24](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_3.cs)]
     [!code-vb[VSSDKCompletionTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_3.vb)]

9. Compilare ed eseguire il progetto. Nell'istanza sperimentale di Visual Studio che viene avviata quando viene eseguito il progetto, il frammento appena registrato deve essere visualizzato in **Gestione frammenti** di codice nel linguaggio **TestSnippets.**

## <a name="add-the-insert-snippet-command-to-the-shortcut-menu"></a>Aggiungere il comando Inserisci frammento di codice al menu di scelta rapida
 Il comando **Inserisci frammento** di codice non è incluso nel menu di scelta rapida per un file di testo. Pertanto, è necessario attivare il comando.

#### <a name="to-add-the-insert-snippet-command-to-the-shortcut-menu"></a>Per aggiungere il comando Inserisci frammento di codice al menu di scelta rapida

1. Aprire `TestCompletionCommandHandler` il file di classe.

     Poiché questa <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>classe implementa , è possibile <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> attivare il comando **Inserisci frammento** di codice nel metodo . Prima di abilitare il comando, verificare che questo metodo non venga chiamato all'interno di una funzione di automazione perché quando si fa clic sul comando **Inserisci frammento** di codice, viene visualizzata l'interfaccia utente di selezione frammento.

     [!code-csharp[VSSDKCompletionTest#25](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_4.cs)]
     [!code-vb[VSSDKCompletionTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_4.vb)]

2. Compilare ed eseguire il progetto. Nell'istanza sperimentale, aprire un file con estensione *.zzz* e quindi fare clic con il pulsante destro del mouse in un punto qualsiasi. Il comando **Inserisci frammento** di codice dovrebbe essere visualizzato nel menu di scelta rapida.

## <a name="implement-snippet-expansion-in-the-snippet-picker-ui"></a>Implementare l'espansione dei frammenti nell'interfaccia utente di Selezione frammentoImplement snippet expansion in the Snippet Picker UI
 Questa sezione illustra come implementare l'espansione del frammento di codice in modo che l'interfaccia utente di selezione frammento di codice viene visualizzata quando si fa clic su **Inserisci frammento** di codice nel menu di scelta rapida. Un frammento di codice viene espanso anche quando un utente digita il collegamento al frammento di codice e quindi preme **TAB**.

 Per visualizzare l'interfaccia utente di selezione frammento e <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> per abilitare la navigazione e l'accettazione del frammento di post-inserimento, usare il metodo . L'inserimento stesso viene <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> gestito dal metodo .

 L'implementazione dell'espansione <xref:Microsoft.VisualStudio.TextManager.Interop> del frammento di codice utilizza interfacce legacy. Quando si esegue la conversione dalle classi dell'editor corrente al codice legacy, tenere presente che le interfacce legacy utilizzano una combinazione di numeri di riga e di colonna per specificare le posizioni in un buffer di testo, ma le classi correnti utilizzano un indice. Pertanto, se un buffer ha tre righe ognuna delle quali ha 10 caratteri (più una nuova riga, che conta come un carattere), il quarto carattere nella terza riga si trova nella posizione 27 nell'implementazione corrente, ma si trova alla riga 2, posizione 3 nell'implementazione precedente.

#### <a name="to-implement-snippet-expansion"></a>Per implementare l'espansione dei frammenti

1. Al file che `TestCompletionCommandHandler` contiene la classe, aggiungere le direttive seguenti. `using`

     [!code-csharp[VSSDKCompletionTest#26](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_5.cs)]
     [!code-vb[VSSDKCompletionTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_5.vb)]

2. Fare `TestCompletionCommandHandler` in modo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> che la classe implementi l'interfaccia.

     [!code-csharp[VSSDKCompletionTest#27](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_6.cs)]
     [!code-vb[VSSDKCompletionTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_6.vb)]

3. Nella `TestCompletionCommandHandlerProvider` classe , <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>importare il file .

     [!code-csharp[VSSDKCompletionTest#28](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_7.cs)]
     [!code-vb[VSSDKCompletionTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_7.vb)]

4. Aggiungere alcuni campi privati per le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>interfacce di espansione del codice e il file .

     [!code-csharp[VSSDKCompletionTest#29](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_8.cs)]
     [!code-vb[VSSDKCompletionTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_8.vb)]

5. Nel costruttore `TestCompletionCommandHandler` della classe impostare i campi seguenti.

     [!code-csharp[VSSDKCompletionTest#30](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_9.cs)]
     [!code-vb[VSSDKCompletionTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_9.vb)]

6. Per visualizzare la selezione frammento di codice quando l'utente <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> fa clic sul comando Inserisci frammento di **codice,** aggiungere il codice seguente al metodo. Per rendere questa spiegazione più `Exec()`leggibile, il codice utilizzato per il completamento delle istruzioni non viene visualizzato, ma i blocchi di codice vengono aggiunti al metodo esistente. Aggiungere il seguente blocco di codice dopo il codice che verifica la presenza di un carattere.

     [!code-csharp[VSSDKCompletionTest#31](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_10.cs)]
     [!code-vb[VSSDKCompletionTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_10.vb)]

7. Se un frammento contiene campi che possono essere esplorati, la sessione di espansione viene mantenuta aperta fino a quando l'espansione non viene accettata in modo esplicito; se il frammento di codice non ha campi, la sessione viene chiusa e viene restituita come `null` dal <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.InvokeInsertionUI%2A> metodo. Nel <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metodo, dopo il codice dell'interfaccia utente di selezione frammento aggiunto nel passaggio precedente, aggiungi il codice seguente per gestire lo spostamento tra frammenti (quando l'utente preme **TAB** o **MAIUSC**+**dopo** l'inserimento del frammento).

     [!code-csharp[VSSDKCompletionTest#32](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_11.cs)]
     [!code-vb[VSSDKCompletionTest#32](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_11.vb)]

8. Per inserire il frammento di codice quando l'utente digita il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> collegamento corrispondente e quindi preme **TAB**, aggiungere codice al metodo . Il metodo privato che inserisce il frammento di codice verrà visualizzato in un passaggio successivo. Aggiungere il codice seguente dopo il codice di navigazione aggiunto nel passaggio precedente.

     [!code-csharp[VSSDKCompletionTest#33](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_12.cs)]
     [!code-vb[VSSDKCompletionTest#33](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_12.vb)]

9. Implementare i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> metodi dell'interfaccia. In questa attuazione, gli <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.EndExpansion%2A> unici <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>metodi di interesse sono e . Gli altri metodi <xref:Microsoft.VisualStudio.VSConstants.S_OK>devono restituire solo .

     [!code-csharp[VSSDKCompletionTest#34](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_13.cs)]
     [!code-vb[VSSDKCompletionTest#34](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_13.vb)]

10. Implementare il metodo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>. Il metodo helper che inserisce effettivamente le espansioni viene illustrato in un passaggio successivo. Fornisce <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> informazioni su righe e colonne, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>che è possibile ottenere dal file .

     [!code-csharp[VSSDKCompletionTest#35](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_14.cs)]
     [!code-vb[VSSDKCompletionTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_14.vb)]

11. Il metodo privato seguente inserisce un frammento di codice, in base al collegamento o al titolo e al percorso. Chiama quindi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansion.InsertNamedExpansion%2A> il metodo con il frammento di codice.

     [!code-csharp[VSSDKCompletionTest#36](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_15.cs)]
     [!code-vb[VSSDKCompletionTest#36](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_15.vb)]

## <a name="build-and-test-code-snippet-expansion"></a>Compilare e testare l'espansione del frammento di codiceBuild and test code snippet expansion
 È possibile verificare se l'espansione dei frammenti funziona nel progetto.

1. Compilare la soluzione. Quando si esegue questo progetto nel debugger, viene avviata una seconda istanza di Visual Studio.

2. Aprire un file di testo e digitare del testo.

3. Fare clic con il pulsante destro del mouse in un punto qualsiasi del testo e quindi **scegliere Inserisci frammento di codice**.

4. L'interfaccia utente di selezione frammento dovrebbe essere visualizzata con un popup che indica **Test campi di sostituzione**. Fare doppio clic sul popup.

     Deve essere inserito il frammento di codice seguente.

    ```
    MessageBox.Show("first");
    MessageBox.Show("second");
    ```

     Non premere **INVIO** o **ESC**.

5. Premere **TAB** e **MAIUSC**+**tab** per passare da "primo" a "secondo".

6. Accettare l'inserimento premendo **INVIO** o **Esc**.

7. In un'altra parte del testo digitare "test" e quindi premere **TAB**. Poiché "test" è il collegamento del frammento di codice, il frammento di codice deve essere inserito nuovamente.

## <a name="next-steps"></a>Passaggi successivi
