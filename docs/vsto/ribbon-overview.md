---
title: Panoramica della barra multifunzione
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- customizing the Ribbon, multiple Ribbons
- Ribbon [Office development in Visual Studio], about Ribbon
- toolbars [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], multiple Ribbons
- toolbars [Office development in Visual Studio]
- custom Ribbon, multiple Ribbons
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 668517705caa7ba6baef0b85305bf4470bc3b26b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72985606"
---
# <a name="ribbon-overview"></a>Panoramica della barra multifunzione
  La barra multifunzione è un modo per organizzare i comandi correlati in modo che siano più facili da trovare. I comandi vengono visualizzati come controlli sulla barra multifunzione. I controlli sono organizzati in *gruppi* lungo una striscia orizzontale sul bordo superiore di una finestra dell'applicazione. I gruppi correlati sono organizzati in schede.

 Per accedere alla maggior parte delle funzionalità a cui è stato eseguito l'accesso tramite menu e barre degli strumenti nelle versioni precedenti del sistema di Microsoft Office, è ora possibile utilizzare la barra multifunzione. Per ulteriori informazioni, vedere l'articolo tecnico [Panoramica degli sviluppatori dell'interfaccia utente per il sistema di Microsoft Office 2007](/previous-versions/office/developer/office-2007/aa338198(v=office.12)).

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

## <a name="customize-the-microsoft-office-ribbon"></a>Personalizzare la barra multifunzione Microsoft Office
 Per personalizzare la barra multifunzione, aggiungere uno degli elementi della barra multifunzione seguenti al progetto di Office:

- **Barra multifunzione (finestra di progettazione visiva)**

- **Barra multifunzione (XML)**

  Ad esempio, per personalizzare la barra multifunzione di Excel, aggiungere un elemento di tale barra a un progetto di componente aggiuntivo VSTO per Excel.

### <a name="ribbon-visual-designer-item"></a>Elemento barra multifunzione (finestra di progettazione visiva)
 L'elemento **barra multifunzione (finestra di progettazione visiva)** fornisce strumenti avanzati che semplificano la progettazione e lo sviluppo di una barra multifunzione personalizzata. Utilizzare l'elemento **barra multifunzione (finestra di progettazione visiva)** per personalizzare la barra multifunzione nei modi seguenti:

- Aggiungere schede personalizzate o predefinite a una barra multifunzione.

- Aggiunta di gruppi personalizzati a una scheda personalizzata o incorporata

  > [!NOTE]
  > Una scheda o un gruppo predefinito è già presente nella barra multifunzione di un'applicazione Microsoft Office. Ad esempio, la scheda **dati** è una scheda incorporata in Excel. Il gruppo **Connections** è un gruppo incorporato nella scheda **dati** .

- Aggiunta di controlli personalizzati a un gruppo personalizzato.

- Aggiunta di controlli personalizzati alla visualizzazione backstage.

  Per altre informazioni su come personalizzare una barra multifunzione usando l'elemento barra multifunzione **(finestra di progettazione visiva)** , vedere [finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md).

### <a name="ribbon-xml-item"></a>Elemento barra multifunzione (XML)
 Utilizzare l'elemento **barra multifunzione (XML)** se si desidera personalizzare la barra multifunzione in un modo non supportato dall'elemento **barra multifunzione (finestra di progettazione visiva)** . Utilizzare l'elemento **barra multifunzione (XML)** per personalizzare la barra multifunzione nei modi seguenti:

- Aggiungere gruppi *predefiniti* a una scheda personalizzata o incorporata.

- Aggiunta di controlli incorporati a un gruppo personalizzato.

- Aggiunta di codice personalizzato per eseguire l'override dei gestori eventi dei controlli incorporati.

- Personalizzazione della barra di accesso rapido.

- Condivisione di una personalizzazione della barra multifunzione tra diversi componenti aggiuntivi VSTO usando un ID completo.

  Per altre informazioni su come personalizzare la barra multifunzione usando l'elemento barra multifunzione **(XML)** , vedere [Ribbon XML](../vsto/ribbon-xml.md).

## <a name="export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Esportare una barra multifunzione dalla finestra di progettazione Ribbon alla barra multifunzione XML
 Se si crea una barra multifunzione usando la finestra di progettazione della barra multifunzione e quindi si decide di personalizzare la barra multifunzione in modo che l'elemento **barra multifunzione (finestra di progettazione visiva)** non supporti, è possibile esportare la barra multifunzione in XML.

 Visual Studio crea automaticamente un elemento **barra multifunzione (XML)** e popola il file XML della barra multifunzione con gli elementi e gli attributi per ogni controllo sulla barra multifunzione.

 Non tutte le proprietà presenti nella finestra **Proprietà** della finestra di progettazione della barra multifunzione vengono trasferite al file XML della barra multifunzione.  In Visual Studio, ad esempio, il valore della proprietà **Image** o **Text** non viene esportato. Questa situazione si verifica perché è necessario creare un metodo di callback nel file di codice della barra multifunzione del progetto esportato per assegnare un'immagine o impostare il testo di un controllo. In Visual Studio non vengono generati automaticamente metodi di callback come parte del processo di esportazione.

 In più, i valori di proprietà predefiniti rimasti invariati non vengono visualizzati nel file XML risultante della barra multifunzione.

 Per ulteriori informazioni su come esportare la barra multifunzione in XML, vedere [procedura: esportare una barra multifunzione dalla finestra di progettazione della barra multifunzione a XML della barra multifunzione](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md).

### <a name="update-the-code"></a>Aggiornare il codice
 Viene aggiunto un nuovo file di codice della barra multifunzione **Esplora soluzioni**. Questo file contiene la classe XML della barra multifunzione. È necessario creare metodi di callback nell'area `Ribbon Callbacks` di questa classe per gestire le azioni dell'utente, ad esempio la selezione di un pulsante. Spostare il codice dai gestori eventi in questi metodi di callback e modificarlo in modo che usi il modello di programmazione di estendibilità della barra multifunzione (RibbonX). Per altre informazioni, vedere [Ribbon XML](../vsto/ribbon-xml.md).

 È anche necessario aggiungere codice alla classe `ThisAddIn`, `ThisWorkbook` o `ThisDocument` che esegue l'override del metodo `CreateRibbonExtensibilityObject` e restituisce la classe XML della barra multifunzione all'applicazione Office.

 Per altre informazioni, vedere [Ribbon XML](../vsto/ribbon-xml.md).

## <a name="add-multiple-ribbon-items-to-a-project"></a>Aggiungere più elementi della barra multifunzione a un progetto
 È possibile aggiungere più elementi della barra multifunzione a un singolo progetto. Questa operazione è utile per eseguire una delle due attività seguenti:

- Creare nastri per i *controlli*di Outlook. Per altre informazioni, vedere [personalizzare una barra multifunzione per Outlook](../vsto/customizing-a-ribbon-for-outlook.md).

    > [!NOTE]
    > Un controllo rappresenta una finestra che viene aperta quando gli utenti eseguono determinate attività, ad esempio la creazione di un messaggio di posta elettronica.

- Consente di selezionare la barra multifunzione da visualizzare in fase di esecuzione.

### <a name="select-which-ribbons-to-display-at-run-time"></a>Selezionare le barre multifunzione da visualizzare in fase di esecuzione
 Poiché un progetto può contenere più di una barra multifunzione, è possibile selezionare la barra multifunzione da visualizzare in fase di esecuzione.

 Per selezionare una barra multifunzione da visualizzare in fase di esecuzione, eseguire l'override del `CreateRibbonExtensibilityObject` metodo nella `ThisAddin` `ThisWorkbook` classe, o `ThisDocument` del progetto e restituire la barra multifunzione che si desidera visualizzare. Nell'esempio seguente viene controllato il valore di un campo denominato `myCondition` e viene restituita la barra multifunzione appropriata.

> [!NOTE]
> La sintassi utilizzata in questo esempio restituisce una barra multifunzione creata utilizzando l'elemento **barra multifunzione (finestra di progettazione visiva)** . La sintassi per la restituzione di una barra multifunzione creata utilizzando un elemento **barra multifunzione (XML)** è leggermente diversa. Per ulteriori informazioni sulla restituzione di un elemento **barra multifunzione (XML)** , vedere [Ribbon XML](../vsto/ribbon-xml.md).

 Aggiungere il codice seguente:

 [!code-vb[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/VisualBasic/trin_Ribbon_choose_Ribbon_4/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/CSharp/trin_Ribbon_choose_Ribbon_4/ThisWorkbook.cs#1)]

### <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Procedura: iniziare a personalizzare la barra multifunzione](../vsto/how-to-get-started-customizing-the-ribbon.md)|Viene illustrato come personalizzare la barra multifunzione di un'applicazione Microsoft Office, aggiungere un elemento barra **multifunzione (finestra di progettazione visiva)** o **barra multifunzione (XML)** a un progetto di Office.|
|[Finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md)|Viene descritto come utilizzare la finestra di progettazione della barra multifunzione per aggiungere schede, gruppi e controlli personalizzati alla barra multifunzione di un'applicazione Microsoft Office.|
|[Procedura dettagliata: creare una scheda personalizzata usando la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)|Illustra come creare una scheda personalizzata della barra multifunzione usando la finestra di progettazione della barra multifunzione. Questa finestra di progettazione può essere usata per aggiungere e posizionare controlli sulla scheda personalizzata.|
|[Panoramica del modello a oggetti della barra multifunzione](../vsto/ribbon-object-model-overview.md)|Fornisce una panoramica di un modello a oggetti fortemente tipizzato per ottenere e impostare le proprietà dei controlli della barra multifunzione in fase di esecuzione.|
|[Procedura dettagliata: aggiornare i controlli in una barra multifunzione in fase di esecuzione](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)|Mostra come usare il modello a oggetti della barra multifunzione per aggiornare i controlli in una barra multifunzione dopo che è stata caricata nell'applicazione di Office.|
|[Personalizzare una barra multifunzione per Outlook](../vsto/customizing-a-ribbon-for-outlook.md)|Vengono fornite informazioni aggiuntive per personalizzare la barra multifunzione in Microsoft Office Outlook.|
|[Personalizzare una barra multifunzione per InfoPath](../vsto/customizing-a-ribbon-for-infopath.md)|Vengono fornite informazioni aggiuntive per personalizzare la barra multifunzione in Microsoft Office InfoPath.|
|[Accedere alla barra multifunzione in fase di esecuzione](../vsto/accessing-the-ribbon-at-run-time.md)|Viene illustrato come visualizzare, nascondere e modificare la barra multifunzione e consentire agli utenti di eseguire il codice dai controlli in un riquadro attività personalizzato, un riquadro azioni o un'area del modulo di Outlook.|
|[Procedura: modificare la posizione di una scheda nella barra multifunzione](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)|Viene illustrato come modificare l'ordine delle schede in una barra multifunzione.|
|[Procedura: personalizzare una scheda incorporata](../vsto/how-to-customize-a-built-in-tab.md)|Illustra come aggiungere gruppi e controlli a una scheda incorporata.|
|[Procedura: aggiungere controlli alla visualizzazione Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)|Viene illustrato come aggiungere controlli al menu visualizzato quando si fa clic sul **file**.|
|[Procedura: aggiungere un pulsante di avvio della finestra di dialogo a un gruppo della barra multifunzione](../vsto/how-to-add-a-dialog-box-launcher-to-a-ribbon-group.md)|Mostra come aggiungere un pulsante di avvio della finestra di dialogo a qualsiasi gruppo su una barra multifunzione.|
|[Procedura: esportare una barra multifunzione dalla finestra di progettazione della barra multifunzione a XML della barra multifunzione](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)|Viene illustrato come personalizzare la barra multifunzione in modi avanzati esportando la barra multifunzione dalla finestra di progettazione al file XML della barra multifunzione.|
|[Ribbon XML](../vsto/ribbon-xml.md)|Viene illustrato come personalizzare una barra multifunzione tramite XML della barra multifunzione.|
|[Procedura dettagliata: creare una scheda personalizzata usando la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)|Viene illustrato come creare una scheda personalizzata della barra multifunzione usando l'elemento **barra multifunzione (XML)** .|
