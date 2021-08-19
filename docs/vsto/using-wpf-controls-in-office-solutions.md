---
title: Usare i controlli WPF in Office soluzioni
description: Informazioni su come usare i controlli Windows Presentation Foundation (WPF) per la progettazione di interfacce utente in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WPF [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 6f6acecd2d6554da0efbcb0b31d61d3f51511180
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122114971"
---
# <a name="use-wpf-controls-in-office-solutions"></a>Usare i controlli WPF in Office soluzioni

Anche se le soluzioni create tramite gli strumenti di sviluppo di Office in Visual Studio sono progettate per essere usate direttamente con i controlli Windows Form, è possibile usare anche i controlli WPF nelle soluzioni. Windows Presentation Foundation (WPF) è un'alternativa a Windows Form per progettare interfacce utente. In WPF viene usato un linguaggio di markup, denominato Extensible Application Markup Language (XAML), che offre nuove tecniche per l'incorporazione di interfacce utente, supporti e documenti. Per altre informazioni, vedere Panoramica [di WPF.](/dotnet/framework/wpf/introduction-to-wpf)

[!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

Qualsiasi elemento dell'interfaccia utente che può contenere i controlli Windows Form in una soluzione Office può ospitare anche i controlli WPF, tra cui:

- Documenti e fogli di lavoro nelle personalizzazioni a livello di documento.

- Riquadri azione nelle personalizzazioni a livello di documento.

- Riquadri attività personalizzati nei componenti aggiuntivi VSTO.

- Aree del modulo nei componenti aggiuntivi VSTO per Outlook.

## <a name="add-wpf-controls-to-office-projects-at-design-time"></a>Aggiungere controlli WPF a Office progetti in fase di progettazione

Non è possibile aggiungere i controlli WPF direttamente agli elementi dell'interfaccia utente nelle soluzioni Office. Aggiungere invece un **elemento Controllo utente (WPF)** al progetto e usarlo come area di progettazione per i controlli WPF. Aggiungere quindi il controllo utente WPF a un elemento dell'interfaccia utente nel progetto.

### <a name="to-add-wpf-controls-to-an-actions-pane-custom-task-pane-or-form-region"></a>Per aggiungere i controlli WPF a un riquadro azioni, un riquadro attività personalizzato o un'area del modulo

1. Aprire un progetto al quale si vuole aggiungere un riquadro attività personalizzato, un riquadro azioni o un'area del modulo.

2. Aggiungere un **elemento Controllo utente (WPF)** al progetto.

3. Dalla casella **degli strumenti** aggiungere controlli WPF all'area di progettazione del controllo utente WPF.

     Per impostazione predefinita, quando la finestra di progettazione dei controlli utente WPF è aperta, la casella **degli** strumenti contiene solo controlli WPF.

4. Compilare il progetto.

5. Aggiungere un riquadro azioni, un'area del modulo o un riquadro attività personalizzato al progetto:

    - Per le aree del modulo, **aggiungere Outlook'elemento Area del** modulo al progetto. Per altre informazioni, [vedere Procedura: Aggiungere un'area del modulo a un progetto Outlook componente aggiuntivo](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).

    - Per i riquadri azioni, aggiungere un **elemento Controllo riquadro azioni** o **Controllo** utente al progetto. Per altre informazioni, vedere Procedura: Aggiungere un riquadro azioni a documenti di Word o Excel [cartelle di lavoro.](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)

    - Per i riquadri attività personalizzati, aggiungere **un elemento Controllo** utente al progetto. Per altre informazioni, vedere [Procedura: Aggiungere un riquadro attività personalizzato a un'applicazione.](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)

6. Dalla scheda *ProjectName* **WPF User Controls** (Controlli utente WPF NomeProgetto) della casella degli strumenti trascinare il controllo utente WPF nella finestra di progettazione per il riquadro azioni, l'area del modulo o il riquadro attività personalizzato. 

     Visual Studio crea automaticamente un oggetto <xref:System.Windows.Forms.Integration.ElementHost> che contiene il controllo utente WPF nell'elemento dell'interfaccia utente.

7. Ricompilare il progetto.

#### <a name="to-add-wpf-controls-to-a-document-or-worksheet-in-a-document-level-project"></a>Per aggiungere controlli WPF a un documento o un foglio di lavoro in un progetto a livello di documento

1. Aprire un progetto a livello di documento per Word o Excel.

2. Aggiungere un **elemento Controllo utente (WPF)** al progetto.

3. Dalla casella **degli strumenti** aggiungere controlli WPF all'area di progettazione del controllo utente WPF.

4. Compilare il progetto.

5. Aggiungere un **elemento Controllo** utente , ovvero un controllo utente Windows Form personalizzato, al progetto.

6. Aprire la finestra di progettazione per il controllo utente Windows Form.

7. Dalla scheda *ProjectName* **WPF User Controls (Controlli** utente WPF NomeProgetto) della Casella degli **strumenti** trascinare il controllo utente WPF nella finestra di progettazione.

     Visual Studio crea automaticamente un oggetto <xref:System.Windows.Forms.Integration.ElementHost> che contiene il controllo utente WPF nel controllo utente Windows Form.

8. Scrivere il codice che aggiunge a livello di codice il controllo utente Windows Form al documento o alla cartella di lavoro. Per altre informazioni, vedere [Aggiungere controlli ai documenti Office in fase di esecuzione.](../vsto/adding-controls-to-office-documents-at-run-time.md)

    > [!NOTE]
    > Non è possibile trascinare il controllo utente Windows Form nel documento o nel foglio di lavoro nella finestra di progettazione.

9. Ricompilare il progetto.

## <a name="host-wpf-controls-by-using-the-elementhost-class"></a>Ospitare controlli WPF usando la classe ElementHost

In Visual Studio vengono fornite funzionalità che consentono di usare i controlli Windows Form nelle soluzioni Office, ma non vengono fornite funzionalità simili per i controlli WPF. Ad esempio, è possibile aggiungere Windows Form a documenti e fogli di lavoro in fase di progettazione trascinando i controlli dalla Casella degli strumenti o in fase di esecuzione usando metodi helper. Questi strumenti non sono tuttavia disponibili per i controlli WPF.

I controlli WPF usano la classe <xref:System.Windows.Forms.Integration.ElementHost> come livello di integrazione tra un form o un controllo Windows Form e i controlli WPF. Quando si aggiungono i controlli WPF alla soluzione in fase di progettazione, Visual Studio genera automaticamente un oggetto <xref:System.Windows.Forms.Integration.ElementHost>.

## <a name="wpf-resources"></a>Risorse WPF

Per altre informazioni sulle problematiche di progettazione e architettura per l'hosting dei controlli WPF in form e controlli Windows Form, vedere gli argomenti seguenti:

- [Windows Architettura di input per l'interoperabilità di form e WPF](/dotnet/framework/wpf/advanced/windows-forms-and-wpf-interoperability-input-architecture)

- [Windows Mapping di form e proprietà WPF](/dotnet/framework/wpf/advanced/windows-forms-and-wpf-property-mapping)

- [Interoperatività di WPF e Windows Forms](/dotnet/framework/wpf/advanced/wpf-and-windows-forms-interoperation)

- [Windows Controlli Form e controlli WPF equivalenti](/dotnet/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls)

Per altre informazioni sull'aggiunta dei controlli WPF a form e controlli Windows Form in Visual Studio in fase di progettazione, vedere gli argomenti seguenti:

- [Procedura dettagliata: Creare nuovo contenuto WPF in Windows form in fase di progettazione](/dotnet/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time)

- [Procedura dettagliata: Disporre il contenuto WPF Windows form in fase di progettazione](/dotnet/framework/winforms/advanced/walkthrough-arranging-wpf-content-on-windows-forms-at-design-time)

- [Procedura dettagliata: Stile del contenuto WPF](/dotnet/framework/winforms/advanced/walkthrough-styling-wpf-content)

## <a name="see-also"></a>Vedi anche

- [Office Personalizzazione dell'interfaccia utente](../vsto/office-ui-customization.md)
- [Windows Panoramica dei controlli form Office documenti](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Panoramica del riquadro Azioni](../vsto/actions-pane-overview.md)
- [Riquadri attività personalizzati](../vsto/custom-task-panes.md)
- [Creare aree Outlook modulo](../vsto/creating-outlook-form-regions.md)
- [Procedura: Aggiungere un riquadro azioni a documenti di Word o Excel cartelle di lavoro](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Procedura: Aggiungere un riquadro attività personalizzato a un'applicazione](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)
- [Procedura: Aggiungere un'area del modulo a Outlook progetto di componente aggiuntivo](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
