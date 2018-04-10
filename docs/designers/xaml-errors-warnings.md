---
title: Errori e avvisi XAML | Microsoft Docs
ms.date: 03/06/2018
ms.technology: vs-ide-designers
ms.topic: article
ms.assetid: 34eac8a0-7ec5-4c40-b97a-0126ed367931
author: karann-msft
ms.author: karann
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 60e29417e1a993adfb2c4bb7c78a6f1ed0209cef
ms.sourcegitcommit: efd8c8e0a9ba515d47efcc7bd370eaaf4771b5bb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/03/2018
---
# <a name="xaml-errors-and-warnings"></a>Errori e avvisi XAML

Durante la creazione di codice XAML, Visual Studio analizza il codice mentre lo si digita. Quando viene rilevato un errore in una riga di codice, viene visualizzata una sottolineatura ondulata. Se si porta il cursore del mouse sulla sottolineatura, vengono visualizzate informazioni sull'errore o sull'avviso. Per alcuni errori e avvisi viene visualizzata una lampadina di azione e la combinazione di tasti **CTRL**+**.** consente di visualizzare le opzioni per la risoluzione del problema.

## <a name="error-types"></a>Tipi di errore

Vari strumenti analizzano il codice XAML in background. Gli errori XAML sono suddivisi nei tre tipi seguenti, a seconda dello strumento che ha rilevato l'errore:

|**Errore rilevato da**|**Formato codice di errore**|  
|--------------------------------|-----------------|  
|Servizio di linguaggio XAML (Editor XAML)|XLSxxxx|  
|Finestra di progettazione XAML|XDGxxxx|  
|Modifica e continuazione XAML|XECxxxx|  

> [!Note]
> Non tutti gli errori/avvisi hanno un codice corrispondente. Gli errori senza codice sono in genere errori della finestra di progettazione XAML.


## <a name="suppress-xaml-designer-errors"></a>Eliminare gli errori della finestra di progettazione XAML

Aprire la finestra di dialogo **Opzioni** selezionando **Strumenti > Opzioni** e selezionare **Editor di testo > XAML > Varie**.

Deselezionare la casella di controllo **Show errors detected by the XAML designer** (Visualizza errori rilevati dalla finestra di progettazione XAML).

![Eliminare gli errori di finestra di progettazione XAML](../designers/media/suppress_xaml_designer_errors.PNG "SuppressXAMLDesignerErrors")


