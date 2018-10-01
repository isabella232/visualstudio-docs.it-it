---
title: 'Procedura: creare tabelle di dati | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Microsoft.VSDesigner.DataSource.DesignTable
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], creating data tables
- Dataset Designer, creating data tables
- tables [Visual Studio], creating
ms.assetid: 0e8bf4c4-3d05-4b20-9926-9d29914b26ed
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 596c2760e100bc45eefdde10743b3d9b45490b91
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47530472"
---
# <a name="how-to-create-data-tables"></a>Procedura: creare tabelle di dati
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

I dati possono essere archiviati in memoria in <xref:System.Data.DataTable> oggetti. (Set di dati sono costituiti da <xref:System.Data.DataTable> oggetti.) È in genere creare nuove tabelle dati con oggetti TableAdapter mediante la [configurazione guidata TableAdapter](http://msdn.microsoft.com/library/3a373dd9-7b34-4d3c-a48b-69414512bac8) o trascinando gli oggetti di database dal **Esplora Server** nel **Progettazione Dataset** .  
  
 Le tabelle di dati vengono create come risultato quando si creano nuovi oggetti TableAdapter nel [configurazione guidata origine dati](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) , ma possono anche essere creati in modo indipendente. È creare una tabella di dati autonomi trascinando un <xref:System.Data.DataTable> dall'oggetto la **set di dati** scheda della finestra di **della casella degli strumenti** nel **Progettazione Dataset**.  
  
> [!NOTE]
>  Per creare le tabelle di dati a livello di codice, vedere [creazione di una DataTable](http://msdn.microsoft.com/library/eecf9d78-60e3-4fdc-8de0-e56c13a89414).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="creating-a-datatable-with-tableadapter"></a>Creazione di un oggetto DataTable con TableAdapter  
 Le tabelle dati con gli oggetti TableAdapter includono metodi che è riempire la tabella con i dati e scrivere le modifiche al database. Vengono creati oggetti TableAdapter eseguendo il **configurazione guidata TableAdapter** o trascinando gli oggetti di database dal **Esplora Server** nel **Progettazione Dataset**.  
  
#### <a name="to-create-a-new-data-table-with-tableadapter"></a>Per creare una nuova tabella di dati con TableAdapter  
  
1.  Aprire il set di dati nel **Progettazione Dataset**. Per informazioni, vedere [procedura: aprire un set di dati in Progettazione Dataset](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Trascinare un **TableAdapter** dal **set di dati** scheda della finestra di **della casella degli strumenti** nel **Progettazione Dataset**.  
  
     Il **configurazione guidata TableAdapter** apre.  
  
3.  Completare la procedura guidata. Per altre informazioni, vedere [configurazione guidata TableAdapter](http://msdn.microsoft.com/library/3a373dd9-7b34-4d3c-a48b-69414512bac8)  
  
#### <a name="to-create-a-new-data-table-with-a-tableadapter-from-server-explorer"></a>Per creare una nuova tabella di dati con un TableAdapter da Esplora Server  
  
1.  Aprire il set di dati nel **progettazione origine dati**.  
  
2.  Trascinare un oggetto di database (ad esempio, una tabella) da **Esplora Server** nel **Progettazione Dataset**.  
  
## <a name="creating-a-standalone-datatable"></a>Creazione di una DataTable autonomo  
 Le tabelle autonome necessario disporre di `Fill` logica implementata per poter essere occupata dai dati. Per informazioni su compilando le tabelle dati autonomo, vedere [popolamento di un set di dati da un oggetto DataAdapter](http://msdn.microsoft.com/library/3fa0ac7d-e266-4954-bfac-3fbe2f913153).  
  
#### <a name="to-create-a-new-stand-alone-data-table"></a>Per creare una nuova tabella di dati autonomo  
  
1.  Aprire il set di dati nel **Progettazione Dataset**.  
  
2.  Trascinare un <xref:System.Data.DataTable> dal **set di dati** scheda della finestra di **della casella degli strumenti** nel **Progettazione Dataset**.  
  
3.  Aggiungere colonne per definire la tabella di dati. Per altre informazioni, vedere [procedura: aggiungere colonne a un oggetto DataTable](http://msdn.microsoft.com/library/8ca21f77-b99a-47a7-a656-7cfd7a1bd9df).  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Data.DataTable>   
 [Procedure dettagliate di data](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Procedura dettagliata: Visualizzazione dei dati in un Windows Form](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [Panoramica degli oggetti TableAdapter](../data-tools/tableadapter-overview.md)   
 [Creazione e modifica di dataset tipizzati](../data-tools/creating-and-editing-typed-datasets.md)   
 [Aggiungere nuove origini dati](../data-tools/add-new-data-sources.md)   
 [Finestra Origini dati](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)   
 [Procedura: Connettersi ai dati di un database](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [La convalida dei dati](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)