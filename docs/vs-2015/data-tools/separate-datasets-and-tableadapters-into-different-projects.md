---
title: Separare i set di impostazioni e i TableAdapter in progetti diversi | Microsoft Docs
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
- TableAdapters, n-tier applications
- n-tier applications, separating Datasets and TableAdapters
ms.assetid: f66a3940-6227-46af-a930-9177f425f4fd
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6f6ec76e79cc1c4759cbe05d8bdcacc1297b655b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655438"
---
# <a name="separate-datasets-and-tableadapters-into-different-projects"></a>Separare set di dati e TableAdapter in progetti diversi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

I DataSet tipizzati sono stati migliorati in modo che le classi [TableAdapters](https://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364) e DataSet possano essere generate in progetti distinti. Ciò consente di separare rapidamente i livelli dell'applicazione e generare applicazioni dati a più livelli.

 Nella procedura riportata di seguito viene descritto il processo di utilizzo del Progettazione DataSet per generare il codice del set di dati in un progetto separato dal progetto che contiene il codice `TableAdapter` generato.

## <a name="separatedatasets-and-tableadapters"></a>Separatedatasets e TableAdapters
 Quando si separa il codice del set di dati da `TableAdapter` codice, il progetto che contiene il codice del set di dati deve trovarsi nella soluzione corrente. Se il progetto non si trova nella soluzione corrente, non sarà disponibile nell'elenco **progetto DataSet** nella finestra **Proprietà** .

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-separate-the-dataset-into-a-different-project"></a>Per separare il set di dati in un progetto diverso

1. Aprire una soluzione contenente un set di dati (file XSD).

   > [!NOTE]
   > Se la soluzione non contiene il progetto in cui si desidera separare il codice del set di dati, creare il progetto o aggiungere un progetto esistente alla soluzione.

2. Fare doppio clic su un file di set di dati tipizzato (un file con estensione XSD) in **Esplora soluzioni** per aprire il set di dati nel **Progettazione DataSet**.

3. Selezionare un'area vuota del **Progettazione DataSet**.

4. Nella finestra **Proprietà** individuare il nodo del **progetto DataSet** .

5. Nell'elenco **progetto DataSet** selezionare il nome del progetto in cui si desidera generare il codice del set di dati.

    Dopo aver selezionato il progetto in cui si desidera generare il codice del set di dati, la proprietà **file del set di dati** viene popolata con un nome di file predefinito. Se necessario, è possibile modificare questo nome. Inoltre, se si desidera generare il codice del set di dati in una directory specifica, è possibile impostare la proprietà **cartella di progetto** sul nome di una cartella.

   > [!NOTE]
   > Quando si separano i set di dati e i TableAdapter (impostando la proprietà del **progetto DataSet** ), le classi del set di dati parziali esistenti nel progetto non verranno spostate automaticamente. Le classi parziali del set di dati esistenti devono essere spostate manualmente nel progetto DataSet.

6. Salvare il set di dati.

    Il codice del set di dati viene generato nel progetto selezionato nella proprietà del **progetto DataSet** e il codice **TableAdapter** viene generato nel progetto corrente.

   Per impostazione predefinita, dopo aver separato il set di dati e `TableAdapter` codice, il risultato è un file di classe discreto in ogni progetto. Il progetto originale include un file denominato DataSetName. designer. vb (o DatasetName.Designer.cs) che contiene il codice `TableAdapter`. Il progetto designato nella proprietà del **progetto DataSet** include un file denominato DataSetName. DataSet. designer. vb (o DataSetName.DataSet.designer.cs) che contiene il codice del set di dati.

> [!NOTE]
> Per visualizzare il file di classe generato, selezionare il set di dati o il progetto `TableAdapter`. Quindi, in **Esplora soluzioni**, selezionare **Mostra tutti i file** .

## <a name="see-also"></a>Vedere anche
 [Panoramica delle applicazioni dati a più livelli](../data-tools/n-tier-data-applications-overview.md) [procedura dettagliata: creazione di un](../data-tools/walkthrough-creating-an-n-tier-data-application.md) [aggiornamento gerarchico](../data-tools/hierarchical-update.md) di un'applicazione dati a più livelli [accesso ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md) [ADO.NET](https://msdn.microsoft.com/library/5b96ed06-9759-4966-a797-a1d5f6ee50ca)
