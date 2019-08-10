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
ms.openlocfilehash: 9d2c85a4af986c62d3e3f3c3a3f4333baa2975ee
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/09/2019
ms.locfileid: "68926423"
---
# <a name="powerpoint-solutions"></a>Soluzioni PowerPoint
  Visual Studio fornisce modelli di progetto che è possibile usare per creare componenti aggiuntivi VSTO per Microsoft Office PowerPoint. È possibile usare i componenti aggiuntivi VSTO per automatizzare PowerPoint, estenderne le funzionalità o personalizzarne l'interfaccia utente.

 Per altre informazioni sui componenti aggiuntivi VSTO, vedere [Introduzione alla programmazione di componenti aggiuntivi VSTO](../vsto/getting-started-programming-vsto-add-ins.md) e [architettura dei componenti aggiuntivi VSTO](../vsto/architecture-of-vsto-add-ins.md). Se non si ha familiarità con la programmazione con Microsoft Office, vedere [Introduzione &#40;allo sviluppo per&#41;Office in Visual Studio](../vsto/getting-started-office-development-in-visual-studio.md).

 [!INCLUDE[appliesto_pptallapp](../vsto/includes/appliesto-pptallapp-md.md)]

> [!NOTE]
> Vuoi sviluppare soluzioni che estendono l'esperienza di Office su [più piattaforme](https://dev.office.com/add-in-availability)? Vedere il nuovo [modello di componenti](https://dev.office.com/docs/add-ins/overview/office-add-ins)aggiuntivi per Office. I componenti aggiuntivi di Office hanno un footprint ridotto rispetto alle soluzioni e ai componenti aggiuntivi VSTO e possono essere compilati con quasi tutte le tecnologie di programmazione Web, ad esempio HTML5, JavaScript, CSS3 e XML.

 ![collegamento al video](../vsto/media/playvideo.gif "collegamento al video") Per una dimostrazione video correlata, [vedere Ricerca per categorie: Creazione di un componente aggiuntivo per Microsoft PowerPoint ](http://go.microsoft.com/fwlink/?LinkId=132767).

## <a name="automate-powerpoint-by-using-the-powerpoint-object-model"></a>Automatizzare PowerPoint usando il modello a oggetti di PowerPoint
 Il modello a oggetti di PowerPoint espone molti tipi che è possibile usare per automatizzare PowerPoint. Questi tipi consentono di scrivere il codice per eseguire attività comuni:

- Creare e formattare presentazioni a livello di codice.

- Aggiungere o rimuovere diapositive dalle presentazioni.

- Aggiungere o modificare forme su una diapositiva.

  Per accedere al modello a oggetti di PowerPoint da un componente aggiuntivo VSTO, usare `Application` il campo `ThisAddIn` della classe nel progetto. Il `Application` campo restituisce un oggetto [applicazione](/previous-versions/office/developer/office-2010/ff764034(v=office.14)) che rappresenta l'istanza corrente di PowerPoint. Per altre informazioni, vedere [Program VSTO Add-ins](../vsto/programming-vsto-add-ins.md).

  Quando si effettuano chiamate nel modello a oggetti di PowerPoint, si USANO i tipi forniti nell'assembly di interoperabilità primario per PowerPoint. L'assembly di interoperabilità primario agisce da ponte tra il codice gestito nel componente aggiuntivo VSTO e il modello a oggetti COM in PowerPoint. Tutti i tipi nell'assembly di interoperabilità primario di PowerPoint sono definiti nello spazio dei nomi [Microsoft. Office. Interop. PowerPoint](/previous-versions/office/developer/office-2010/ff763170(v=office.14)) . Per altre informazioni sugli assembly di interoperabilità primari, vedere [Cenni &#40;preliminari&#41; sullo sviluppo di soluzioni Office](../vsto/office-solutions-development-overview-vsto.md) e assembly di interoperabilità [primari di Office](../vsto/office-primary-interop-assemblies.md).

## <a name="WordOMDocumentation"></a>Usare la documentazione del modello a oggetti di PowerPoint
 Per informazioni complete sul modello a oggetti di PowerPoint, è possibile usare il riferimento di assembly di interoperabilità primario (PIA) di PowerPoint e il riferimento del modello a oggetti VBA.

### <a name="primary-interop-assembly-reference"></a>Riferimento all'assembly di interoperabilità primario
 Nella documentazione di riferimento dell'assembly di interoperabilità primario (PIA) di PowerPoint sono descritti i tipi di assembly di interoperabilità primario per PowerPoint. Questa documentazione è disponibile nel percorso seguente: [Riferimento all'assembly di interoperabilità primario di PowerPoint 2010](http://go.microsoft.com/fwlink/?LinkId=189588).

 Per ulteriori informazioni sulla progettazione dell'assembly di interoperabilità primario di PowerPoint, ad esempio le differenze tra classi e interfacce nell'assembly di interoperabilità primario e il modo in cui vengono implementati gli eventi nell'assembly di interoperabilità primario di Office, vedere [Cenni preliminari sulle classi e sulle interfacce negli](http://go.microsoft.com/fwlink/?LinkId=199885)

### <a name="vba-object-model-reference"></a>Riferimento del modello a oggetti VBA
 Nel riferimento del modello a oggetti VBA è illustrato il modello a oggetti di PowerPoint esposto al codice Visual Basic Applications (VBA). Per altre informazioni, vedere [riferimento del modello a oggetti di PowerPoint 2010](http://go.microsoft.com/fwlink/?LinkId=199770).

 Tutti gli oggetti e i membri nel riferimento del modello a oggetti VBA corrispondono a tipi e membri nell'assembly di interoperabilità primario (PIA) di PowerPoint. Ad esempio, l'oggetto Presentation nel riferimento del modello a oggetti VBA corrisponde al tipo di [presentazione](/previous-versions/office/developer/office-2010/ff761925(v=office.14)) nell'assembly di interoperabilità primario di PowerPoint. Nonostante il riferimento del modello a oggetti VBA fornisca esempi di codice per la maggior parte delle proprietà, dei metodi e degli eventi, è necessario convertire il codice VBA in questo riferimento a Visual Basic o a Visual C# se si vuole usarli in un progetto di componente aggiuntivo VSTO PowerPoint creato con Visual Studio.

## <a name="customize-the-user-interface-of-powerpoint"></a>Personalizzare l'interfaccia utente di PowerPoint
 È possibile modificare l'interfaccia utente di PowerPoint nei modi seguenti.

|Attività|Per altre informazioni|
|----------|--------------------------|
|Creare un riquadro attività personalizzato.|[Riquadri attività personalizzati](../vsto/custom-task-panes.md)|
|Aggiungere schede personalizzate alla barra multifunzione.|[Panoramica della barra multifunzione](../vsto/ribbon-overview.md)|
|Aggiungere gruppi personalizzati a una scheda incorporata nella barra multifunzione.|[Procedura: Personalizzare una scheda incorporata](../vsto/how-to-customize-a-built-in-tab.md)|

 Per ulteriori informazioni sulla personalizzazione dell'interfaccia utente di PowerPoint e di altre applicazioni di Microsoft Office, vedere [personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md).

## <a name="see-also"></a>Vedere anche
- [Procedura dettagliata: Creare il primo componente aggiuntivo VSTO per PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)
- [Introduzione alla programmazione di componenti aggiuntivi VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
- [Panoramica &#40;dello sviluppo di soluzioni Office VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Architettura dei componenti aggiuntivi VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Procedura: Creazione di progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Componenti aggiuntivi VSTO di programma](../vsto/programming-vsto-add-ins.md)
- [Scrivere codice nelle soluzioni Office](../vsto/writing-code-in-office-solutions.md)
- [Assembly di interoperabilità primari di Office](../vsto/office-primary-interop-assemblies.md)
- [Personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md)
- [PowerPoint 2010 nello sviluppo per Office](http://go.microsoft.com/fwlink/?LinkId=199015)
