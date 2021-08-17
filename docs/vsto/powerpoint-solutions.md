---
title: PowerPoint soluzioni
description: Informazioni su Visual Studio modelli di progetto che è possibile usare per creare VSTO componenti aggiuntivi per Microsoft PowerPoint.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office solutions [Office development in Visual Studio], PowerPoint
- templates [Office development in Visual Studio], PowerPoint
- solutions [Office development in Visual Studio], PowerPoint
- projects [Office development in Visual Studio], PowerPoint
- PowerPoint [Office development in Visual Studio]
- Office projects [Office development in Visual Studio], PowerPoint
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 97cec1fe5e1954ff04c56f40e3b0313aa35c2170
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122025901"
---
# <a name="powerpoint-solutions"></a>PowerPoint soluzioni
  Visual Studio fornisce modelli di progetto che è possibile usare per creare componenti aggiuntivi VSTO per Microsoft Office PowerPoint. È possibile usare i componenti aggiuntivi VSTO per automatizzare PowerPoint, estenderne le funzionalità o personalizzarne l'interfaccia utente.

 Per altre informazioni VSTO componenti aggiuntivi, [](getting-started-programming-vsto-add-ins.md) vedere Introduzione alla programmazione VSTO componenti aggiuntivi e Architettura di VSTO [componenti aggiuntivi](architecture-of-vsto-add-ins.md). Se non si ha esperienza di programmazione con Microsoft Office, vedere Introduzione &#40;Office [sviluppo in Visual Studio&#41;](getting-started-office-development-in-visual-studio.md).

 [!INCLUDE[appliesto_pptallapp](includes/appliesto-pptallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="automate-powerpoint-by-using-the-powerpoint-object-model"></a>Automatizzare PowerPoint usando il modello PowerPoint a oggetti
 Il modello a oggetti di PowerPoint espone molti tipi che è possibile usare per automatizzare PowerPoint. Questi tipi consentono di scrivere il codice per eseguire attività comuni:

- Creare e formattare presentazioni a livello di codice.

- Aggiungere o rimuovere diapositive dalle presentazioni.

- Aggiungere o modificare forme su una diapositiva.

  Per accedere al PowerPoint a oggetti da VSTO componente aggiuntivo, usare il campo `Application` della `ThisAddIn` classe nel progetto. Il `Application` campo restituisce un oggetto [Application](/previous-versions/office/developer/office-2010/ff764034(v=office.14)) che rappresenta l'istanza corrente di PowerPoint. Per altre informazioni, vedere [Programmi VSTO componenti aggiuntivi](programming-vsto-add-ins.md).

  Quando si effettuano chiamate nel modello a oggetti di PowerPoint, si USANO i tipi forniti nell'assembly di interoperabilità primario per PowerPoint. L'assembly di interoperabilità primario agisce da ponte tra il codice gestito nel componente aggiuntivo VSTO e il modello a oggetti COM in PowerPoint. Tutti i tipi nell PowerPoint assembly di interoperabilità primario sono definiti in [Microsoft.Office. Interoperabilità. PowerPoint](/previous-versions/office/developer/office-2010/ff763170(v=office.14)) Namespace. Per altre informazioni sugli assembly di interoperabilità primari, vedere [panoramica](office-solutions-development-overview-vsto.md) Office sviluppo di soluzioni &#40;VSTO&#41;e Office assembly [di interoperabilità primari](office-primary-interop-assemblies.md).

## <a name="use-the-powerpoint-object-model-documentation"></a><a name="WordOMDocumentation"></a>Usare la documentazione PowerPoint modello a oggetti
 Per informazioni complete sul modello a oggetti di PowerPoint, è possibile usare il riferimento di assembly di interoperabilità primario (PIA) di PowerPoint e il riferimento del modello a oggetti VBA.

### <a name="primary-interop-assembly-reference"></a>Informazioni di riferimento sull'assembly di interoperabilità primario
 Nella documentazione di riferimento dell'assembly di interoperabilità primario (PIA) di PowerPoint sono descritti i tipi di assembly di interoperabilità primario per PowerPoint. Questa documentazione è disponibile nel percorso seguente: riferimento all'assembly di interoperabilità primario [PowerPoint 2010.](office-primary-interop-assemblies.md)

 Per altre informazioni sulla progettazione dell'assembly di interoperabilità primario PowerPoint, ad esempio le differenze tra classi e interfacce nell'assembly di interoperabilità primario e il modo in cui vengono implementati gli eventi nell'assembly di interoperabilità primario, vedere Panoramica delle classi e delle interfacce negli assembly di interoperabilità primari [di Office](/previous-versions/office/developer/office-2010/ff759900(v=office.14)).

### <a name="vba-object-model-reference"></a>Informazioni di riferimento sul modello a oggetti VBA
 Nel riferimento del modello a oggetti VBA è illustrato il modello a oggetti di PowerPoint esposto al codice Visual Basic Applications (VBA). Per altre informazioni, vedere PowerPoint riferimento al modello a oggetti [di 2010.](/office/vba/api/overview/PowerPoint/object-model)

 Tutti gli oggetti e i membri nel riferimento del modello a oggetti VBA corrispondono a tipi e membri nell'assembly di interoperabilità primario (PIA) di PowerPoint. Ad esempio, l'oggetto Presentation nel riferimento al modello a oggetti VBA corrisponde al tipo [Presentation](/previous-versions/office/developer/office-2010/ff761925(v=office.14)) PowerPoint PIA. Nonostante il riferimento del modello a oggetti VBA fornisca esempi di codice per la maggior parte delle proprietà, dei metodi e degli eventi, è necessario convertire il codice VBA in questo riferimento a Visual Basic o a Visual C# se si vuole usarli in un progetto di componente aggiuntivo VSTO PowerPoint creato con Visual Studio.

## <a name="customize-the-user-interface-of-powerpoint"></a>Personalizzare l'interfaccia utente di PowerPoint
 È possibile modificare l'interfaccia utente di PowerPoint nei modi seguenti.

|Attività|Per ulteriori informazioni|
|----------|--------------------------|
|Creare un riquadro attività personalizzato.|[Riquadri attività personalizzati](custom-task-panes.md)|
|Aggiungere schede personalizzate alla barra multifunzione.|[Panoramica della barra multifunzione](ribbon-overview.md)|
|Aggiungere gruppi personalizzati a una scheda incorporata nella barra multifunzione.|[Procedura: Personalizzare una scheda incorporata](how-to-customize-a-built-in-tab.md)|

 Per altre informazioni sulla personalizzazione dell'interfaccia utente di PowerPoint e altre Microsoft Office applicazioni, vedere Office [personalizzazione dell'interfaccia utente](office-ui-customization.md).

## <a name="see-also"></a>Vedi anche
- [Procedura dettagliata: Creare il primo VSTO componente aggiuntivo per PowerPoint](walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)
- [Introduzione alla programmazione VSTO componenti aggiuntivi](getting-started-programming-vsto-add-ins.md)
- [Office panoramica dello sviluppo di soluzioni &#40;VSTO&#41;](office-solutions-development-overview-vsto.md)
- [Architettura dei componenti aggiuntivi VSTO](architecture-of-vsto-add-ins.md)
- [Procedura: Creare Office progetti in Visual Studio](how-to-create-office-projects-in-visual-studio.md)
- [Componenti aggiuntivi VSTO programma](programming-vsto-add-ins.md)
- [Scrivere codice in Office soluzioni](writing-code-in-office-solutions.md)
- [Office assembly di interoperabilità primari](office-primary-interop-assemblies.md)
- [Office Personalizzazione dell'interfaccia utente](office-ui-customization.md)
- [PowerPoint 2010 in Office sviluppo](/previous-versions/office/developer/office-2010/ff604967(v=office.14))
