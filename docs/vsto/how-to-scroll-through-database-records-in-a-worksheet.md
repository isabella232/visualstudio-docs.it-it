---
title: 'Procedura: Scorrere i record di database in un foglio di lavoro'
description: Informazioni su come usare la finestra di progettazione per visualizzare un singolo campo da una tabella di database in un foglio Microsoft Excel foglio Microsoft Excel dati
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- databases [Office development in Visual Studio], scrolling records
- records [Office development in Visual Studio], scrolling
- data [Office development in Visual Studio], scrolling database records
- worksheets [Office development in Visual Studio], scrolling records
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 94055cdc5bd95850e87d349e573ca3253ba84eba8b92a611730e827cd5a5da0e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121366108"
---
# <a name="how-to-scroll-through-database-records-in-a-worksheet"></a>Procedura: Scorrere i record di database in un foglio di lavoro
  La procedura seguente illustra come usare la finestra di progettazione per visualizzare un singolo campo di una tabella di database in un foglio di lavoro di Microsoft Office Excel, con controlli che consentono all'utente finale di scorrere tutti i record.

 È possibile usare la finestra di progettazione solo nei progetti a livello di documento. Tuttavia, è anche possibile aggiungere controlli e associarli ai dati a livello di codice in fase di esecuzione. Per altre informazioni, vedere [Walkthrough: Simple data binding in VSTO Add-in project](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md).

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

## <a name="to-scroll-through-database-records-in-a-worksheet"></a>Per scorrere i record di database in un foglio di lavoro

1. Aprire un Excel di applicazione in Visual Studio.

2. Aprire la **finestra Origini** dati e creare un'origine dati dal database. Per altre informazioni, vedere [Aggiungere nuove connessioni.](../data-tools/add-new-connections.md)

3. Espandere la tabella contenente i dati da visualizzare e selezionare la colonna specifica.

4. Aprire l'elenco dei controlli e **selezionare NamedRange**.

5. Trascinare <xref:Microsoft.Office.Tools.Excel.NamedRange> il controllo nella cella in cui si desidera visualizzare i dati.

6. Dalla scheda **Windows Forms** della **Casella** degli strumenti aggiungere un controllo al foglio di lavoro e impostare i controlli <xref:System.Windows.Forms.BindingNavigator> da usare. Per altre informazioni, vedere [Panoramica del controllo BindingNavigator &#40;Windows Forms&#41;](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms).

## <a name="see-also"></a>Vedi anche
- [Associare dati ai controlli in Office soluzioni](../vsto/binding-data-to-controls-in-office-solutions.md)
