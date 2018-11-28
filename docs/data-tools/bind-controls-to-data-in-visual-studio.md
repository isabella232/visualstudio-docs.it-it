---
title: Associare controlli ai dati
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data, displaying
- data sources, displaying data
- Data Sources window
- dislaying data
ms.assetid: be8b6623-86a6-493e-ab7a-050de4661fd6
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: c4e27f5ce9536e7128330ebe932709a9be408b7e
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305263"
---
# <a name="bind-controls-to-data-in-visual-studio"></a>Associazione di controlli ai dati in Visual Studio

È possibile visualizzare i dati per gli utenti dell'applicazione mediante l'associazione dei dati ai controlli. È possibile creare questi controlli con associazione a dati trascinando elementi dal **Zdroje dat** finestra in un'area di progettazione oppure controlli su una superficie in Visual Studio.

In questo argomento vengono descritte le origini dati che è possibile utilizzare per creare controlli associati a dati. Vengono inoltre descritte alcune delle attività generali coinvolte nell'associazione ai dati. Per altre informazioni su come creare controlli associati a dati, vedere [controlli di associare Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) e [WPF di associare controlli ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

## <a name="data-sources"></a>Origini dati

Nel contesto di associazione dati, un'origine dati rappresenta i dati in memoria che può essere associato a un'interfaccia utente. In pratica, un'origine dati può essere una classe di Entity Framework, un set di dati, un endpoint del servizio che è incapsulato in un oggetto proxy .NET, una classe LINQ to SQL, o qualsiasi oggetto .NET o raccolta. Solo per alcune origini dati è possibile creare controlli associati a dati mediante il trascinamento di elementi dalla finestra Origini dati **. Nella tabella seguente vengono indicate le origini dati supportate.

| Origine dati | Supporto del trascinamento della selezione in Progettazione Windows Form** | Supporto del trascinamento della selezione in WPF Designer** | Supporto del trascinamento della selezione in Silverlight Designer** |
| - | - | - | - |
| Set di dati | Yes | Yes | No |
| Entity Data Model | Sì<sup>1</sup> | Yes | Yes |
| Classi LINQ to SQL | Non<sup>2</sup> | Non<sup>2</sup> | Non<sup>2</sup> |
| Servizi (inclusi [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)], servizi WCF e servizi Web) | Yes | Yes | Yes |
| Object | Yes | Yes | Yes |
| SharePoint | Yes | Yes | Yes |

1. Generare il modello usando il **Entity Data Model** procedura guidata, quindi trascinare tali oggetti nella finestra di progettazione.

2. Le classi LINQ to SQL non sono visualizzate nella finestra Origini dati **. È comunque possibile aggiungere una nuova origine dati dell'oggetto basata sulle classi LINQ to SQL, quindi trascinare tali oggetti nella finestra di progettazione per creare controlli con associazione a dati. Per altre informazioni, vedere [procedura dettagliata: creazione di classi LINQ to SQL (O-R Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).

## <a name="data-sources-window"></a>Finestra Origini dati

Nella finestra Origini dati** sono visualizzate le voci relative alle origini dati disponibili per il progetto. In questa finestra è visibile quando un'area di progettazione di form è la finestra attiva nel progetto oppure è possibile aprirlo (quando un progetto è aperto), scegliendo **View** > **Other Windows**  >   **Zdroje dat**. È possibile trascinare elementi da questa finestra per creare controlli associati ai dati sottostanti ed è anche possibile configurare le origini dati facendo clic.

![Finestra Origini dati](../data-tools/media/raddata-data-sources-window.png)

Per ogni tipo di dati visualizzato nella finestra Origini dati** viene creato un controllo predefinito quando si trascina l'elemento nella finestra di progettazione. Prima di trascinare un elemento dal **Zdroje dat** finestra, è possibile modificare il controllo che viene creato. Per altre informazioni, vedere [impostare il controllo da creare durante il trascinamento dalla finestra Origini dei dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

## <a name="tasks-involved-in-binding-controls-to-data"></a>Attività coinvolte nell'associazione di controlli a dati

Nella tabella seguente sono elencate alcune delle attività più comuni eseguite per associare controlli ai dati.

|Attività|Altre informazioni|
|----------| - |
|Aprire la finestra Origini dati**|Aprire un'area di progettazione nell'editor e scegliere **View** > **Zdroje dat**.|
|Aggiungere un'origine dati al progetto.|[Aggiungi nuova origine dati](../data-tools/add-new-data-sources.md)|
|Impostare il controllo che viene creato quando si trascina un elemento dalla finestra Origini dati** alla finestra di progettazione.|[Impostare il controllo da creare durante il trascinamento dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)|
|Modificare l'elenco dei controlli associati agli elementi nella finestra Origini dati **.|[Aggiungere controlli personalizzati alla finestra Origini dati](../data-tools/add-custom-controls-to-the-data-sources-window.md)|
|Creare controlli associati a dati.|[Associare controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)<br /><br /> [Associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)|
|Associare a un oggetto o una raccolta.|[Associare oggetti in Visual Studio](../data-tools/bind-objects-in-visual-studio.md)|
|Filtrare i dati visualizzati nell'interfaccia utente.|[Filtrare e ordinare i dati in un'applicazione Windows Forms](../data-tools/filter-and-sort-data-in-a-windows-forms-application.md)|
|Personalizzare le didascalie per controlli.|[Personalizzare la modalità in cui in Visual Studio vengono create didascalie per controlli con associazione a dati](../data-tools/customize-how-visual-studio-creates-captions-for-data-bound-controls.md)|

## <a name="see-also"></a>Vedere anche

- [Visual Studio Data Tools per .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
- [Data binding in Windows Form](/dotnet/framework/winforms/windows-forms-data-binding)