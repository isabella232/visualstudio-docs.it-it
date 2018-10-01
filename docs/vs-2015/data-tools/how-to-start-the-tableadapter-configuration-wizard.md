---
title: 'Procedura: avviare la configurazione guidata TableAdapter | Microsoft Docs'
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
- TableAdapters, Configuration Wizard
- TableAdapter Configuration Wizard
ms.assetid: 301f2dcd-ed72-4229-80ef-3b59cb062d5d
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 0cf7d3e5ace98ac73f97909b184ce04b86d4b9ee
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47527152"
---
# <a name="how-to-start-the-tableadapter-configuration-wizard"></a>Procedura: avviare la Configurazione guidata TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il **configurazione guidata TableAdapter** crea e modifica TableAdapter in set di dati fortemente tipizzati. La procedura guidata crea TableAdapter in base alle istruzioni SQL inserite nella procedura stessa o in base a stored procedure esistenti nel database. Può anche creare nuove stored procedure nel database in base alle istruzioni SQL inserite nella procedura stessa.  
  
### <a name="to-start-the-tableadapter-configuration-wizard-to-create-a-new-tableadapter"></a>Per avviare la Configurazione guidata TableAdapter per creare un nuovo TableAdapter  
  
1.  Aprire il set di dati nel **Progettazione Dataset**. Per altre informazioni, vedere [procedura: aprire un set di dati in Progettazione Dataset](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
    > [!NOTE]
    >  Se non è un set di dati nel progetto, vedere [creare e configurare i set di dati](../data-tools/create-and-configure-datasets-in-visual-studio.md).  
  
2.  Se si sta creando un nuovo TableAdapter, trascinare un **TableAdapter** dall'oggetto il **set di dati** scheda della finestra di **della casella degli strumenti** nel **Progettazione Dataset**.  
  
3.  Nel **Seleziona connessione dati** pagina, selezionare una connessione dati dall'elenco delle connessioni attualmente disponibili o **nuova connessione** per creare una nuova connessione.  
  
### <a name="to-start-the-tableadapter-configuration-wizard-to-edit-an-existing-tableadapter"></a>Per avviare la Configurazione guidata TableAdapter per modificare un TableAdapter esistente  
  
1.  Aprire il set di dati nel **Progettazione Dataset**. Per altre informazioni, vedere [procedura: aprire un set di dati in Progettazione Dataset](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Fare doppio clic su TableAdapter nel **Progettazione Dataset** e scegliere **configura**. Verrà visualizzata la procedura guidata per la **genera le istruzioni SQL** pagina o nella **Associa comandi alle Stored procedure esistenti** pagina, a seconda di come è stato originariamente configurato TableAdapter.  
  
3.  Completare la procedura guidata.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedure dettagliate di data](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Associazione di controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Panoramica degli oggetti TableAdapter](../data-tools/tableadapter-overview.md)   
 [Creazione e modifica di dataset tipizzati](../data-tools/creating-and-editing-typed-datasets.md)   
 [Aggiungere nuove origini dati](../data-tools/add-new-data-sources.md)   
 [Procedura: Connettersi ai dati di un database](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [La convalida dei dati](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Procedura: ordinare e filtrare i dati ADO.NET con il componente BindingSource di Windows Form](http://msdn.microsoft.com/library/6c206daf-d706-4602-9dbe-435343052063)   
 [Procedura: creare una tabella di ricerca con il componente BindingSource di Windows Form](http://msdn.microsoft.com/library/622fce80-879d-44be-abbf-8350ec22ca2b)   
 [Procedura dettagliata: visualizzazione di dati in un Windows Form](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)