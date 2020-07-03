---
title: 'Procedura dettagliata: visualizzazione di descrizioni comandi di informazioni rapide | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 0eb70e5d39708ffd532fe39d6d597043621158d5
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2020
ms.locfileid: "85904835"
---
# <a name="walkthrough-display-quickinfo-tooltips"></a>Procedura dettagliata: visualizzare le descrizioni comandi di informazioni rapide
Informazioni rapide è una funzionalità di IntelliSense che visualizza le firme e le descrizioni dei metodi quando un utente sposta il puntatore del mouse su un nome di metodo. È possibile implementare funzionalità basate su linguaggio, ad esempio informazioni rapide, definendo gli identificatori per i quali si desidera fornire descrizioni informazioni rapide e quindi creare una descrizione comando in cui visualizzare il contenuto. È possibile definire informazioni rapide nel contesto di un servizio di linguaggio oppure è possibile definire l'estensione del nome di file e il tipo di contenuto e visualizzare il informazioni rapide per solo quel tipo oppure è possibile visualizzare informazioni rapide per un tipo di contenuto esistente, ad esempio "Text". Questa procedura dettagliata illustra come visualizzare informazioni rapide per il tipo di contenuto "Text".

 Nell'esempio informazioni rapide in questa procedura dettagliata vengono visualizzate le descrizioni comandi quando un utente sposta il puntatore del mouse su un nome di metodo. Per questa progettazione è necessario implementare le quattro interfacce seguenti:

- interfaccia di origine

- interfaccia del provider di origine

- interfaccia controller

- interfaccia del provider controller

  I provider di origine e di controller sono componenti Managed Extensibility Framework (MEF) e sono responsabili dell'esportazione delle classi di origine e del controller e dell'importazione di servizi e broker, ad esempio <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> , che crea il buffer di testo della descrizione comando e <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> , che attiva la sessione informazioni rapide.

  In questo esempio l'origine informazioni rapide usa un elenco hardcoded di nomi e descrizioni di metodi, ma nelle implementazioni complete il servizio di linguaggio e la documentazione della lingua sono responsabili di fornire tale contenuto.

## <a name="prerequisites"></a>Prerequisiti
 A partire da Visual Studio 2015, non è necessario installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare Visual Studio SDK in un secondo momento. Per altre informazioni, vedere [installare Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Creare un progetto MEF

### <a name="to-create-a-mef-project"></a>Per creare un progetto MEF

1. Creare un progetto VSIX in C#. Nella finestra di dialogo **nuovo progetto** selezionare **Visual C#/extensibility**, quindi **progetto VSIX**. Assegnare un nome alla soluzione `QuickInfoTest` .

2. Aggiungere un modello di elemento classificatore editor al progetto. Per altre informazioni, vedere [creare un'estensione con un modello di elemento dell'editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Eliminare i file di classe esistenti.

## <a name="implement-the-quickinfo-source"></a>Implementare l'origine informazioni rapide
 L'origine informazioni rapide è responsabile della raccolta del set di identificatori e delle relative descrizioni e dell'aggiunta del contenuto al buffer di testo della descrizione comando quando viene rilevato uno degli identificatori. In questo esempio, gli identificatori e le relative descrizioni vengono aggiunti solo nel costruttore di origine.

#### <a name="to-implement-the-quickinfo-source"></a>Per implementare l'origine informazioni rapide

1. Aggiungere un file di classe e assegnargli il nome `TestQuickInfoSource`.

2. Aggiungere un riferimento a *Microsoft. VisualStudio. Language. IntelliSense*.

3. Aggiungere le importazioni seguenti.

     [!code-vb[VSSDKQuickInfoTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_1.vb)]
     [!code-csharp[VSSDKQuickInfoTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_1.cs)]

4. Dichiarare una classe che implementa <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> e denominarla `TestQuickInfoSource` .

     [!code-vb[VSSDKQuickInfoTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_2.vb)]
     [!code-csharp[VSSDKQuickInfoTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_2.cs)]

5. Aggiungere campi per il provider di origine informazioni rapide, il buffer di testo e un set di nomi di metodo e firme di metodi. In questo esempio, i nomi e le firme del metodo vengono inizializzati nel `TestQuickInfoSource` costruttore.

     [!code-vb[VSSDKQuickInfoTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_3.vb)]
     [!code-csharp[VSSDKQuickInfoTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_3.cs)]

6. Aggiungere un costruttore che imposta il provider di origine informazioni rapide e il buffer di testo e popola il set di nomi di metodo e le firme e le descrizioni dei metodi.

     [!code-vb[VSSDKQuickInfoTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_4.vb)]
     [!code-csharp[VSSDKQuickInfoTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_4.cs)]

7. Implementare il metodo <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A>. In questo esempio, il metodo trova la parola corrente o la parola precedente se il cursore si trova alla fine di una riga o di un buffer di testo. Se la parola è uno dei nomi di metodo, la descrizione per il nome del metodo viene aggiunta al contenuto informazioni rapide.

     [!code-vb[VSSDKQuickInfoTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_5.vb)]
     [!code-csharp[VSSDKQuickInfoTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_5.cs)]

8. È inoltre necessario implementare un metodo Dispose (), poiché <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> implementa <xref:System.IDisposable> :

     [!code-vb[VSSDKQuickInfoTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_6.vb)]
     [!code-csharp[VSSDKQuickInfoTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_6.cs)]

## <a name="implement-a-quickinfo-source-provider"></a>Implementare un provider di origine informazioni rapide
 Il provider dell'origine informazioni rapide serve principalmente per esportarsi come parte del componente MEF e creare un'istanza dell'origine informazioni rapide. Poiché si tratta di una parte del componente MEF, può importare altre parti del componente MEF.

#### <a name="to-implement-a-quickinfo-source-provider"></a>Per implementare un provider di origine informazioni rapide

1. Dichiarare un provider di origine informazioni rapide denominato `TestQuickInfoSourceProvider` che implementa <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider> ed esportarlo con un oggetto <xref:Microsoft.VisualStudio.Utilities.NameAttribute> di "ToolTip informazioni rapide source", <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> di before = "default" e <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> di "Text".

     [!code-vb[VSSDKQuickInfoTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_7.vb)]
     [!code-csharp[VSSDKQuickInfoTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_7.cs)]

2. Importare due servizi dell'editor, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> e <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> , come proprietà di `TestQuickInfoSourceProvider` .

     [!code-vb[VSSDKQuickInfoTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_8.vb)]
     [!code-csharp[VSSDKQuickInfoTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_8.cs)]

3. Implementare <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A> per restituire un nuovo oggetto `TestQuickInfoSource` .

     [!code-vb[VSSDKQuickInfoTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_9.vb)]
     [!code-csharp[VSSDKQuickInfoTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_9.cs)]

## <a name="implement-a-quickinfo-controller"></a>Implementare un controller informazioni rapide
 I controller informazioni rapide determinano quando viene visualizzato informazioni rapide. In questo esempio, informazioni rapide viene visualizzato quando il puntatore è posizionato su una parola che corrisponde a uno dei nomi di metodo. Il controller informazioni rapide implementa un gestore eventi di passaggio del mouse che attiva una sessione informazioni rapide.

### <a name="to-implement-a-quickinfo-controller"></a>Per implementare un controller informazioni rapide

1. Dichiarare una classe che implementa <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> e denominarla `TestQuickInfoController` .

     [!code-vb[VSSDKQuickInfoTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_10.vb)]
     [!code-csharp[VSSDKQuickInfoTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_10.cs)]

2. Aggiungere campi privati per la visualizzazione di testo, i buffer di testo rappresentati nella visualizzazione di testo, la sessione informazioni rapide e il provider del controller informazioni rapide.

     [!code-vb[VSSDKQuickInfoTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_11.vb)]
     [!code-csharp[VSSDKQuickInfoTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_11.cs)]

3. Aggiungere un costruttore che imposta i campi e aggiunge il gestore dell'evento di passaggio del mouse.

     [!code-vb[VSSDKQuickInfoTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_12.vb)]
     [!code-csharp[VSSDKQuickInfoTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_12.cs)]

4. Aggiungere il gestore eventi di passaggio del mouse che attiva la sessione informazioni rapide.

     [!code-vb[VSSDKQuickInfoTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_13.vb)]
     [!code-csharp[VSSDKQuickInfoTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_13.cs)]

5. Implementare il <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A> metodo in modo che rimuova il gestore dell'evento di passaggio del mouse quando il controller viene scollegato dalla visualizzazione di testo.

     [!code-vb[VSSDKQuickInfoTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_14.vb)]
     [!code-csharp[VSSDKQuickInfoTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_14.cs)]

6. Implementare il <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A> metodo e il <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A> metodo come metodi vuoti per questo esempio.

     [!code-vb[VSSDKQuickInfoTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_15.vb)]
     [!code-csharp[VSSDKQuickInfoTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_15.cs)]

## <a name="implementing-the-quickinfo-controller-provider"></a>Implementazione del provider del controller informazioni rapide
 Il provider del controller informazioni rapide serve principalmente per esportarsi come parte del componente MEF e creare un'istanza del controller informazioni rapide. Poiché si tratta di una parte del componente MEF, può importare altre parti del componente MEF.

### <a name="to-implement-the-quickinfo-controller-provider"></a>Per implementare il provider del controller informazioni rapide

1. Dichiarare una classe denominata `TestQuickInfoControllerProvider` che implementa <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider> ed esportarla con una <xref:Microsoft.VisualStudio.Utilities.NameAttribute> di "ToolTip informazioni rapide controller" e un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> di "Text":

     [!code-vb[VSSDKQuickInfoTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_16.vb)]
     [!code-csharp[VSSDKQuickInfoTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_16.cs)]

2. Importare <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> come proprietà.

     [!code-vb[VSSDKQuickInfoTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_17.vb)]
     [!code-csharp[VSSDKQuickInfoTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_17.cs)]

3. Implementare il <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A> Metodo creando un'istanza del controller informazioni rapide.

     [!code-vb[VSSDKQuickInfoTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_18.vb)]
     [!code-csharp[VSSDKQuickInfoTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_18.cs)]

## <a name="build-and-test-the-code"></a>Compilare e testare il codice
 Per testare questo codice, compilare la soluzione QuickInfoTest ed eseguirla nell'istanza sperimentale.

### <a name="to-build-and-test-the-quickinfotest-solution"></a>Per compilare e testare la soluzione QuickInfoTest

1. Compilare la soluzione.

2. Quando si esegue questo progetto nel debugger, viene avviata una seconda istanza di Visual Studio.

3. Creare un file di testo e digitare il testo che include le parole "Add" e "Subtract".

4. Spostare il puntatore su una delle occorrenze di "Add". Verrà visualizzata la firma e la descrizione del `add` metodo.

## <a name="see-also"></a>Vedere anche
- [Procedura dettagliata: collegare un tipo di contenuto a un'estensione di file](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
