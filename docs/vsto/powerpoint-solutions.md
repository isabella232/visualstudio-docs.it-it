---
title: Soluzioni PowerPoint
ms.date: 02/02/2017
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
ms.openlocfilehash: 8ae3d06b2f031ed2deede1a80bec356a0abd939e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60040230"
---
# <a name="powerpoint-solutions"></a>Soluzioni PowerPoint
  Visual Studio fornisce modelli di progetto che è possibile usare per creare componenti aggiuntivi VSTO per Microsoft Office PowerPoint. È possibile usare i componenti aggiuntivi VSTO per automatizzare PowerPoint, estenderne le funzionalità o personalizzarne l'interfaccia utente.

 Per altre informazioni sui componenti aggiuntivi VSTO, vedere [iniziare a usare programming VSTO Add-ins](../vsto/getting-started-programming-vsto-add-ins.md) e [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md). Se ha familiarità con la programmazione con Microsoft Office, vedere [iniziare a usare &#40;sviluppo per Office in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md).

 [!INCLUDE[appliesto_pptallapp](../vsto/includes/appliesto-pptallapp-md.md)]

> [!NOTE]
>  Se ti interessa sviluppare soluzioni che estendono l'esperienza di Office attraverso [piattaforme multiple](https://dev.office.com/add-in-availability)? Consultare la nuova [modello di componenti aggiuntivi di Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Componenti aggiuntivi di Office con footprint ridotto rispetto alle soluzioni e componenti aggiuntivi VSTO e si possono essere compilate usando praticamente qualsiasi tecnologia, ad esempio HTML5, JavaScript, CSS3 e XML di programmazione web.

 ![collegamento a video](../vsto/media/playvideo.gif "collegamento a video") per una dimostrazione video correlata, vedere [ricerca per categorie Creare un componente aggiuntivo per Microsoft PowerPoint? ](http://go.microsoft.com/fwlink/?LinkId=132767).

## <a name="automate-powerpoint-by-using-the-powerpoint-object-model"></a>Automazione di PowerPoint usando il modello a oggetti PowerPoint
 Il modello a oggetti di PowerPoint espone molti tipi che è possibile usare per automatizzare PowerPoint. Questi tipi consentono di scrivere il codice per eseguire attività comuni:

- Creare e formattare presentazioni a livello di codice.

- Aggiungere o rimuovere diapositive dalle presentazioni.

- Aggiungere o modificare forme su una diapositiva.

  Per accedere a modello a oggetti di PowerPoint da un componente aggiuntivo VSTO, usare il `Application` campo il `ThisAddIn` classe nel progetto. Il campo `Application` restituisce un oggetto <xref:Microsoft.Office.Interop.PowerPoint.Application> che rappresenta l'istanza corrente di PowerPoint. Per altre informazioni, vedere [programma VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).

  Quando si effettuano chiamate nel modello a oggetti di PowerPoint, si USANO i tipi forniti nell'assembly di interoperabilità primario per PowerPoint. L'assembly di interoperabilità primario agisce da ponte tra il codice gestito nel componente aggiuntivo VSTO e il modello a oggetti COM in PowerPoint. Tutti i tipi dell'assembly di interoperabilità primario di PowerPoint sono definiti nello spazio dei nomi <xref:Microsoft.Office.Interop.PowerPoint> . Per altre informazioni sugli assembly di interoperabilità primari, vedere [Cenni preliminari sullo sviluppo di soluzioni Office &#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md) e [assembly di interoperabilità primari di Office](../vsto/office-primary-interop-assemblies.md).

## <a name="WordOMDocumentation"></a> Uso della documentazione sul modello a oggetti di PowerPoint
 Per informazioni complete sul modello a oggetti di PowerPoint, è possibile usare il riferimento di assembly di interoperabilità primario (PIA) di PowerPoint e il riferimento del modello a oggetti VBA.

### <a name="primary-interop-assembly-reference"></a>Riferimento all'assembly di interoperabilità primario
 Nella documentazione di riferimento dell'assembly di interoperabilità primario (PIA) di PowerPoint sono descritti i tipi di assembly di interoperabilità primario per PowerPoint. Questa documentazione è disponibile dal percorso seguente: [Riferimento all'assembly di interoperabilità primario di PowerPoint 2010](http://go.microsoft.com/fwlink/?LinkId=189588).

 Per altre informazioni sulla progettazione di PowerPoint assembly di interoperabilità primario, ad esempio le differenze tra classi e interfacce nell'assembly di interoperabilità primario e sull'implementazione degli eventi nell'assembly di interoperabilità primario, vedere [panoramica delle classi e interfacce negli assembly di interoperabilità primari di Office ](http://go.microsoft.com/fwlink/?LinkId=199885).

### <a name="vba-object-model-reference"></a>Riferimento del modello a oggetti VBA
 Nel riferimento del modello a oggetti VBA è illustrato il modello a oggetti di PowerPoint esposto al codice Visual Basic Applications (VBA). Per altre informazioni, vedere [riferimento di modello di oggetti di PowerPoint 2010](http://go.microsoft.com/fwlink/?LinkId=199770)

 Tutti gli oggetti e i membri nel riferimento del modello a oggetti VBA corrispondono a tipi e membri nell'assembly di interoperabilità primario (PIA) di PowerPoint. Ad esempio, l'oggetto di presentazione nel riferimento del modello a oggetti VBA corrisponde alla <xref:Microsoft.Office.Interop.PowerPoint.Presentation> tipo nell'assembly di interoperabilità primario di PowerPoint. Nonostante il riferimento del modello a oggetti VBA fornisca esempi di codice per la maggior parte delle proprietà, dei metodi e degli eventi, è necessario convertire il codice VBA in questo riferimento a Visual Basic o a Visual C# se si vuole usarli in un progetto di componente aggiuntivo VSTO PowerPoint creato con Visual Studio.

## <a name="customize-the-user-interface-of-powerpoint"></a>Personalizzare l'interfaccia utente di PowerPoint
 È possibile modificare l'interfaccia utente di PowerPoint nei modi seguenti.

|Attività|Per altre informazioni|
|----------|--------------------------|
|Creare un riquadro attività personalizzato.|[Riquadri attività personalizzati](../vsto/custom-task-panes.md)|
|Aggiungere schede personalizzate alla barra multifunzione.|[Panoramica della barra multifunzione](../vsto/ribbon-overview.md)|
|Aggiungere gruppi personalizzati a una scheda incorporata nella barra multifunzione.|[Procedura: Personalizzare una scheda incorporata](../vsto/how-to-customize-a-built-in-tab.md)|

 Per altre informazioni sulla personalizzazione dell'interfaccia utente di PowerPoint e altre applicazioni Microsoft Office, vedere [personalizzazione dell'interfaccia utente Office](../vsto/office-ui-customization.md).

## <a name="see-also"></a>Vedere anche
- [Procedura dettagliata: Creare un componente aggiuntivo di VSTO per PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)
- [Introduzione a programming VSTO Add-ins](../vsto/getting-started-programming-vsto-add-ins.md)
- [Panoramica dello sviluppo di soluzioni Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Architettura dei componenti aggiuntivi VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Procedura: Creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Programmazione di componenti aggiuntivi VSTO](../vsto/programming-vsto-add-ins.md)
- [Scrivere il codice nelle soluzioni Office](../vsto/writing-code-in-office-solutions.md)
- [Assembly di interoperabilità primari di Office](../vsto/office-primary-interop-assemblies.md)
- [Personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md)
- [PowerPoint 2010 nello sviluppo per Office](http://go.microsoft.com/fwlink/?LinkId=199015)
