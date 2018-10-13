---
title: Associare controlli WPF ai dati in Visual Studio2 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9cd13723e1483a33e4b98dc544c6e8448dc9a980
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49208242"
---
# <a name="bind-wpf-controls-to-data-in-visual-studio"></a>Associare controlli WPF ai dati in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile creare con associazione a dati [!INCLUDE[TLA#tla_titlewinclient](../includes/tlasharptla-titlewinclient-md.md)] controlli usando il **Zdroje dat** finestra. In primo luogo, aggiungere un'origine dati per il **Zdroje dat** finestra. Quindi, trascinare elementi dal **Zdroje dat** finestra per il**WPF Designer**.  
  
##  <a name="adding"></a> Aggiungere un'origine dati alla finestra Origini dati  
 Prima di creare controlli associati a dati, è innanzitutto necessario aggiungere un'origine dati per il **Zdroje dat** finestra.  
  
#### <a name="to-add-a-data-source-to-the-data-sources-window"></a>Per aggiungere un'origine dati alla finestra Origini dati  
  
1.  Nel **View** dal menu **Other Windows**e quindi fare clic su **Zdroje dat**.  
  
2.  Fare clic su **Aggiungi nuova origine dati**e completare la **configurazione dell'origine dati** procedura guidata.  
  
3.  Eseguire una delle attività seguenti per creare controlli associati ai dati:  
  
    -   [Creazione di un controllo associato a un singolo campo di dati](#simple).  
  
    -   [Creazione di un controllo associato a più campi di dati](#complex).  
  
    -   [Creazione di un set di controlli che sono associati a più campi di dati](#details).  
  
    -   [Associazione dati a controlli esistenti nella finestra di progettazione](#existing).  
  
##  <a name="simple"></a> Creare un controllo associato a un singolo campo di dati  
 Dopo aver aggiunto un'origine dati per il **Zdroje dat** finestra, è possibile creare un nuovo controllo associato a dati che visualizza un singolo campo di dati, ad esempio un <xref:System.Windows.Controls.ComboBox> o <xref:System.Windows.Controls.TextBox>.  
  
#### <a name="to-create-a-control-that-is-bound-to-a-single-field-of-data"></a>Per creare un controllo associato a un unico campo di dati  
  
1.  Nel **Zdroje dat** finestra, espandere un elemento che rappresenta una tabella o un oggetto. Individuare l'elemento figlio che rappresenta la colonna o la proprietà a cui eseguire l'associazione. Per un esempio visivo, vedere [finestra Origini dati](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).  
  
2.  Facoltativamente, selezionare il controllo da creare. Ogni elemento di **Zdroje dat** finestra dispone di un controllo predefinito che viene creato quando si trascina l'elemento nella finestra di progettazione. Il controllo predefinito dipende dal tipo di dati sottostante dell'elemento.  
  
     Per scegliere un controllo diverso, fare clic sulla freccia a discesa accanto all'elemento e selezionare un controllo. Per altre informazioni, vedere [impostare il controllo da creare durante il trascinamento dalla finestra Origini dei dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
3.  Trascinare l'elemento in un contenitore valido nella finestra di progettazione. Per altre informazioni sui contenitori validi, vedere [WPF di associare controlli ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Crea il nuovo controllo associato a dati e un oggetto <xref:System.Windows.Controls.Label> nel contenitore. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] genera anche [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] e il codice per associare il controllo ai dati. Per altre informazioni, vedere [WPF di associare controlli ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
##  <a name="complex"></a> Creare un controllo associato a più campi di dati  
 Dopo aver aggiunto un'origine dati per il **Zdroje dat** finestra, è possibile creare un nuovo controllo associato a dati che visualizza più campi di dati, ad esempio un <xref:System.Windows.Controls.DataGrid> o <xref:System.Windows.Controls.ListView>.  
  
#### <a name="to-create-a-control-that-is-bound-to-multiple-fields-of-data"></a>Per creare un controllo associato a più campi di dati  
  
1.  Nel **Zdroje dat** finestra, selezionare un elemento che rappresenta una tabella o un oggetto. Per un esempio visivo, vedere [finestra Origini dati](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).  
  
2.  Facoltativamente, selezionare il controllo da creare. Per impostazione predefinita, ogni elemento nella **Zdroje dat** intervallo che rappresenta una tabella di dati o un oggetto è impostato per creare un <xref:System.Windows.Controls.DataGrid> (se il progetto è destinato a .NET Framework 4) o <xref:System.Windows.Controls.ListView> (per le versioni precedenti di .NET Framework).  
  
     Per selezionare un controllo diverso, fare clic sulla freccia a discesa accanto all'elemento e selezionare un controllo. Per altre informazioni, vedere [impostare il controllo da creare durante il trascinamento dalla finestra Origini dei dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
    > [!NOTE]
    >  Se si preferisce non visualizzare una determinata colonna o proprietà, espandere l'elemento per visualizzarne i figli. Fare clic sulla freccia giù accanto alla colonna o proprietà che non si desidera visualizzare e quindi fare clic su **None**.  
  
3.  Trascinare l'elemento in un contenitore valido nella finestra di progettazione, ad esempio <xref:System.Windows.Controls.Grid>. Per altre informazioni sui contenitori validi, vedere [WPF di associare controlli ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
     Tramite [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] viene creato il nuovo controllo associato a dati nel contenitore. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] genera anche [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] e il codice per associare il controllo ai dati. Per altre informazioni, vedere [WPF di associare controlli ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
##  <a name="details"></a> Creare un set di controlli associati a più campi di dati  
 Dopo aver aggiunto un'origine dati per il **Zdroje dat** finestra, è possibile associare una tabella di dati o un oggetto a un set di controlli. Viene creato un controllo diverso per ogni colonna o proprietà nella tabella o nell'oggetto.  
  
#### <a name="to-create-a-set-of-controls-that-are-bound-to-multiple-fields-of-data"></a>Per creare un set di controlli associati a più campi di dati  
  
1.  Nel **Zdroje dat** finestra, selezionare un elemento che rappresenta una tabella o un oggetto. Per un esempio visivo, vedere [finestra Origini dati](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).  
  
2.  Fare clic sulla freccia giù accanto all'elemento e selezionare **dettagli**.  
  
    > [!NOTE]
    >  Se si preferisce non visualizzare una determinata colonna o proprietà, espandere l'elemento per visualizzarne i figli. Fare clic sulla freccia giù accanto alla colonna o proprietà che non si desidera visualizzare e quindi fare clic su **None**.  
  
3.  Trascinare l'elemento in un contenitore valido nella finestra di progettazione, ad esempio <xref:System.Windows.Controls.Grid>. Per altre informazioni sui contenitori validi, vedere [WPF di associare controlli ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] crea i nuovi controlli associati a dati nel contenitore. Ogni controllo è associato a una colonna o a una proprietà diversa ed è accompagnato da un controllo <xref:System.Windows.Controls.Label> opportunamente denominato. Tramite [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] vengono inoltre generati [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] e il codice per associare i controlli ai dati. Per altre informazioni, vedere [WPF di associare controlli ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
##  <a name="existing"></a> Binddata a controlli esistenti nella finestra di progettazione  
 Dopo aver aggiunto un'origine dati per il **Zdroje dat** finestra, è possibile aggiungere un data binding a un controllo esistente nella finestra di progettazione.  
  
#### <a name="to-bind-data-to-an-existing-control-in-the-designer"></a>Per associare dati a un controllo esistente nella finestra di progettazione  
  
1.  Nel **Zdroje dat** (finestra), usare una delle procedure riportate di seguito:  
  
    -   Per aggiungere un data binding a un controllo esistente che visualizza più campi di dati, ad esempio <xref:System.Windows.Controls.DataGrid> o <xref:System.Windows.Controls.ListView>, selezionare l'elemento che rappresenta la tabella o l'oggetto da associare al controllo.  
  
    -   Per aggiungere un data binding a un controllo esistente che visualizza più campi di dati, ad esempio <xref:System.Windows.Controls.ComboBox> o <xref:System.Windows.Controls.TextBox>, espandere l'elemento che rappresenta la tabella o l'oggetto che contiene i dati, quindi selezionare l'elemento che rappresenta i dati da associare al controllo.  
  
2.  Trascinare l'elemento selezionato dal **Zdroje dat** finestra in un controllo esistente nella finestra di progettazione. Il controllo deve essere un obiettivo di rilascio valido. Per altre informazioni, vedere [WPF di associare controlli ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Genera l'errore [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] e il codice per associare il controllo ai dati. Per altre informazioni, vedere [WPF di associare controlli ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
    > [!NOTE]
    >  Se il controllo è già associato a dati, il data binding per il controllo viene reimpostato sull'elemento trascinato nel controllo più di recente.  
  
## <a name="see-also"></a>Vedere anche  
 [Associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [Creare tabelle di ricerca nelle applicazioni WPF](../data-tools/create-lookup-tables-in-wpf-applications.md)   
 [Visualizzare i dati correlati nelle applicazioni WPF](../data-tools/display-related-data-in-wpf-applications.md)   
 [Associare controlli WPF a un set di dati](../data-tools/bind-wpf-controls-to-a-dataset.md)   
 [Associare controlli WPF a un servizio dati WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)   
 [Procedura dettagliata: visualizzazione dei dati correlati in un'applicazione WPF](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)

