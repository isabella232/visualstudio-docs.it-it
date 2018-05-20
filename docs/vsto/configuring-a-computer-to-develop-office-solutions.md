---
title: Configurare un computer per sviluppare soluzioni Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, installing tools
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 58458b51115834b5b94e858676ee8039d5894c70
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="configure-a-computer-to-develop-office-solutions"></a>Configurare un computer per sviluppare soluzioni Office

Per creare componenti aggiuntivi VSTO e personalizzazioni per Microsoft Office, installare una versione supportata di Visual Studio, .NET Framework e Microsoft Office.

|Software|Versioni supportate|
|--------------|------------------------|
|Visual Studio 2017| Qualsiasi edizione con il **sviluppo per Office/SharePoint** carico di lavoro.|
|.NET Framework|-.NET Framework 4 o versione successivo.|
|Microsoft Office|<ul><li>Qualsiasi edizione di Office incluso Office Professional Plus per Office 365.</li><li>Qualsiasi applicazione autonoma tra le seguenti:<br /><br /> <ul><li>Excel</li><li>InfoPath (solo Office 2013 e Office 2010)</li><li>Outlook</li><li>PowerPoint</li><li>Progetto</li><li>Visio</li><li>Word</li></ul></li></ul><br /> Visual Basic, Applications Edition (VBA) deve essere installato unitamente a Office. **Importante:** non sono supportate le versioni a portata di clic delle applicazioni di Office 2010.|

Per i passaggi di installazione dettagliate, vedere [procedura: configurare un computer per sviluppare soluzioni Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md).

## <a name="if-project-templates-dont-appear-or-they-dont-work-in-visual-studio"></a>Se non vengono visualizzati i modelli di progetto o non funzionano in Visual Studio

Se si installa una versione supportata di Visual Studio, .NET Framework e Microsoft Office, ma i modelli di progetto Office non vengono visualizzati in Visual Studio **nuovo progetto** la finestra di dialogo oppure viene visualizzato un errore quando si tenta di utilizzare uno, Verificare quanto segue:

- Assicurarsi che nel computer siano installati gli strumenti di sviluppo di Microsoft Office.

     Gli strumenti di sviluppo di Office sono un componente facoltativo di Visual Studio, ma in genere vengono installati automaticamente insieme a Visual Studio. Se si personalizza l'installazione di Visual Studio specificando i componenti da installare, selezionare **Microsoft Office Developer Tools** durante l'installazione per installare gli strumenti.

     Per assicurarsi che questi strumenti siano installati, avviare il programma di installazione di Visual Studio e scegliere il **modifica** pulsante. Selezionare la casella di controllo **Microsoft Office Developer Tools** , quindi scegliere il pulsante **Aggiorna** .

- Assicurarsi che non in esecuzione una versione di Office che è stato recapitato da a portata di clic. Vedere [procedura: verificare se Outlook è un'applicazione a portata di clic in un computer](http://msdn.microsoft.com/library/office/ff864733(v=office.14).aspx).

- Verificare che sia in esecuzione solo una versione di Microsoft Office.

Se si continua a riscontrare problemi, vedere [supporto aggiuntivo per gli errori nelle soluzioni Office](../vsto/additional-support-for-errors-in-office-solutions.md).

## <a name="see-also"></a>Vedere anche

[Iniziare a &#40;sviluppo per Office in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)  
[Procedura: configurare un computer per sviluppare soluzioni Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)  
[Procedura: installare Visual Studio Tools per Office runtime ridistribuibile](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)  
[Procedura: assembly di interoperabilità primari di installazione di Office](../vsto/how-to-install-office-primary-interop-assemblies.md)  
[Funzionalità disponibili in base al tipo di progetto e applicazioni di Office](../vsto/features-available-by-office-application-and-project-type.md)
