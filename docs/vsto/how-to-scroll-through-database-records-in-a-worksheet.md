---
title: 'Procedura: scorrere i record di un database in un foglio di foglio'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8127a5f61e292fb777be4854796535bbe01226aa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545795"
---
# <a name="how-to-scroll-through-database-records-in-a-worksheet"></a>Procedura: scorrere i record di un database in un foglio di foglio
  Nella procedura riportata di seguito viene illustrato come utilizzare la finestra di progettazione per visualizzare un singolo campo da una tabella di database in un Microsoft Office foglio di lavoro di Excel, con controlli che consentono all'utente finale di scorrere tutti i record.

 È possibile utilizzare la finestra di progettazione solo nei progetti a livello di documento. Tuttavia, è anche possibile aggiungere controlli e associarli ai dati a livello di codice in fase di esecuzione. Per altre informazioni, vedere [procedura dettagliata: data binding semplice in un progetto di componente aggiuntivo VSTO](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md).

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

## <a name="to-scroll-through-database-records-in-a-worksheet"></a>Per scorrere i record del database in un foglio di foglio

1. Aprire un progetto di applicazione Excel in Visual Studio.

2. Aprire la finestra **origini dati** e creare un'origine dati dal database. Per altre informazioni, vedere [aggiungere nuove connessioni](../data-tools/add-new-connections.md).

3. Espandere la tabella che contiene i dati che si desidera visualizzare e selezionare la colonna specifica.

4. Aprire l'elenco dei controlli e selezionare **NamedRange**.

5. Trascinare il <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo nella cella in cui si desidera visualizzare i dati.

6. Dalla scheda **Windows Forms** della **casella degli strumenti**aggiungere un <xref:System.Windows.Forms.BindingNavigator> controllo al foglio di lavoro e impostare i controlli che si desidera utilizzare. Per ulteriori informazioni, vedere [Cenni preliminari sul controllo BindingNavigator &#40;Windows Forms&#41;](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms).

## <a name="see-also"></a>Vedere anche
- [Associare i dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)
