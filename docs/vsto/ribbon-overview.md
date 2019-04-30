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
ms.openlocfilehash: 8697a49c57840d358eeaa597fe984b6671958b09
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446960"
---
# <a name="ribbon-overview"></a>Panoramica della barra multifunzione
  La barra multifunzione è un modo per organizzare i comandi correlati in modo che siano più semplici da trovare. I comandi vengono visualizzati come controlli della barra multifunzione. I controlli sono organizzati in *gruppi* lungo una striscia orizzontale nella parte superiore di una finestra dell'applicazione. I gruppi correlati sono organizzati in schede.

 La maggior parte delle funzionalità che erano accessibili tramite i menu e barre degli strumenti nelle versioni precedenti di Microsoft Office system è ora accessibile tramite la barra multifunzione. Per altre informazioni, vedere l'articolo tecnico [Panoramica per gli sviluppatori dell'interfaccia utente per Microsoft Office system 2007](http://go.microsoft.com/fwlink/?LinkID=70860).

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

## <a name="customize-the-microsoft-office-ribbon"></a>Personalizzare la barra multifunzione di Microsoft Office
 Per personalizzare la barra multifunzione, aggiungere uno dei seguenti elementi della barra multifunzione al progetto di Office:

- **Sulla barra multifunzione (finestra di progettazione visiva)**

- **Sulla barra multifunzione (XML)**

  Ad esempio, per personalizzare la barra multifunzione di Excel, aggiungere un elemento di tale barra a un progetto di componente aggiuntivo VSTO per Excel.

### <a name="ribbon-visual-designer-item"></a>Elemento della barra multifunzione (finestra di progettazione visiva)
 Il **sulla barra multifunzione (finestra di progettazione visiva)** elemento fornisce strumenti avanzati che rendono più semplice per progettare e sviluppare una barra multifunzione personalizzata. Usare la **sulla barra multifunzione (finestra di progettazione visiva)** elemento personalizzazione della barra multifunzione nei modi seguenti:

- Aggiungere schede personalizzate o incorporate a una barra multifunzione.

- Aggiunta di gruppi personalizzati a una scheda personalizzata o incorporata

  > [!NOTE]
  > Una scheda incorporata o il gruppo è uno già esistente nella barra multifunzione di un'applicazione Microsoft Office. Ad esempio, il **dati** scheda è una scheda incorporata in Excel. Il **connessioni** è un gruppo predefinito sulle **dati** scheda.

- Aggiunta di controlli personalizzati a un gruppo personalizzato.

- Aggiunta di controlli personalizzati alla visualizzazione backstage.

  Per altre informazioni su come personalizzare una barra multifunzione usando il **sulla barra multifunzione (finestra di progettazione visiva)** elemento, vedere [progettazione della barra multifunzione](../vsto/ribbon-designer.md).

### <a name="ribbon-xml-item"></a>Elemento della barra multifunzione (XML)
 Usare la **sulla barra multifunzione (XML)** dell'elemento se si desidera personalizzare la barra multifunzione in modo che non è supportato dal **della barra multifunzione (finestra di progettazione visiva)** elemento. Usare la **sulla barra multifunzione (XML)** elemento personalizzazione della barra multifunzione nei modi seguenti:

- Aggiungere *incorporati* gruppi per una scheda personalizzata o incorporata.

- Aggiunta di controlli incorporati a un gruppo personalizzato.

- Aggiunta di codice personalizzato per eseguire l'override dei gestori eventi dei controlli incorporati.

- Personalizzazione della barra di accesso rapido.

- Condivisione di una personalizzazione della barra multifunzione tra diversi componenti aggiuntivi VSTO usando un ID completo.

  Per altre informazioni su come personalizzare la barra multifunzione usando il **sulla barra multifunzione (XML)** elemento, vedere [XML della barra multifunzione](../vsto/ribbon-xml.md).

## <a name="export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Esportare una barra multifunzione dalla finestra di progettazione della barra multifunzione XML della barra multifunzione
 Se si crea una barra multifunzione usando la finestra di progettazione della barra multifunzione e quindi decidere che si desidera personalizzare la barra multifunzione in modo che il **sulla barra multifunzione (finestra di progettazione visiva)** elemento non supporta, è possibile esportare la barra multifunzione in XML.

 Visual Studio crea automaticamente un **sulla barra multifunzione (XML)** di elemento e popolare il file XML della barra multifunzione con elementi e attributi per ogni controllo sulla barra multifunzione.

 Non tutte le proprietà presenti il **proprietà** finestra di progettazione della barra multifunzione vengono trasferite nel file XML della barra multifunzione.  Ad esempio, Visual Studio non esportare il valore della **immagine** oppure **testo** proprietà. Questa situazione si verifica perché è necessario creare un metodo di callback nel file di codice della barra multifunzione del progetto esportato per assegnare un'immagine o impostare il testo di un controllo. In Visual Studio non vengono generati automaticamente metodi di callback come parte del processo di esportazione.

 In più, i valori di proprietà predefiniti rimasti invariati non vengono visualizzati nel file XML risultante della barra multifunzione.

 Per altre informazioni su come esportare la barra multifunzione in XML, vedere [come: Esportare una barra multifunzione dalla finestra di progettazione della barra multifunzione XML della barra multifunzione](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md).

### <a name="update-the-code"></a>Aggiornare il codice
 Viene aggiunto un nuovo file di codice della barra multifunzione **Esplora soluzioni**. Questo file contiene la classe XML della barra multifunzione. È necessario creare metodi di callback nell'area `Ribbon Callbacks` di questa classe per gestire le azioni dell'utente, ad esempio la selezione di un pulsante. Spostare il codice dai gestori eventi in questi metodi di callback e modificarlo in modo che usi il modello di programmazione di estendibilità della barra multifunzione (RibbonX). Per altre informazioni, vedere [Ribbon XML](../vsto/ribbon-xml.md).

 È anche necessario aggiungere codice alla classe `ThisAddIn`, `ThisWorkbook` o `ThisDocument` che esegue l'override del metodo `CreateRibbonExtensibilityObject` e restituisce la classe XML della barra multifunzione all'applicazione Office.

 Per altre informazioni, vedere [Ribbon XML](../vsto/ribbon-xml.md).

## <a name="add-multiple-ribbon-items-to-a-project"></a>Aggiungere più elementi della barra multifunzione a un progetto
 È possibile aggiungere più elementi della barra multifunzione a un singolo progetto. Questa operazione è utile per eseguire una delle due attività seguenti:

- Creazione di barre multifunzione per Outlook *Inspectors*. Per altre informazioni, vedere [personalizzare una barra multifunzione per Outlook](../vsto/customizing-a-ribbon-for-outlook.md).

    > [!NOTE]
    > Un controllo rappresenta una finestra che viene aperta quando gli utenti eseguono determinate attività, ad esempio la creazione di un messaggio di posta elettronica.

- Selezionare la barra multifunzione da visualizzare in fase di esecuzione.

### <a name="select-which-ribbons-to-display-at-runtime"></a>Selezionare le barre multifunzione da visualizzare in fase di esecuzione
 Poiché un progetto può contenere più barre multifunzione, è possibile selezionare la barra multifunzione da visualizzare in fase di esecuzione.

 Per selezionare una barra multifunzione da visualizzare in fase di esecuzione, eseguire l'override di `CreateRibbonExtensibilityObject` metodo nella `ThisAddin`, `ThisWorkbook`, o `ThisDocument` classe del progetto e restituire la barra multifunzione che si desidera visualizzare. L'esempio seguente controlla il valore di un campo denominato `myCondition` e restituisce la barra multifunzione appropriata.

> [!NOTE]
> La sintassi usata in questo esempio restituisce una barra multifunzione che è stata creata utilizzando il **sulla barra multifunzione (finestra di progettazione visiva)** elemento. La sintassi per la restituzione di una barra multifunzione che viene creata usando un **sulla barra multifunzione (XML)** elemento è leggermente diverso. Per altre informazioni sulla restituzione di un **sulla barra multifunzione (XML)** elemento, vedere [XML della barra multifunzione](../vsto/ribbon-xml.md).

 Aggiungere il codice seguente:

 [!code-vb[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/VisualBasic/trin_Ribbon_choose_Ribbon_4/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/CSharp/trin_Ribbon_choose_Ribbon_4/ThisWorkbook.cs#1)]

### <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Procedura: Introduzione alla personalizzazione della barra multifunzione](../vsto/how-to-get-started-customizing-the-ribbon.md)|Illustra come personalizzare la barra multifunzione di un'applicazione Microsoft Office, aggiungere un **sulla barra multifunzione (finestra di progettazione visiva)** oppure **della barra multifunzione (XML)** elemento a un progetto di Office.|
|[Finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md)|Descrive come è possibile usare la finestra di progettazione della barra multifunzione per aggiungere schede personalizzate, gruppi e controlli alla barra multifunzione di un'applicazione Microsoft Office.|
|[Procedura dettagliata: Creare una scheda personalizzata usando la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)|Illustra come creare una scheda personalizzata della barra multifunzione usando la finestra di progettazione della barra multifunzione. Questa finestra di progettazione può essere usata per aggiungere e posizionare controlli sulla scheda personalizzata.|
|[Panoramica del modello a oggetti della barra multifunzione](../vsto/ribbon-object-model-overview.md)|Viene fornita una panoramica del modello a oggetti fortemente tipizzati che è possibile usare per ottenere e impostare le proprietà dei controlli della barra multifunzione in fase di esecuzione.|
|[Procedura dettagliata: Aggiornare i controlli in una barra multifunzione in fase di esecuzione](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)|Mostra come usare il modello a oggetti della barra multifunzione per aggiornare i controlli in una barra multifunzione dopo che è stata caricata nell'applicazione di Office.|
|[Personalizzare una barra multifunzione per Outlook](../vsto/customizing-a-ribbon-for-outlook.md)|Fornisce materiale sussidiario per personalizzare la barra multifunzione in Microsoft Office Outlook.|
|[Personalizzare una barra multifunzione per InfoPath](../vsto/customizing-a-ribbon-for-infopath.md)|Fornisce materiale sussidiario per personalizzare la barra multifunzione in Microsoft Office InfoPath.|
|[Accedere alla barra multifunzione in fase di esecuzione](../vsto/accessing-the-ribbon-at-run-time.md)|Illustra come mostrare, nascondere e modificare la barra multifunzione e consentire agli utenti di eseguire il codice dai controlli in un riquadro attività personalizzato, nel riquadro azioni o area del modulo di Outlook.|
|[Procedura: Modificare la posizione di una scheda della barra multifunzione](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)|Viene illustrato come modificare l'ordine delle schede in una barra multifunzione.|
|[Procedura: Personalizzare una scheda incorporata](../vsto/how-to-customize-a-built-in-tab.md)|Illustra come aggiungere gruppi e controlli a una scheda incorporata.|
|[Procedura: Aggiungere controlli alla visualizzazione Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)|Viene illustrato come aggiungere controlli al menu visualizzato quando si sceglie la **File**.|
|[Procedura: Aggiungere un pulsante di visualizzazione della finestra di dialogo a un gruppo della barra multifunzione](../vsto/how-to-add-a-dialog-box-launcher-to-a-ribbon-group.md)|Illustra come per aggiungere un pulsante di visualizzazione della finestra di dialogo a un gruppo in una barra multifunzione.|
|[Procedura: Esportare una barra multifunzione dalla finestra di progettazione della barra multifunzione XML della barra multifunzione](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)|Viene illustrato come personalizzare la barra multifunzione nella modalità avanzate esportandola dalla finestra di progettazione XML della barra multifunzione.|
|[Ribbon XML](../vsto/ribbon-xml.md)|Viene illustrato come è possibile personalizzare una barra multifunzione utilizzando XML della barra multifunzione.|
|[Procedura dettagliata: Creare una scheda personalizzata usando la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)|Viene illustrato come creare una scheda della barra multifunzione personalizzata usando il **sulla barra multifunzione (XML)** elemento.|
