---
title: 'Procedura dettagliata: Visualizzazione di descrizioni comando di informazioni rapide | Microsoft Docs'
description: Informazioni su come visualizzare informazioni rapide per il contenuto di testo usando questa procedura dettagliata. Informazioni rapide visualizza le firme e le descrizioni dei metodi per un nome di metodo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - QuickInfo
ms.assetid: 23fb8384-4f12-446f-977f-ce7910347947
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
dev_langs:
- csharp
- vb
ms.openlocfilehash: 6039f8a3bbdc2f2263886486b3be17ec3e0b5053
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122049051"
---
# <a name="walkthrough-display-quickinfo-tooltips"></a>Procedura dettagliata: Visualizzare le descrizioni comando di Informazioni rapide
QuickInfo è una funzionalità intelliSense che visualizza le firme e le descrizioni dei metodi quando un utente sposta il puntatore su un nome di metodo. È possibile implementare funzionalità basate sulla lingua, ad esempio Informazioni rapide, definendo gli identificatori per cui si desidera fornire descrizioni di informazioni rapide e quindi creando una descrizione comando in cui visualizzare il contenuto. È possibile definire Informazioni rapide nel contesto di un servizio di linguaggio oppure definire l'estensione e il tipo di contenuto del nome file e visualizzare le informazioni rapide solo per quel tipo oppure è possibile visualizzare informazioni rapide per un tipo di contenuto esistente, ad esempio "text". Questa procedura dettagliata illustra come visualizzare informazioni rapide per il tipo di contenuto "text".

 L'esempio QuickInfo in questa procedura dettagliata visualizza le descrizioni comando quando un utente sposta il puntatore su un nome di metodo. Questa progettazione richiede l'implementazione di queste quattro interfacce:

- interfaccia di origine

- Interfaccia del provider di origine

- interfaccia controller

- Interfaccia del provider di controller

  I provider di origine e controller sono parti del componente Managed Extensibility Framework (MEF) e sono responsabili dell'esportazione delle classi di origine e controller e dell'importazione di servizi e broker, ad esempio , che crea il buffer di testo della descrizione comando, e di , che attiva la sessione <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> QuickInfo.

  In questo esempio, l'origine QuickInfo usa un elenco hard-coded di nomi e descrizioni dei metodi, ma nelle implementazioni complete, il servizio di linguaggio e la documentazione del linguaggio sono responsabili di fornire tale contenuto.

## <a name="prerequisites"></a>Prerequisiti
 A partire Visual Studio 2015, non è necessario installare Visual Studio SDK dall'Area download. È incluso come funzionalità facoltativa nella configurazione Visual Studio configurazione. È anche possibile installare VS SDK in un secondo momento. Per altre informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-mef-project"></a>Creare un progetto MEF

### <a name="to-create-a-mef-project"></a>Per creare un progetto MEF

1. Creare un progetto VSIX C#. Nella finestra **di dialogo Nuovo Project** selezionare Visual **C# /Extensibility** e quindi **VSIX Project**. Assegnare alla soluzione il nome `QuickInfoTest` .

2. Aggiungere un modello di elemento Editor Classifier al progetto. Per altre informazioni, vedere [Creare un'estensione con un modello di elemento dell'editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Eliminare i file di classe esistenti.

## <a name="implement-the-quickinfo-source"></a>Implementare l'origine di informazioni rapide
 L'origine QuickInfo è responsabile della raccolta del set di identificatori e delle relative descrizioni e dell'aggiunta del contenuto al buffer di testo della descrizione comando quando viene rilevato uno degli identificatori. In questo esempio gli identificatori e le relative descrizioni vengono appena aggiunti nel costruttore di origine.

#### <a name="to-implement-the-quickinfo-source"></a>Per implementare l'origine di informazioni rapide

1. Aggiungere un file di classe e assegnargli il nome `TestQuickInfoSource`.

2. Aggiungere un riferimento a *Microsoft.VisualStudio.Language.IntelliSense*.

3. Aggiungere le importazioni seguenti.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet1":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet1":::

4. Dichiarare una classe che implementa <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> e assegnare alla classe il nome `TestQuickInfoSource` .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet2":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet2":::

5. Aggiungere campi per il provider di origine QuickInfo, il buffer di testo e un set di nomi di metodo e firme di metodo. In questo esempio i nomi e le firme dei metodi vengono inizializzati nel `TestQuickInfoSource` costruttore .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet3":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet3":::

6. Aggiungere un costruttore che imposta il provider di origine QuickInfo e il buffer di testo e popola il set di nomi dei metodi e le firme e le descrizioni dei metodi.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet4":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet4":::

7. Implementare il metodo <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A>. In questo esempio, il metodo trova la parola corrente o la parola precedente se il cursore si trova alla fine di una riga o di un buffer di testo. Se la parola è uno dei nomi dei metodi, la descrizione per tale nome di metodo viene aggiunta al contenuto di Informazioni rapide.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet5":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet5":::

8. È anche necessario implementare un metodo Dispose(), poiché <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> implementa <xref:System.IDisposable> :

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet6":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet6":::

## <a name="implement-a-quickinfo-source-provider"></a>Implementare un provider di origine QuickInfo
 Il provider dell'origine informazioni rapide serve principalmente per esportare se stesso come parte del componente MEF e creare un'istanza dell'origine di Informazioni rapide. Poiché è una parte del componente MEF, può importare altre parti del componente MEF.

#### <a name="to-implement-a-quickinfo-source-provider"></a>Per implementare un provider di origine QuickInfo

1. Dichiarare un provider di origine QuickInfo denominato che implementa e esportarlo con un valore di `TestQuickInfoSourceProvider` <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider> <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "ToolTip QuickInfo Source", un elemento <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> before="default" e un valore di <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text".

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet7":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet7":::

2. Importare due servizi editor, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> e , come proprietà di <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> `TestQuickInfoSourceProvider` .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet8":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet8":::

3. Implementare <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A> per restituire un nuovo oggetto `TestQuickInfoSource` .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet9":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet9":::

## <a name="implement-a-quickinfo-controller"></a>Implementare un controller di informazioni rapide
 I controller di informazioni rapide determinano quando vengono visualizzate le informazioni rapide. In questo esempio, QuickInfo viene visualizzato quando il puntatore si trova su una parola che corrisponde a uno dei nomi dei metodi. Il controller di Informazioni rapide implementa un gestore dell'evento di passaggio del mouse che attiva una sessione di informazioni rapide.

### <a name="to-implement-a-quickinfo-controller"></a>Per implementare un controller di informazioni rapide

1. Dichiarare una classe che implementa <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> e assegnare alla classe il nome `TestQuickInfoController` .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet10":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet10":::

2. Aggiungere campi privati per la visualizzazione di testo, i buffer di testo rappresentati nella visualizzazione testo, la sessione di informazioni rapide e il provider di controller di informazioni rapide.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet11":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet11":::

3. Aggiungere un costruttore che imposta i campi e aggiunge il gestore dell'evento del passaggio del mouse.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet12":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet12":::

4. Aggiungere il gestore dell'evento di passaggio del mouse che attiva la sessione di informazioni rapide.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet13":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet13":::

5. Implementare il metodo in modo che rimova il gestore dell'evento del passaggio del mouse quando <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A> il controller viene scollegato dalla visualizzazione testo.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet14":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet14":::

6. Implementare <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A> il metodo e il metodo come metodi <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A> vuoti per questo esempio.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet15":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet15":::

## <a name="implementing-the-quickinfo-controller-provider"></a>Implementazione del provider di controller di Informazioni rapide
 Il provider del controller di Informazioni rapide serve principalmente per esportare se stesso come parte del componente MEF e creare un'istanza del controller di Informazioni rapide. Poiché è una parte del componente MEF, può importare altre parti del componente MEF.

### <a name="to-implement-the-quickinfo-controller-provider"></a>Per implementare il provider di controller di Informazioni rapide

1. Dichiarare una classe denominata `TestQuickInfoControllerProvider` che implementa <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider> ed esportarla con <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "ToolTip QuickInfo Controller" e <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text":

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet16":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet16":::

2. Importare <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> come proprietà.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet17":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet17":::

3. Implementare <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A> il metodo creando un'istanza del controller di Informazioni rapide.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet18":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet18":::

## <a name="build-and-test-the-code"></a>Compilare e testare il codice
 Per testare questo codice, compilare la soluzione QuickInfoTest ed eseguirla nell'istanza sperimentale.

### <a name="to-build-and-test-the-quickinfotest-solution"></a>Per compilare e testare la soluzione QuickInfoTest

1. Compilare la soluzione.

2. Quando si esegue questo progetto nel debugger, viene avviata una seconda istanza di Visual Studio.

3. Creare un file di testo e digitare un testo che includa le parole "add" e "subtract".

4. Spostare il puntatore su una delle occorrenze di "add". Devono essere visualizzate la firma e la `add` descrizione del metodo.

## <a name="see-also"></a>Vedi anche
- [Procedura dettagliata: Collegare un tipo di contenuto a un'estensione di file](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
