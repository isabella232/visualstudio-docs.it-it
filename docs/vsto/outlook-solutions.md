---
title: soluzioni Outlook
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], Outlook
- Office projects [Office development in Visual Studio], Outlook
- Office solutions [Office development in Visual Studio], Outlook
- templates [Office development in Visual Studio], Outlook
- projects [Office development in Visual Studio], Outlook
- Outlook [Office development in Visual Studio]
- e-mail [Office development in Visual Studio], Outlook solutions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4150751cbb8de64fc237335bc26407f932276075
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442381"
---
# <a name="outlook-solutions"></a>soluzioni Outlook
  Visual Studio offre modelli di progetto che è possibile usare per creare componenti aggiuntivi VSTO per Microsoft Office Outlook. È possibile usare i componenti aggiuntivi VSTO per automatizzare Outlook, estenderne le funzionalità o personalizzarne l'interfaccia utente. Per altre informazioni sui componenti aggiuntivi VSTO, vedere [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

> [!NOTE]
> Se ti interessa sviluppare soluzioni che estendono l'esperienza di Office attraverso [piattaforme multiple](https://dev.office.com/add-in-availability)? Consultare la nuova [modello di componenti aggiuntivi di Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Componenti aggiuntivi di Office con footprint ridotto rispetto alle soluzioni e componenti aggiuntivi VSTO e si possono essere compilate usando praticamente qualsiasi tecnologia, ad esempio HTML5, JavaScript, CSS3 e XML di programmazione web.

## <a name="create-an-outlook-vsto-add-in-project"></a>Creare un progetto del componente aggiuntivo VSTO di Outlook
 Creare progetti Outlook usando uno dei modelli di progetto **Componente aggiuntivo per Outlook** nella finestra di dialogo **Nuovo progetto** . Questo modello include i riferimenti agli assembly e i file di progetto necessari.

 Per altre informazioni su come creare un progetto di componente aggiuntivo VSTO, vedere [come: Creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Per altre informazioni sui modelli di progetto, vedere [Cenni preliminari sui modelli di progetto di Office](../vsto/office-project-templates-overview.md).

## <a name="outlook-vsto-add-in-programming-model"></a>Outlook VSTO Add-in modello di programmazione
 Quando si crea un progetto di componente aggiuntivo VSTO per Outlook, Visual Studio genera una classe, chiamata `ThisAddIn`, che costituisce la base della soluzione. Questa classe fornisce un punto di partenza per la scrittura del codice ed espone inoltre il modello a oggetti di Outlook nel componente aggiuntivo VSTO.

 Per altre informazioni sul `ThisAddIn` classe e altre funzionalità, è possibile usare in un componente aggiuntivo VSTO, vedere [programma VSTO Add-ins](../vsto/programming-vsto-add-ins.md).

## <a name="automate-outlook-by-using-the-outlook-object-model"></a>Automatizzare Outlook usando il modello a oggetti
 Il modello a oggetti di Outlook espone diversi tipi che è possibile usare per automatizzare Outlook. Questi tipi consentono di scrivere il codice per eseguire attività comuni:

- Creare e inviare messaggi di posta elettronica a livello di codice.

- Inviare nuove convocazioni riunione.

- Cercare elementi in cartelle di Outlook.

  Per altre informazioni, vedere [Cenni preliminari sul modello a oggetti di Outlook](../vsto/outlook-object-model-overview.md).

## <a name="customize-the-user-interface-of-an-outlook-application"></a>Personalizzare l'interfaccia utente di un'applicazione di Outlook

|Attività|Per altre informazioni|
|----------|--------------------------|
|Aggiungere schede personalizzate alla barra multifunzione di un controllo di Outlook.|[Panoramica della barra multifunzione](../vsto/ribbon-overview.md)|
|Aggiungere gruppi personalizzati a una scheda predefinita in un controllo di Outlook.|[Procedura: Personalizzare una scheda incorporata](../vsto/how-to-customize-a-built-in-tab.md)|
|Aggiungere un riquadro attività personalizzato da visualizzare in un controllo di Outlook|[Riquadri attività personalizzati](../vsto/custom-task-panes.md).|
|Aggiungere un'area del modulo che estende o sostituisce moduli di Outlook esistenti.|[Creare aree del modulo di Outlook](../vsto/creating-outlook-form-regions.md)|

 Per altre informazioni sulla personalizzazione dell'interfaccia utente di Outlook e altre applicazioni Microsoft Office, vedere [personalizzazione dell'interfaccia utente Office](../vsto/office-ui-customization.md).

## <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Cenni preliminari sul modello a oggetti di Outlook](../vsto/outlook-object-model-overview.md)|Contiene una panoramica degli oggetti forniti dal modello a oggetti di Word.|
|[Creare aree del modulo di Outlook](../vsto/creating-outlook-form-regions.md)|Descrive gli strumenti disponibili in Visual Studio che semplificano la progettazione, lo sviluppo e il debug delle aree del modulo.|
|[Procedura dettagliata: Creare il primo aggiuntivo VSTO per Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)|Mostra come creare un componente aggiuntivo VSTO per Microsoft Office Outlook.|
|[Outlook 2010 nello sviluppo per Office](http://go.microsoft.com/fwlink/?LinkId=199013)|Area di MSDN Library in cui è possibile trovare articoli e documentazione di riferimento sullo sviluppo di soluzioni Office (non specifiche per lo sviluppo di Office con Visual Studio).|
