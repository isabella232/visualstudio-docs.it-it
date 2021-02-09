---
title: Usare i controlli WPF nelle soluzioni Office
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
ms.workload:
- office
ms.openlocfilehash: 7bc720e6218e4cbb76b14f356d190b738e31ede3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921910"
---
# <a name="use-wpf-controls-in-office-solutions"></a>Usare i controlli WPF nelle soluzioni Office

Anche se le soluzioni create tramite gli strumenti di sviluppo di Office in Visual Studio sono progettate per essere usate direttamente con i controlli Windows Form, è possibile usare anche i controlli WPF nelle soluzioni. Windows Presentation Foundation (WPF) è un'alternativa a Windows Form per progettare interfacce utente. In WPF viene usato un linguaggio di markup, denominato Extensible Application Markup Language (XAML), che offre nuove tecniche per l'incorporazione di interfacce utente, supporti e documenti. Per ulteriori informazioni, vedere [Cenni preliminari su WPF](/dotnet/framework/wpf/introduction-to-wpf).

[!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

Qualsiasi elemento dell'interfaccia utente che può contenere i controlli Windows Form in una soluzione Office può ospitare anche i controlli WPF, tra cui:

- Documenti e fogli di lavoro nelle personalizzazioni a livello di documento.

- Riquadri azione nelle personalizzazioni a livello di documento.

- Riquadri attività personalizzati nei componenti aggiuntivi VSTO.

- Aree del modulo nei componenti aggiuntivi VSTO per Outlook.

## <a name="add-wpf-controls-to-office-projects-at-design-time"></a>Aggiungere controlli WPF ai progetti di Office in fase di progettazione

Non è possibile aggiungere i controlli WPF direttamente agli elementi dell'interfaccia utente nelle soluzioni Office. Aggiungere invece un elemento del **controllo utente (WPF)** al progetto e usarlo come area di progettazione per i controlli WPF. Aggiungere quindi il controllo utente WPF a un elemento dell'interfaccia utente nel progetto.

### <a name="to-add-wpf-controls-to-an-actions-pane-custom-task-pane-or-form-region"></a>Per aggiungere i controlli WPF a un riquadro azioni, un riquadro attività personalizzato o un'area del modulo

1. Aprire un progetto al quale si vuole aggiungere un riquadro attività personalizzato, un riquadro azioni o un'area del modulo.

2. Aggiungere un elemento del **controllo utente (WPF)** al progetto.

3. Dalla **casella degli strumenti** aggiungere controlli WPF all'area di progettazione del controllo utente WPF.

     Per impostazione predefinita, quando la finestra di progettazione del controllo utente WPF è aperta, la **casella degli strumenti** contiene solo i controlli WPF.

4. Compilare il progetto.

5. Aggiungere un riquadro azioni, un'area del modulo o un riquadro attività personalizzato al progetto:

    - Per le aree del modulo, aggiungere un elemento dell' **area del modulo di Outlook** al progetto. Per altre informazioni, vedere [procedura: aggiungere un'area del modulo a un progetto di componente aggiuntivo di Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).

    - Per i riquadri azioni, aggiungere un **controllo del riquadro azioni** o un elemento del **controllo utente** al progetto. Per altre informazioni, vedere [procedura: aggiungere un riquadro azioni ai documenti di Word o alle cartelle di lavoro di Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).

    - Per i riquadri attività personalizzati, aggiungere un elemento del **controllo utente** al progetto. Per altre informazioni, vedere [procedura: aggiungere un riquadro attività personalizzato a un'applicazione](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).

6. Dalla scheda  **controlli utente WPF** di NomeProgetto della **casella degli strumenti** trascinare il controllo utente WPF nella finestra di progettazione per il riquadro azioni, l'area del modulo o il riquadro attività personalizzato.

     Visual Studio crea automaticamente un oggetto <xref:System.Windows.Forms.Integration.ElementHost> che contiene il controllo utente WPF nell'elemento dell'interfaccia utente.

7. Ricompilare il progetto.

#### <a name="to-add-wpf-controls-to-a-document-or-worksheet-in-a-document-level-project"></a>Per aggiungere controlli WPF a un documento o un foglio di lavoro in un progetto a livello di documento

1. Aprire un progetto a livello di documento per Word o Excel.

2. Aggiungere un elemento del **controllo utente (WPF)** al progetto.

3. Dalla **casella degli strumenti** aggiungere controlli WPF all'area di progettazione del controllo utente WPF.

4. Compilare il progetto.

5. Aggiungere un elemento di **controllo utente** , ovvero un Windows Form controllo utente, al progetto.

6. Aprire la finestra di progettazione per il controllo utente Windows Form.

7. Dalla scheda  **controlli utente WPF** di NomeProgetto della **casella degli strumenti** trascinare il controllo utente WPF nella finestra di progettazione.

     Visual Studio crea automaticamente un oggetto <xref:System.Windows.Forms.Integration.ElementHost> che contiene il controllo utente WPF nel controllo utente Windows Form.

8. Scrivere il codice che aggiunge a livello di codice il controllo utente Windows Form al documento o alla cartella di lavoro. Per altre informazioni, vedere [aggiungere controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md).

    > [!NOTE]
    > Non è possibile trascinare il controllo utente Windows Form nel documento o nel foglio di lavoro nella finestra di progettazione.

9. Ricompilare il progetto.

## <a name="host-wpf-controls-by-using-the-elementhost-class"></a>Ospitare controlli WPF tramite la classe ElementHost

In Visual Studio vengono fornite funzionalità che consentono di usare i controlli Windows Form nelle soluzioni Office, ma non vengono fornite funzionalità simili per i controlli WPF. Ad esempio, è possibile aggiungere controlli Windows Form ai documenti e ai fogli di elaborazione in fase di progettazione trascinando i controlli dalla **casella degli strumenti** o in fase di esecuzione usando metodi helper. Questi strumenti non sono tuttavia disponibili per i controlli WPF.

I controlli WPF usano la classe <xref:System.Windows.Forms.Integration.ElementHost> come livello di integrazione tra un form o un controllo Windows Form e i controlli WPF. Quando si aggiungono i controlli WPF alla soluzione in fase di progettazione, Visual Studio genera automaticamente un oggetto <xref:System.Windows.Forms.Integration.ElementHost>.

## <a name="wpf-resources"></a>Risorse WPF

Per altre informazioni sulle problematiche di progettazione e architettura per l'hosting dei controlli WPF in form e controlli Windows Form, vedere gli argomenti seguenti:

- [Architettura di input per l'interoperabilità Windows Form e WPF](/dotnet/framework/wpf/advanced/windows-forms-and-wpf-interoperability-input-architecture)

- [Mapping delle proprietà Windows Form e WPF](/dotnet/framework/wpf/advanced/windows-forms-and-wpf-property-mapping)

- [Interoperatività di WPF e Windows Form](/dotnet/framework/wpf/advanced/wpf-and-windows-forms-interoperation)

- [Controlli di Windows Form e controlli WPF equivalenti](/dotnet/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls)

Per altre informazioni sull'aggiunta dei controlli WPF a form e controlli Windows Form in Visual Studio in fase di progettazione, vedere gli argomenti seguenti:

- [Procedura dettagliata: creare nuovi contenuti WPF in Windows Form in fase di progettazione](/dotnet/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time)

- [Procedura dettagliata: disposizione del contenuto WPF in Windows Form in fase di progettazione](/dotnet/framework/winforms/advanced/walkthrough-arranging-wpf-content-on-windows-forms-at-design-time)

- [Procedura dettagliata: stile contenuto WPF](/dotnet/framework/winforms/advanced/walkthrough-styling-wpf-content)

## <a name="see-also"></a>Vedi anche

- [Personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md)
- [Cenni preliminari sui controlli Windows Form nei documenti di Office](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Panoramica del riquadro azioni](../vsto/actions-pane-overview.md)
- [Riquadri attività personalizzati](../vsto/custom-task-panes.md)
- [Creazione di aree del modulo di Outlook](../vsto/creating-outlook-form-regions.md)
- [Procedura: aggiungere un riquadro azioni ai documenti di Word o alle cartelle di lavoro di Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Procedura: aggiungere un riquadro attività personalizzato a un'applicazione](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)
- [Procedura: aggiungere un'area del modulo a un progetto di componente aggiuntivo di Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
