---
title: 'Procedura: aggiungere query globali a un oggetto TableAdapter | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
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
- global functions, datasets
- scalar functions, datasets
- TableAdapters, global queries
- data [Visual Studio], TableAdapters
- datasets [Visual Basic], scalar functions
- TableAdapter Query Configuration Wizard
- datasets [Visual Basic], global functions
- TableAdapter queries
- queries [Visual Studio], TableAdapters
ms.assetid: 4abffd6b-2e9f-4ef3-99b2-6e9ae4ad4679
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: fd185c9a6803a5e66b1fdaac0f040815328ddb82
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49193895"
---
# <a name="how-to-add-global-queries-to-a-tableadapter"></a>Procedura: aggiungere query globali a un oggetto TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Query globali* sono le query SQL che restituiscono un singolo valore (scalare) o nessun valore. In genere, funzioni globali di eseguono operazioni di database, ad esempio inserimenti, aggiornamenti, eliminazioni e l'aggregazione di informazioni, ad esempio per restituire un conteggio di clienti in una tabella o gli addebiti totali per tutti gli elementi in un ordine particolare.  
  
 Aggiungere query globali mediante l'esecuzione di **configurazione guidata Query TableAdapter** dall'interno di **Progettazione Dataset**.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-global-query-to-a-dataset"></a>Per aggiungere una query globali a un set di dati  
  
1.  Aprire un set di dati di **Progettazione Dataset**. Per altre informazioni, vedere [procedura: aprire un set di dati in Progettazione Dataset](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Trascinare un **Query** dal **set di dati** scheda della finestra di **della casella degli strumenti** in un'area vuota del **Progettazione Dataset**.  
  
     Il [modifica di TableAdapter](../data-tools/editing-tableadapters.md) apre.  
  
3.  Scegliere una connessione per la query da usare. È possibile sceglierne uno dall'elenco o creare una nuova connessione. Se si crea una nuova connessione, si avrà la possibilità di salvarlo nel file di configurazione dell'applicazione. Per altre informazioni, vedere [procedura: salvare e modificare le stringhe di connessione](~/E:/Repos/visualstudio-docs-pr/docs/data-tools/how-to-save-and-edit-connection-strings.md).  
  
4.  Scegliere se usare le istruzioni SQL o stored procedure.  
  
5.  Scegliere la stored procedure da utilizzare o scegliere il **scegliere un tipo di Query** pagina della procedura guidata, scegliere il tipo di query desiderato e quindi fare clic su **successivo**.  
  
6.  Fornire una query che esegue l'attività desiderata, ad esempio, `SELECT COUNT(*) AS CustomerCount FROM Customers`.  
  
    > [!NOTE]
    >  Trascinamento di una query direttamente sul **Progettazione Dataset** crea un metodo che restituirà solo un valore scalare (singolo). Mentre la query o stored procedure selezionata può restituire più di un singolo valore, il metodo creato dalla procedura guidata restituirà solo un singolo valore. Ad esempio, la query potrebbe restituire la prima colonna della prima riga dei dati restituiti.  
  
7.  Completare la procedura guidata. la query viene aggiunta per il **Progettazione Dataset**. Per informazioni sull'esecuzione delle query, vedere [procedura: eseguire query TableAdapter](http://msdn.microsoft.com/library/c7518855-f896-41c1-b3de-1a8116280593).  
  
## <a name="see-also"></a>Vedere anche  
 [Creare e configurare oggetti TableAdapter](../data-tools/create-and-configure-tableadapters.md)   
 [Procedura: creare query TableAdapter](../data-tools/how-to-create-tableadapter-queries.md)   
 [Associazione di controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Panoramica degli oggetti TableAdapter](../data-tools/tableadapter-overview.md)   
 [Creazione e modifica di dataset tipizzati](../data-tools/creating-and-editing-typed-datasets.md)   
 [Aggiungere nuove origini dati](../data-tools/add-new-data-sources.md)   
 [Procedura: Connettersi ai dati di un database](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [La convalida dei dati](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Procedura: esplorare i dati con il controllo BindingNavigator di Windows Form](http://msdn.microsoft.com/library/0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb)   
 [Procedura dettagliata: visualizzazione di dati in un Windows Form](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)