---
title: Accedere a un'area del modulo in fase di esecuzione
description: Informazioni su come accedere a un'area del modulo in diversi tipi di progetto e versioni di Microsoft Office in fase di esecuzione.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Inspectors [Office development in Visual Studio]
- Explorers [Office development in Visual Studio]
- form regions [Office development in Visual Studio], accessing at run time
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 62d8236b987afbb7dc9d5e4462b79ffb4fe00bc5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99928874"
---
# <a name="access-a-form-region-at-run-time"></a>Accedere a un'area del modulo in fase di esecuzione

|Si applica a|
|----------------|
|Le informazioni fornite in questo argomento sono valide solo per i tipi di progetto e le versioni di Microsoft Office seguenti. Per ulteriori informazioni, vedere [funzionalità disponibili in base ai tipi di progetto e applicazioni di Office](../vsto/features-available-by-office-application-and-project-type.md).<br /><br /> **Tipo di progetto**<br /><br /> -Progetti di componente aggiuntivo VSTO<br /><br /> **Versione di Microsoft Office**<br /><br /> -   [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)]|

 Usare la classe `Globals` per accedere alle aree del modulo da qualsiasi punto del progetto Outlook. Per ulteriori informazioni sulla `Globals` classe, vedere [accesso globale a oggetti nei progetti di Office](../vsto/global-access-to-objects-in-office-projects.md).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="access-form-regions-that-appear-in-a-specific-outlook-inspector-window"></a>Accedere alle aree del modulo visualizzate in una specifica finestra di controllo di Outlook
 Per accedere a tutte le aree del modulo visualizzate in uno specifico controllo Outlook, chiamare la proprietà `FormRegions` della classe `Globals` e passare un oggetto <xref:Microsoft.Office.Interop.Outlook.Inspector> che rappresenta il controllo.

 Nell'esempio seguente viene recuperata la raccolta di aree del modulo visualizzate nel controllo che ha attualmente lo stato attivo. Viene quindi effettuato l'accesso a un'area del modulo della raccolta denominata `formRegion1` e il testo visualizzato in una casella di testo viene impostato su `Hello World`.

 [!code-vb[Trin_Outlook_FR_Access#2](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#2)]
 [!code-csharp[Trin_Outlook_FR_Access#2](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#2)]

## <a name="access-form-regions-that-appear-in-a-specific-outlook-explorer-window"></a>Accedere alle aree del modulo visualizzate in una specifica finestra di Outlook Explorer
 Per accedere a tutte le aree del modulo visualizzate in una specifica finestra di esplorazione Outlook, chiamare la proprietà `FormRegions` della classe `Globals` e passare un oggetto <xref:Microsoft.Office.Interop.Outlook.Explorer> che rappresenta la finestra di esplorazione.

 Nell'esempio seguente viene recuperata la raccolta di aree del modulo visualizzate nella finestra di esplorazione che ha attualmente lo stato attivo. Viene quindi effettuato l'accesso a un'area del modulo della raccolta denominata `formRegion1` e il testo visualizzato in una casella di testo viene impostato su `Hello World`.

 [!code-vb[Trin_Outlook_FR_Access#3](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#3)]
 [!code-csharp[Trin_Outlook_FR_Access#3](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#3)]

## <a name="access-all-form-regions"></a>Accedere a tutte le aree del modulo
 Per accedere a tutte le aree del modulo visualizzate in tutte le finestre di esplorazione e in tutti i controlli, chiamare la proprietà `FormRegions` della classe `Globals` .

 Nell'esempio seguente viene recuperata la raccolta di aree del modulo visualizzate in tutte le finestre di esplorazione e in tutti i controlli. Viene quindi effettuato l'accesso a un'area del modulo denominata `formRegion1` e il testo visualizzato in una casella di testo viene impostato su `Hello World`.

 [!code-vb[Trin_Outlook_FR_Access#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#1)]
 [!code-csharp[Trin_Outlook_FR_Access#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#1)]

## <a name="access-controls-on-a-form-region"></a>Controlli di accesso in un'area del modulo
 Per accedere ai controlli presenti in un'area del modulo usando la classe `Globals` , è necessario rendere tali controlli accessibili al codice dall'esterno del file di codice dell'area del modulo.

### <a name="form-regions-designed-in-the-form-region-designer"></a>Aree del modulo progettate nella finestra di progettazione dell'area del modulo
 Per C# cambiare il modificatore di ogni controllo a cui si vuole accedere. Per eseguire questa operazione, selezionare ogni controllo nella finestra di progettazione dell'area del modulo e impostare la proprietà **Modificatori** su **Interna** o **pubblica** nella finestra **Proprietà** . Ad esempio, se si imposta la proprietà **Modifier** di `textBox1` su **Internal**, è possibile accedere a `textBox1` digitando `Globals.FormRegions.FormRegion1.textBox1`.

 Per Visual Basic non è necessario cambiare il modificatore.

### <a name="imported-form-regions"></a>Aree del modulo importate
 Quando si importa un'area del modulo progettata in Outlook, il modificatore di accesso di ogni controllo presente nell'area del modulo diventa privato. Dal momento che non è possibile usare la finestra di progettazione dell'area del modulo per modificare un'area del modulo importata, non esiste alcun modo per cambiare il modificatore di un controllo nella finestra **Proprietà** .

 Per consentire l'accesso a un controllo dall'esterno del file di codice dell'area del modulo, creare una proprietà in tale file di codice per la restituzione del controllo.

 Per altre informazioni su come creare le proprietà in C#, vedere [procedura: dichiarare e usare le proprietà di lettura/scrittura &#40;&#35; Guida di programmazione di C&#41;](/dotnet/csharp/programming-guide/classes-and-structs/how-to-declare-and-use-read-write-properties).

 Per ulteriori informazioni su come creare proprietà in Visual Basic, vedere [procedura: creare una proprietà (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/procedures/how-to-create-a-property).

## <a name="see-also"></a>Vedi anche
- [Linee guida per la creazione di aree del modulo di Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [Procedura dettagliata: progettare un'area del modulo di Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Procedura: aggiungere un'area del modulo a un progetto di componente aggiuntivo di Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Azioni personalizzate nelle aree del modulo di Outlook](../vsto/custom-actions-in-outlook-form-regions.md)
- [Associare un'area del modulo a una classe messaggio di Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
- [Procedura dettagliata: importare un'area del modulo progettata in Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
- [Procedura: impedire la visualizzazione di un'area del modulo in Outlook](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)
- [Creazione di aree del modulo di Outlook](../vsto/creating-outlook-form-regions.md)
- [Accedere alla barra multifunzione in fase di esecuzione](../vsto/accessing-the-ribbon-at-run-time.md)
