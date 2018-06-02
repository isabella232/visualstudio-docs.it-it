---
title: Soluzioni Project
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c3364c778b8dfc290ef06b7daa5ba063ac31f3db
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/01/2018
ms.locfileid: "34692600"
---
# <a name="project-solutions"></a>Soluzioni Project
  [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] fornisce modelli di progetto che è possibile usare per creare componenti aggiuntivi VSTO per Microsoft Office Project. È possibile usare i componenti aggiuntivi VSTO per automatizzare Project, estenderne le funzionalità o personalizzarne l'interfaccia utente.  
  
 Per ulteriori informazioni sui componenti aggiuntivi VSTO, vedere [Introduzione alla programmazione di componenti aggiuntivi VSTO](../vsto/getting-started-programming-vsto-add-ins.md) e [architettura di aggiuntivi](../vsto/architecture-of-vsto-add-ins.md). Se si ha familiarità con la programmazione con Microsoft Office, vedere [Introduzione &#40;sviluppo per Office in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md).  
  
 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]  
  
> [!NOTE]  
>  Interessati allo sviluppo di soluzioni che estendono l'esperienza di Office in [più piattaforme](https://dev.office.com/add-in-availability)? Vedere la nuova [modello aggiuntivi di Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Componenti aggiuntivi di Office hanno un footprint ridotto rispetto alle soluzioni e i componenti aggiuntivi VSTO e possono essere creati con quasi tutte le tecnologie, ad esempio HTML5, JavaScript, CSS3 e XML di programmazione web.  
  
## <a name="automate-project-by-using-the-project-object-model"></a>Automatizzare progetto utilizzando il modello a oggetti progetto  
 Il modello a oggetti di Project espone diversi tipi che è possibile usare per automatizzare Project. Questi tipi consentono di scrivere codice per eseguire attività comuni, ad esempio la creazione e la modifica di attività in un progetto a livello di codice.  
  
 Per accedere al modello a oggetti di Project da un componente aggiuntivo VSTO, usare il campo `Application` della classe `ThisAddIn` nel progetto. Il `Application` campo restituisce un `Microsoft.Office.Interop.MsProject.Application` oggetto che rappresenta l'istanza corrente del progetto. Per altre informazioni, vedere [componenti aggiuntivi VSTO programma](../vsto/programming-vsto-add-ins.md).  
  
 Quando si effettuano chiamate nel modello a oggetti di Project, si usano i tipi forniti nell'assembly di interoperabilità primario per Project. L'assembly di interoperabilità primario agisce da ponte tra il codice gestito nel componente aggiuntivo VSTO e il modello a oggetti COM in Project. Tutti i tipi nell'assembly di interoperabilità primario di Project sono definiti nel `Microsoft.Office.Interop.MSProject` dello spazio dei nomi. Per ulteriori informazioni sugli assembly di interoperabilità primari, vedere [Cenni preliminari sullo sviluppo di soluzioni Office &#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md) e [assembly di interoperabilità primari di Office](../vsto/office-primary-interop-assemblies.md).  
  
## <a name="use-the-project-object-model-documentation"></a>Utilizzo della documentazione del modello oggetto progetto  
 Per informazioni complete sul modello a oggetti di Project, vedere la documentazione di riferimento del modello a oggetti VBA di Project. Nel riferimento del modello a oggetti VBA è illustrato il modello a oggetti di Project esposto al codice Visual Basic Applications (VBA). Per altre informazioni, vedere [riferimenti al modello a oggetti Project 2010](http://go.microsoft.com/fwlink/?LinkId=199771).  
  
 Tutti gli oggetti e i membri nel riferimento del modello a oggetti VBA corrispondono a tipi e membri nell'assembly di interoperabilità primario (PIA) di Project. Ad esempio, l'oggetto calendario nel riferimento del modello a oggetti VBA corrisponde al `Microsoft.Office.Interop.MSProject.Calendar` tipo nell'assembly di interoperabilità primario di Project. Sebbene il riferimento del modello a oggetti VBA fornisca esempi di codice per la maggior parte delle proprietà, dei metodi e degli eventi, è necessario convertire il codice VBA di questo riferimento in Visual Basic o Visual C# se si vuole usarli in un progetto di componente aggiuntivo VSTO di Project creato con Visual Studio.  
  
> [!NOTE]  
>  Attualmente non è prevista la documentazione di riferimento per l'assembly di interoperabilità primario di Project.  
  
### <a name="infrastructure-types-in-the-project-primary-interop-assembly"></a>Tipi di infrastruttura nell'assembly di interoperabilità primario di project  
 Quando si scrive un codice che usa l'assembly di interoperabilità primario di Project, si può notare che molti tipi non sono descritti nel riferimento di VBA. Questi tipi aggiuntivi, che consentono di convertire in codice gestito gli oggetti del modello a oggetti basato su COM di Project, non possono essere usati direttamente nel codice.  
  
 Per altre informazioni, vedere [Panoramica di classi e interfacce negli assembly di interoperabilità primari di Office](http://go.microsoft.com/fwlink/?LinkId=189592).  
  
## <a name="customize-the-user-interface-of-project"></a>Personalizzare l'interfaccia utente del progetto  
 È possibile personalizzare l'interfaccia utente di Project nei modi seguenti.  
  
|Attività|Per altre informazioni|  
|----------|--------------------------|  
|Aggiungere schede personalizzate alla barra multifunzione in Project|[Panoramica della barra multifunzione](../vsto/ribbon-overview.md)|  
  
 Per ulteriori informazioni sulla personalizzazione dell'interfaccia utente di Project e di altre applicazioni di Microsoft Office, vedere [personalizzazione dell'interfaccia utente Office](../vsto/office-ui-customization.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: Creare il primo aggiuntivo VSTO per project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)   
 [Introduzione alla programmazione di componenti aggiuntivi VSTO](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Cenni preliminari sullo sviluppo di soluzioni di Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Architettura dei componenti aggiuntivi VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programma-componenti aggiuntivi VSTO](../vsto/programming-vsto-add-ins.md)   
 [Scrivere il codice nelle soluzioni Office](../vsto/writing-code-in-office-solutions.md)   
 [Assembly di interoperabilità primari di Office](../vsto/office-primary-interop-assemblies.md)   
 [Personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md)   
 [Project 2010 e Project Server 2010 nello sviluppo per Office](http://go.microsoft.com/fwlink/?LinkId=199016)  
  
  