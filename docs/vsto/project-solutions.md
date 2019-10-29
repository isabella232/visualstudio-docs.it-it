---
title: Soluzioni di progetto
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 84dfe7cf86df2139b06a320d1c6441665a08a1b1
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985632"
---
# <a name="project-solutions"></a>Soluzioni di progetto
  [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] fornisce modelli di progetto che è possibile usare per creare componenti aggiuntivi VSTO per Microsoft Office Project. È possibile usare i componenti aggiuntivi VSTO per automatizzare Project, estenderne le funzionalità o personalizzarne l'interfaccia utente.

 Per altre informazioni sui componenti aggiuntivi VSTO, vedere [Introduzione alla programmazione di componenti aggiuntivi VSTO](../vsto/getting-started-programming-vsto-add-ins.md) e [architettura dei componenti aggiuntivi VSTO](../vsto/architecture-of-vsto-add-ins.md). Se non si ha familiarità con la programmazione con Microsoft Office, vedere [Introduzione &#40;allo sviluppo per&#41;Office in Visual Studio](../vsto/getting-started-office-development-in-visual-studio.md).

 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="automate-project-by-using-the-project-object-model"></a>Automatizzare il progetto usando il modello a oggetti di Project
 Il modello a oggetti di Project espone diversi tipi che è possibile usare per automatizzare Project. Questi tipi consentono di scrivere codice per eseguire attività comuni, ad esempio la creazione e la modifica di attività in un progetto a livello di codice.

 Per accedere al modello a oggetti di Project da un componente aggiuntivo VSTO, usare il campo `Application` della classe `ThisAddIn` nel progetto. Il campo `Application` restituisce un oggetto `Microsoft.Office.Interop.MsProject.Application` che rappresenta l'istanza corrente di Project. Per altre informazioni, vedere [Program VSTO Add-ins](../vsto/programming-vsto-add-ins.md).

 Quando si effettuano chiamate nel modello a oggetti di Project, si usano i tipi forniti nell'assembly di interoperabilità primario per Project. L'assembly di interoperabilità primario agisce da ponte tra il codice gestito nel componente aggiuntivo VSTO e il modello a oggetti COM in Project. Tutti i tipi dell'assembly di interoperabilità primario di Project sono definiti nello spazio dei nomi `Microsoft.Office.Interop.MSProject`. Per altre informazioni sugli assembly di interoperabilità primari, vedere [Cenni &#40;preliminari&#41; sullo sviluppo di soluzioni Office](../vsto/office-solutions-development-overview-vsto.md) e [assembly di interoperabilità primari di Office](../vsto/office-primary-interop-assemblies.md).

## <a name="use-the-project-object-model-documentation"></a>Usare la documentazione del modello a oggetti di Project
 Per informazioni complete sul modello a oggetti di Project, vedere la documentazione di riferimento del modello a oggetti VBA di Project. Nel riferimento del modello a oggetti VBA è illustrato il modello a oggetti di Project esposto al codice Visual Basic Applications (VBA). Per altre informazioni, vedere [riferimento del modello a oggetti di Project](/office/vba/api/project.object).

 Tutti gli oggetti e i membri nel riferimento del modello a oggetti VBA corrispondono a tipi e membri nell'assembly di interoperabilità primario (PIA) di Project. Ad esempio, l'oggetto Calendar nel riferimento del modello a oggetti VBA corrisponde al tipo di `Microsoft.Office.Interop.MSProject.Calendar` nell'assembly di interoperabilità primario del progetto. Sebbene il riferimento del modello a oggetti VBA fornisca esempi di codice per la maggior parte delle proprietà, dei metodi e degli eventi, è necessario convertire il codice VBA C# in questo riferimento a Visual Basic o a Visual se si vuole usarli in un progetto di componente aggiuntivo VSTO di Project creato da con Visual Studio.

> [!NOTE]
> Attualmente non è prevista la documentazione di riferimento per l'assembly di interoperabilità primario di Project.

### <a name="infrastructure-types-in-the-project-primary-interop-assembly"></a>Tipi di infrastruttura nell'assembly di interoperabilità primario di Project
 Quando si scrive un codice che usa l'assembly di interoperabilità primario di Project, si può notare che molti tipi non sono descritti nel riferimento di VBA. Questi tipi aggiuntivi, che consentono di convertire in codice gestito gli oggetti del modello a oggetti basato su COM di Project, non possono essere usati direttamente nel codice.

 Per ulteriori informazioni, vedere [Panoramica di classi e interfacce negli assembly di interoperabilità primari di Office](/previous-versions/office/office-12/ms247299(v=office.12)).

## <a name="customize-the-user-interface-of-project"></a>Personalizzare l'interfaccia utente del progetto
 È possibile personalizzare l'interfaccia utente di Project nei modi seguenti.

|Attività|Per altre informazioni|
|----------|--------------------------|
|Aggiungere schede personalizzate alla barra multifunzione in Project|[Panoramica della barra multifunzione](../vsto/ribbon-overview.md)|

 Per ulteriori informazioni sulla personalizzazione dell'interfaccia utente di Project e di altre applicazioni di Microsoft Office, vedere [personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md).

## <a name="see-also"></a>Vedere anche
- [Procedura dettagliata: creare il primo componente aggiuntivo VSTO per Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)
- [Introduzione alla programmazione di componenti aggiuntivi VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
- [Panoramica &#40;dello sviluppo di soluzioni Office VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Architettura dei componenti aggiuntivi VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Componenti aggiuntivi VSTO di programma](../vsto/programming-vsto-add-ins.md)
- [Scrivere codice nelle soluzioni Office](../vsto/writing-code-in-office-solutions.md)
- [Assembly di interoperabilità primari di Office](../vsto/office-primary-interop-assemblies.md)
- [Personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md)
- [Project 2010 e Project Server 2010 nello sviluppo per Office](/previous-versions/office/developer/office-2010/ee758031(v=office.14))
