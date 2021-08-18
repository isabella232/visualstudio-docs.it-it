---
title: Associare i controlli ai dati
description: Associare i controlli ai dati in Visual Studio. Creare controlli associati a dati trascinando gli elementi dalla finestra Origini dati .
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- data, displaying
- data sources, displaying data
- Data Sources window
- displaying data
ms.assetid: be8b6623-86a6-493e-ab7a-050de4661fd6
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: adbe3262e1da3c0d28f16bf32d94952c6565e142
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122081932"
---
# <a name="bind-controls-to-data-in-visual-studio"></a>Associare controlli ai dati in Visual Studio

È possibile visualizzare i dati per gli utenti dell'applicazione mediante l'associazione dei dati ai controlli. È possibile creare questi controlli associati a  dati trascinando elementi dalla finestra Origini dati in un'area di progettazione o controlli su un'area in Visual Studio.

In questo argomento vengono descritte le origini dati che è possibile utilizzare per creare controlli associati a dati. Vengono inoltre descritte alcune delle attività generali coinvolte nell'associazione ai dati. Per informazioni più specifiche su come creare controlli con associazione a dati, vedere Associare i controlli Windows Forms ai dati [in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) e Associare i controlli WPF ai dati in [Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

## <a name="data-sources"></a>Origini dati

Nel contesto di data binding, un'origine dati rappresenta i dati in memoria che possono essere associati all'interfaccia utente. In termini pratici, un'origine dati può essere una classe Entity Framework, un set di dati, un endpoint di servizio incapsulato in un oggetto proxy .NET, una classe LINQ to SQL o qualsiasi oggetto o raccolta .NET. Solo per alcune origini dati è possibile creare controlli associati a dati mediante il trascinamento di elementi dalla finestra **Origini dati**. Nella tabella seguente vengono indicate le origini dati supportate.

| Origine dati | Supporto del trascinamento della selezione in **Progettazione Windows Form** | Supporto del trascinamento della selezione in **WPF Designer** | Supporto del trascinamento della selezione in **Silverlight Designer** |
| - | - | - | - |
| Set di dati | Sì | Sì | No |
| Entity Data Model | Sì<sup>1</sup> | Sì | Sì |
| Classi LINQ to SQL | No<sup>2</sup> | No<sup>2</sup> | No<sup>2</sup> |
| Servizi (inclusi [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)], servizi WCF e servizi Web) | Sì | Sì | Sì |
| Oggetto | Sì | Sì | Sì |
| SharePoint | Sì | Sì | Sì |

1. Generare il modello usando la **Entity Data Model** guidata, quindi trascinare tali oggetti nella finestra di progettazione.

2. Le classi LINQ to SQL non vengono visualizzate nella finestra **Origini dati**. È comunque possibile aggiungere una nuova origine dati dell'oggetto basata sulle classi LINQ to SQL, quindi trascinare tali oggetti nella finestra di progettazione per creare controlli con associazione a dati. Per altre informazioni, vedere [Procedura dettagliata: creazione di classi LINQ to SQL (O-R Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).

## <a name="data-sources-window"></a>Finestra Origini dati

Nella finestra **Origini dati** sono visualizzate le voci relative alle origini dati disponibili per il progetto. Questa finestra è visibile quando un'area di progettazione del modulo è la finestra attiva nel progetto oppure è possibile aprirla (quando un progetto è aperto) scegliendo Visualizza altre Windows  >    >  **origini dati**. È possibile trascinare elementi da questa finestra per creare controlli associati ai dati sottostanti ed è anche possibile configurare le origini dati facendo clic con il pulsante destro del mouse.

![Finestra Origini dati](../data-tools/media/raddata-data-sources-window.png)

Per ogni tipo di dati visualizzato nella finestra **Origini dati** viene creato un controllo predefinito quando si trascina l'elemento nella finestra di progettazione. Prima di trascinare un elemento dalla **finestra Origini** dati, è possibile modificare il controllo creato. Per altre informazioni, vedere [Impostare il controllo da creare durante il trascinamento dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

## <a name="tasks-involved-in-binding-controls-to-data"></a>Attività coinvolte nell'associazione di controlli a dati

Nella tabella seguente sono elencate alcune delle attività più comuni eseguite per associare i controlli ai dati.

|Attività|Altre informazioni|
|----------| - |
|Aprire la finestra **Origini dati**.|Aprire un'area di progettazione nell'editor e scegliere **Visualizza**  >  **origini dati**.|
|Aggiungere un'origine dati al progetto.|[Aggiungere nuove origini dati](../data-tools/add-new-data-sources.md)|
|Impostare il controllo che viene creato quando si trascina un elemento dalla finestra **Origini dati** alla finestra di progettazione.|[Impostare il controllo da creare durante il trascinamento dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)|
|Modificare l'elenco dei controlli associati agli elementi nella finestra **Origini dati**.|[Aggiungere controlli personalizzati alla finestra Origini dati](../data-tools/add-custom-controls-to-the-data-sources-window.md)|
|Creare controlli associati a dati.|[Associare controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)<br /><br /> [Associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)|
|Eseguire l'associazione a un oggetto o a una raccolta.|[Associare oggetti in Visual Studio](../data-tools/bind-objects-in-visual-studio.md)|
|Filtrare i dati visualizzati nell'interfaccia utente.|[Filtrare e ordinare i dati in un'applicazione Windows Forms](../data-tools/filter-and-sort-data-in-a-windows-forms-application.md)|
|Personalizzare le didascalie per i controlli.|[Personalizzare la modalità in cui in Visual Studio vengono create didascalie per controlli con associazione a dati](../data-tools/customize-how-visual-studio-creates-captions-for-data-bound-controls.md)|

## <a name="see-also"></a>Vedi anche

- [Visual Studio data tools per .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
- [Windows Moduli data binding](/dotnet/framework/winforms/windows-forms-data-binding)
