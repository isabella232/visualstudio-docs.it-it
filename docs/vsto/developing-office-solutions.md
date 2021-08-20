---
title: Sviluppare Office soluzioni
description: Informazioni su come progettare un progetto usando Office strumenti di sviluppo in Visual Studio. Informazioni anche su come iniziare a implementare il codice e l'interfaccia utente personalizzata.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, about developing solutions
- solutions [Office development in Visual Studio], developing
- Office solutions [Office development in Visual Studio], developing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: f9bc17fddd98132d95a994483afb3e3d3a6e6801
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122148272"
---
# <a name="develop-office-solutions"></a>Sviluppare Office soluzioni
  Dopo aver progettato un progetto usando gli strumenti di sviluppo di Office in Visual Studio e configurato i file di progetto, è possibile iniziare a concentrarsi sull'implementazione del codice e dell'interfaccia utente personalizzata.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="office-solutions-programming-model"></a>Office di programmazione delle soluzioni
 Il modello a oggetti Office espone una serie di oggetti programmabili. Ogni volta che è possibile programmare soluzioni Office usando codice gestito, è necessario scrivere codice che usa tipi negli assembly di interoperabilità primari di Office. Nelle soluzioni create mediante i modelli di progetto di Office in Visual Studio, è inoltre possibile scrivere il codice direttamente per le classi generate del progetto. Per altre informazioni, vedere [Scrivere codice in Office soluzioni](../vsto/writing-code-in-office-solutions.md).

## <a name="program-different-types-of-office-solutions"></a>Programmare diversi tipi di Office soluzioni
 Il tipo di soluzione che si sta creando determina le funzionalità che è possibile usare nel progetto. Ad esempio, è possibile aggiungere controlli Windows Form e controlli estesi di Office (denominato *controlli host*) alle personalizzazioni a livello di documento trascinando gli elementi dalla **casella degli strumenti** in Visual Studio in fase di progettazione. Tuttavia, se si sviluppa un componente aggiuntivo VSTO, è possibile aggiungere questi tipi di controlli solo a documenti in fase di esecuzione, mediante la scrittura di codice.

 Per altre informazioni sulle funzionalità specifiche di tipi diversi di soluzioni, vedere gli argomenti seguenti:

- [Programmi VSTO componenti aggiuntivi](../vsto/programming-vsto-add-ins.md).

- [Programmare personalizzazioni a livello di documento.](../vsto/programming-document-level-customizations.md)

- [Office personalizzazione dell'interfaccia utente](../vsto/office-ui-customization.md).

  Per informazioni generali su come pianificare le soluzioni Office e le procedure per la creazione di progetti, vedere [Progettare](../vsto/designing-and-creating-office-solutions.md)e creare Office soluzioni .

## <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Scrivere codice in Office soluzioni](../vsto/writing-code-in-office-solutions.md)|Vengono descritti diversi aspetti della scrittura del codice nelle soluzioni Office.|
|[Programmi VSTO componenti aggiuntivi](../vsto/programming-vsto-add-ins.md)|Offre una panoramica del modello di programmazione dei componenti aggiuntivi VSTO e delle attività di programmazione correlate.|
|[Programmare personalizzazioni a livello di documento](../vsto/programming-document-level-customizations.md)|Viene fornita una panoramica del modello di programmazione delle personalizzazioni a livello di documento e delle attività di programmazione correlate.|
|[Office Personalizzazione dell'interfaccia utente](../vsto/office-ui-customization.md)|Descrive i diversi modi in cui è possibile personalizzare l'interfaccia utente delle applicazioni di Office mediante componenti aggiuntivi VSTO e personalizzazioni a livello di documento.|
|[Dati nelle soluzioni Office dati](../vsto/data-in-office-solutions.md)|Vengono descritti i diversi modi in cui è possibile usare i dati nelle soluzioni Office come, ad esempio, l'associazione dei dati ai controlli e la memorizzazione nella cache di dati in personalizzazioni a livello di documento.|
|[Impatto del salvataggio automatico sulle Office soluzioni](./how-autosave-impacts-office-solutions.md)|Descrive le modifiche che potrebbe essere necessario apportare per Office quando è abilitato il salvataggio automatico.|
|[Risolvere i problemi Office soluzioni](../vsto/troubleshooting-office-solutions.md)|Vengono forniti suggerimenti per la risoluzione dei problemi comuni che possono verificarsi durante la creazione di soluzioni Office.|
|[Supporto del threading in Office](../vsto/threading-support-in-office.md)|Viene fornita una panoramica dell'utilizzo di più thread nelle soluzioni Office.|
|[Accessibilità nei Office progetto](../vsto/accessibility-in-office-projects.md)|Vengono descritte le funzionalità di accessibilità disponibili nelle soluzioni Office.|

## <a name="see-also"></a>Vedi anche
- [Procedura: Creare e modificare proprietà di documenti personalizzati](../vsto/how-to-create-and-modify-custom-document-properties.md)
- [Procedura: Leggere e scrivere nelle proprietà del documento](../vsto/how-to-read-from-and-write-to-document-properties.md)
- [Procedura: Impostare come destinazione l Office'interfaccia utente multilingue](../vsto/how-to-target-the-office-multilingual-user-interface.md)
- [Procedura dettagliata: Creare il primo VSTO per l'Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)
- [Procedura dettagliata: Creare la prima personalizzazione a livello di documento per Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)
- [Procedura dettagliata: Creare il primo VSTO aggiuntivo per Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)
- [Procedura dettagliata: Creare il primo VSTO aggiuntivo per PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)
- [Procedura dettagliata: Creare il primo VSTO per l'Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)
- [Procedura dettagliata: Creare il primo VSTO per Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)
- [Procedura dettagliata: Creare la prima personalizzazione a livello di documento per Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)
