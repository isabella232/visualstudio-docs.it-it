---
title: Associare controlli WPF ai dati (parte 2) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: 00dd5147-db0b-4b59-8d6c-8229b09ca9dd
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 06428a633aec41489a8a77655d6ea9442ffffaa0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85540088"
---
# <a name="bind-wpf-controls-to-data-in-visual-studio"></a>Associare controlli WPF ai dati in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile creare [!INCLUDE[TLA#tla_titlewinclient](../includes/tlasharptla-titlewinclient-md.md)] controlli associati a dati utilizzando la finestra **origini dati** . Prima di tutto, aggiungere un'origine dati alla finestra **origini dati** . Trascinare quindi gli elementi dalla finestra **origini dati** a**WPF Designer**.

## <a name="add-a-data-source-to-the-data-sources-window"></a><a name="adding"></a> Aggiungere un'origine dati alla finestra Origini dati
 Prima di poter creare controlli associati a dati, è necessario innanzitutto aggiungere un'origine dati alla finestra **origini dati** .

#### <a name="to-add-a-data-source-to-the-data-sources-window"></a>Per aggiungere un'origine dati alla finestra Origini dati

1. Scegliere **altre finestre**dal menu **Visualizza** , quindi fare clic su **origini dati**.

2. Fare clic su **Aggiungi nuova origine dati** e completare la **Configurazione guidata origine dati**.

3. Eseguire una delle attività seguenti per creare controlli associati ai dati:

    - [Creazione di un controllo associato a un singolo campo di dati](#simple).

    - [Creazione di un controllo associato a più campi di dati](#complex).

    - [Creazione di un set di controlli associati a più campi di dati](#details).

    - [Associazione di dati a controlli esistenti nella finestra di progettazione](#existing).

## <a name="create-a-control-that-is-bound-to-a-single-field-of-data"></a><a name="simple"></a> Creare un controllo associato a un singolo campo di dati
 Dopo avere aggiunto un'origine dati alla finestra **origini dati** , è possibile creare un nuovo controllo associato a dati che visualizza un singolo campo di dati, ad esempio <xref:System.Windows.Controls.ComboBox> o <xref:System.Windows.Controls.TextBox> .

#### <a name="to-create-a-control-that-is-bound-to-a-single-field-of-data"></a>Per creare un controllo associato a un unico campo di dati

1. Nella finestra **origini dati** espandere un elemento che rappresenta una tabella o un oggetto. Individuare l'elemento figlio che rappresenta la colonna o la proprietà a cui eseguire l'associazione. Per un esempio visivo, vedere [finestra Origini dati](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).

2. Facoltativamente, selezionare il controllo da creare. Ogni elemento nella finestra **origini dati** dispone di un controllo predefinito che viene creato quando si trascina l'elemento nella finestra di progettazione. Il controllo predefinito dipende dal tipo di dati sottostante dell'elemento.

     Per scegliere un controllo diverso, fare clic sulla freccia a discesa accanto all'elemento e selezionare un controllo. Per ulteriori informazioni, vedere [impostare il controllo da creare durante il trascinamento dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

3. Trascinare l'elemento in un contenitore valido nella finestra di progettazione. Per altre informazioni sui contenitori validi, vedere [associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Crea il nuovo controllo con associazione a dati e un titolo appropriato <xref:System.Windows.Controls.Label> nel contenitore. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] genera anche [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] e il codice per associare il controllo ai dati. Per altre informazioni, vedere [associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

## <a name="create-a-control-that-is-bound-to-multiple-fields-of-data"></a><a name="complex"></a> Creare un controllo associato a più campi di dati
 Dopo avere aggiunto un'origine dati alla finestra **origini dati** , è possibile creare un nuovo controllo associato a dati che Visualizza più campi di dati, ad esempio <xref:System.Windows.Controls.DataGrid> o <xref:System.Windows.Controls.ListView> .

#### <a name="to-create-a-control-that-is-bound-to-multiple-fields-of-data"></a>Per creare un controllo associato a più campi di dati

1. Nella finestra **origini dati** selezionare un elemento che rappresenta una tabella o un oggetto. Per un esempio visivo, vedere [finestra Origini dati](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).

2. Facoltativamente, selezionare il controllo da creare. Per impostazione predefinita, ogni elemento nella finestra **origini dati** che rappresenta una tabella di dati o un oggetto viene impostato per creare un <xref:System.Windows.Controls.DataGrid> (se il progetto è destinato a .NET Framework 4) o <xref:System.Windows.Controls.ListView> (per le versioni precedenti del .NET Framework).

     Per selezionare un controllo diverso, fare clic sulla freccia a discesa accanto all'elemento e selezionare un controllo. Per ulteriori informazioni, vedere [impostare il controllo da creare durante il trascinamento dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

    > [!NOTE]
    > Se si preferisce non visualizzare una determinata colonna o proprietà, espandere l'elemento per visualizzarne i figli. Fare clic sulla freccia a discesa accanto alla colonna o alla proprietà che non si desidera visualizzare, quindi fare clic su **nessuno**.

3. Trascinare l'elemento in un contenitore valido nella finestra di progettazione, ad esempio <xref:System.Windows.Controls.Grid>. Per altre informazioni sui contenitori validi, vedere [associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Crea il nuovo controllo associato a dati nel contenitore. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] genera anche [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] e il codice per associare il controllo ai dati. Per altre informazioni, vedere [associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

## <a name="create-a-set-of-controls-that-are-bound-to-multiple-fields-of-data"></a><a name="details"></a> Creare un set di controlli associati a più campi di dati
 Dopo avere aggiunto un'origine dati alla finestra **origini dati** , è possibile associare una tabella dati o un oggetto a un set di controlli. Viene creato un controllo diverso per ogni colonna o proprietà nella tabella o nell'oggetto.

#### <a name="to-create-a-set-of-controls-that-are-bound-to-multiple-fields-of-data"></a>Per creare un set di controlli associati a più campi di dati

1. Nella finestra **origini dati** selezionare un elemento che rappresenta una tabella o un oggetto. Per un esempio visivo, vedere [finestra Origini dati](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).

2. Fare clic sulla freccia a discesa accanto all'elemento e selezionare **Dettagli**.

    > [!NOTE]
    > Se si preferisce non visualizzare una determinata colonna o proprietà, espandere l'elemento per visualizzarne i figli. Fare clic sulla freccia a discesa accanto alla colonna o alla proprietà che non si desidera visualizzare, quindi fare clic su **nessuno**.

3. Trascinare l'elemento in un contenitore valido nella finestra di progettazione, ad esempio <xref:System.Windows.Controls.Grid>. Per altre informazioni sui contenitori validi, vedere [associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Crea i nuovi controlli associati a dati nel contenitore. Ogni controllo è associato a una colonna o a una proprietà diversa ed è accompagnato da un controllo <xref:System.Windows.Controls.Label> opportunamente denominato. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] genera anche [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] e il codice per associare i controlli ai dati. Per altre informazioni, vedere [associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

## <a name="binddata-to-existing-controls-in-the-designer"></a><a name="existing"></a> BindData ai controlli esistenti nella finestra di progettazione
 Dopo avere aggiunto un'origine dati alla finestra **origini dati** , è possibile aggiungere una data binding a un controllo esistente nella finestra di progettazione.

#### <a name="to-bind-data-to-an-existing-control-in-the-designer"></a>Per associare dati a un controllo esistente nella finestra di progettazione

1. Nella finestra **origini dati** usare una delle procedure seguenti:

    - Per aggiungere un data binding a un controllo esistente che visualizza più campi di dati, ad esempio <xref:System.Windows.Controls.DataGrid> o <xref:System.Windows.Controls.ListView>, selezionare l'elemento che rappresenta la tabella o l'oggetto da associare al controllo.

    - Per aggiungere un data binding a un controllo esistente che visualizza più campi di dati, ad esempio <xref:System.Windows.Controls.ComboBox> o <xref:System.Windows.Controls.TextBox>, espandere l'elemento che rappresenta la tabella o l'oggetto che contiene i dati, quindi selezionare l'elemento che rappresenta i dati da associare al controllo.

2. Trascinare l'elemento selezionato dalla finestra **origini dati** su un controllo esistente nella finestra di progettazione. Il controllo deve essere una destinazione di rilascio valida. Per altre informazioni, vedere [associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] genera [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] e il codice per associare il controllo ai dati. Per altre informazioni, vedere [associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

    > [!NOTE]
    > Se il controllo è già associato a dati, l'associazione dati per il controllo viene reimpostata sull'elemento trascinato nel controllo più di recente.

## <a name="see-also"></a>Vedere anche
 [Associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md) [creare tabelle di ricerca nelle applicazioni WPF](../data-tools/create-lookup-tables-in-wpf-applications.md) [visualizzare dati correlati nelle applicazioni WPF](../data-tools/display-related-data-in-wpf-applications.md) [associare controlli WPF a un DataSet](../data-tools/bind-wpf-controls-to-a-dataset.md) [associare controlli WPF a una procedura dettagliata di WCF Data Services](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md) [: visualizzazione di dati correlati in un'applicazione WPF](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)
