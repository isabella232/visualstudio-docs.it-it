---
title: 'Procedura dettagliata: visualizzazione di descrizioni comandi di informazioni rapide | Microsoft Docs'
description: Informazioni su come visualizzare informazioni rapide per il contenuto di testo usando questa procedura dettagliata. Informazioni rapide Visualizza le firme del metodo e le descrizioni per il nome di un metodo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - QuickInfo
ms.assetid: 23fb8384-4f12-446f-977f-ce7910347947
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- csharp
- vb
ms.openlocfilehash: d374aa41d85b1d64b6623cb99f6183787a2afc53
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217255"
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

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet1":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet1":::

4. Dichiarare una classe che implementa <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> e denominarla `TestQuickInfoSource` .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet2":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet2":::

5. Aggiungere campi per il provider di origine informazioni rapide, il buffer di testo e un set di nomi di metodo e firme di metodi. In questo esempio, i nomi e le firme del metodo vengono inizializzati nel `TestQuickInfoSource` costruttore.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet3":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet3":::

6. Aggiungere un costruttore che imposta il provider di origine informazioni rapide e il buffer di testo e popola il set di nomi di metodo e le firme e le descrizioni dei metodi.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet4":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet4":::

7. Implementare il metodo <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A>. In questo esempio, il metodo trova la parola corrente o la parola precedente se il cursore si trova alla fine di una riga o di un buffer di testo. Se la parola è uno dei nomi di metodo, la descrizione per il nome del metodo viene aggiunta al contenuto informazioni rapide.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet5":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet5":::

8. È inoltre necessario implementare un metodo Dispose (), poiché <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> implementa <xref:System.IDisposable> :

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet6":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet6":::

## <a name="implement-a-quickinfo-source-provider"></a>Implementare un provider di origine informazioni rapide
 Il provider dell'origine informazioni rapide serve principalmente per esportarsi come parte del componente MEF e creare un'istanza dell'origine informazioni rapide. Poiché si tratta di una parte del componente MEF, può importare altre parti del componente MEF.

#### <a name="to-implement-a-quickinfo-source-provider"></a>Per implementare un provider di origine informazioni rapide

1. Dichiarare un provider di origine informazioni rapide denominato `TestQuickInfoSourceProvider` che implementa <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider> ed esportarlo con un oggetto <xref:Microsoft.VisualStudio.Utilities.NameAttribute> di "ToolTip informazioni rapide source", <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> di before = "default" e <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> di "Text".

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet7":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet7":::

2. Importare due servizi dell'editor, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> e <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> , come proprietà di `TestQuickInfoSourceProvider` .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet8":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet8":::

3. Implementare <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A> per restituire un nuovo oggetto `TestQuickInfoSource` .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet9":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet9":::

## <a name="implement-a-quickinfo-controller"></a>Implementare un controller informazioni rapide
 I controller informazioni rapide determinano quando viene visualizzato informazioni rapide. In questo esempio, informazioni rapide viene visualizzato quando il puntatore è posizionato su una parola che corrisponde a uno dei nomi di metodo. Il controller informazioni rapide implementa un gestore eventi di passaggio del mouse che attiva una sessione informazioni rapide.

### <a name="to-implement-a-quickinfo-controller"></a>Per implementare un controller informazioni rapide

1. Dichiarare una classe che implementa <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> e denominarla `TestQuickInfoController` .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet10":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet10":::

2. Aggiungere campi privati per la visualizzazione di testo, i buffer di testo rappresentati nella visualizzazione di testo, la sessione informazioni rapide e il provider del controller informazioni rapide.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet11":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet11":::

3. Aggiungere un costruttore che imposta i campi e aggiunge il gestore dell'evento di passaggio del mouse.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet12":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet12":::

4. Aggiungere il gestore eventi di passaggio del mouse che attiva la sessione informazioni rapide.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet13":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet13":::

5. Implementare il <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A> metodo in modo che rimuova il gestore dell'evento di passaggio del mouse quando il controller viene scollegato dalla visualizzazione di testo.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet14":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet14":::

6. Implementare il <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A> metodo e il <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A> metodo come metodi vuoti per questo esempio.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet15":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet15":::

## <a name="implementing-the-quickinfo-controller-provider"></a>Implementazione del provider del controller informazioni rapide
 Il provider del controller informazioni rapide serve principalmente per esportarsi come parte del componente MEF e creare un'istanza del controller informazioni rapide. Poiché si tratta di una parte del componente MEF, può importare altre parti del componente MEF.

### <a name="to-implement-the-quickinfo-controller-provider"></a>Per implementare il provider del controller informazioni rapide

1. Dichiarare una classe denominata `TestQuickInfoControllerProvider` che implementa <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider> ed esportarla con una <xref:Microsoft.VisualStudio.Utilities.NameAttribute> di "ToolTip informazioni rapide controller" e un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> di "Text":

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet16":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet16":::

2. Importare <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> come proprietà.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet17":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet17":::

3. Implementare il <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A> Metodo creando un'istanza del controller informazioni rapide.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet18":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet18":::

## <a name="build-and-test-the-code"></a>Compilare e testare il codice
 Per testare questo codice, compilare la soluzione QuickInfoTest ed eseguirla nell'istanza sperimentale.

### <a name="to-build-and-test-the-quickinfotest-solution"></a>Per compilare e testare la soluzione QuickInfoTest

1. Compilare la soluzione.

2. Quando si esegue questo progetto nel debugger, viene avviata una seconda istanza di Visual Studio.

3. Creare un file di testo e digitare il testo che include le parole "Add" e "Subtract".

4. Spostare il puntatore su una delle occorrenze di "Add". Verrà visualizzata la firma e la descrizione del `add` metodo.

## <a name="see-also"></a>Vedi anche
- [Procedura dettagliata: collegare un tipo di contenuto a un'estensione di file](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
