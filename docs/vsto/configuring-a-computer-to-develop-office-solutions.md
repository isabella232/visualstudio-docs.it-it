---
title: Configurare un computer per lo sviluppo Office soluzioni
description: Informazioni su come installare una versione supportata di Visual Studio, .NET Framework e Microsoft Office in modo da poter creare componenti aggiuntivi e personalizzazioni di VSTO per Microsoft Office.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, installing tools
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 7c74dca2c88538ddb0ddb17938ca50f3ab831276
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122047114"
---
# <a name="configure-a-computer-to-develop-office-solutions"></a>Configurare un computer per lo sviluppo Office soluzioni

Per creare componenti aggiuntivi VSTO e personalizzazioni per Microsoft Office, installare una versione supportata di Visual Studio, .NET Framework e Microsoft Office.

|Software|Versioni supportate|
|--------------|------------------------|
|Visual Studio 2017| Qualsiasi edizione con il carico **Office/SharePoint di sviluppo.**|
|.NET Framework|- Il .NET Framework 4 o versione successiva.|
|Microsoft Office|<ul><li>Qualsiasi edizione suite di Office incluse Microsoft 365 per le aziende.</li><li>Qualsiasi applicazione autonoma tra le seguenti:<br /><br /> <ul><li>Excel</li><li>InfoPath (solo Office 2013 e Office 2010)</li><li>Outlook</li><li>PowerPoint</li><li>Project</li><li>Visio</li><li>Word</li></ul></li></ul><br /> Visual Basic, Applications Edition (VBA) deve essere installato unitamente a Office. **Importante:** Le versioni click-to-run di Office 2010 non sono supportate.|

Per informazioni dettagliate sulla procedura di installazione, [vedere Procedura: Configurare un computer per lo sviluppo Office soluzioni](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md).

## <a name="if-project-templates-dont-appear-or-they-dont-work-in-visual-studio"></a>Se i modelli di progetto non vengono visualizzati o non funzionano in Visual Studio

Se si installa una versione supportata di Visual Studio, .NET Framework e Microsoft Office, ma i modelli di progetto Office non vengono visualizzati nella finestra di dialogo Visual Studio Nuovo **Project** o viene visualizzato un errore quando si tenta di usarne una, verificare quanto segue:

- Assicurarsi che nel computer siano installati gli strumenti di sviluppo di Microsoft Office.

     Office strumenti di sviluppo sono un componente facoltativo Visual Studio, ma vengono installati automaticamente insieme Visual Studio. Se si personalizza l'installazione di Visual Studio specificando i componenti da installare, selezionare **Microsoft Office Developer Tools** durante l'installazione per installare gli strumenti.

     Per assicurarsi che questi strumenti siano installati, avviare il Visual Studio programma di installazione e scegliere il **pulsante** Modifica. Selezionare la casella di controllo **Microsoft Office Developer Tools** , quindi scegliere il pulsante **Aggiorna** .

- Assicurarsi che non sia in esecuzione una versione di Office che è stata recapitata da A click-to-run. Vedere [Procedura: Verificare se Outlook è un'applicazione a](/previous-versions/office/developer/office-2010/ff864733(v=office.14))esecuzione a clic in un computer.

- Assicurarsi di eseguire solo una versione di Microsoft Office.

Se continuano a verificarsi problemi, vedere [Supporto aggiuntivo per gli errori in Office soluzioni](../vsto/additional-support-for-errors-in-office-solutions.md).

## <a name="see-also"></a>Vedi anche
- [Introduzione allo &#40;Office sviluppo in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Procedura: Configurare un computer per sviluppare Office soluzioni](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)
- [Procedura: Installare il runtime Visual Studio Tools per Office ridistribuibile](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)
- [Procedura: Installare Office assembly di interoperabilità primari](../vsto/how-to-install-office-primary-interop-assemblies.md)
- [Funzionalità disponibili in base Office'applicazione e al tipo di progetto](../vsto/features-available-by-office-application-and-project-type.md)