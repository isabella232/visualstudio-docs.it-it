---
title: soluzioni Outlook
description: Informazioni su come usare VSTO componenti aggiuntivi per automatizzare Outlook, estendere Outlook funzionalità o personalizzare l'interfaccia Outlook utente.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 3ae690d5ef3aeaba6d587970f7dff1ddc34e4be7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122147856"
---
# <a name="outlook-solutions"></a>soluzioni Outlook
  Visual Studio offre modelli di progetto che è possibile usare per creare componenti aggiuntivi VSTO per Microsoft Office Outlook. È possibile usare i componenti aggiuntivi VSTO per automatizzare Outlook, estenderne le funzionalità o personalizzarne l'interfaccia utente. Per altre informazioni sui componenti aggiuntivi VSTO, vedere [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="create-an-outlook-vsto-add-in-project"></a>Creare un Outlook VSTO componente aggiuntivo Project
 Creare progetti Outlook usando uno dei modelli di progetto **Componente aggiuntivo per Outlook** nella finestra di dialogo **Nuovo progetto** . Questo modello include i riferimenti agli assembly e i file di progetto necessari.

 Per altre informazioni su come creare un progetto VSTO componente aggiuntivo, vedere [Procedura:](../vsto/how-to-create-office-projects-in-visual-studio.md)Creare Office progetti in Visual Studio . Per altre informazioni sui modelli di progetto, vedere panoramica Office [dei modelli di progetto.](../vsto/office-project-templates-overview.md)

## <a name="outlook-vsto-add-in-programming-model"></a>Outlook VSTO di programmazione del componente aggiuntivo
 Quando si crea un progetto di componente aggiuntivo VSTO per Outlook, Visual Studio genera una classe, chiamata `ThisAddIn`, che costituisce la base della soluzione. Questa classe fornisce un punto di partenza per la scrittura del codice ed espone inoltre il modello a oggetti di Outlook nel componente aggiuntivo VSTO.

 Per altre informazioni sulla classe e su altre funzionalità che è possibile usare in un componente aggiuntivo VSTO, vedere Componenti aggiuntivi VSTO `ThisAddIn` [programma](../vsto/programming-vsto-add-ins.md).

## <a name="automate-outlook-by-using-the-outlook-object-model"></a>Automatizzare Outlook usando il modello Outlook a oggetti
 Il modello a oggetti di Outlook espone diversi tipi che è possibile usare per automatizzare Outlook. Questi tipi consentono di scrivere il codice per eseguire attività comuni:

- Creare e inviare messaggi di posta elettronica a livello di codice.

- Inviare nuove convocazioni riunione.

- Cercare elementi in cartelle di Outlook.

  Per altre informazioni, vedere panoramica [del modello Outlook a oggetti](../vsto/outlook-object-model-overview.md).

## <a name="customize-the-user-interface-of-an-outlook-application"></a>Personalizzare l'interfaccia utente di un'Outlook personalizzata

|Attività|Per ulteriori informazioni|
|----------|--------------------------|
|Aggiungere schede personalizzate alla barra multifunzione di un controllo di Outlook.|[Panoramica della barra multifunzione](../vsto/ribbon-overview.md)|
|Aggiungere gruppi personalizzati a una scheda predefinita in un controllo di Outlook.|[Procedura: Personalizzare una scheda incorporata](../vsto/how-to-customize-a-built-in-tab.md)|
|Aggiungere un riquadro attività personalizzato da visualizzare in un controllo di Outlook|[Riquadri attività personalizzati](../vsto/custom-task-panes.md).|
|Aggiungere un'area del modulo che estende o sostituisce moduli di Outlook esistenti.|[Creare aree Outlook modulo](../vsto/creating-outlook-form-regions.md)|

 Per altre informazioni sulla personalizzazione dell'interfaccia utente di Outlook e altre Microsoft Office applicazioni, vedere Office [personalizzazione dell'interfaccia utente](../vsto/office-ui-customization.md).

## <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Outlook panoramica del modello a oggetti](../vsto/outlook-object-model-overview.md)|Contiene una panoramica degli oggetti forniti dal modello a oggetti di Word.|
|[Creare aree Outlook modulo](../vsto/creating-outlook-form-regions.md)|Descrive gli strumenti disponibili in Visual Studio che semplificano la progettazione, lo sviluppo e il debug delle aree del modulo.|
|[Procedura dettagliata: Creare la prima VSTO Add-In per Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)|Mostra come creare un componente aggiuntivo VSTO per Microsoft Office Outlook.|
|[Outlook 2010 in Office sviluppo](/previous-versions/office/developer/office-2010/ff458122(v=office.14))|Area di MSDN Library in cui è possibile trovare articoli e documentazione di riferimento sullo sviluppo di soluzioni Office (non specifiche per lo sviluppo di Office con Visual Studio).|
