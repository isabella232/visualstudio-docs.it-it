---
title: Associare controlli ai dati in Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data, displaying
- data sources, displaying data
- Data Sources window
- dislaying data
ms.assetid: be8b6623-86a6-493e-ab7a-050de4661fd6
caps.latest.revision: 42
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 85bfcb03ea2f383d8f1517d17c866c2320891aaa
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47529262"
---
# <a name="bind-controls-to-data-in-visual-studio"></a>Associare controlli ai dati in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [associare controlli ai dati in Visual Studio](https://docs.microsoft.com/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).  
  
  
È possibile visualizzare i dati per gli utenti dell'applicazione mediante l'associazione dei dati ai controlli. È possibile creare questi controlli con associazione a dati trascinando elementi dal **Zdroje dat** finestra in un'area di progettazione oppure controlli su una superficie in Visual Studio.  
  
 In questo argomento vengono descritte le origini dati che è possibile utilizzare per creare controlli associati a dati. Vengono inoltre descritte alcune delle attività generali coinvolte nell'associazione ai dati. Per altre informazioni su come creare controlli associati a dati, vedere [controlli di associare Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) e [WPF di associare controlli ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
## <a name="data-sources"></a>Origini dati  
 Nel contesto di associazione dati, un'origine dati rappresenta i dati in memoria che può essere associato a un'interfaccia utente. In pratica, un'origine dati può essere una classe di Entity Framework, un set di dati, un endpoint del servizio che è incapsulato in un oggetto proxy .NET, una classe LINQ to SQL, o qualsiasi oggetto .NET o raccolta. Alcune origini dati consentono di creare controlli associati a dati trascinando elementi dal **Zdroje dat** finestra, mentre altre origini dati non lo è. Nella tabella seguente vengono indicate le origini dati supportate.  
  
|Origine dati|Supporto di trascinamento e rilascio in **Progettazione Windows Form**|Supporto di trascinamento e rilascio in **WPF Designer**|Supporto di trascinamento e rilascio in **Silverlight Designer**|  
|-----------------|---------------------------------------------------------------|-----------------------------------------------------|-------------------------------------------------------------|  
|Set di dati|Yes|Yes|No|  
|Entity Data Model|Sì<sup>1</sup>|Yes|Yes|  
|Classi LINQ to SQL|Non<sup>2</sup>|Non<sup>2</sup>|Non<sup>2</sup>|  
|Servizi (inclusi [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)], WCF services e i servizi web)|Yes|Yes|Yes|  
|Object|Yes|Yes|Yes|  
|SharePoint|Yes|Yes|Yes|  
  
 1. Generare il modello usando il **Entity Data Model** procedura guidata, quindi trascinare tali oggetti nella finestra di progettazione.  
  
 2. Classi LINQ to SQL non vengono visualizzati nei **Zdroje dat** finestra. È comunque possibile aggiungere una nuova origine dati dell'oggetto basata sulle classi LINQ to SQL, quindi trascinare tali oggetti nella finestra di progettazione per creare controlli con associazione a dati. Per altre informazioni, vedere [procedura dettagliata: creazione di classi LINQ to SQL (O-R Designer)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233).  
  
## <a name="data-sources-window"></a>Finestra Origini dati  
 Origini dati sono disponibili per il progetto come elementi di **Zdroje dat** finestra. In questa finestra è visibile o sia accessibile dal **vista** menu, quando un'area di progettazione di form è la finestra attiva nel progetto. È possibile trascinare elementi da questa finestra per creare controlli associati ai dati sottostanti ed è anche possibile configurare le origini dati facendo clic.  
  
 ![Finestra Origini dati](../data-tools/media/raddata-data-sources-window.png "raddata finestra Origini dati")  
  
 Per ogni tipo di dati che viene visualizzato nei **Zdroje dat** finestra, viene creato un controllo predefinito quando si trascina l'elemento nella finestra di progettazione. Prima di trascinare un elemento dal **Zdroje dat** finestra, è possibile modificare il controllo che verrà creato. Per altre informazioni, vedere [impostare il controllo da creare durante il trascinamento dalla finestra Origini dei dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
## <a name="tasks-involved-in-binding-controls-to-data"></a>Attività coinvolte nell'associazione di controlli ai dati  
 Nella tabella seguente sono elencate alcune delle attività più comuni eseguite per associare controlli ai dati.  
  
|Attività|Altre informazioni|  
|----------|----------------------|  
|Aprire il **Zdroje dat** finestra.|Aprire un'area di progettazione nell'editor e scegliere **View** > **Zdroje dat**.|  
|Aggiungere un'origine dati al progetto.|[Aggiungi nuova origine dati](../data-tools/add-new-data-sources.md)|  
|Impostare il controllo creato quando si trascina un elemento dal **Zdroje dat** finestra di progettazione.|[Impostare il controllo da creare durante il trascinamento dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)|  
|Modificare l'elenco dei controlli associati a elementi di **Zdroje dat** finestra.|[Aggiungere controlli personalizzati alla finestra Origini dati](../data-tools/add-custom-controls-to-the-data-sources-window.md)|  
|Creare controlli associati a dati.|[Associare controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)<br /><br /> [Associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)|  
|Associare a un oggetto o una raccolta.|[Associare oggetti in Visual Studio](../data-tools/bind-objects-in-visual-studio.md)|  
|Filtrare i dati visualizzati nell'interfaccia utente.|[Filtrare e ordinare i dati in un'applicazione Windows Forms](../data-tools/filter-and-sort-data-in-a-windows-forms-application.md)|  
|Personalizzare le didascalie per controlli.|[Personalizzare la modalità in cui in Visual Studio vengono create didascalie per controlli con associazione a dati](../data-tools/customize-how-visual-studio-creates-captions-for-data-bound-controls.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Visual Studio data tools for .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)  (Strumenti dati di Visual Studio per .NET)  
 [Data binding in Windows Form](http://msdn.microsoft.com/library/c3826d8e-ea25-4ad4-a669-45bfb19192aa)

