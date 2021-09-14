---
title: Office dei modelli di progetto
description: Informazioni su come Microsoft Office strumenti di sviluppo in Visual Studio modelli di progetto per la creazione di diversi tipi di Office soluzioni.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- templates [Office development in Visual Studio], about project templates
- Excel Workbook project template
- Word Template project template
- Excel [Office development in Visual Studio], project templates
- Project [Office development in Visual Studio], project templates
- project templates [Office development in Visual Studio]
- project templates, Word
- InfoPath [Office development in Visual Studio], project templates
- Excel Template project template
- project templates, 2007 Microsoft Office system
- project templates, Excel
- PowerPoint [Office development in Visual Studio], project templates
- Word [Office development in Visual Studio], Word project templates
- Office projects [Office development in Visual Studio], templates
- Excel projects in Visual Studio
- Word Document project template
- Visio [Office development in Visual Studio], project templates
- Word projects in Visual Studio
- Outlook [Office development in Visual Studio], project templates
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 2436ccd10cc6ce8eb670be5e6cc537e0193171b9
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710603"
---
# <a name="office-project-templates-overview"></a>Office dei modelli di progetto
  Gli strumenti di sviluppo di applicazioni per Microsoft Office in Visual Studio includono modelli di progetto per la creazione dei seguenti tipi di soluzioni Office:

- [Personalizzazioni a livello di documento](#DocLevel)

- [Componenti aggiuntivi VSTO](#AppLevel)

  Per un confronto dettagliato di questi tipi di soluzioni Office, vedere panoramica dello sviluppo di Office [soluzioni &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

  I modelli di progetto di Office sono disponibili nella finestra di dialogo **Nuovo progetto** nel nodo **Office** dei nodi relativi ai linguaggi **Visual C#** e **Visual Basic** . Ogni modello genera un progetto con la configurazione appropriata per l'applicazione di destinazione, inclusi i riferimenti all'assembly e le impostazioni di debug.

  Ciascun progetto fornisce i file e il codice per la creazione di un tipo specifico di soluzione. Il codice generato per ogni progetto include i gestori degli eventi di avvio e di arresto. È possibile aggiungere codice a questi gestori eventi per inizializzare la soluzione al momento del caricamento ed eseguirne la pulizia quando viene scaricata. Per altre informazioni, vedere [progetti Office nell'ambiente Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md) ed Eventi in Office [progetti](../vsto/events-in-office-projects.md).

> [!NOTE]
> Gli strumenti di sviluppo di applicazioni per Office sono inclusi in alcune edizioni di Visual Studio. Per altre informazioni, vedere [Configurare un computer per sviluppare Office soluzioni](../vsto/configuring-a-computer-to-develop-office-solutions.md).

## <a name="document-level-customizations"></a><a name="DocLevel"></a> Personalizzazioni a livello di documento
 Il nodo **Office** nella finestra di dialogo **Nuovo progetto** fornisce i modelli di progetto riportati di seguito per cominciare a creare personalizzazioni a livello di documento per Word ed Excel.

- **Documento VSTO di Word 2013 e 2016**

- **Modello VSTO di Word 2013 e 2016**

- **Cartella di lavoro VSTO di Excel 2013 e 2016**

- **Modello VSTO di Excel 2013 e 2016**

- **Documento VSTO di Word 2010**

- **Modello VSTO di Word 2010**

- **Cartella di lavoro VSTO di Excel 2010**

- **Modello VSTO di Excel 2010**

  I modelli di progetto relativi al documento di Word e alla cartella di lavoro di Excel forniscono il codice per cominciare a creare una soluzione basata su un documento o su una cartella di lavoro specifica. In questi tipi di soluzioni, il codice viene eseguito solo quando il documento associato viene aperto in Word o in Excel.

  I modelli di progetto relativi al modello di Word e al modello di Excel si comportano in modo identico ai modelli di progetto relativi al documento di Word e alla cartella di lavoro di Excel. Tuttavia, i modelli di progetto relativi al modello di Word e al modello di Excel semplificano la creazione, da parte dell'utente, di nuove copie del documento o della cartella di lavoro locale del modello personalizzato nella soluzione. Le funzionalità nella soluzione sono disponibili dal nuovo documento che l'utente crea dal modello.

> [!NOTE]
> I modelli di Word che fanno riferimento alle estensioni di codice gestito non possono essere usati come componenti VSTO componenti aggiuntivi. L'assembly non viene chiamato se il modello viene caricato dalla directory Startup di Word. Per altre informazioni, vedere Limitazioni dei modelli globali [e Excel componenti aggiuntivi (file con estensione xla).](#Limitations)

 Per informazioni introduttive su questi tipi di progetto, vedere i seguenti argomenti:

- [Programmare personalizzazioni a livello di documento](../vsto/programming-document-level-customizations.md)

- [Soluzioni Word](../vsto/word-solutions.md)

- [Excel soluzioni](../vsto/excel-solutions.md)

- [Procedura dettagliata: Creare la prima personalizzazione a livello di documento per Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)

- [Procedura dettagliata: Creare la prima personalizzazione a livello di documento per Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)

## <a name="vsto-add-ins"></a><a name="AppLevel"></a>VSTO Componenti aggiuntivi
 Il nodo **Office/SharePoint** nella finestra di dialogo **Nuovo progetto** fornisce i modelli di progetto seguenti, con i quali è possibile cominciare a creare componenti aggiuntivi VSTO.

- **Componente aggiuntivo VSTO di Excel 2013 e 2016**

- **Componente aggiuntivo VSTO di InfoPath 2013**

- **Componente aggiuntivo VSTO di Outlook 2013 e 2016**

- **Componente aggiuntivo di PowerPoint 2013 e 2016**

- **Componente aggiuntivo di Project 2013 e 2016**

- **Componente aggiuntivo di Visio 2013 e 2016**

- **Componente aggiuntivo di Word 2013 e 2016**

- **Componente aggiuntivo per Excel 2010**

- **Componente aggiuntivo per InfoPath 2010**

- **Componente aggiuntivo per Outlook 2010**

- **Componente aggiuntivo per PowerPoint 2010**

- **Componente aggiuntivo per Project 2010**

- **Componente aggiuntivo per Visio 2010**

- **Componente aggiuntivo per Word 2010**

  Quando si crea un progetto basato su uno di questi modelli di progetto, il codice nella soluzione viene eseguito all'avvio dell'applicazione associata. A differenza dei progetti a livello di documento, il codice non è associato a un singolo documento.

  Per altre informazioni sulle attività iniziali relative a questi tipi di progetti, vedere gli argomenti seguenti:

- [Introduzione alla programmazione VSTO componenti aggiuntivi](../vsto/getting-started-programming-vsto-add-ins.md)

- [Componenti aggiuntivi VSTO programma](../vsto/programming-vsto-add-ins.md)

- [Procedura dettagliata: Creare il primo VSTO componente aggiuntivo per Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)

- [Procedura dettagliata: Creare il primo VSTO componente aggiuntivo per Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)

- [Procedura dettagliata: Creare il primo VSTO componente aggiuntivo per PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)

- [Procedura dettagliata: Creare il primo VSTO componente aggiuntivo per Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)

- [Procedura dettagliata: Creare il primo VSTO componente aggiuntivo per Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)

## <a name="document-vs-template-solutions"></a>Soluzioni per documenti e modelli
 Quando si progetta una soluzione per un documento di Word o una cartella di lavoro di Excel, è necessario determinare il modo migliore per rendere tale documento disponibile agli utenti.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 In alcune situazioni, può essere conveniente distribuire una copia del documento a ciascun utente. In questo caso, creare la soluzione usando un progetto documento di Excel o Word.

 In altri casi è preferibile rendere il modello disponibile su un server, in modo che ciascun utente possa aprirlo e salvarne una copia locale come documento. In questo caso, creare la soluzione usando un progetto di modello di Excel o Word.

## <a name="comparison"></a>Confronto
 Le differenze tra documenti e modelli sono illustrate nella tabella seguente.

|Documenti|Modelli|
|---------------|---------------|
|I documenti possono essere aperti e modificati dagli utenti, a meno che non siano in sola lettura. Tutte le modifiche salvate vengono mantenute nell'originale.|Gli utenti possono aprire un modello e salvarne una copia locale per creare un nuovo documento. L'originale può essere modificato solo da utenti che dispongono di speciali autorizzazioni.|
|All'apertura del documento viene generato l'evento <xref:Microsoft.Office.Tools.Word.Document.Open> .|All'apertura del modello viene generato l'evento <xref:Microsoft.Office.Tools.Word.Document.New> .|

## <a name="limitations-of-global-templates-and-excel-add-ins-xla-files"></a><a name="Limitations"></a>Limitazioni dei modelli globali e Excel componenti aggiuntivi (file con estensione xla)
 I documenti, le cartelle di lavoro e i modelli potrebbero non funzionare correttamente come modelli globali o come componenti aggiuntivi VSTO di Excel (file xla).

## <a name="word-templates"></a>Modelli di Word
 Se un modello di Microsoft Office Word usa estensioni di codice gestito, l'assembly del progetto non viene chiamato se il modello è associato come modello globale o se viene caricato dalla directory di avvio di Word. Inoltre il documento non riconosce il formato di un modello che fa parte di una soluzione Office.

## <a name="excel-add-ins-xla-files"></a>Excel Componenti aggiuntivi (file con estensione xla)
 Non è disponibile Office progetto per la creazione di un Excel VSTO componente aggiuntivo (file *con estensione xla).* È possibile salvare una cartella di lavoro come file xla, anche se questa operazione non è supportata né consigliata. Se si salva una cartella di lavoro con estensioni di codice gestito come file Microsoft Office Excel Add-In  **\* (xla),** è possibile selezionarla nella finestra di dialogo Componenti aggiuntivi da applicare a un'altra cartella di lavoro. In alcuni casi, il codice verrà eseguito nella cartella di lavoro di destinazione dopo l'applicazione del componente aggiuntivo VSTO, ma tale uso della soluzione Office non è supportato.

## <a name="see-also"></a>Vedi anche
- [Progettare e creare Office personalizzate](../vsto/designing-and-creating-office-solutions.md)
- [Sviluppare Office soluzioni](../vsto/developing-office-solutions.md)
- [Procedura: Creare Office progetti in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Introduzione alla programmazione delle personalizzazioni a livello di documento per Excel](../vsto/getting-started-programming-document-level-customizations-for-excel.md)
- [Introduzione alla programmazione delle personalizzazioni a livello di documento per Word](../vsto/getting-started-programming-document-level-customizations-for-word.md)
- [Introduzione alla programmazione VSTO componenti aggiuntivi](../vsto/getting-started-programming-vsto-add-ins.md)
