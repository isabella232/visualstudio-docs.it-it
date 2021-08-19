---
title: Office Personalizzazione dell'interfaccia utente
description: Informazioni su come personalizzare l'interfaccia utente delle applicazioni Microsoft Office usando gli strumenti di sviluppo Office in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- menus [Office development in Visual Studio], customizing
- actions panes [Office development in Visual Studio], creating
- WPF [Office development in Visual Studio]
- toolbars [Office development in Visual Studio], customizing
- Office applications [Office development in Visual Studio], UI customization
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 0b3f49a6e1ff74eda4561b4fc0283ca9196f8040
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122155629"
---
# <a name="office-ui-customization"></a>Office Personalizzazione dell'interfaccia utente
  È possibile personalizzare l'interfaccia utente (UI) delle applicazioni Microsoft Office mediante gli strumenti di sviluppo di Office in Visual Studio. Questo argomento descrive le funzionalità dell'interfaccia utente che è possibile personalizzare nelle sezioni seguenti:

- [Confronto delle funzionalità dell'interfaccia utente](#Comparison)

- [Riquadri azioni e riquadri attività personalizzati](#Actions)

- [Interfaccia utente della barra multifunzione personalizzata](#Ribbon)

- [Visualizzazione Backstage](#Backstage)

- [Aree del modulo di Outlook](#FormRegion)

- [Controlli sui documenti](#Controls)

- [Menu di scelta rapida](#Shortcut)

## <a name="comparison-of-ui-features"></a><a name="Comparison"></a> Confronto delle funzionalità dell'interfaccia utente
 Nella tabella seguente vengono confrontate le principali funzionalità dell'interfaccia utente che è possibile personalizzare nei progetti di Microsoft Office.

|Funzionalità|Tipi di progetti non supportati|Applicazioni Microsoft Office supportate|
|-------------|-----------------------------|---------------------------------------------|
|Riquadro Azioni|Personalizzazioni a livello di documento|Excel<br /><br /> Word|
|Riquadri attività personalizzati|Componenti aggiuntivi VSTO|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Word|
|Interfaccia utente della barra multifunzione personalizzata|Personalizzazioni a livello di documento<br /><br /> Componenti aggiuntivi VSTO|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Project<br /><br /> Word<br /><br /> Visio|
|Visualizzazione Backstage|Personalizzazioni a livello di documento<br /><br /> Componenti aggiuntivi VSTO|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)].<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Project<br /><br /> Word<br /><br /> Visio|
|Aree del modulo di Outlook|Componenti aggiuntivi VSTO|Outlook|
|Controlli sui documenti|Personalizzazioni a livello di documento<br /><br /> Componenti aggiuntivi VSTO|Excel<br /><br /> Word|
|Menu di scelta rapida|Personalizzazioni a livello di documento<br /><br /> Componenti aggiuntivi VSTO|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Project<br /><br /> Word<br /><br /> Visio<br /><br /> Excel|

## <a name="actions-panes-and-custom-task-panes"></a><a name="Actions"></a> Riquadri azioni e riquadri attività personalizzati
 I riquadri attività sono pannelli dell'interfaccia utente in genere ancorati a un lato di una finestra in un'applicazione di Microsoft Office. Quasi tutte le applicazioni di Microsoft Office includono riquadri attività incorporati. Un esempio di riquadro attività è il riquadro attività Guida in linea in Word.

 Gli strumenti di sviluppo per Office in Visual Studio forniscono due diversi modi per personalizzare i riquadri attività:

- È possibile aggiungere un riquadro azioni a una personalizzazione a livello di documento. Per impostazione predefinita, viene visualizzato il riquadro azioni sul lato destro dell'applicazione, a destra del documento. Tuttavia, il riquadro azioni può apparire anche a sinistra, in alto o in basso nel documento.

- È possibile aggiungere un riquadro attività personalizzato a un componente aggiuntivo VSTO. Gli utenti possono ancorare i riquadri attività personalizzati a diversi lati della finestra dell'applicazione oppure possono trascinare i riquadri attività personalizzati in qualsiasi posizione all'interno della finestra.

  I riquadri azioni e i riquadri attività personalizzati forniscono funzionalità grazie all'ampia gamma di controlli per consentire agli utenti di eseguire attività quali l'immissione di dati. Rispetto a un gruppo della barra multifunzione, i riquadri azioni e i riquadri attività personalizzati forniscono un'area molto più grande per includere testo e controlli.

  Per altre informazioni sui riquadri azioni, vedere [Panoramica del riquadro Azioni.](../vsto/actions-pane-overview.md) Per altre informazioni sui riquadri attività personalizzati, vedere [Riquadri attività personalizzati.](../vsto/custom-task-panes.md)

## <a name="custom-ribbon-ui"></a><a name="Ribbon"></a> Interfaccia utente personalizzata della barra multifunzione
 È possibile personalizzare l'interfaccia utente della barra multifunzione per esporre funzionalità da aggiungere alle applicazioni di Office. La barra multifunzione è un modo per organizzare i comandi correlati (sotto forma di controlli) in modo che siano più semplici da trovare. È possibile creare proprie schede della barra multifunzione e i gruppi per consentire agli utenti di accedere alle funzionalità offerte nella soluzione. La maggior parte delle funzionalità che erano accessibili tramite i menu e le barre degli strumenti nelle versioni precedenti di Microsoft Office ora è accessibile tramite la barra multifunzione.

 Per altre informazioni, vedere Panoramica [della barra multifunzione.](../vsto/ribbon-overview.md)

## <a name="backstage-view"></a><a name="Backstage"></a> Visualizzazione Backstage
 In Office applicazioni fare clic sulla **scheda File per** aprire la visualizzazione Backstage. Questa visualizzazione fornisce un'interfaccia utente che combina le azioni e le attività a livello di file e sostituisce la funzionalità simile disponibile dal pulsante Microsoft Office di Microsoft Office System 2007. La visualizzazione Backstage è completamente estensibile tramite XML.

 Visual Studio non fornisce una finestra di progettazione o l'API per la personalizzazione della visualizzazione Backstage. Tuttavia, se si aggiunge un elemento barra multifunzione **(XML)** al progetto Office, è possibile aggiungere codice XML al file XML della barra multifunzione per personalizzare la visualizzazione Backstage. Per altre informazioni sugli elementi **della barra multifunzione (XML),** vedere [XML della barra multifunzione.](../vsto/ribbon-xml.md)

 Per altre informazioni sulla personalizzazione della visualizzazione Backstage, vedere Introduction [to the Office 2010 Backstage view for developers](/previous-versions/office/developer/office-2010/ee691833(v=office.14)) (Introduzione alla visualizzazione Backstage di Office 2010 per gli sviluppatori) e Customize the Office [2010 Backstage view for developers](/previous-versions/office/developer/office-2010/ee815851(v=office.14))(Personalizzare la visualizzazione Backstage di Office 2010 per gli sviluppatori).

## <a name="outlook-form-regions"></a><a name="FormRegion"></a>Outlook aree del modulo
 Utilizzare aree di modulo per aggiungere funzionalità personalizzate ai moduli standard di Microsoft Office Outlook. È possibile creare aree del modulo che estendono qualsiasi modulo esistente con campi o controlli aggiuntivi. Se si crea una nuova area del modulo utilizzando gli strumenti di sviluppo per Office in Visual Studio, è possibile utilizzare solo i controlli Windows Form nell'area del modulo. Se si importa un'area di modulo progettata in Outlook, è possibile utilizzare solo controlli nativi di Outlook.

 È possibile creare aree del modulo che occupano aree diverse dell'interfaccia utente di Outlook. Ad esempio, le aree adiacenti del modulo vengono visualizzate nella parte inferiore della prima pagina di un modulo ed ogni area può essere compressa. È possibile, inoltre, aggiungere un’area del modulo separata visualizzata come pagina del modulo aggiuntiva completa che può apparire in qualsiasi modulo personalizzato o modulo standard esistente.

 Per altre informazioni, vedere [Creare Outlook modulo.](../vsto/creating-outlook-form-regions.md)

## <a name="controls-on-documents"></a><a name="Controls"></a> Controlli sui documenti
 È possibile aggiungere un'ampia gamma di controlli ai documenti di Word e ai fogli di lavoro di Excel. Ad esempio, è possibile aggiungere un controllo selezione data a un documento in modo che l'utente possa immettere le date in un formato standard o inserire un pulsante in un foglio di lavoro per inviare dati a un database.

 Quando si sviluppano progetti a livello di documento per Excel o Word, è possibile utilizzare la finestra di progettazione di Visual Studio per aggiungere questi controlli al documento o cartella di lavoro nel progetto in fase di creazione oppure aggiungere i controlli a livello di codice in fase di runtime. Quando si sviluppano progetti di componente aggiuntivo VSTO per Excel o Word, è possibile aggiungere controlli a livello di codice a qualsiasi cartella di lavoro o documento aperto in fase di esecuzione.

 Per altre informazioni, vedere [Panoramica degli elementi host](../vsto/host-items-and-host-controls-overview.md) e dei controlli host e Windows dei form Office panoramica dei [documenti.](../vsto/windows-forms-controls-on-office-documents-overview.md)

## <a name="shortcut-menus"></a><a name="Shortcut"></a> Menu di scelta rapida
 Quando si preme il pulsante destro del mouse in un documento o in una finestra dell'applicazione, viene visualizzato un menu di scelta rapida. È possibile impostare un menu di scelta rapida in modo che venga visualizzato dopo un evento, ad esempio quando un utente fa clic con il pulsante destro del mouse su un documento, una cartella di lavoro o un controllo host. È possibile aggiungere diversi comandi o controlli di menu a a un menu di scelta rapida. Creare menu di scelta rapida utilizzando XML. Se si aggiunge un **elemento barra multifunzione (XML)** al progetto Office, è possibile aggiungere codice XML al file XML della barra multifunzione per creare menu di scelta rapida. Per altre informazioni sull'uso di XML per creare menu di scelta rapida, vedere [Procedura: Aggiungere comandi ai menu di scelta rapida.](../vsto/how-to-add-commands-to-shortcut-menus.md)

## <a name="see-also"></a>Vedi anche
- [Panoramica della barra multifunzione](../vsto/ribbon-overview.md)
- [Windows di controlli form in Office documenti](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Panoramica del riquadro Azioni](../vsto/actions-pane-overview.md)
- [Creare aree Outlook modulo](../vsto/creating-outlook-form-regions.md)
- [Riquadri attività personalizzati](../vsto/custom-task-panes.md)
- [Usare i controlli WPF in Office soluzioni](../vsto/using-wpf-controls-in-office-solutions.md)
- [Procedura: Visualizzare la scheda Sviluppatore sulla barra multifunzione](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)
- [Procedura: Visualizzare gli errori dell'interfaccia utente del componente aggiuntivo](../vsto/how-to-show-add-in-user-interface-errors.md)
- [Procedura dettagliata: Raccogliere dati usando un modulo Windows dati](../vsto/walkthrough-collecting-data-using-a-windows-form.md)
