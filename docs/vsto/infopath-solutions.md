---
title: soluzioni InfoPath
description: Informazioni su come usare Visual Studio per creare componenti aggiuntivi VSTO per Microsoft InfoPath 2013 e InfoPath 2010.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8d5e26614c7f06c803093cd7e19b7e9842b397fb
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527744"
---
# <a name="infopath-solutions"></a>soluzioni InfoPath
  Visual Studio fornisce modelli di progetto che è possibile usare per creare componenti aggiuntivi VSTO per Microsoft Office InfoPath 2013 e InfoPath 2010. InfoPath non è disponibile in Office 2016.

> [!NOTE]
> È comunque possibile creare un componente aggiuntivo VSTO per InfoPath anche se è stato installato Office 2016. È sufficiente installare InfoPath 2013 o Office 2013 side-by-side con Office 2016.

 [!INCLUDE[appliesto_infoallapp](../vsto/includes/appliesto-infoallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 I componenti aggiuntivi VSTO per InfoPath sono simili ai componenti aggiuntivi VSTO per altre applicazioni di Microsoft Office. Questi tipi di soluzioni sono costituiti da un assembly caricato dall'applicazione. Gli utenti finali possono avere accesso alle funzionalità di questo assembly indipendentemente dal modulo o dal modello di modulo aperto. Per altre informazioni sui componenti aggiuntivi VSTO, vedere [Introduzione alla programmazione di componenti aggiuntivi VSTO](../vsto/getting-started-programming-vsto-add-ins.md) e [architettura dei componenti aggiuntivi VSTO](../vsto/architecture-of-vsto-add-ins.md).

> [!NOTE]
> Visual Studio 2015 non include i progetti del modello di modulo InfoPath forniti nelle versioni precedenti di Visual Studio. Non è nemmeno possibile usare Visual Studio 2015 per aprire o modificare un progetto del modello di modulo InfoPath creato in una versione precedente di Visual Studio. Tuttavia, è possibile aprire e modificare un progetto del modello di modulo InfoPath usando Visual Studio Tools for Applications. Per ulteriori informazioni, vedere la pagina relativa all' [utilizzo dei progetti VSTO 2008 in InfoPath 2010.](/archive/blogs/infopath/working-with-vsto-2008-projects-in-infopath-2010)

## <a name="automate-infopath-by-using-an-add-in"></a>Automatizzare InfoPath utilizzando un componente aggiuntivo
 Per accedere al modello a oggetti InfoPath da un componente aggiuntivo VSTO di Office creato mediante gli strumenti di sviluppo per Office in Visual Studio, usare il campo `Application` della classe `ThisAddIn` nel progetto. Il campo `Application` restituisce un oggetto <xref:Microsoft.Office.Interop.InfoPath.Application> che rappresenta l'istanza corrente di InfoPath. Per altre informazioni, vedere [Program VSTO Add-ins](../vsto/programming-vsto-add-ins.md).

 Quando si effettuano chiamate nel modello a oggetti di InfoPath da un componente aggiuntivo VSTO, si usano i tipi forniti nell'assembly di interoperabilità primario per InfoPath. L'assembly di interoperabilità primario agisce da ponte tra il codice gestito nel componente aggiuntivo VSTO e il modello a oggetti COM in InfoPath. Tutti i tipi nell'assembly di interoperabilità primario di InfoPath sono definiti nello spazio dei nomi <xref:Microsoft.Office.Interop.InfoPath> . Per ulteriori informazioni sull'assembly di interoperabilità primario di InfoPath, vedere [informazioni sull'assembly di](/office/client-developer/infopath/external-automation/about-the-microsoft-office-infopath-primary-interop-assembly)interoperabilità primario di InfoPath Microsoft Office. Per altre informazioni generali sugli assembly di interoperabilità primari, vedere [Cenni preliminari sullo sviluppo di soluzioni Office &#40;&#41;VSTO ](../vsto/office-solutions-development-overview-vsto.md) e [assembly di interoperabilità primari di Office](../vsto/office-primary-interop-assemblies.md).

## <a name="customize-the-user-interface-of-infopath-by-using-an-add-in"></a>Personalizzare l'interfaccia utente di InfoPath utilizzando un componente aggiuntivo
 Quando si crea un componente aggiuntivo VSTO per InfoPath, sono disponibili diverse opzioni di personalizzazione dell'interfaccia utente. Nella tabella riportata di seguito vengono elencate alcune di queste opzioni.

|Attività|Per ulteriori informazioni|
|----------|--------------------------|
|Creare un riquadro attività personalizzato.|[Riquadri attività personalizzati](../vsto/custom-task-panes.md)|
|Aggiungere schede personalizzate alla barra multifunzione in InfoPath.|[Personalizzare una barra multifunzione per InfoPath](../vsto/customizing-a-ribbon-for-infopath.md)|

 Per ulteriori informazioni sulla personalizzazione dell'interfaccia utente di InfoPath e di altre applicazioni di Microsoft Office, vedere [personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md).

## <a name="see-also"></a>Vedere anche
- [Informazioni sull'assembly di interoperabilità primario di Microsoft Office InfoPath](/office/client-developer/infopath/external-automation/about-the-microsoft-office-infopath-primary-interop-assembly)
- [Introduzione alla programmazione di componenti aggiuntivi VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
- [Panoramica sullo sviluppo di soluzioni Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Architettura dei componenti aggiuntivi VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Componenti aggiuntivi VSTO di programma](../vsto/programming-vsto-add-ins.md)
- [Scrivere codice nelle soluzioni Office](../vsto/writing-code-in-office-solutions.md)
- [Assembly di interoperabilità primari di Office](../vsto/office-primary-interop-assemblies.md)
- [Personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md)
- [InfoPath 2010 nello sviluppo per Office](/previous-versions/office/developer/office-2010/ff604966(v=office.14))