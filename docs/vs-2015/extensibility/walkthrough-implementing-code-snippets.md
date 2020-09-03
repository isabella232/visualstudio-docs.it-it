---
title: 'Procedura dettagliata: implementazione di frammenti di codice | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: adbc5382-d170-441c-9fd0-80faa1816478
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cb720589bc9bc31b7cf2a04b05559cb9c9d46961
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201987"
---
# <a name="walkthrough-implementing-code-snippets"></a>Procedura dettagliata: implementazione di frammenti di codice
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile creare frammenti di codice e includerli in un'estensione dell'editor in modo che gli utenti dell'estensione possano aggiungerli al proprio codice.  
  
 Un frammento di codice è un frammento di codice o altro testo che può essere incorporato in un file. Per visualizzare tutti i frammenti di codice registrati per determinati linguaggi di programmazione, scegliere **Gestione frammenti di codice**dal menu **strumenti** . Per inserire un frammento di codice in un file, fare clic con il pulsante destro del mouse sul punto in cui si desidera il frammento, scegliere **Inserisci frammento** o **Racchiudi**tra, individuare il frammento desiderato, quindi fare doppio clic su di esso. Premere TAB o MAIUSC + TAB per modificare le parti pertinenti del frammento, quindi premere INVIO o ESC per accettarlo. Per altre informazioni, vedere [Code Snippets](../ide/code-snippets.md) (Frammenti di codice).  
  
 Un frammento di codice è contenuto in un file XML con estensione del nome di file. snippet. Un frammento può contenere campi che vengono evidenziati dopo l'inserimento del frammento, in modo che l'utente possa trovarli e modificarli. Un file di frammento fornisce inoltre informazioni per **Gestione frammenti di codice** in modo che sia in grado di visualizzare il nome del frammento nella categoria corretta. Per informazioni sullo schema del frammento di [codice, vedere riferimenti allo schema dei frammenti di codice](../ide/code-snippets-schema-reference.md).  
  
 Questa procedura dettagliata illustra come eseguire queste attività:  
  
1. Creare e registrare frammenti di codice per una lingua specifica.  
  
2. Aggiungere il comando **Inserisci frammento** a un menu di scelta rapida.  
  
3. Implementare l'espansione del frammento.  
  
   Questa procedura dettagliata è basata su [procedura dettagliata: visualizzazione del completamento delle istruzioni](../extensibility/walkthrough-displaying-statement-completion.md).  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. Viene inclusa come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare Visual Studio SDK in un secondo momento. Per ulteriori informazioni, vedere [installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-and-registering-code-snippets"></a>Creazione e registrazione di frammenti di codice  
 In genere, i frammenti di codice sono associati a un servizio di linguaggio registrato. Tuttavia, non è necessario implementare un <xref:Microsoft.VisualStudio.Package.LanguageService> per registrare i frammenti di codice. In alternativa, è sufficiente specificare un GUID nel file di indice del frammento e quindi usare lo stesso GUID nell'oggetto <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> aggiunto al progetto.  
  
 Nei passaggi seguenti viene illustrato come creare frammenti di codice e associarli a un GUID specifico.  
  
1. Creare la struttura di directory seguente:  
  
    **%InstallDir%\TestSnippets\Snippets\1033\\**  
  
    dove *% InstallDir%* è la cartella di installazione di Visual Studio. Sebbene questo percorso venga in genere utilizzato per installare frammenti di codice, è possibile specificare qualsiasi percorso.  
  
2. Nella cartella \ 1033 \ creare un file con estensione XML e denominarlo **TestSnippets.xml**. Sebbene questo nome venga in genere utilizzato per un file di indice del frammento, è possibile specificare qualsiasi nome purché disponga di un'estensione di file XML. Aggiungere il testo seguente e quindi eliminare il GUID segnaposto e aggiungere il proprio.  
  
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
  
3. Creare un file nella cartella snippet, denominarlo **test** `.snippet` , quindi aggiungere il testo seguente:  
  
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
  
   Nei passaggi seguenti viene illustrato come registrare i frammenti di codice.  
  
#### <a name="to-register-code-snippets-for-a-specific-guid"></a>Per registrare i frammenti di codice per un GUID specifico  
  
1. Aprire il progetto **CompletionTest** . Per informazioni su come creare questo progetto, vedere [procedura dettagliata: visualizzazione del completamento delle istruzioni](../extensibility/walkthrough-displaying-statement-completion.md).  
  
2. Nel progetto aggiungere i riferimenti agli assembly seguenti:  
  
    - Microsoft. VisualStudio. TextManager. Interop  
  
    - Microsoft. VisualStudio. TextManager. Interop. 8.0  
  
    - Microsoft. MSXML  
  
3. Nel progetto aprire il file source. Extension. vsixmanifest.  
  
4. Verificare che la scheda **Asset** contenga un tipo di contenuto **VSPackage** e che il **progetto** sia impostato sul nome del progetto.  
  
5. Selezionare il progetto CompletionTest e nella Finestra Proprietà impostare **genera pkgdef file** su **true**. Salvare il progetto.  
  
6. Aggiungere una `SnippetUtilities` classe statica al progetto.  
  
     [!code-csharp[VSSDKCompletionTest#22](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#22)]
     [!code-vb[VSSDKCompletionTest#22](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#22)]  
  
7. Nella classe SnippetUtilities definire un GUID e assegnargli il valore usato nel file di SnippetsIndex.xml.  
  
     [!code-csharp[VSSDKCompletionTest#23](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#23)]
     [!code-vb[VSSDKCompletionTest#23](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#23)]  
  
8. Aggiungere alla <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> `TestCompletionHandler` classe. Questo attributo può essere aggiunto a qualsiasi classe pubblica o interna (non statica) nel progetto. Potrebbe essere necessario aggiungere un' `using` istruzione per lo spazio dei nomi Microsoft. VisualStudio. Shell.  
  
     [!code-csharp[VSSDKCompletionTest#24](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#24)]
     [!code-vb[VSSDKCompletionTest#24](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#24)]  
  
9. Compilare ed eseguire il progetto. Nell'istanza sperimentale di Visual Studio che inizia quando viene eseguito il progetto, il frammento appena registrato dovrebbe essere visualizzato in **Gestione frammenti di codice** nel linguaggio **TestSnippets** .  
  
## <a name="adding-the-insert-snippet-command-to-the-shortcut-menu"></a>Aggiunta del comando Insert Snippet al menu di scelta rapida  
 Il comando **Inserisci frammento** non è incluso nel menu di scelta rapida per un file di testo. Pertanto, è necessario abilitare il comando.  
  
#### <a name="to-add-the-insert-snippet-command-to-the-shortcut-menu"></a>Per aggiungere il comando Inserisci frammento al menu di scelta rapida  
  
1. Aprire il `TestCompletionCommandHandler` file di classe.  
  
     Poiché questa classe implementa <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> , è possibile attivare il comando **Inserisci frammento** nel <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodo. Prima di abilitare il comando, verificare che questo metodo non venga chiamato all'interno di una funzione di automazione perché, quando si fa clic sul comando **Inserisci frammento** , viene visualizzata l'interfaccia utente di selezione frammenti di codice.  
  
     [!code-csharp[VSSDKCompletionTest#25](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#25)]
     [!code-vb[VSSDKCompletionTest#25](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#25)]  
  
2. Compilare ed eseguire il progetto. Nell'istanza sperimentale aprire un file con estensione ZZZ e quindi fare clic con il pulsante destro del mouse in un punto qualsiasi all'interno. Il comando **Inserisci frammento** verrà visualizzato nel menu di scelta rapida.  
  
## <a name="implementing-snippet-expansion-in-the-snippet-picker-ui"></a>Implementazione dell'espansione del frammento nell'interfaccia utente di selezione frammenti  
 Questa sezione illustra come implementare l'espansione dei frammenti di codice in modo che l'interfaccia utente di selezione frammenti venga visualizzata quando si fa clic su **Inserisci frammento** di codice nel menu di scelta rapida. Un frammento di codice viene espanso anche quando un utente digita il collegamento dei frammenti di codice e quindi preme TAB.  
  
 Per visualizzare l'interfaccia utente della selezione frammenti e per abilitare l'accettazione dello spostamento e del frammento di post-inserimento, utilizzare il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metodo. L'inserimento stesso viene gestito dal <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> metodo.  
  
 L'implementazione dell'espansione del frammento di codice usa <xref:Microsoft.VisualStudio.TextManager.Interop> interfacce legacy. Quando si esegue la conversione dalle classi editor correnti al codice legacy, tenere presente che le interfacce legacy utilizzano una combinazione di numeri di riga e di colonna per specificare le posizioni in un buffer di testo, ma le classi correnti utilizzano un solo indice. Se, pertanto, un buffer ha tre righe, ognuna delle quali ha dieci caratteri, più una nuova riga, che viene conteggiata come 1 carattere, il quarto carattere nella terza riga si trova nella posizione 27 nell'implementazione corrente, ma è alla riga 2, posizione 3 nell'implementazione precedente.  
  
#### <a name="to-implement-snippet-expansion"></a>Per implementare l'espansione del frammento  
  
1. Aggiungere le istruzioni seguenti al file che contiene la `TestCompletionCommandHandler` classe `using` .  
  
     [!code-csharp[VSSDKCompletionTest#26](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#26)]
     [!code-vb[VSSDKCompletionTest#26](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#26)]  
  
2. Fare in modo che la `TestCompletionCommandHandler` classe implementi l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> interfaccia.  
  
     [!code-csharp[VSSDKCompletionTest#27](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#27)]
     [!code-vb[VSSDKCompletionTest#27](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#27)]  
  
3. Nella `TestCompletionCommandHandlerProvider` classe importare il <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> .  
  
     [!code-csharp[VSSDKCompletionTest#28](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#28)]
     [!code-vb[VSSDKCompletionTest#28](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#28)]  
  
4. Aggiungere alcuni campi privati per le interfacce di espansione del codice e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .  
  
     [!code-csharp[VSSDKCompletionTest#29](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#29)]
     [!code-vb[VSSDKCompletionTest#29](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#29)]  
  
5. Nel costruttore della `TestCompletionCommandHandler` classe impostare i campi seguenti.  
  
     [!code-csharp[VSSDKCompletionTest#30](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#30)]
     [!code-vb[VSSDKCompletionTest#30](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#30)]  
  
6. Per visualizzare la selezione frammenti quando l'utente fa clic sul comando **Inserisci frammento** , aggiungere il codice seguente al <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metodo. Per rendere più leggibile questa spiegazione, il codice Exec () utilizzato per il completamento delle istruzioni non viene visualizzato, bensì i blocchi di codice vengono aggiunti al metodo esistente. Aggiungere il blocco di codice seguente dopo il codice che verifica la presenza di un carattere.  
  
     [!code-csharp[VSSDKCompletionTest#31](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#31)]
     [!code-vb[VSSDKCompletionTest#31](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#31)]  
  
7. Se un frammento contiene campi che possono essere spostati, la sessione di espansione viene mantenuta aperta fino a quando l'espansione non viene accettata in modo esplicito; Se il frammento non contiene campi, la sessione viene chiusa e viene restituita come `null` dal <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.InvokeInsertionUI%2A> metodo. Nel <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metodo, dopo il codice dell'interfaccia utente della selezione frammenti aggiunto nel passaggio precedente, aggiungere il codice seguente per gestire la navigazione dei frammenti (quando l'utente preme TAB o MAIUSC + TAB dopo l'inserimento del frammento).  
  
     [!code-csharp[VSSDKCompletionTest#32](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#32)]
     [!code-vb[VSSDKCompletionTest#32](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#32)]  
  
8. Per inserire il frammento di codice quando l'utente digita il collegamento corrispondente e quindi preme TAB, aggiungere il codice al <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metodo. Il metodo privato che inserisce il frammento verrà visualizzato in un passaggio successivo. Aggiungere il codice seguente dopo il codice di navigazione aggiunto nel passaggio precedente.  
  
     [!code-csharp[VSSDKCompletionTest#33](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#33)]
     [!code-vb[VSSDKCompletionTest#33](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#33)]  
  
9. Implementare i metodi dell' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> interfaccia. In questa implementazione, gli unici metodi di interesse sono <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.EndExpansion%2A> e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> . Gli altri metodi devono solo restituire <xref:Microsoft.VisualStudio.VSConstants.S_OK> .  
  
     [!code-csharp[VSSDKCompletionTest#34](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#34)]
     [!code-vb[VSSDKCompletionTest#34](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#34)]  
  
10. Implementare il metodo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>. Il metodo helper che inserisce effettivamente le espansioni verrà trattato in un passaggio successivo. <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan>Fornisce informazioni su righe e colonne, che è possibile ottenere da <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .  
  
     [!code-csharp[VSSDKCompletionTest#35](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#35)]
     [!code-vb[VSSDKCompletionTest#35](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#35)]  
  
11. Il metodo privato seguente inserisce un frammento di codice, basato sul collegamento o sul titolo e sul percorso. Chiama quindi il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansion.InsertNamedExpansion%2A> metodo con il frammento.  
  
     [!code-csharp[VSSDKCompletionTest#36](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#36)]
     [!code-vb[VSSDKCompletionTest#36](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#36)]  
  
## <a name="building-and-testing-code-snippet-expansion"></a>Compilazione e test dell'espansione del frammento di codice  
 È possibile verificare se l'espansione del frammento di codice funziona nel progetto.  
  
1. Compilare la soluzione. Quando si esegue questo progetto nel debugger, viene creata una seconda istanza di Visual Studio.  
  
2. Aprire un file di testo e digitare il testo.  
  
3. Fare clic con il pulsante destro del mouse in un punto qualsiasi del testo e quindi scegliere **Inserisci frammento**.  
  
4. L'interfaccia utente di selezione frammenti dovrebbe essere visualizzata con un popup che indica i **campi di sostituzione dei test**. Fare doppio clic sulla finestra popup.  
  
     Inserire il frammento di codice seguente.  
  
    ```  
    MessageBox.Show("first");  
    MessageBox.Show("second");  
    ```  
  
     Non premere INVIO o ESC.  
  
5. Premere TAB e MAIUSC + TAB per passare tra "First" e "Second".  
  
6. Accettare l'inserimento premendo invio o ESC.  
  
7. In una parte diversa del testo digitare "test", quindi premere TAB. Poiché "test" è il collegamento dei frammenti di codice, il frammento di codice deve essere inserito nuovamente.  
  
## <a name="next-steps"></a>Passaggi successivi
