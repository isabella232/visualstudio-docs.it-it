---
title: Project soluzioni
description: Informazioni su come usare VSTO componenti aggiuntivi per automatizzare Project, estendere Project funzionalità o personalizzare l'interfaccia Project utente.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [Office development in Visual Studio], Project
- Office solutions [Office development in Visual Studio], Project
- Project [Office development in Visual Studio]
- templates [Office development in Visual Studio], Project
- Office projects [Office development in Visual Studio], Project
- solutions [Office development in Visual Studio], Project
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 6d03ff38fbbf4084c8dd60738b2d5340d53638a1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122115044"
---
# <a name="project-solutions"></a>Project soluzioni
  [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] fornisce modelli di progetto che è possibile usare per creare componenti aggiuntivi VSTO per Microsoft Office Project. È possibile usare i componenti aggiuntivi VSTO per automatizzare Project, estenderne le funzionalità o personalizzarne l'interfaccia utente.

 Per altre informazioni VSTO componenti aggiuntivi, vedere [](../vsto/getting-started-programming-vsto-add-ins.md) Introduzione alla programmazione VSTO componenti aggiuntivi e Architettura dei componenti aggiuntivi VSTO [componenti aggiuntivi](../vsto/architecture-of-vsto-add-ins.md). Se non si ha esperienza di programmazione con Microsoft Office, vedere Introduzione &#40;Office [sviluppo in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md).

 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="automate-project-by-using-the-project-object-model"></a>Automatizzare il progetto usando il modello a oggetti del progetto
 Il modello a oggetti di Project espone diversi tipi che è possibile usare per automatizzare Project. Questi tipi consentono di scrivere codice per eseguire attività comuni, ad esempio la creazione e la modifica di attività in un progetto a livello di codice.

 Per accedere al Project a oggetti da un VSTO componente aggiuntivo, usare il campo `Application` della `ThisAddIn` classe nel progetto. Il `Application` campo restituisce un oggetto che rappresenta `Microsoft.Office.Interop.MsProject.Application` l'istanza corrente di Project. Per altre informazioni, vedere [Programmi VSTO componenti aggiuntivi](../vsto/programming-vsto-add-ins.md).

 Quando si effettuano chiamate nel modello a oggetti di Project, si usano i tipi forniti nell'assembly di interoperabilità primario per Project. L'assembly di interoperabilità primario agisce da ponte tra il codice gestito nel componente aggiuntivo VSTO e il modello a oggetti COM in Project. Tutti i tipi dell'assembly di interoperabilità primario di Project sono definiti nello spazio dei nomi `Microsoft.Office.Interop.MSProject`. Per altre informazioni sugli assembly di interoperabilità primari, vedere [Office](../vsto/office-solutions-development-overview-vsto.md) panoramica dello sviluppo di soluzioni &#40;VSTO&#41;e Office assembly [di interoperabilità primari](../vsto/office-primary-interop-assemblies.md).

## <a name="use-the-project-object-model-documentation"></a>Usare la documentazione del modello a oggetti del progetto
 Per informazioni complete sul modello a oggetti di Project, vedere la documentazione di riferimento del modello a oggetti VBA di Project. Nel riferimento del modello a oggetti VBA è illustrato il modello a oggetti di Project esposto al codice Visual Basic Applications (VBA). Per altre informazioni, vedere informazioni di [Project riferimento al modello a oggetti](/office/vba/api/project.object).

 Tutti gli oggetti e i membri nel riferimento del modello a oggetti VBA corrispondono a tipi e membri nell'assembly di interoperabilità primario (PIA) di Project. Ad esempio, l'oggetto Calendar nel riferimento al modello a oggetti VBA corrisponde al tipo `Microsoft.Office.Interop.MSProject.Calendar` nell'Project PIA. Anche se il riferimento al modello a oggetti VBA fornisce esempi di codice per la maggior parte delle proprietà, dei metodi e degli eventi, è necessario convertire il codice VBA in questo riferimento in Visual Basic o Visual C# se si vuole usarli in un progetto di componente aggiuntivo Project VSTO creato usando Visual Studio.

> [!NOTE]
> Attualmente non è prevista la documentazione di riferimento per l'assembly di interoperabilità primario di Project.

### <a name="infrastructure-types-in-the-project-primary-interop-assembly"></a>Tipi di infrastruttura nell'assembly di interoperabilità primario del progetto
 Quando si scrive un codice che usa l'assembly di interoperabilità primario di Project, si può notare che molti tipi non sono descritti nel riferimento di VBA. Questi tipi aggiuntivi, che consentono di convertire in codice gestito gli oggetti del modello a oggetti basato su COM di Project, non possono essere usati direttamente nel codice.

 Per altre informazioni, vedere Panoramica di classi e [interfacce negli Office di interoperabilità primari.](/previous-versions/office/office-12/ms247299(v=office.12))

## <a name="customize-the-user-interface-of-project"></a>Personalizzare l'interfaccia utente del progetto
 È possibile personalizzare l'interfaccia utente di Project nei modi seguenti.

|Attività|Per ulteriori informazioni|
|----------|--------------------------|
|Aggiungere schede personalizzate alla barra multifunzione in Project|[Panoramica della barra multifunzione](../vsto/ribbon-overview.md)|

 Per altre informazioni sulla personalizzazione dell'interfaccia utente di Project e altre Microsoft Office applicazioni, vedere Office [personalizzazione dell'interfaccia utente](../vsto/office-ui-customization.md).

## <a name="see-also"></a>Vedi anche
- [Procedura dettagliata: Creare il primo VSTO componente aggiuntivo per il progetto](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)
- [Introduzione alla programmazione VSTO componenti aggiuntivi](../vsto/getting-started-programming-vsto-add-ins.md)
- [Office panoramica dello sviluppo di soluzioni &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Architettura dei componenti aggiuntivi VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Procedura: Creare progetti Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Componenti VSTO programma](../vsto/programming-vsto-add-ins.md)
- [Scrivere codice in Office soluzioni](../vsto/writing-code-in-office-solutions.md)
- [Office assembly di interoperabilità primari](../vsto/office-primary-interop-assemblies.md)
- [Office Personalizzazione dell'interfaccia utente](../vsto/office-ui-customization.md)
- [Project 2010 e Project Server 2010 in Office sviluppo](/previous-versions/office/developer/office-2010/ee758031(v=office.14))
