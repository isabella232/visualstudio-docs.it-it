---
title: 'Procedura: modificare query TableAdapter | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vbData.Microsoft.VSDesigner.DataSource.DbSource
- vbdata.Microsoft.VSDesigner.DataSource.DbSource
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- queries [Visual Basic], editing
- TableAdapters, editing queries
- data [Visual Studio], TableAdapters
- editing queries
ms.assetid: aac7b7b4-bd91-4225-95d4-a07643568c43
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 687336b979ef7e6d46ea6deb4a5682f3aec065be
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49287898"
---
# <a name="how-to-edit-tableadapter-queries"></a>Procedura: modificare query TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Modificare query TableAdapter con la [modifica di TableAdapter](../data-tools/editing-tableadapters.md) nel **Progettazione Dataset**. Quando non sono più di si adatta alle esigenze dell'applicazione, è necessario modificare una query TableAdapter. (In alternativa, è possibile creare query aggiuntive sul TableAdapter. Per altre informazioni sull'aggiunta di nuove query, vedere [procedura: creare query TableAdapter](../data-tools/how-to-create-tableadapter-queries.md).)  
  
> [!NOTE]
>  Se il [configurazione guidata TableAdapter](http://msdn.microsoft.com/library/3a373dd9-7b34-4d3c-a48b-69414512bac8) apre anziché il **configurazione guidata Query TableAdapter**, si potrebbe essere stata selezionata principale dell'oggetto TableAdapter `Fill` Progettazione query e non fa parte del Query aggiuntive dell'oggetto TableAdapter. Per informazioni sulla modifica di TableAdapter principale `Fill` eseguire una query, vedere [procedura: modificare oggetti TableAdapter](http://msdn.microsoft.com/library/ca178745-e35a-45f1-a395-23cddfd8f855).  
  
 ![TableAdapter con più query](../data-tools/media/tableadapter.gif "TableAdapter")  
  
### <a name="to-edit-a-tableadapter-query"></a>Per modificare una query TableAdapter  
  
1.  Aprire il dataset nel **Progettazione Dataset**. Per altre informazioni, vedere [procedura: aprire un set di dati in Progettazione Dataset](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Selezionare la query TableAdapter che si desidera modificare.  
  
3.  La query TableAdapter e scegliere **configura**.  
  
     Il **configurazione guidata Query TableAdapter** si apre, è possibile modificare la query o stored procedure per tale query.  
  
4.  Completare la **configurazione guidata Query TableAdapter** con le modifiche desiderate. Per altre informazioni, vedere [modifica di TableAdapter](../data-tools/editing-tableadapters.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetti TableAdapter](http://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364)   
 [Connessione ai dati in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparare l'applicazione per ricevere dati](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Recupero di dati nell'applicazione](../data-tools/fetching-data-into-your-application.md)   
 [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modifica dei dati nell'applicazione](../data-tools/editing-data-in-your-application.md)   
 [La convalida dei dati](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Salvataggio dei dati](../data-tools/saving-data.md)   
 [Procedure dettagliate di data](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)