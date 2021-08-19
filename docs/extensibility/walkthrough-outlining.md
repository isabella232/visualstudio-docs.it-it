---
title: 'Procedura dettagliata: Struttura dei | Microsoft Docs'
description: Informazioni su come definire e visualizzare aree strutturate nel contesto di un servizio di linguaggio o per l'estensione di file e il tipo di contenuto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - outlining
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
dev_langs:
- csharp
- vb
ms.openlocfilehash: 987f45f32e5fda2b1d8dfa2db1036c70288a2d66
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122078518"
---
# <a name="walkthrough-outlining"></a>Procedura dettagliata: definizione della struttura
Configurare funzionalità basate sulla lingua, ad esempio la struttura, definendo i tipi di aree di testo da espandere o comprimere. È possibile definire aree nel contesto di un servizio di linguaggio o definire un'estensione di file e un tipo di contenuto personalizzati e applicare la definizione dell'area solo a tale tipo oppure applicare le definizioni di area a un tipo di contenuto esistente, ad esempio "text". Questa procedura dettagliata illustra come definire e visualizzare aree strutturate.

## <a name="prerequisites"></a>Prerequisiti
 A partire Visual Studio 2015, non si installa Visual Studio SDK dall'Area download. È incluso come funzionalità facoltativa nella configurazione Visual Studio configurazione. È anche possibile installare VS SDK in un secondo momento. Per altre informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Creare un Managed Extensibility Framework (MEF)

### <a name="to-create-a-mef-project"></a>Per creare un progetto MEF

1. Creare un progetto VSIX. Assegnare alla soluzione il nome `OutlineRegionTest`.

2. Aggiungere un modello di elemento Editor Classifier al progetto. Per altre informazioni, vedere [Creare un'estensione con un modello di elemento dell'editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Eliminare i file di classe esistenti.

## <a name="implement-an-outlining-tagger"></a>Implementare un tagger di struttura
 Le aree di struttura sono contrassegnate da un tipo di tag ( <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> ). Questo tag fornisce il comportamento di struttura standard. L'area strutturata può essere espansa o compressa. L'area evidenziata è contrassegnata da un segno più ( ) se è compressa o da un segno meno ( ) se è espansa e l'area espansa è delimitata da una linea **+** **-** verticale.

 La procedura seguente illustra come definire un tagger che crea aree struttura per tutte le aree delimitate dalle parentesi quadre (**[**,**]**).

### <a name="to-implement-an-outlining-tagger"></a>Per implementare un tagger di struttura

1. Aggiungere un file di classe e assegnargli il nome `OutliningTagger`.

2. Importare gli spazi dei nomi seguenti.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet1":::

3. Creare una classe denominata `OutliningTagger` e fare in modo che implementi <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> :

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet2":::

4. Aggiungere alcuni campi per tenere traccia del buffer di testo e dello snapshot e per accumulare i set di righe che devono essere contrassegnate come aree di struttura. Questo codice include un elenco di oggetti Region (da definire in un secondo momento) che rappresentano le aree di struttura.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet3":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet3":::

5. Aggiungere un costruttore di tagger che inizializza i campi, analizza il buffer e aggiunge un gestore eventi <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> all'evento .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet4":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet4":::

6. Implementare <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> il metodo , che crea un'istanza degli intervalli di tag. In questo esempio si presuppone che gli intervalli nell'oggetto passato al metodo siano contigui, anche se potrebbe <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> non essere sempre il caso. Questo metodo crea un'istanza di un nuovo intervallo di tag per ognuna delle aree di struttura.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet5":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet5":::

7. Dichiarare un `TagsChanged` gestore eventi.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet6":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet6":::

8. Aggiungere un `BufferChanged` gestore eventi che risponde agli eventi <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> analizzando il buffer di testo.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet7":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet7":::

9. Aggiungere un metodo che analizza il buffer. L'esempio qui riportato è solo a scopo illustrativo. Analizza in modo sincrono il buffer in aree struttura nidificate.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet8":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet8":::

10. Il metodo helper seguente ottiene un numero intero che rappresenta il livello della struttura, in modo che 1 sia la coppia di parentesi graffe più a sinistra.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet9":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet9":::

11. Il metodo helper seguente converte un'area (definita più avanti in questo articolo) in snapshotSpan.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet10":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet10":::

12. Il codice seguente è solo a scopo illustrativo. Definisce una classe PartialRegion che contiene il numero di riga e l'offset dell'inizio di un'area di struttura e un riferimento all'area padre (se presente). Questo codice consente al parser di configurare aree struttura nidificate. Una classe Region derivata contiene un riferimento al numero di riga della fine di un'area di struttura.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet11":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet11":::

## <a name="implement-a-tagger-provider"></a>Implementare un provider di tagger
 Esportare un provider di tagger per il tagger. Il provider di tag crea un oggetto per un buffer del tipo di contenuto "text", altrimenti restituisce un se il `OutliningTagger` buffer ne ha già `OutliningTagger` uno.

### <a name="to-implement-a-tagger-provider"></a>Per implementare un provider di tag

1. Creare una classe denominata `OutliningTaggerProvider` che implementa <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> e esportarla con gli attributi ContentType e TagType.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet12":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet12":::

2. Implementare <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> il metodo aggiungendo un oggetto alle proprietà del `OutliningTagger` buffer.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet13":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet13":::

## <a name="build-and-test-the-code"></a>Compilare e testare il codice
 Per testare questo codice, compilare la soluzione OutlineRegionTest ed eseguirla nell'istanza sperimentale.

### <a name="to-build-and-test-the-outlineregiontest-solution"></a>Per compilare e testare la soluzione OutlineRegionTest

1. Compilare la soluzione.

2. Quando si esegue questo progetto nel debugger, viene avviata una seconda istanza di Visual Studio.

3. Creare un file di testo. Digitare un testo che includa sia le parentesi di apertura che le parentesi di chiusura.

    ```
    [
       Hello
    ]
    ```

4. Deve essere presente un'area di struttura che include entrambe le parentesi quadre. Dovrebbe essere possibile fare clic sul segno meno a sinistra della parentesi aperta per comprimere l'area di struttura. Quando l'area è compressa, il simbolo dei puntini di sospensione (*...*) dovrebbe  essere visualizzato a sinistra dell'area compressa e quando si sposta il puntatore del mouse sui puntini di sospensione dovrebbe essere visualizzato un popup contenente il testo al passaggio del mouse.

## <a name="see-also"></a>Vedi anche
- [Procedura dettagliata: Collegare un tipo di contenuto a un'estensione di file](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
