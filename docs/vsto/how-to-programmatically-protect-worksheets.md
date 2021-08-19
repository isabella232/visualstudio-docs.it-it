---
title: 'Procedura: Proteggere i fogli di lavoro a livello di codice'
description: Informazioni su come usare la funzionalità di protezione in Microsoft Excel per impedire a utenti e codice di modificare oggetti in un foglio di lavoro.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- protection, adding to worksheets
- documents [Office development in Visual Studio], document protection
- document protection, adding to worksheets
- worksheets, protecting
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 7de3df087bc275153ebd7a0bfc50c087ea559ee3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122155837"
---
# <a name="how-to-programmatically-protect-worksheets"></a>Procedura: Proteggere i fogli di lavoro a livello di codice
  La funzionalità di protezione di Microsoft Office Excel consente di impedire la modifica degli oggetti di un foglio di lavoro da parte degli utenti o mediante codice. Per impostazione predefinita, dopo l'attivazione della protezione tutte le celle risultano bloccate.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Nelle personalizzazioni a livello di documento è possibile proteggere i fogli di lavoro tramite la finestra di progettazione di Excel. È anche possibile proteggere un foglio di lavoro a livello di codice in fase di esecuzione, in qualsiasi tipo di progetto.

> [!NOTE]
> Non è possibile aggiungere controlli Windows Form alle aree protette di un foglio di lavoro.

## <a name="use-the-designer"></a>Usare la finestra di progettazione

### <a name="to-protect-a-worksheet-in-the-designer"></a>Per proteggere un foglio di lavoro nella finestra di progettazione

1. Nel gruppo **Modifiche** della scheda **Verifica** fare clic su **Proteggi foglio**.

    Verrà **visualizzata la finestra di** dialogo Proteggi foglio . È possibile impostare una password e specificare le azioni che gli utenti possono eseguire nel foglio di lavoro, ad esempio formattare le celle o inserire righe.

   È anche possibile consentire agli utenti di modificare intervalli specifici nei fogli di lavoro protetti.

### <a name="to-allow-editing-in-specific-ranges"></a>Per consentire la modifica in intervalli specifici

1. Nel gruppo **Modifiche** della scheda **Verifica** fare clic su **Consenti agli utenti di modificare gli intervalli**.

     Verrà **visualizzata la finestra di dialogo Consenti** agli utenti di modificare gli intervalli .  È possibile specificare gli intervalli che possono essere sbloccati mediante l'inserimento di una password e gli utenti che possono modificarli senza immettere alcuna password.

## <a name="use-code-at-run-time"></a>Usare il codice in fase di esecuzione
 Il codice seguente imposta la password tramite la variabile getPasswordFromUser, che contiene la password ottenuta dall'utente, e consente solo l'ordinamento.

### <a name="to-protect-a-worksheet-by-using-code-in-a-document-level-customization"></a>Per proteggere un foglio di lavoro mediante codice in una personalizzazione a livello di documento

1. Chiamare il metodo <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A> del foglio di lavoro. Questo esempio presuppone l'utilizzo di un foglio di lavoro denominato `Sheet1`.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet27":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet27":::

### <a name="to-protect-a-worksheet-by-using-code-in-a-vsto-add-in"></a>Per proteggere un foglio di lavoro mediante codice in un componente aggiuntivo VSTO

1. Chiamare il metodo <xref:Microsoft.Office.Interop.Excel._Worksheet.Protect%2A> del foglio di lavoro attivo.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet17":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet17":::

## <a name="see-also"></a>Vedi anche
- [Usare i fogli di lavoro](../vsto/working-with-worksheets.md)
- [Procedura: Rimuovere la protezione dai fogli di lavoro a livello di codice](../vsto/how-to-programmatically-remove-protection-from-worksheets.md)
- [Procedura: Proteggere le cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-protect-workbooks.md)
- [Procedura: Nascondere fogli di lavoro a livello di codice](../vsto/how-to-programmatically-hide-worksheets.md)
- [Panoramica degli elementi host e dei controlli host](../vsto/host-items-and-host-controls-overview.md)
- [Elemento host Foglio di lavoro](../vsto/worksheet-host-item.md)
- [Accesso globale agli oggetti nei Office progetto](../vsto/global-access-to-objects-in-office-projects.md)
- [Parametri facoltativi nelle Office soluzioni](../vsto/optional-parameters-in-office-solutions.md)
