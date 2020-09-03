---
title: Soluzioni Visio
ms.date: 08/14/2019
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
ms.openlocfilehash: a79b3c9964a24daf0a12ab90f47fb5903d89cdd0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72985501"
---
# <a name="visio-solutions"></a>Soluzioni Visio
  Visual Studio fornisce modelli di progetto che è possibile usare per creare componenti aggiuntivi VSTO per Microsoft Office Visio. È possibile usare i componenti aggiuntivi VSTO per automatizzare Visio, estenderne le funzionalità o personalizzarne l'interfaccia utente Visio.

 Per altre informazioni sui componenti aggiuntivi VSTO, vedere [Introduzione alla programmazione di componenti aggiuntivi VSTO](../vsto/getting-started-programming-vsto-add-ins.md) e [architettura dei componenti aggiuntivi VSTO](../vsto/architecture-of-vsto-add-ins.md). Se non si ha familiarità con la programmazione con Microsoft Office, vedere [introduzione &#40;sviluppo per Office in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md).

 **Si applica a:** le informazioni in questo argomento si applicano a progetti di componente aggiuntivo VSTO per Visio 2010. Per altre informazioni, vedere [Features Available by Office Application and Project Type](../vsto/features-available-by-office-application-and-project-type.md).

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="automate-visio-by-using-the-visio-object-model"></a>Automatizzare Visio usando il modello a oggetti di Visio
 Il modello a oggetti di Visio espone molte classi utilizzabili per automatizzare Visio affinché crei diagrammi per risorse di vario tipo, fra cui organigrammi, diagrammi di flusso, pianificazioni di progetto, diagrammi di rete e spazi di ufficio. L'API consente di scrivere codice per eseguire attività comuni:

- Creare e posizionare forme e testo nei diagrammi.

- Gestire il comportamento delle forme in base alla logica di business e all'input dell'utente.

- Controllare la visualizzazione dei diagrammi, ad esempio mediante panoramica e zoom.

- Personalizzare l'interfaccia utente dell'applicazione.

- Importare dati esterni in Visio, connetterli a forme e visualizzarli graficamente in una pagina.

  È possibile visualizzare procedure dettagliate ed esempi di codice per l'utilizzo del modello a oggetti di Visio per utilizzare documenti e forme in [utilizzare documenti di Visio](../vsto/working-with-visio-documents.md) e utilizzare le [forme di Visio](../vsto/working-with-visio-shapes.md).

  Per accedere al modello a oggetti di Visio da un componente aggiuntivo VSTO, usare nel progetto il campo `Application` della classe `ThisAddIn` . Il campo `Application` restituisce un oggetto `Microsoft.Office.Interop.Visio.Application` che rappresenta l'istanza corrente di Visio. Per altre informazioni, vedere [Program VSTO Add-ins](../vsto/programming-vsto-add-ins.md).

  Quando si effettuano chiamate nel modello a oggetti di Visio, si usano i tipi che sono stati forniti nell'assembly di interoperabilità primario (PIA) per Visio. L'assembly di interoperabilità primario funge da ponte tra il codice gestito nel componente aggiuntivo VSTO e il modello a oggetti COM in Visio. Tutti i tipi dell'assembly di interoperabilità primario di Visio sono definiti nello spazio dei nomi `Microsoft.Office.Interop.Visio`. Per altre informazioni sugli assembly di interoperabilità primari, vedere [Panoramica sullo sviluppo di soluzioni Office &#40;&#41;VSTO ](../vsto/office-solutions-development-overview-vsto.md) e [assembly di interoperabilità primari di Office](../vsto/office-primary-interop-assemblies.md).

## <a name="visio-object-model-overview"></a>Panoramica del modello a oggetti di Visio
 Per una panoramica del modello a oggetti di Visio, vedere [Cenni preliminari](../vsto/visio-object-model-overview.md)sul modello a oggetti di Visio, che include collegamenti al riferimento del modello a oggetti di Visio e agli SDK.

## <a name="customize-the-user-interface-of-visio"></a>Personalizzare l'interfaccia utente di Visio
 L'interfaccia utente di Visio offre le opzioni di personalizzazione seguenti.

|Attività|Per ulteriori informazioni|
|----------|--------------------------|
|Personalizzare la barra multifunzione.|[Cenni preliminari sulla barra multifunzione](../vsto/ribbon-overview.md)|

 Per informazioni sulla personalizzazione dell'interfaccia utente di Visio, vedere la documentazione di riferimento di VBA relativa alla classe [Visio.UIObject](/office/vba/api/Visio.UIObject) .

## <a name="see-also"></a>Vedere anche
- [Introduzione alla programmazione di componenti aggiuntivi VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
- [Panoramica sullo sviluppo di soluzioni Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)
- [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Componenti aggiuntivi VSTO di programma](../vsto/programming-vsto-add-ins.md)
- [Scrivere codice nelle soluzioni Office](../vsto/writing-code-in-office-solutions.md)
- [assembly di interoperabilità primari di Office](../vsto/office-primary-interop-assemblies.md)
- [Personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md)
- [Panoramica del modello a oggetti di Visio](../vsto/visio-object-model-overview.md)
- [Visio 2010 nello sviluppo per Office](/previous-versions/office/developer/office-2010/ff604964(v=office.14))
