---
title: Visio soluzioni
description: Informazioni su come usare VSTO componenti aggiuntivi per automatizzare Visio, estendere le funzionalità di Visio o personalizzare l'interfaccia utente Visio utente.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 14f3c77d35f0c2fea648897e091ac454dda5156b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122046217"
---
# <a name="visio-solutions"></a>Visio soluzioni
  Visual Studio fornisce modelli di progetto che è possibile usare per creare componenti aggiuntivi VSTO per Microsoft Office Visio. È possibile usare i componenti aggiuntivi VSTO per automatizzare Visio, estenderne le funzionalità o personalizzarne l'interfaccia utente Visio.

 Per altre informazioni sui VSTO, vedere [](../vsto/getting-started-programming-vsto-add-ins.md) Introduzione alla programmazione VSTO componenti aggiuntivi e Architettura VSTO [componenti aggiuntivi](../vsto/architecture-of-vsto-add-ins.md). Se non si ha esperienza di programmazione con Microsoft Office, vedere [Introduzione &#40;Office sviluppo in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md).

 **Si applica a:** le informazioni in questo argomento si applicano a progetti di componente aggiuntivo VSTO per Visio 2010. Per altre informazioni, vedere [Features Available by Office Application and Project Type](../vsto/features-available-by-office-application-and-project-type.md).

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="automate-visio-by-using-the-visio-object-model"></a>Automatizzare Visio usando il modello Visio a oggetti
 Il modello a oggetti di Visio espone molte classi utilizzabili per automatizzare Visio affinché crei diagrammi per risorse di vario tipo, fra cui organigrammi, diagrammi di flusso, pianificazioni di progetto, diagrammi di rete e spazi di ufficio. L'API consente di scrivere codice per eseguire attività comuni:

- Creare e posizionare forme e testo nei diagrammi.

- Gestire il comportamento delle forme in base alla logica di business e all'input dell'utente.

- Controllare la visualizzazione dei diagrammi, ad esempio mediante panoramica e zoom.

- Personalizzare l'interfaccia utente dell'applicazione.

- Importare dati esterni in Visio, connetterli a forme e visualizzarli graficamente in una pagina.

  È possibile visualizzare procedure dettagliate ed esempi di codice per l'uso del modello [a](../vsto/working-with-visio-documents.md) oggetti di Visio per lavorare con documenti e forme in Usare documenti di Visio e Usare forme Visio [.](../vsto/working-with-visio-shapes.md)

  Per accedere al modello a oggetti di Visio da un componente aggiuntivo VSTO, usare nel progetto il campo `Application` della classe `ThisAddIn` . Il campo `Application` restituisce un oggetto `Microsoft.Office.Interop.Visio.Application` che rappresenta l'istanza corrente di Visio. Per altre informazioni, vedere [Programmi VSTO componenti aggiuntivi](../vsto/programming-vsto-add-ins.md).

  Quando si effettuano chiamate nel modello a oggetti di Visio, si usano i tipi che sono stati forniti nell'assembly di interoperabilità primario (PIA) per Visio. L'assembly di interoperabilità primario funge da ponte tra il codice gestito nel componente aggiuntivo VSTO e il modello a oggetti COM in Visio. Tutti i tipi dell'assembly di interoperabilità primario di Visio sono definiti nello spazio dei nomi `Microsoft.Office.Interop.Visio`. Per altre informazioni sugli assembly di interoperabilità primari, vedere Office [sullo](../vsto/office-solutions-development-overview-vsto.md) sviluppo di soluzioni &#40;VSTO&#41;e Office assembly di [interoperabilità primari.](../vsto/office-primary-interop-assemblies.md)

## <a name="visio-object-model-overview"></a>Visio panoramica del modello a oggetti
 È possibile trovare una panoramica del modello Visio a oggetti in panoramica del modello [Visio a](../vsto/visio-object-model-overview.md)oggetti, che include collegamenti alle informazioni di riferimento sul modello Visio a oggetti e agli SDK.

## <a name="customize-the-user-interface-of-visio"></a>Personalizzare l'interfaccia utente di Visio
 L'interfaccia utente di Visio offre le opzioni di personalizzazione seguenti.

|Attività|Per ulteriori informazioni|
|----------|--------------------------|
|Personalizzare la barra multifunzione.|[Cenni preliminari sulla barra multifunzione](../vsto/ribbon-overview.md)|

 Per informazioni sulla personalizzazione dell'interfaccia utente di Visio, vedere la documentazione di riferimento di VBA relativa alla classe [Visio.UIObject](/office/vba/api/Visio.UIObject) .

## <a name="see-also"></a>Vedi anche
- [Introduzione alla programmazione VSTO componenti aggiuntivi](../vsto/getting-started-programming-vsto-add-ins.md)
- [Office sullo sviluppo di soluzioni &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Architettura dei componenti aggiuntivi VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Procedura: Creare progetti Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Componenti VSTO programma](../vsto/programming-vsto-add-ins.md)
- [Scrivere codice in Office soluzioni](../vsto/writing-code-in-office-solutions.md)
- [Office assembly di interoperabilità primari](../vsto/office-primary-interop-assemblies.md)
- [Office Personalizzazione dell'interfaccia utente](../vsto/office-ui-customization.md)
- [Visio panoramica del modello a oggetti](../vsto/visio-object-model-overview.md)
- [Visio 2010 in Office sviluppo](/previous-versions/office/developer/office-2010/ff604964(v=office.14))
