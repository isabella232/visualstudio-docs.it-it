---
title: Associare i controlli ai dati
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data, displaying
- data sources, displaying data
- Data Sources window
- displaying data
ms.assetid: be8b6623-86a6-493e-ab7a-050de4661fd6
caps.latest.revision: 42
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 31e2086126e9a17554c80b53858205e83fd504fd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72673041"
---
# <a name="bind-controls-to-data-in-visual-studio"></a>Associare controlli ai dati in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile visualizzare i dati per gli utenti dell'applicazione mediante l'associazione dei dati ai controlli. È possibile creare questi controlli associati a dati trascinando gli elementi dalla finestra **origini dati** in un'area di progettazione o in controlli di una superficie in Visual Studio.

 In questo argomento vengono descritte le origini dati che è possibile utilizzare per creare controlli associati a dati. Vengono inoltre descritte alcune delle attività generali coinvolte nell'associazione ai dati. Per informazioni più specifiche su come creare controlli associati a dati, vedere [associare Windows Forms controlli ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) e [associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

## <a name="data-sources"></a>Origini dati
 Nel contesto di data binding, un'origine dati rappresenta i dati in memoria che possono essere associati all'interfaccia utente. In pratica, un'origine dati può essere una classe Entity Framework, un set di dati, un endpoint di servizio incapsulato in un oggetto proxy .NET, una classe LINQ to SQL o qualsiasi oggetto o raccolta .NET. Solo per alcune origini dati è possibile creare controlli associati a dati mediante il trascinamento di elementi dalla finestra **Origini dati**. Nella tabella seguente vengono indicate le origini dati supportate.

|Origine dati|Supporto del trascinamento della selezione in **Progettazione Windows Form**|Supporto del trascinamento della selezione in **WPF Designer**|Supporto del trascinamento della selezione in **Silverlight Designer**|
|-----------------|---------------------------------------------------------------|-----------------------------------------------------|-------------------------------------------------------------|
|Set di dati|Sì|Sì|No|
|Entity Data Model|Sì<sup>1</sup>|Sì|Sì|
|Classi LINQ to SQL|No<sup>2</sup>|No<sup>2</sup>|No<sup>2</sup>|
|Servizi (inclusi [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)], servizi WCF e servizi Web)|Sì|Sì|Sì|
|Oggetto|Sì|Sì|Sì|
|SharePoint|Sì|Sì|Sì|

 1. Generare il modello utilizzando la procedura guidata **Entity Data Model** , quindi trascinare tali oggetti nella finestra di progettazione.

 2. Le classi LINQ to SQL non vengono visualizzate nella finestra **Origini dati**. È comunque possibile aggiungere una nuova origine dati dell'oggetto basata sulle classi LINQ to SQL, quindi trascinare tali oggetti nella finestra di progettazione per creare controlli con associazione a dati. Per ulteriori informazioni, vedere [procedura dettagliata: creazione di classi di LINQ to SQL (O-R Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233).

## <a name="data-sources-window"></a>Finestra Origini dati
 Nella finestra **Origini dati** sono visualizzate le voci relative alle origini dati disponibili per il progetto. Questa finestra è visibile oppure è accessibile dal menu **Visualizza** quando un'area di progettazione del modulo è la finestra attiva nel progetto. È possibile trascinare elementi da questa finestra per creare controlli associati ai dati sottostanti ed è inoltre possibile configurare le origini dati facendo clic con il pulsante destro del mouse.

 ![Finestra Origini dati](../data-tools/media/raddata-data-sources-window.png "finestra Origini dati raddata")

 Per ogni tipo di dati visualizzato nella finestra **Origini dati** viene creato un controllo predefinito quando si trascina l'elemento nella finestra di progettazione. Prima di trascinare un elemento dalla finestra **origini dati** , è possibile modificare il controllo che verrà creato. Per ulteriori informazioni, vedere [impostare il controllo da creare durante il trascinamento dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

## <a name="tasks-involved-in-binding-controls-to-data"></a>Attività coinvolte nell'associazione di controlli a dati
 Nella tabella seguente sono elencate alcune delle attività più comuni eseguite per associare i controlli ai dati.

|Attività|Altre informazioni|
|----------|----------------------|
|Aprire la finestra **Origini dati**.|Aprire un'area di progettazione nell'editor e scegliere **Visualizza**  >  **origini dati**.|
|Aggiungere un'origine dati al progetto.|[Aggiungi nuova origine dati](../data-tools/add-new-data-sources.md)|
|Impostare il controllo che viene creato quando si trascina un elemento dalla finestra **Origini dati** alla finestra di progettazione.|[Impostare il controllo da creare durante il trascinamento dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)|
|Modificare l'elenco dei controlli associati agli elementi nella finestra **Origini dati**.|[Aggiungere controlli personalizzati alla finestra Origini dati](../data-tools/add-custom-controls-to-the-data-sources-window.md)|
|Creare controlli associati a dati.|[Associare controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)<br /><br /> [Associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)|
|Eseguire l'associazione a un oggetto o a una raccolta.|[Associare oggetti in Visual Studio](../data-tools/bind-objects-in-visual-studio.md)|
|Filtrare i dati visualizzati nell'interfaccia utente.|[Filtrare e ordinare i dati in un'applicazione Windows Forms](../data-tools/filter-and-sort-data-in-a-windows-forms-application.md)|
|Personalizzare le didascalie per i controlli.|[Personalizzare la modalità in cui in Visual Studio vengono create didascalie per controlli con associazione a dati](../data-tools/customize-how-visual-studio-creates-captions-for-data-bound-controls.md)|

## <a name="see-also"></a>Vedere anche
 Data Binding [di Visual Studio Data Tools per .net](../data-tools/visual-studio-data-tools-for-dotnet.md) [Windows Forms](https://msdn.microsoft.com/library/c3826d8e-ea25-4ad4-a669-45bfb19192aa)
