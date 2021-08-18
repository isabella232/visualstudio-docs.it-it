---
title: Panoramica della barra multifunzione
description: Informazioni su come la barra multifunzione è un modo per organizzare i comandi correlati in modo che siano più facili da trovare e come i comandi vengono visualizzati come controlli sulla barra multifunzione.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 2f125edbf25c5a7732f3ce168bf96b90f4d94c11
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122099516"
---
# <a name="ribbon-overview"></a>Panoramica della barra multifunzione
  La barra multifunzione è un modo per organizzare i comandi correlati in modo che siano più facili da trovare. I comandi vengono visualizzati come controlli sulla barra multifunzione. I controlli sono organizzati *in gruppi* lungo una striscia orizzontale sul bordo superiore di una finestra dell'applicazione. I gruppi correlati sono organizzati in schede.

 La maggior parte delle funzionalità a cui è stato eseguito l'accesso tramite menu e barre degli strumenti nelle versioni precedenti del Microsoft Office è ora accessibile tramite la barra multifunzione. Per altre informazioni, vedere l'articolo tecnico [Developer overview of the user interface for the 2007 Microsoft Office system](/previous-versions/office/developer/office-2007/aa338198(v=office.12)).

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

## <a name="customize-the-microsoft-office-ribbon"></a>Personalizzare la barra Microsoft Office multifunzione
 Per personalizzare la barra multifunzione, aggiungere uno degli elementi seguenti della barra multifunzione al Office progetto:

- **Barra multifunzione (finestra di progettazione visiva)**

- **Barra multifunzione (XML)**

  Ad esempio, per personalizzare la barra multifunzione di Excel, aggiungere un elemento di tale barra a un progetto di componente aggiuntivo VSTO per Excel.

### <a name="ribbon-visual-designer-item"></a>Elemento Barra multifunzione (finestra di progettazione visiva)
 **L'elemento Barra multifunzione (finestra di** progettazione visiva) offre strumenti avanzati che semplificano la progettazione e lo sviluppo di una barra multifunzione personalizzata. Usare **l'elemento Barra multifunzione (finestra di** progettazione visiva) per personalizzare la barra multifunzione nei modi seguenti:

- Aggiungere schede personalizzate o predefinite a una barra multifunzione.

- Aggiunta di gruppi personalizzati a una scheda personalizzata o incorporata

  > [!NOTE]
  > Una scheda o un gruppo predefinito è già presente nella barra multifunzione di un'Microsoft Office applicazione. Ad esempio, **la scheda** Dati è una scheda predefinita in Excel. Il **gruppo** Connessioni è un gruppo predefinito nella **scheda** Dati.

- Aggiunta di controlli personalizzati a un gruppo personalizzato.

- Aggiunta di controlli personalizzati alla visualizzazione backstage.

  Per altre informazioni su come personalizzare una barra multifunzione usando l'elemento Barra multifunzione **(finestra di** progettazione visiva), vedere Finestra di [progettazione della barra multifunzione.](../vsto/ribbon-designer.md)

### <a name="ribbon-xml-item"></a>Elemento barra multifunzione (XML)
 Usare **l'elemento** Barra multifunzione (XML) se si vuole personalizzare la barra multifunzione in un modo non supportato dall'elemento Barra **multifunzione (finestra di progettazione** visiva). Usare **l'elemento Barra multifunzione (XML)** per personalizzare la barra multifunzione nei modi seguenti:

- Aggiungere *gruppi predefiniti* a una scheda personalizzata o a una scheda incorporata.

- Aggiunta di controlli incorporati a un gruppo personalizzato.

- Aggiunta di codice personalizzato per eseguire l'override dei gestori eventi dei controlli incorporati.

- Personalizzazione della barra di accesso rapido.

- Condivisione di una personalizzazione della barra multifunzione tra diversi componenti aggiuntivi VSTO usando un ID completo.

  Per altre informazioni su come personalizzare la barra multifunzione usando l'elemento Barra multifunzione **(XML),** vedere XML [della barra multifunzione.](../vsto/ribbon-xml.md)

## <a name="export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Esportare una barra multifunzione dalla finestra di progettazione della barra multifunzione al file XML della barra multifunzione
 Se si crea una barra multifunzione usando la finestra di progettazione della barra multifunzione e quindi si decide di personalizzare la barra multifunzione in modi non supportati dall'elemento Barra multifunzione **(finestra** di progettazione visiva), è possibile esportare la barra multifunzione in XML.

 Visual Studio crea automaticamente un elemento della barra **multifunzione (XML)** e popola il file XML della barra multifunzione con elementi e attributi per ogni controllo della barra multifunzione.

 Non tutte le proprietà presenti  nella finestra Proprietà della finestra di progettazione della barra multifunzione vengono trasferite nel file XML della barra multifunzione.  Ad esempio, Visual Studio non esporta il valore della **proprietà Image** **o Text.** Questa situazione si verifica perché è necessario creare un metodo di callback nel file di codice della barra multifunzione del progetto esportato per assegnare un'immagine o impostare il testo di un controllo. In Visual Studio non vengono generati automaticamente metodi di callback come parte del processo di esportazione.

 In più, i valori di proprietà predefiniti rimasti invariati non vengono visualizzati nel file XML risultante della barra multifunzione.

 Per altre informazioni su come esportare la barra multifunzione in XML, vedere Procedura: Esportare una barra multifunzione dalla finestra di progettazione della barra [multifunzione in XML della barra multifunzione.](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)

### <a name="update-the-code"></a>Aggiornare il codice
 Viene aggiunto un nuovo file di codice della barra **multifunzione Esplora soluzioni**. Questo file contiene la classe XML della barra multifunzione. È necessario creare metodi di callback nell'area `Ribbon Callbacks` di questa classe per gestire le azioni dell'utente, ad esempio la selezione di un pulsante. Spostare il codice dai gestori eventi in questi metodi di callback e modificarlo in modo che usi il modello di programmazione di estendibilità della barra multifunzione (RibbonX). Per altre informazioni, vedere [Ribbon XML](../vsto/ribbon-xml.md).

 È anche necessario aggiungere codice alla classe `ThisAddIn`, `ThisWorkbook` o `ThisDocument` che esegue l'override del metodo `CreateRibbonExtensibilityObject` e restituisce la classe XML della barra multifunzione all'applicazione Office.

 Per altre informazioni, vedere [Ribbon XML](../vsto/ribbon-xml.md).

## <a name="add-multiple-ribbon-items-to-a-project"></a>Aggiungere più elementi della barra multifunzione a un progetto
 È possibile aggiungere più elementi della barra multifunzione a un singolo progetto. Questa operazione è utile per eseguire una delle due attività seguenti:

- Creare barre multifunzione per Outlook *controlli*. Per altre informazioni, vedere [Personalizzare una barra multifunzione per Outlook](../vsto/customizing-a-ribbon-for-outlook.md).

    > [!NOTE]
    > Un controllo rappresenta una finestra che viene aperta quando gli utenti eseguono determinate attività, ad esempio la creazione di un messaggio di posta elettronica.

- Selezionare la barra multifunzione da visualizzare in fase di esecuzione.

### <a name="select-which-ribbons-to-display-at-run-time"></a>Selezionare le barre multifunzione da visualizzare in fase di esecuzione
 Poiché un progetto può contenere più di una barra multifunzione, è possibile selezionare la barra multifunzione da visualizzare in fase di esecuzione.

 Per selezionare una barra multifunzione da visualizzare in fase di esecuzione, eseguire l'override del metodo nella classe , o del progetto e restituire la barra `CreateRibbonExtensibilityObject` `ThisAddin` multifunzione da `ThisWorkbook` `ThisDocument` visualizzare. Nell'esempio seguente viene controllato il valore di un campo denominato `myCondition` e viene restituita la barra multifunzione appropriata.

> [!NOTE]
> La sintassi usata in questo esempio restituisce una barra multifunzione creata usando l'elemento **Barra multifunzione (finestra di progettazione** visiva). La sintassi per la restituzione di una barra multifunzione creata usando un elemento della barra **multifunzione (XML)** è leggermente diversa. Per altre informazioni sulla restituzione di un elemento **della barra multifunzione (XML),** vedere [XML della barra multifunzione.](../vsto/ribbon-xml.md)

 Aggiungere il codice seguente:

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_Ribbon_choose_Ribbon_4/ThisWorkbook.vb" id="Snippet1":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_Ribbon_choose_Ribbon_4/ThisWorkbook.cs" id="Snippet1":::

### <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Procedura: Iniziare a personalizzare la barra multifunzione](../vsto/how-to-get-started-customizing-the-ribbon.md)|Illustra come personalizzare la barra multifunzione di un'applicazione Microsoft Office, aggiungere un elemento Barra multifunzione **(finestra** di progettazione visiva) o Barra **multifunzione (XML)** a un Office progetto.|
|[Finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md)|Viene descritto come usare la finestra di progettazione della barra multifunzione per aggiungere schede, gruppi e controlli personalizzati alla barra multifunzione di un'Microsoft Office personalizzata.|
|[Procedura dettagliata: Creare una scheda personalizzata usando la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)|Illustra come creare una scheda personalizzata della barra multifunzione usando la finestra di progettazione della barra multifunzione. Questa finestra di progettazione può essere usata per aggiungere e posizionare controlli sulla scheda personalizzata.|
|[Panoramica del modello a oggetti della barra multifunzione](../vsto/ribbon-object-model-overview.md)|Fornisce una panoramica di un modello a oggetti fortemente tipizzato per ottenere e impostare le proprietà dei controlli della barra multifunzione in fase di esecuzione.|
|[Procedura dettagliata: Aggiornare i controlli in una barra multifunzione in fase di esecuzione](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)|Mostra come usare il modello a oggetti della barra multifunzione per aggiornare i controlli in una barra multifunzione dopo che è stata caricata nell'applicazione di Office.|
|[Personalizzare una barra multifunzione per Outlook](../vsto/customizing-a-ribbon-for-outlook.md)|Fornisce indicazioni per la personalizzazione della barra multifunzione in Microsoft Office Outlook.|
|[Personalizzare una barra multifunzione per InfoPath](../vsto/customizing-a-ribbon-for-infopath.md)|Fornisce indicazioni per la personalizzazione della barra multifunzione in Microsoft Office InfoPath.|
|[Accedere alla barra multifunzione in fase di esecuzione](../vsto/accessing-the-ribbon-at-run-time.md)|Illustra come visualizzare, nascondere e modificare la barra multifunzione e consentire agli utenti di eseguire il codice dai controlli in un riquadro attività personalizzato, in un riquadro azioni o in un Outlook del modulo.|
|[Procedura: Modificare la posizione di una scheda sulla barra multifunzione](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)|Illustra come modificare l'ordine delle schede in una barra multifunzione.|
|[Procedura: Personalizzare una scheda incorporata](../vsto/how-to-customize-a-built-in-tab.md)|Illustra come aggiungere gruppi e controlli a una scheda incorporata.|
|[Procedura: Aggiungere controlli alla visualizzazione Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)|Illustra come aggiungere controlli al menu visualizzato quando si fa clic su **File**.|
|[Procedura: Aggiungere un'utilità di avvio della finestra di dialogo a un gruppo della barra multifunzione](../vsto/how-to-add-a-dialog-box-launcher-to-a-ribbon-group.md)|Mostra come aggiungere un'utilità di avvio della finestra di dialogo a qualsiasi gruppo su una barra multifunzione.|
|[Procedura: Esportare una barra multifunzione dalla finestra di progettazione della barra multifunzione al file XML della barra multifunzione](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)|Illustra come personalizzare la barra multifunzione in modi avanzati esportando la barra multifunzione dalla finestra di progettazione al file XML della barra multifunzione.|
|[Ribbon XML](../vsto/ribbon-xml.md)|Viene illustrato come personalizzare una barra multifunzione usando xml della barra multifunzione.|
|[Procedura dettagliata: Creare una scheda personalizzata usando la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)|Illustra come creare una scheda personalizzata della barra multifunzione usando **l'elemento barra multifunzione (XML).**|
