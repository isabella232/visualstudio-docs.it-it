---
title: soluzioni InfoPath
description: Informazioni su come usare Visual Studio per creare VSTO componenti aggiuntivi per Microsoft InfoPath 2013 e InfoPath 2010.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], InfoPath
- templates [Office development in Visual Studio], InfoPath
- InfoPath [Office development in Visual Studio]
- Office development in Visual Studio, InfoPath solutions
- projects [Office development in Visual Studio], InfoPath
- Office solutions [Office development in Visual Studio], InfoPath
- Office projects [Office development in Visual Studio], InfoPath
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 22d8a0bf0ec927cff6499a8401ce0601add22f02
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122155699"
---
# <a name="infopath-solutions"></a>soluzioni InfoPath
  Visual Studio fornisce modelli di progetto che è possibile usare per creare componenti aggiuntivi VSTO per Microsoft Office InfoPath 2013 e InfoPath 2010. InfoPath non è disponibile in Office 2016.

> [!NOTE]
> È comunque possibile creare un VSTO componente aggiuntivo per InfoPath anche se è stato installato Office 2016. È sufficiente installare InfoPath 2013 o Office 2013 side-by-side con Office 2016.

 [!INCLUDE[appliesto_infoallapp](../vsto/includes/appliesto-infoallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 I componenti aggiuntivi VSTO per InfoPath sono simili ai componenti aggiuntivi VSTO per altre applicazioni di Microsoft Office. Questi tipi di soluzioni sono costituiti da un assembly caricato dall'applicazione. Gli utenti finali possono avere accesso alle funzionalità di questo assembly indipendentemente dal modulo o dal modello di modulo aperto. Per altre informazioni VSTO componenti aggiuntivi, vedere [](../vsto/getting-started-programming-vsto-add-ins.md) Introduzione alla programmazione VSTO componenti aggiuntivi e Architettura dei componenti aggiuntivi VSTO [componenti aggiuntivi](../vsto/architecture-of-vsto-add-ins.md).

> [!NOTE]
> Visual Studio 2015 non include i progetti del modello di modulo InfoPath forniti nelle versioni precedenti di Visual Studio. Non è nemmeno possibile usare Visual Studio 2015 per aprire o modificare un progetto del modello di modulo InfoPath creato in una versione precedente di Visual Studio. Tuttavia, è possibile aprire e modificare un progetto del modello di modulo InfoPath usando Visual Studio Tools for Applications. Per altre informazioni, vedere [Usare VSTO 2008 in InfoPath 2010.](/archive/blogs/infopath/working-with-vsto-2008-projects-in-infopath-2010)

## <a name="automate-infopath-by-using-an-add-in"></a>Automatizzare InfoPath tramite un componente aggiuntivo
 Per accedere al modello a oggetti InfoPath da un componente aggiuntivo VSTO di Office creato mediante gli strumenti di sviluppo per Office in Visual Studio, usare il campo `Application` della classe `ThisAddIn` nel progetto. Il campo `Application` restituisce un oggetto <xref:Microsoft.Office.Interop.InfoPath.Application> che rappresenta l'istanza corrente di InfoPath. Per altre informazioni, vedere [Programmi VSTO componenti aggiuntivi](../vsto/programming-vsto-add-ins.md).

 Quando si chiama il modello a oggetti di InfoPath da un componente aggiuntivo VSTO, si usano i tipi forniti nell'assembly di interoperabilità primario per InfoPath. L'assembly di interoperabilità primario agisce da ponte tra il codice gestito nel componente aggiuntivo VSTO e il modello a oggetti COM in InfoPath. Tutti i tipi nell'assembly di interoperabilità primario di InfoPath sono definiti nello spazio dei nomi <xref:Microsoft.Office.Interop.InfoPath> . Per altre informazioni sull'assembly di interoperabilità primario di InfoPath, vedere About the Microsoft Office InfoPath primary interop assembly ( Informazioni sull'assembly di interoperabilità primario [di InfoPath).](/office/client-developer/infopath/external-automation/about-the-microsoft-office-infopath-primary-interop-assembly) Per altre informazioni sugli assembly di interoperabilità primari in generale, vedere Office panoramica dello sviluppo di soluzioni &#40;VSTO&#41;[e](../vsto/office-solutions-development-overview-vsto.md) Office assembly di [interoperabilità primari](../vsto/office-primary-interop-assemblies.md).

## <a name="customize-the-user-interface-of-infopath-by-using-an-add-in"></a>Personalizzare l'interfaccia utente di InfoPath usando un componente aggiuntivo
 Quando si crea un componente VSTO componente aggiuntivo per InfoPath, sono disponibili diverse opzioni di personalizzazione dell'interfaccia utente. Nella tabella riportata di seguito vengono elencate alcune di queste opzioni.

|Attività|Per ulteriori informazioni|
|----------|--------------------------|
|Creare un riquadro attività personalizzato.|[Riquadri attività personalizzati](../vsto/custom-task-panes.md)|
|Aggiungere schede personalizzate alla barra multifunzione in InfoPath.|[Personalizzare una barra multifunzione per InfoPath](../vsto/customizing-a-ribbon-for-infopath.md)|

 Per altre informazioni sulla personalizzazione dell'interfaccia utente di InfoPath e altre Microsoft Office applicazioni, vedere Office [personalizzazione dell'interfaccia utente](../vsto/office-ui-customization.md).

## <a name="see-also"></a>Vedi anche
- [Informazioni sull'Microsoft Office di interoperabilità primario di InfoPath](/office/client-developer/infopath/external-automation/about-the-microsoft-office-infopath-primary-interop-assembly)
- [Introduzione alla programmazione VSTO componenti aggiuntivi](../vsto/getting-started-programming-vsto-add-ins.md)
- [Office panoramica dello sviluppo di soluzioni &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Architettura dei componenti aggiuntivi VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Procedura: Creare progetti Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Componenti VSTO programma](../vsto/programming-vsto-add-ins.md)
- [Scrivere codice in Office soluzioni](../vsto/writing-code-in-office-solutions.md)
- [Office assembly di interoperabilità primari](../vsto/office-primary-interop-assemblies.md)
- [Office Personalizzazione dell'interfaccia utente](../vsto/office-ui-customization.md)
- [InfoPath 2010 in Office sviluppo](/previous-versions/office/developer/office-2010/ff604966(v=office.14))