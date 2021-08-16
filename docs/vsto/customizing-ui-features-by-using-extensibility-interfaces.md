---
title: Personalizzare le funzionalità dell'interfaccia utente usando le interfacce di estendibilità
description: Informazioni sul fatto che Office strumenti di sviluppo in Visual Studio interfacce di estendibilità che consentono di personalizzare le funzionalità dell'interfaccia utente.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ICustomTaskPaneConsumer interface
- IRibbonExtensibility interface
- UI customizing [Office development in Visual Studio]
- user interfaces [Office development in Visual Studio], customizing
- application-level add-ins [Office development in Visual Studio], extensibility interfaces
- customizing UI features [Office development in Visual Studio]
- FormRegionStartup interface
- add-ins [Office development in Visual Studio], extensibility interfaces
- extensibility interfaces [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: b09bef8bfedc1420172c11ab8913d2ba9b305964ef0cd4d0212477d84490de43
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121424411"
---
# <a name="customize-ui-features-by-using-extensibility-interfaces"></a>Personalizzare le funzionalità dell'interfaccia utente usando le interfacce di estendibilità
  Gli strumenti di sviluppo di Office in Visual Studio forniscono classi e finestre di progettazione che gestiscono molti dettagli di implementazione quando vengono usate per creare riquadri attività personalizzati, personalizzazioni della barra multifunzione e aree del modulo di Outlook in un componente aggiuntivo VSTO. Tuttavia, se sono necessari requisiti speciali è anche possibile implementare *l'interfaccia di estendibilità* per ogni funzionalità.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

## <a name="overview-of-extensibility-interfaces"></a>Panoramica delle interfacce di estendibilità
 Microsoft Office definisce un set di interfacce di estendibilità che possono essere implementate nei componenti aggiuntivi VSTO COM per personalizzare determinate funzionalità, ad esempio la barra multifunzione. Queste interfacce forniscono il controllo completo sulle funzionalità alle quali forniscono l'accesso. Tuttavia, l'implementazione di queste interfacce richiede una certa conoscenza dell'interoperabilità COM nel codice gestito. In alcuni casi, il modello di programmazione di queste interfacce non è intuitivo neppure per gli sviluppatori abituati a .NET Framework.

 Quando si crea un componente aggiuntivo VSTO usando i modelli di progetto di Office in Visual Studio, non è necessario implementare interfacce di estendibilità per personalizzare funzionalità come la barra multifunzione. Queste interfacce vengono implementate automaticamente da [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Al contrario, è possibile usare classi e finestre di progettazione più intuitive fornite da Visual Studio. Tuttavia, è anche possibile implementare le interfacce di estendibilità direttamente nel componente aggiuntivo VSTO.

 Per altre informazioni sulle classi e le finestre di progettazione Visual Studio per queste [](../vsto/ribbon-designer.md)funzionalità, vedere Riquadri attività [personalizzati,](../vsto/custom-task-panes.md)Finestra di progettazione della barra multifunzione e Creare Outlook [modulo.](../vsto/creating-outlook-form-regions.md)

## <a name="extensibility-interfaces-you-can-implement-in-a-vsto-add-in"></a>Interfacce di estendibilità che è possibile implementare in un VSTO componente aggiuntivo
 La tabella seguente elenca le interfacce di estendibilità implementabili e le applicazioni che le supportano.

|Interfaccia|Descrizione|Applicazioni|
|---------------|-----------------|------------------|
|<xref:Microsoft.Office.Core.IRibbonExtensibility>|Implementare questa interfaccia per personalizzare l'interfaccia utente della barra multifunzione. **Nota:**  È possibile aggiungere un **elemento Barra multifunzione (XML)** a un progetto per generare un'implementazione predefinita nel VSTO <xref:Microsoft.Office.Core.IRibbonExtensibility> componente aggiuntivo. Per altre informazioni, vedere [Ribbon XML](../vsto/ribbon-xml.md).|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> InfoPath 2010<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Project<br /><br /> Visio<br /><br /> Word|
|<xref:Microsoft.Office.Core.ICustomTaskPaneConsumer>|Implementare questa interfaccia per creare un riquadro attività personalizzato.|Excel<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Word|
|<xref:Microsoft.Office.Interop.Outlook.FormRegionStartup>|Implementare questa interfaccia per creare un'area di modulo Outlook.|Outlook|

 Esistono diverse altre interfacce di estendibilità definite dalle applicazioni di Microsoft Office, ad esempio <xref:Microsoft.Office.Core.IBlogExtensibility>, <xref:Microsoft.Office.Core.EncryptionProvider>e <xref:Microsoft.Office.Core.SignatureProvider>. In Visual Studio l'implementazione di queste interfacce in un componente aggiuntivo VSTO creato usando i modelli di progetto di Office non è supportata.

## <a name="use-extensibility-interfaces"></a>Usare le interfacce di estendibilità
 Per personalizzare una funzionalità dell'interfaccia utente usando un'interfaccia di estendibilità, implementare l'interfaccia appropriata nel progetto del componente aggiuntivo VSTO. Eseguire quindi l'override del metodo <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> in modo da ottenere un'istanza della classe che implementi l'interfaccia.

 Per un'applicazione di esempio che illustra come implementare le interfacce , e in un componente aggiuntivo VSTO per Outlook, vedere l'esempio di gestione dell'interfaccia utente in Office di <xref:Microsoft.Office.Core.IRibbonExtensibility> <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> <xref:Microsoft.Office.Interop.Outlook.FormRegionStartup> sviluppo. [](../vsto/office-development-samples.md)

### <a name="example-of-implementing-an-extensibility-interface"></a>Esempio di implementazione di un'interfaccia di estendibilità
 Nell'esempio di codice riportato di seguito viene illustrata l'implementazione dell'interfaccia <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> per creare un riquadro attività personalizzato. Nell'esempio vengono definite due classi:

- La classe `TaskPaneHelper` implementa <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> per creare e visualizzare un riquadro attività personalizzato.

- La classe `TaskPaneUI` fornisce l'interfaccia utente del riquadro attività. Gli attributi della classe `TaskPaneUI` rendono la classe visibile a COM, permettendo alle applicazioni di Microsoft Office di individuare la classe. In questo esempio, <xref:System.Windows.Forms.UserControl>è un'interfaccia utente vuota, ma è possibile aggiungere i controlli modificando il codice.

  > [!NOTE]
  > Per esporre la classe `TaskPaneUI` a COM è necessario impostare anche la proprietà **Registra per interoperabilità COM** per il progetto.

  :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_SimpleExtensibilityInterface/ThisAddIn.vb" id="Snippet1":::
  :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_SimpleExtensibilityInterface/ThisAddIn.cs" id="Snippet1":::

  Per altre informazioni sull'implementazione di , vedere Creare riquadri attività personalizzati nel sistema Office <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> [2007](/previous-versions/office/developer/office-2007/aa338197(v=office.12)) nella documentazione Microsoft Office.

### <a name="example-of-overriding-the-requestservice-method"></a>Esempio di override del metodo RequestService
 L'esempio di codice seguente illustra come eseguire l'override del metodo <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> per ottenere un'istanza della classe `TaskPaneHelper` dall'esempio di codice precedente. Viene verificato il valore del parametro *serviceGuid* per determinare l'interfaccia necessaria e quindi viene restituito un oggetto che implementa l'interfaccia.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_SimpleExtensibilityInterface/ThisAddIn.vb" id="Snippet2":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_SimpleExtensibilityInterface/ThisAddIn.cs" id="Snippet2":::

## <a name="see-also"></a>Vedi anche
- [Office esempi di sviluppo e procedure dettagliate](../vsto/office-development-samples-and-walkthroughs.md)
- [Componenti aggiuntivi VSTO programma](../vsto/programming-vsto-add-ins.md)
- [Sviluppare Office soluzioni](../vsto/developing-office-solutions.md)
- [Chiamare il codice VSTO componenti aggiuntivi da altre Office soluzioni](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)
- [Procedura: Creare Office progetti in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Architettura dei componenti aggiuntivi VSTO](../vsto/architecture-of-vsto-add-ins.md)
