---
title: Riferimento gestito (Office sviluppo in Visual Studio)
description: Informazioni sulla documentazione di riferimento sulle API per gli spazi dei nomi e i tipi usati Office progetti che hanno come destinazione il .NET Framework.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 08/14/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- reference [Office development in Visual Studio], 2007 Microsoft Office system
- Office development in Visual Studio, reference
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 5452ea5990b4facb108deffe87870100ec17ca0c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122032511"
---
# <a name="managed-reference-office-development-in-visual-studio"></a>Riferimento gestito (Office sviluppo in Visual Studio)
  Questa sezione include documentazione di riferimento alle API per gli spazi dei nomi e i tipi usati nei progetti di Office destinati a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o [!INCLUDE[net_v45](includes/net-v45-md.md)]. Per la documentazione di riferimento sulle API sugli spazi dei nomi e sui tipi usati nei progetti Office che hanno come destinazione .NET Framework 3.5, vedere la sezione di riferimento seguente nella documentazione di Visual Studio: Riferimento gestito [(sviluppo di Office in Visual Studio).](managed-reference-office-development-in-visual-studio.md)

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="in-this-section"></a>Contenuto della sezione
 <xref:Microsoft.Office.Tools>

 Contiene classi comuni per la programmazione di soluzioni Office. Includono la classe base per i componenti aggiuntivi VSTO, classi per la creazione di riquadri attività personalizzati nei componenti aggiuntivi VSTO, classi per la creazione di smart tag nelle soluzioni Excel e Word e classi per la creazione di riquadri azioni nelle personalizzazioni a livello di documento.

 <xref:Microsoft.Office.Tools.Excel>

 Contiene i controlli e gli elementi host che si possono usare nelle soluzioni per Excel.

 <xref:Microsoft.Office.Tools.Excel.Controls>

 Contiene i controlli Excel e Windows Form che si possono usare nelle soluzioni per Excel.

 <xref:Microsoft.Office.Tools.Outlook>

 Contiene le classi usate dai componenti aggiuntivi VSTO per Outlook, comprese le classi usate per creare aree del modulo personalizzate.

 <xref:Microsoft.Office.Tools.Ribbon>

 Contiene le classi usate per modificare a livello di codice le personalizzazioni della barra multifunzione create usando la finestra di progettazione della barra multifunzione.

 <xref:Microsoft.Office.Tools.Word>

 Contiene i controlli e gli elementi host che si possono usare nelle soluzioni per Word.

 <xref:Microsoft.Office.Tools.Word.Controls>

 Contiene i controlli Word e Windows Form che si possono usare nelle soluzioni per Word.

 <xref:Microsoft.VisualStudio.Tools.Applications>

 Contiene la classe <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> e un set di classi di dati memorizzati nella cache correlate. Queste classi possono essere usate per modificare alcuni aspetti delle personalizzazioni a livello di documento nei computer in cui non è installato Microsoft Office.

 <xref:Microsoft.VisualStudio.Tools.Applications.Deployment>

 Contiene l'interfaccia <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> (che è possibile implementare per creare un' *azione post-distribuzione* per una soluzione Office), le eccezioni che possono essere generate quando si installa una soluzione Office e altre API che appartengono all'infrastruttura di Visual Studio.

 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime>

 Contiene la maggior parte delle eccezioni che possono essere generate da [!INCLUDE[vsto_runtime](includes/vsto-runtime-md.md)], diverse classi che si possono usare per memorizzare i dati nelle personalizzazioni a livello di documento e altre API che fanno parte dell'infrastruttura di Visual Studio.

 <xref:Microsoft.VisualStudio.Tools.Office.BuildTasks>

 Contiene classi di attività MSBuild che vengono usate per compilare progetti di Office.

## <a name="see-also"></a>Vedi anche
- [Visual Studio degli strumenti per Office runtime](visual-studio-tools-for-office-runtime-overview.md)
- [Introduzione allo &#40;Office sviluppo in Visual Studio&#41;](getting-started-office-development-in-visual-studio.md)
- [Office esempi di sviluppo e procedure dettagliate](office-development-samples-and-walkthroughs.md)
- [Progettare e creare Office soluzioni](designing-and-creating-office-solutions.md)
