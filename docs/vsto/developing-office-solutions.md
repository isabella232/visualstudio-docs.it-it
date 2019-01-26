---
title: Sviluppare soluzioni Office
ms.date: 02/02/2017
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1aa7be95b0812b27c302500bd166abcb00c7089d
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "54874525"
---
# <a name="develop-office-solutions"></a>Sviluppare soluzioni Office
  Dopo aver progettato un progetto usando gli strumenti di sviluppo di Office in Visual Studio e configurato i file di progetto, è possibile iniziare a concentrarsi sull'implementazione del codice e dell'interfaccia utente personalizzata.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
> [!NOTE]  
>  Se ti interessa sviluppare soluzioni che estendono l'esperienza di Office attraverso [piattaforme multiple](https://dev.office.com/add-in-availability)? Consultare la nuova [modello di componenti aggiuntivi di Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Componenti aggiuntivi di Office con footprint ridotto rispetto alle soluzioni e componenti aggiuntivi VSTO e si possono essere compilate usando praticamente qualsiasi tecnologia, ad esempio HTML5, JavaScript, CSS3 e XML di programmazione web.  
  
## <a name="office-solutions-programming-model"></a>Modello di programmazione di soluzioni Office  
 Il modello a oggetti Office espone una serie di oggetti programmabili. Ogni volta che è possibile programmare soluzioni Office usando codice gestito, è necessario scrivere codice che usa tipi negli assembly di interoperabilità primari di Office. Nelle soluzioni create mediante i modelli di progetto di Office in Visual Studio, è inoltre possibile scrivere il codice direttamente per le classi generate del progetto. Per altre informazioni, vedere [scrivere codice nelle soluzioni Office](../vsto/writing-code-in-office-solutions.md).  
  
## <a name="program-different-types-of-office-solutions"></a>Tipi diversi di programma di soluzioni Office  
 Il tipo di soluzione che si sta creando determina le funzionalità che è possibile usare nel progetto. Ad esempio, è possibile aggiungere controlli Windows Form e controlli estesi di Office (denominato *controlli host*) alle personalizzazioni a livello di documento trascinando gli elementi dalla **casella degli strumenti** in Visual Studio in fase di progettazione. Tuttavia, se si sviluppa un componente aggiuntivo VSTO, è possibile aggiungere questi tipi di controlli solo a documenti in fase di esecuzione, mediante la scrittura di codice.  
  
 Per altre informazioni sulle funzionalità specifiche di tipi diversi di soluzioni, vedere gli argomenti seguenti:  
  
- [Programmazione di componenti aggiuntivi VSTO](../vsto/programming-vsto-add-ins.md).  
  
- [Programmazione delle personalizzazioni a livello di documento](../vsto/programming-document-level-customizations.md).  
  
- [Personalizzazione dell'interfaccia utente Office](../vsto/office-ui-customization.md).  
  
  Per informazioni complementari che consentono di pianificare le procedure per creare progetti e soluzioni Office, vedere [progettazione e creazione di soluzioni Office](../vsto/designing-and-creating-office-solutions.md).  
  
## <a name="related-topics"></a>Argomenti correlati  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Scrivere il codice nelle soluzioni Office](../vsto/writing-code-in-office-solutions.md)|Vengono descritti diversi aspetti della scrittura del codice nelle soluzioni Office.|  
|[Programmazione di componenti aggiuntivi VSTO](../vsto/programming-vsto-add-ins.md)|Offre una panoramica del modello di programmazione dei componenti aggiuntivi VSTO e delle attività di programmazione correlate.|  
|[Programmazione delle personalizzazioni a livello di documento](../vsto/programming-document-level-customizations.md)|Viene fornita una panoramica del modello di programmazione delle personalizzazioni a livello di documento e delle attività di programmazione correlate.|  
|[Personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md)|Descrive i diversi modi in cui è possibile personalizzare l'interfaccia utente delle applicazioni di Office mediante componenti aggiuntivi VSTO e personalizzazioni a livello di documento.|  
|[Dati nelle soluzioni Office](../vsto/data-in-office-solutions.md)|Vengono descritti i diversi modi in cui è possibile usare i dati nelle soluzioni Office come, ad esempio, l'associazione dei dati ai controlli e la memorizzazione nella cache di dati in personalizzazioni a livello di documento.|  
|[Modalità salvataggio automatico influisce sulle soluzioni Office](./how-autosave-impacts-office-solutions.md)|Descrive le regolazioni che potrebbe essere necessario apportare alle soluzioni Office quando è abilitato.|
|[Risolvere i problemi di soluzioni Office](../vsto/troubleshooting-office-solutions.md)|Vengono forniti suggerimenti per la risoluzione dei problemi comuni che possono verificarsi durante la creazione di soluzioni Office.|  
|[Supporto del threading in Office](../vsto/threading-support-in-office.md)|Viene fornita una panoramica dell'utilizzo di più thread nelle soluzioni Office.|  
|[Accessibilità nei progetti di Office](../vsto/accessibility-in-office-projects.md)|Vengono descritte le funzionalità di accessibilità disponibili nelle soluzioni Office.|  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Creare e modificare le proprietà personalizzate dei documenti](../vsto/how-to-create-and-modify-custom-document-properties.md)   
 [Procedura: Leggere e scrivere le proprietà del documento](../vsto/how-to-read-from-and-write-to-document-properties.md)   
 [Procedura: Destinazione dell'interfaccia utente multilingue di Office](../vsto/how-to-target-the-office-multilingual-user-interface.md)   
 [Procedura dettagliata: Creare un componente aggiuntivo di VSTO per Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)   
 [Procedura dettagliata: Creare una personalizzazione a livello di documento per Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)   
 [Procedura dettagliata: Creare il primo aggiuntivo VSTO per Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)   
 [Procedura dettagliata: Creare un componente aggiuntivo di VSTO per PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)   
 [Procedura dettagliata: Creare il primo aggiuntivo VSTO per Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)   
 [Procedura dettagliata: Creare un componente aggiuntivo di VSTO per Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)   
 [Procedura dettagliata: Creare una personalizzazione a livello di documento per Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)  
