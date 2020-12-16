---
title: Soluzioni PowerPoint
description: Informazioni su come usare Visual Studio per creare i modelli di progetto che è possibile usare per creare componenti aggiuntivi VSTO per Microsoft PowerPoint.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4e297b0d269d5ff0bff0deeadd6bd346de00a324
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528039"
---
# <a name="powerpoint-solutions"></a>Soluzioni PowerPoint
  Visual Studio fornisce modelli di progetto che è possibile usare per creare componenti aggiuntivi VSTO per Microsoft Office PowerPoint. È possibile usare i componenti aggiuntivi VSTO per automatizzare PowerPoint, estenderne le funzionalità o personalizzarne l'interfaccia utente.

 Per altre informazioni sui componenti aggiuntivi VSTO, vedere [Introduzione alla programmazione di componenti aggiuntivi VSTO](getting-started-programming-vsto-add-ins.md) e [architettura dei componenti aggiuntivi VSTO](architecture-of-vsto-add-ins.md). Se non si ha familiarità con la programmazione con Microsoft Office, vedere [introduzione &#40;sviluppo per Office in Visual Studio&#41;](getting-started-office-development-in-visual-studio.md).

 [!INCLUDE[appliesto_pptallapp](includes/appliesto-pptallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="automate-powerpoint-by-using-the-powerpoint-object-model"></a>Automatizzare PowerPoint usando il modello a oggetti di PowerPoint
 Il modello a oggetti di PowerPoint espone molti tipi che è possibile usare per automatizzare PowerPoint. Questi tipi consentono di scrivere il codice per eseguire attività comuni:

- Creare e formattare presentazioni a livello di codice.

- Aggiungere o rimuovere diapositive dalle presentazioni.

- Aggiungere o modificare forme su una diapositiva.

  Per accedere al modello a oggetti di PowerPoint da un componente aggiuntivo VSTO, usare il `Application` campo della `ThisAddIn` classe nel progetto. Il `Application` campo restituisce un oggetto [applicazione](/previous-versions/office/developer/office-2010/ff764034(v=office.14)) che rappresenta l'istanza corrente di PowerPoint. Per altre informazioni, vedere [Program VSTO Add-ins](programming-vsto-add-ins.md).

  Quando si effettuano chiamate nel modello a oggetti di PowerPoint, si USANO i tipi forniti nell'assembly di interoperabilità primario per PowerPoint. L'assembly di interoperabilità primario agisce da ponte tra il codice gestito nel componente aggiuntivo VSTO e il modello a oggetti COM in PowerPoint. Tutti i tipi nell'assembly di interoperabilità primario di PowerPoint sono definiti nello spazio dei nomi [Microsoft. Office. Interop. PowerPoint](/previous-versions/office/developer/office-2010/ff763170(v=office.14)) . Per altre informazioni sugli assembly di interoperabilità primari, vedere [Panoramica sullo sviluppo di soluzioni Office &#40;&#41;VSTO ](office-solutions-development-overview-vsto.md) e [assembly di interoperabilità primari di Office](office-primary-interop-assemblies.md).

## <a name="use-the-powerpoint-object-model-documentation"></a><a name="WordOMDocumentation"></a> Usare la documentazione del modello a oggetti di PowerPoint
 Per informazioni complete sul modello a oggetti di PowerPoint, è possibile usare il riferimento di assembly di interoperabilità primario (PIA) di PowerPoint e il riferimento del modello a oggetti VBA.

### <a name="primary-interop-assembly-reference"></a>Riferimento all'assembly di interoperabilità primario
 Nella documentazione di riferimento dell'assembly di interoperabilità primario (PIA) di PowerPoint sono descritti i tipi di assembly di interoperabilità primario per PowerPoint. Questa documentazione è disponibile nel percorso seguente: [riferimento all'assembly di interoperabilità primario di PowerPoint 2010](office-primary-interop-assemblies.md).

 Per ulteriori informazioni sulla progettazione dell'assembly di interoperabilità primario di PowerPoint, ad esempio le differenze tra classi e interfacce nell'assembly di interoperabilità primario e il modo in cui vengono implementati gli eventi nell' [assembly di interoperabilità primario di Office, vedere Cenni preliminari sulle classi e sulle interfacce negli](/previous-versions/office/developer/office-2010/ff759900(v=office.14))

### <a name="vba-object-model-reference"></a>Riferimento del modello a oggetti VBA
 Nel riferimento del modello a oggetti VBA è illustrato il modello a oggetti di PowerPoint esposto al codice Visual Basic Applications (VBA). Per altre informazioni, vedere [riferimento del modello a oggetti di PowerPoint 2010](/office/vba/api/overview/PowerPoint/object-model).

 Tutti gli oggetti e i membri nel riferimento del modello a oggetti VBA corrispondono a tipi e membri nell'assembly di interoperabilità primario (PIA) di PowerPoint. Ad esempio, l'oggetto Presentation nel riferimento del modello a oggetti VBA corrisponde al tipo di [presentazione](/previous-versions/office/developer/office-2010/ff761925(v=office.14)) nell'assembly di interoperabilità primario di PowerPoint. Nonostante il riferimento del modello a oggetti VBA fornisca esempi di codice per la maggior parte delle proprietà, dei metodi e degli eventi, è necessario convertire il codice VBA in questo riferimento a Visual Basic o a Visual C# se si vuole usarli in un progetto di componente aggiuntivo VSTO PowerPoint creato con Visual Studio.

## <a name="customize-the-user-interface-of-powerpoint"></a>Personalizzare l'interfaccia utente di PowerPoint
 È possibile modificare l'interfaccia utente di PowerPoint nei modi seguenti.

|Attività|Per ulteriori informazioni|
|----------|--------------------------|
|Creare un riquadro attività personalizzato.|[Riquadri attività personalizzati](custom-task-panes.md)|
|Aggiungere schede personalizzate alla barra multifunzione.|[Panoramica della barra multifunzione](ribbon-overview.md)|
|Aggiungere gruppi personalizzati a una scheda incorporata nella barra multifunzione.|[Procedura: personalizzare una scheda incorporata](how-to-customize-a-built-in-tab.md)|

 Per ulteriori informazioni sulla personalizzazione dell'interfaccia utente di PowerPoint e di altre applicazioni di Microsoft Office, vedere [personalizzazione dell'interfaccia utente di Office](office-ui-customization.md).

## <a name="see-also"></a>Vedere anche
- [Procedura dettagliata: creare il primo componente aggiuntivo VSTO per PowerPoint](walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)
- [Introduzione alla programmazione di componenti aggiuntivi VSTO](getting-started-programming-vsto-add-ins.md)
- [Panoramica sullo sviluppo di soluzioni Office &#40;VSTO&#41;](office-solutions-development-overview-vsto.md)
- [Architettura dei componenti aggiuntivi VSTO](architecture-of-vsto-add-ins.md)
- [Procedura: creare progetti di Office in Visual Studio](how-to-create-office-projects-in-visual-studio.md)
- [Componenti aggiuntivi VSTO di programma](programming-vsto-add-ins.md)
- [Scrivere codice nelle soluzioni Office](writing-code-in-office-solutions.md)
- [Assembly di interoperabilità primari di Office](office-primary-interop-assemblies.md)
- [Personalizzazione dell'interfaccia utente di Office](office-ui-customization.md)
- [PowerPoint 2010 nello sviluppo per Office](/previous-versions/office/developer/office-2010/ff604967(v=office.14))
