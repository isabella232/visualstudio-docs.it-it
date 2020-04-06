---
title: 'Procedura dettagliata: Visualizzazione delle descrizioni comandi delle informazioni rapide . Documenti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - QuickInfo
ms.assetid: 23fb8384-4f12-446f-977f-ce7910347947
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- csharp
- vb
ms.openlocfilehash: 47a14ca0692ad0338b56fd1d372307fb0e2ccc4c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697442"
---
# <a name="walkthrough-display-quickinfo-tooltips"></a>Procedura dettagliata: Visualizzare le descrizioni comandi di informazioni rapideWalkthrough: Display QuickInfo tooltips
Informazioni rapide è una funzionalità IntelliSense che visualizza le firme e le descrizioni dei metodi quando un utente sposta il puntatore sul nome di un metodo. È possibile implementare funzionalità basate sul linguaggio, ad esempio informazioni rapide, definendo gli identificatori per i quali si desidera fornire descrizioni di informazioni rapide e quindi creando una descrizione comando in cui visualizzare il contenuto. È possibile definire informazioni rapide nel contesto di un servizio di linguaggio oppure è possibile definire l'estensione di file e il tipo di contenuto e visualizzare le informazioni rapide solo per quel tipo oppure è possibile visualizzare informazioni rapide per un tipo di contenuto esistente (ad esempio "testo"). In questa procedura dettagliata viene illustrato come visualizzare informazioni rapide per il tipo di contenuto "testo".

 Nell'esempio di informazioni rapide in questa procedura dettagliata vengono visualizzate le descrizioni comandi quando un utente sposta il puntatore sul nome di un metodo. Questa progettazione richiede l'implementazione di queste quattro interfacce:This design requires you to implement these four interfaces:

- interfaccia di origine

- interfaccia del provider di origine

- interfaccia del controller

- interfaccia del provider del controller

  I provider di origine e controller sono parti del componente Managed Extensibility Framework (MEF) e sono responsabili <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>dell'esportazione delle classi di <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>origine e del controller e dell'importazione di servizi e broker, ad esempio il buffer di testo della descrizione comandi, e la , che attiva la sessione di informazioni rapide.

  In questo esempio, l'origine di informazioni rapide utilizza un elenco hardcoded di nomi e descrizioni di metodo, ma nelle implementazioni complete, il servizio di linguaggio e la documentazione del linguaggio sono responsabili della fornitura di tale contenuto.

## <a name="prerequisites"></a>Prerequisiti
 A partire da Visual Studio 2015, non è necessario installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio.It's included as an optional feature in Visual Studio setup. È anche possibile installare l'SDK di VISUAL SMI in un secondo momento. Per ulteriori informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-mef-project"></a>Creare un progetto MEF

### <a name="to-create-a-mef-project"></a>Per creare un progetto MEF

1. Creare un progetto VSIX di C. (Nella finestra di dialogo **Nuovo progetto,** selezionare **Visual Cè / Extensibility**, quindi **Progetto VSIX**. Denominare `QuickInfoTest`la soluzione .

2. Aggiungere un modello di elemento Classificatore editor al progetto. Per ulteriori informazioni, consultate [Creare un'estensione con un modello di elemento dell'editor.](../extensibility/creating-an-extension-with-an-editor-item-template.md)

3. Eliminare i file di classe esistenti.

## <a name="implement-the-quickinfo-source"></a>Implementare l'origine di informazioni rapideImplement the QuickInfo source
 L'origine di informazioni rapide è responsabile della raccolta del set di identificatori e delle relative descrizioni e dell'aggiunta del contenuto al buffer di testo della descrizione comandi quando viene rilevato uno degli identificatori. In questo esempio, gli identificatori e le relative descrizioni vengono appena aggiunti nel costruttore di origine.

#### <a name="to-implement-the-quickinfo-source"></a>Per implementare l'origine di informazioni rapide

1. Aggiungere un file di classe e assegnargli il nome `TestQuickInfoSource`.

2. Aggiungere un riferimento a *Microsoft.VisualStudio.Language.IntelliSense*.

3. Aggiungere le importazioni seguenti.

     [!code-vb[VSSDKQuickInfoTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_1.vb)]
     [!code-csharp[VSSDKQuickInfoTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_1.cs)]

4. Dichiarare una classe <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>che implementa `TestQuickInfoSource`, quindi denominarla .

     [!code-vb[VSSDKQuickInfoTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_2.vb)]
     [!code-csharp[VSSDKQuickInfoTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_2.cs)]

5. Aggiungere campi per il provider di origine di informazioni rapide, il buffer di testo e un set di nomi di metodi e firme di metodo. In questo esempio, i nomi e le `TestQuickInfoSource` firme dei metodi vengono inizializzati nel costruttore.

     [!code-vb[VSSDKQuickInfoTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_3.vb)]
     [!code-csharp[VSSDKQuickInfoTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_3.cs)]

6. Aggiungere un costruttore che imposta il provider di origine di informazioni rapide e il buffer di testo e popola il set di nomi di metodo e le firme e le descrizioni dei metodi.

     [!code-vb[VSSDKQuickInfoTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_4.vb)]
     [!code-csharp[VSSDKQuickInfoTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_4.cs)]

7. Implementare il metodo <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A>. In questo esempio, il metodo trova la parola corrente o la parola precedente se il cursore si trova alla fine di una riga o di un buffer di testo. Se la parola è uno dei nomi di metodo, la descrizione del nome del metodo viene aggiunta al contenuto delle informazioni rapide.

     [!code-vb[VSSDKQuickInfoTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_5.vb)]
     [!code-csharp[VSSDKQuickInfoTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_5.cs)]

8. È inoltre necessario implementare un <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> <xref:System.IDisposable>metodo Dispose(), poiché implements :

     [!code-vb[VSSDKQuickInfoTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_6.vb)]
     [!code-csharp[VSSDKQuickInfoTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_6.cs)]

## <a name="implement-a-quickinfo-source-provider"></a>Implementare un provider di origine di informazioni rapideImplement a QuickInfo source provider
 Il provider dell'origine di informazioni rapide serve principalmente per esportare se stesso come parte del componente MEF e creare un'istanza dell'origine di informazioni rapide. Poiché è una parte componente MEF, è possibile importare altre parti del componente MEF.

#### <a name="to-implement-a-quickinfo-source-provider"></a>Per implementare un provider di origine di informazioni rapideTo implement a QuickInfo source provider

1. Dichiarare un provider di `TestQuickInfoSourceProvider` origine <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>di informazioni rapide <xref:Microsoft.VisualStudio.Utilities.NameAttribute> denominato che implementa ed esportarlo con un'origine "ToolTip QuickInfo Source", una <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> di Before : "default" e un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> di "text".

     [!code-vb[VSSDKQuickInfoTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_7.vb)]
     [!code-csharp[VSSDKQuickInfoTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_7.cs)]

2. Importare due servizi <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>editor e `TestQuickInfoSourceProvider`, come proprietà di .

     [!code-vb[VSSDKQuickInfoTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_8.vb)]
     [!code-csharp[VSSDKQuickInfoTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_8.cs)]

3. Implementare <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A> per `TestQuickInfoSource`restituire un nuovo file .

     [!code-vb[VSSDKQuickInfoTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_9.vb)]
     [!code-csharp[VSSDKQuickInfoTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_9.cs)]

## <a name="implement-a-quickinfo-controller"></a>Implementare un controller di informazioni rapideImplement a QuickInfo controller
 I controller di informazioni rapide determinano quando viene visualizzata l'informazione rapida. In questo esempio, informazioni rapide viene visualizzato quando il puntatore è posizionato su una parola che corrisponde a uno dei nomi di metodo. Il controller di informazioni rapide implementa un gestore dell'evento di passaggio del mouse che attiva una sessione di informazioni rapide.

### <a name="to-implement-a-quickinfo-controller"></a>Per implementare un controller di informazioni rapideTo implement a QuickInfo controller

1. Dichiarare una classe <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController>che implementa `TestQuickInfoController`, quindi denominarla .

     [!code-vb[VSSDKQuickInfoTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_10.vb)]
     [!code-csharp[VSSDKQuickInfoTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_10.cs)]

2. Aggiungere campi privati per la visualizzazione di testo, i buffer di testo rappresentati nella visualizzazione di testo, la sessione di informazioni rapide e il provider del controller di informazioni rapide.

     [!code-vb[VSSDKQuickInfoTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_11.vb)]
     [!code-csharp[VSSDKQuickInfoTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_11.cs)]

3. Aggiungere un costruttore che imposta i campi e aggiunge il gestore dell'evento di passaggio del mouse.

     [!code-vb[VSSDKQuickInfoTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_12.vb)]
     [!code-csharp[VSSDKQuickInfoTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_12.cs)]

4. Aggiungere il gestore dell'evento di passaggio del mouse che attiva la sessione di informazioni rapide.

     [!code-vb[VSSDKQuickInfoTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_13.vb)]
     [!code-csharp[VSSDKQuickInfoTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_13.cs)]

5. Implementare <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A> il metodo in modo che rimuova il gestore eventi di passaggio del mouse quando il controller viene scollegato dalla visualizzazione di testo.

     [!code-vb[VSSDKQuickInfoTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_14.vb)]
     [!code-csharp[VSSDKQuickInfoTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_14.cs)]

6. Implementare <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A> il <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A> metodo e il metodo come metodi vuoti per questo esempio.

     [!code-vb[VSSDKQuickInfoTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_15.vb)]
     [!code-csharp[VSSDKQuickInfoTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_15.cs)]

## <a name="implementing-the-quickinfo-controller-provider"></a>Implementazione del provider del controller di informazioni rapideImplementing the QuickInfo controller provider
 Il provider del controller di informazioni rapide serve principalmente per esportare se stesso come parte del componente MEF e creare un'istanza del controller di informazioni rapide. Poiché è una parte componente MEF, è possibile importare altre parti del componente MEF.

### <a name="to-implement-the-quickinfo-controller-provider"></a>Per implementare il provider del controller di informazioni rapideTo implement the QuickInfo controller provider

1. Dichiarare una `TestQuickInfoControllerProvider` classe <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider>denominata che implementa <xref:Microsoft.VisualStudio.Utilities.NameAttribute> ed esportarla con un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "ToolTip QuickInfo Controller" e un "text":

     [!code-vb[VSSDKQuickInfoTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_16.vb)]
     [!code-csharp[VSSDKQuickInfoTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_16.cs)]

2. Importare <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> come proprietà.

     [!code-vb[VSSDKQuickInfoTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_17.vb)]
     [!code-csharp[VSSDKQuickInfoTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_17.cs)]

3. Implementare <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A> il metodo mediante la creazione di un'istanza del controller di informazioni rapide.

     [!code-vb[VSSDKQuickInfoTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_18.vb)]
     [!code-csharp[VSSDKQuickInfoTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_18.cs)]

## <a name="build-and-test-the-code"></a>Compilare e testare il codiceBuild and test the Code
 Per testare questo codice, compilare la soluzione QuickInfoTest ed eseguirla nell'istanza sperimentale.

### <a name="to-build-and-test-the-quickinfotest-solution"></a>Per compilare e testare la soluzione QuickInfoTest

1. Compilare la soluzione.

2. Quando si esegue questo progetto nel debugger, viene avviata una seconda istanza di Visual Studio.

3. Creare un file di testo e digitare del testo che includa le parole "add" e "subtract".

4. Spostare il puntatore su una delle occorrenze di "add". Verranno visualizzate la `add` firma e la descrizione del metodo.

## <a name="see-also"></a>Vedere anche
- [Procedura dettagliata: Collegare un tipo di contenuto a un'estensione di fileWalkthrough: Link a content type to a file name extension](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
