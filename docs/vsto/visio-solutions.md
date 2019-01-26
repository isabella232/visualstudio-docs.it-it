---
title: Soluzioni Visio
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], Visio
- solutions [Office development in Visual Studio], Visio
- Visio [Office development in Visual Studio]
- templates [Office development in Visual Studio], Visio
- projects [Office development in Visual Studio], Visio
- Office solutions [Office development in Visual Studio], Visio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 41a583b54caa706d0e103bb8652b80a25b6837b7
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "54873016"
---
# <a name="visio-solutions"></a>Soluzioni Visio
  Visual Studio fornisce modelli di progetto che è possibile usare per creare componenti aggiuntivi VSTO per Microsoft Office Visio. È possibile usare i componenti aggiuntivi VSTO per automatizzare Visio, estenderne le funzionalità o personalizzarne l'interfaccia utente Visio.  
  
 Per altre informazioni sui componenti aggiuntivi VSTO, vedere [iniziare a usare programming VSTO Add-ins](../vsto/getting-started-programming-vsto-add-ins.md) e [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md). Se ha familiarità con la programmazione con Microsoft Office, vedere [iniziare a usare &#40;sviluppo per Office in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md).  
  
 **Si applica a:** Le informazioni contenute in questo argomento si applicano ai progetti di componente aggiuntivo VSTO per Visio 2010. Per altre informazioni, vedere [Funzionalità disponibili in base ai tipi di progetto e applicazioni di Office](../vsto/features-available-by-office-application-and-project-type.md).  
  
> [!NOTE]  
>  Se ti interessa sviluppare soluzioni che estendono l'esperienza di Office attraverso [piattaforme multiple](https://dev.office.com/add-in-availability)? Consultare la nuova [modello di componenti aggiuntivi di Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Componenti aggiuntivi di Office con footprint ridotto rispetto alle soluzioni e componenti aggiuntivi VSTO e si possono essere compilate usando praticamente qualsiasi tecnologia, ad esempio HTML5, JavaScript, CSS3 e XML di programmazione web.  
  
## <a name="automate-visio-by-using-the-visio-object-model"></a>Automatizzare Visio usando il modello a oggetti Visio  
 Il modello a oggetti di Visio espone molte classi utilizzabili per automatizzare Visio affinché crei diagrammi per risorse di vario tipo, fra cui organigrammi, diagrammi di flusso, pianificazioni di progetto, diagrammi di rete e spazi di ufficio. L'API consente di scrivere codice per eseguire attività comuni:  
  
- Creare e posizionare forme e testo nei diagrammi.  
  
- Gestire il comportamento delle forme in base alla logica di business e all'input dell'utente.  
  
- Controllare la visualizzazione dei diagrammi, ad esempio mediante panoramica e zoom.  
  
- Personalizzare l'interfaccia utente dell'applicazione.  
  
- Importare dati esterni in Visio, connetterli a forme e visualizzarli graficamente in una pagina.  
  
  È possibile visualizzare procedure dettagliate ed esempi per usare il modello a oggetti di Visio per usare documenti e forme in di codice [lavorare con i documenti di Visio](../vsto/working-with-visio-documents.md) e [forme di Visio](../vsto/working-with-visio-shapes.md).  
  
  Per accedere al modello a oggetti di Visio da un componente aggiuntivo VSTO, usare nel progetto il campo `Application` della classe `ThisAddIn` . Il campo `Application` restituisce un oggetto `Microsoft.Office.Interop.Visio.Application` che rappresenta l'istanza corrente di Visio. Per altre informazioni, vedere [programma VSTO Add-ins](../vsto/programming-vsto-add-ins.md).  
  
  Quando si effettuano chiamate nel modello a oggetti di Visio, si usano i tipi che sono stati forniti nell'assembly di interoperabilità primario (PIA) per Visio. L'assembly di interoperabilità primario funge da ponte tra il codice gestito nel componente aggiuntivo VSTO e il modello a oggetti COM in Visio. Tutti i tipi dell'assembly di interoperabilità primario di Visio sono definiti nello spazio dei nomi `Microsoft.Office.Interop.Visio`. Per altre informazioni sugli assembly di interoperabilità primari, vedere [Cenni preliminari sullo sviluppo di soluzioni Office &#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md) e [assembly di interoperabilità primari di Office](../vsto/office-primary-interop-assemblies.md).  
  
## <a name="visio-object-model-overview"></a>Panoramica del modello a oggetti Visio  
 È possibile trovare una panoramica del modello a oggetti Visio in [Panoramica del modello a oggetti Visio](../vsto/visio-object-model-overview.md), che include i collegamenti per il riferimento del modello a oggetti Visio e agli SDK.  
  
## <a name="customize-the-user-interface-of-visio"></a>Personalizzare l'interfaccia utente di Visio  
 L'interfaccia utente di Visio offre le opzioni di personalizzazione seguenti.  
  
|Attività|Per altre informazioni|  
|----------|--------------------------|  
|Personalizzare la barra multifunzione.|[Panoramica della barra multifunzione](../vsto/ribbon-overview.md)|  
  
 Per informazioni sulla personalizzazione dell'interfaccia utente di Visio, vedere la documentazione di riferimento di VBA relativa alla classe [Visio.UIObject](/office/vba/api/Visio.UIObject) .  
  
## <a name="see-also"></a>Vedere anche  
 [Introduzione a programming VSTO Add-ins](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Panoramica dello sviluppo di soluzioni Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)   
 [Procedura: Creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programmazione di componenti aggiuntivi VSTO](../vsto/programming-vsto-add-ins.md)   
 [Scrivere il codice nelle soluzioni Office](../vsto/writing-code-in-office-solutions.md)   
 [Assembly di interoperabilità primari di Office](../vsto/office-primary-interop-assemblies.md)   
 [Personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md)   
 [Panoramica del modello a oggetti Visio](../vsto/visio-object-model-overview.md)   
 [Visio 2010 nello sviluppo per Office](http://go.microsoft.com/fwlink/?LinkId=199017)  
