---
title: Separare DataSet e TableAdapter in progetti diversi | Microsoft Docs
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
- TableAdapters, n-tier applications
- n-tier applications, separating Datasets and TableAdapters
ms.assetid: f66a3940-6227-46af-a930-9177f425f4fd
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1e94c76254b14bdf82e4e7a219cbb0f35cb532f1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49824326"
---
# <a name="separate-datasets-and-tableadapters-into-different-projects"></a>Separare set di dati e TableAdapter in progetti diversi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
I dataset tipizzati sono stati migliorati in modo che il [TableAdapter](http://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364) e classi di set di dati possono essere generate in progetti separati. Ciò consente di separare i livelli applicazione rapidamente e generare applicazioni dati a più livelli.  
  
 La procedura seguente descrive il processo d'uso di[creazione e modifica di dataset tipizzati](../data-tools/creating-and-editing-typed-datasets.md) per generare codice del set di dati in un progetto separato dal progetto che contiene il generato `TableAdapter` codice.  
  
## <a name="separatedatasets-and-tableadapters"></a>Separatedatasets e gli oggetti TableAdapter  
 Quando si separa il codice di set di dati da `TableAdapter` codice, il progetto che contiene il codice del dataset deve trovarsi nella soluzione corrente. Se non si trova il progetto nella soluzione corrente, non sarà disponibile nel **DataSetProject** nell'elenco il **proprietà** finestra.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-separate-the-dataset-into-a-different-project"></a>Per separare il set di dati in un progetto diverso  
  
1. Aprire una soluzione che contiene un set di dati (file con estensione XSD).  
  
   > [!NOTE]
   >  Se la soluzione non contiene il progetto in cui si desidera separare il codice di set di dati, creare il progetto oppure aggiungere un progetto esistente alla soluzione.  
  
2. Fare doppio clic su un file di set di dati tipizzato (un file con estensione XSD) in **Esplora soluzioni** per aprire il dataset nella cache le **Progettazione Dataset**.  
  
3. Selezionare un'area vuota del **Progettazione Dataset**.  
  
4. Nel **delle proprietà** finestra, individuare il **DataSetProject** nodo.  
  
5. Nel **DataSetProject** elencare, selezionare il nome del progetto in cui si desidera generare il codice del set di dati.  
  
    Dopo aver selezionato il progetto in cui si desidera generare il codice del set di dati, il **DataSet File** proprietà viene popolata con un nome file predefinito. Se necessario, è possibile modificare questo nome. Inoltre, se si desidera generare il codice del set di dati in una directory specifica, è possibile impostare il **cartella del progetto** proprietà sul nome di una cartella.  
  
   > [!NOTE]
   >  Quando si separano i DataSet e TableAdapter (impostando il **DataSetProject** proprietà), sarà spostate automaticamente classi parziali del dataset presenti nel progetto. Le classi parziali del dataset devono essere spostate manualmente nel progetto di dataset.  
  
6. Salvare il set di dati.  
  
    Il codice di set di dati viene generato nel progetto selezionato nel **DataSetProject** proprietà e il **TableAdapter** codice viene generato nel progetto corrente.  
  
   Per impostazione predefinita, dopo aver separato il set di dati e `TableAdapter` code, il risultato è un file di classe discreti in ogni progetto. Il progetto originale include un file denominato NomeDataset.Designer.vb (o NomeDataset.Designer.cs) che contiene il `TableAdapter` codice. Il progetto che è designato nel **DataSetProject** proprietà dispone di un file denominato NomeDataset (o NomeDataset) che contiene il codice di set di dati.  
  
> [!NOTE]
>  Per visualizzare il file di classe generata, selezionare il set di dati o `TableAdapter` progetto. Quindi, nella **Esplora soluzioni**, selezionare **Mostra tutti i file** .  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica delle applicazioni dati a più livelli](../data-tools/n-tier-data-applications-overview.md)   
 [Procedura dettagliata: Creazione di un'applicazione dati a più livelli](../data-tools/walkthrough-creating-an-n-tier-data-application.md)   
 [Aggiornamento gerarchico](../data-tools/hierarchical-update.md)   
 [Accesso ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)   
 [ADO.NET](http://msdn.microsoft.com/library/5b96ed06-9759-4966-a797-a1d5f6ee50ca)

