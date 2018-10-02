---
title: 'Procedura: visualizzare correlati i dati in una Windows Forms Application | Microsoft Docs'
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
- Windows Forms, displaying data
- displaying data, related data
- related data, displaying
- displaying tables, related data
- data [Windows Forms], displaying
- displaying table data
- data [Windows Forms], related
- displaying data on forms, related data
- displaying table information
ms.assetid: 60b1f1ec-6257-42ab-83f0-06d54ed364fd
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: fc62789860cc10f5c410849936715a8ef82eae3f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47531542"
---
# <a name="how-to-display-related-data-in-a-windows-forms-application"></a>Procedura: Visualizzare dati correlati in un'applicazione Windows Forms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile visualizzare i dati correlati trascinando gli elementi che condividono lo stesso nodo tabella principale dal [finestra Origini dati](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) nel form. Ad esempio, se si dispone di un tipo di dati di origine che ha un `Customers` tabella e un processo di `Orders` tabella, si vedrebbe entrambe le tabelle come nodi di primo livello (nella visualizzazione struttura ad albero) nel **Zdroje dat** finestra. Espandere la `Customers` nodo in modo che è possibile visualizzare le colonne, e si noterà che l'ultima colonna nell'elenco è un nodo che rappresenta il `Orders` tabella. Questo nodo rappresenta gli ordini correlati per un cliente. Ciò significa che se si desidera creare un form che consente di selezionare un cliente e quindi visualizzare un elenco di ordini per quel cliente, è necessario trascinare gli elementi da visualizzare selezionandole da questa unica gerarchia.  
  
 ![Finestra Origini dati che mostra relazione](../data-tools/media/datasources2.gif "DataSources2")  
Creazione di controlli con associazione a dati che consentono di visualizzare i record correlati  
  
 ![collegamento a video](../data-tools/media/playvideo.gif "PlayVideo") per una versione video di questo argomento, vedere [How do i: aggiornare le tabelle correlate](http://go.microsoft.com/fwlink/?LinkId=143527).  
  
### <a name="to-create-controls-that-display-related-records"></a>Per creare controlli che consentono di visualizzare i record correlati  
  
1.  Aprire il form nel [finestra di progettazione Windows Form](http://msdn.microsoft.com/en-us/3c3d61f8-f36c-4d41-b9c3-398376fabb15).  
  
2.  Aprire il **Zdroje dat** finestra. Per altre informazioni, vedere [procedura: aprire la finestra Origini dati](../data-tools/how-to-open-the-data-sources-window.md).  
  
3.  Espandere il nodo che rappresenta la tabella padre nella relazione. (La tabella padre è la tabella sul lato "uno" di una relazione uno-a-molti).  
  
4.  Trascinare gli elementi desiderati dalla tabella padre della relazione da visualizzare il **Zdroje dat** finestra nei form.  
  
5.  Le tabelle figlio correlate vengono visualizzate come nodi espandibili nella parte inferiore dell'elenco di colonne della tabella padre. Trascinare gli elementi che si desidera visualizzare da un nodo correlato nel form.  
  
    > [!NOTE]
    >  Trascinare un elemento da un nodo di livello superiore crea un oggetto separato non correlato [componente BindingSource](http://msdn.microsoft.com/library/3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9) che semplifica lo spostamento ai record correlati. Per associare i dati correlati è necessario selezionare le tabelle dallo stesso nodo gerarchico.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedure dettagliate di data](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Procedura dettagliata: Visualizzazione dei dati in un Windows Form](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [Panoramica degli oggetti TableAdapter](../data-tools/tableadapter-overview.md)   
 [Creazione e modifica di dataset tipizzati](../data-tools/creating-and-editing-typed-datasets.md)   
 [Aggiungere nuove origini dati](../data-tools/add-new-data-sources.md)   
 [Procedura: Connettersi ai dati di un database](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [La convalida dei dati](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Procedura: esplorare i dati con il controllo BindingNavigator di Windows Form](http://msdn.microsoft.com/library/0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb)