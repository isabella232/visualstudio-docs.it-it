---
title: Configurare un computer per sviluppare soluzioni Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, installing tools
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e78b66e1d7e9520f4aa54d8bcee54803659f9f6f
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "54863435"
---
# <a name="configure-a-computer-to-develop-office-solutions"></a>Configurare un computer per sviluppare soluzioni Office

Per creare componenti aggiuntivi VSTO e personalizzazioni per Microsoft Office, installare una versione supportata di Visual Studio, .NET Framework e Microsoft Office.

|Software|Versioni supportate|
|--------------|------------------------|
|Visual Studio 2017| Tutte le edizioni con il **sviluppo per Office/SharePoint** carico di lavoro.|
|.NET Framework|-.NET Framework 4 o versione successivo.|
|Microsoft Office|<ul><li>Qualsiasi edizione di Office incluso Office Professional Plus per Office 365.</li><li>Qualsiasi applicazione autonoma tra le seguenti:<br /><br /> <ul><li>Excel</li><li>InfoPath (solo Office 2013 e Office 2010)</li><li>Outlook</li><li>PowerPoint</li><li>Progetto</li><li>Visio</li><li>Word</li></ul></li></ul><br /> Visual Basic, Applications Edition (VBA) deve essere installato unitamente a Office. **Importante:** Le versioni A portata di clic delle applicazioni di Office 2010 non sono supportate.|

Per i passaggi di installazione dettagliate, vedere [come: Configurare un computer per sviluppare soluzioni Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md).

## <a name="if-project-templates-dont-appear-or-they-dont-work-in-visual-studio"></a>Se non vengono visualizzati i modelli di progetto o non funzionano in Visual Studio

Se si installa una versione supportata di Visual Studio, .NET Framework e Microsoft Office, ma i modelli di progetto di Office non vengono visualizzati in Visual Studio **nuovo progetto** nella finestra di dialogo oppure viene visualizzato un errore quando si tenta di usarne uno, Verificare quanto segue:

- Assicurarsi che nel computer siano installati gli strumenti di sviluppo di Microsoft Office.

     Office developer tools sono un componente facoltativo di Visual Studio, ma vengono installati automaticamente insieme a Visual Studio. Se si personalizza l'installazione di Visual Studio specificando i componenti da installare, selezionare **Microsoft Office Developer Tools** durante l'installazione per installare gli strumenti.

     Per assicurarsi che questi strumenti vengono installati, avviare il programma di installazione di Visual Studio e scegliere il **Modify** pulsante. Selezionare la casella di controllo **Microsoft Office Developer Tools** , quindi scegliere il pulsante **Aggiorna** .

- Assicurarsi che non si esegue una versione di Office a portata di a portata di clic. Vedere [Procedura: Verificare se Outlook è un'applicazione a portata di clic in un computer](/previous-versions/office/developer/office-2010/ff864733(v=office.14)).

- Assicurarsi che si esegue solo una versione di Microsoft Office.

Se si continua a verificarsi problemi, vedere [supporto aggiuntivo per gli errori nelle soluzioni Office](../vsto/additional-support-for-errors-in-office-solutions.md).

## <a name="see-also"></a>Vedere anche

[Iniziare a usare &#40;sviluppo per Office in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)  
[Procedura: Configurare un computer per sviluppare soluzioni Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)  
[Procedura: Installare Visual Studio Tools per Office runtime redistributable](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)  
[Procedura: Installare l'assembly di interoperabilità primari di Office](../vsto/how-to-install-office-primary-interop-assemblies.md)  
[Funzionalità disponibili in base al tipo di progetto e applicazioni di Office](../vsto/features-available-by-office-application-and-project-type.md)
