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
ms.openlocfilehash: 7a0304c217599e790b8cfa9e738245927336470e
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/25/2020
ms.locfileid: "88801841"
---
# <a name="configure-a-computer-to-develop-office-solutions"></a>Configurare un computer per sviluppare soluzioni Office

Per creare componenti aggiuntivi VSTO e personalizzazioni per Microsoft Office, installare una versione supportata di Visual Studio, .NET Framework e Microsoft Office.

|Software|Versioni supportate|
|--------------|------------------------|
|Visual Studio 2017| Qualsiasi edizione con il carico di lavoro di **sviluppo di Office/SharePoint** .|
|.NET Framework|-Il .NET Framework 4 o versione successiva.|
|Microsoft Office|<ul><li>Qualsiasi edizione di Office inclusa Microsoft 365 app per Enterprise.</li><li>Qualsiasi applicazione autonoma tra le seguenti:<br /><br /> <ul><li>Excel</li><li>InfoPath (solo Office 2013 e Office 2010)</li><li>Outlook</li><li>PowerPoint</li><li>Project</li><li>Visio</li><li>Word</li></ul></li></ul><br /> Visual Basic, Applications Edition (VBA) deve essere installato unitamente a Office. **Importante:** Le versioni a cui si fa clic per eseguire le applicazioni Office 2010 non sono supportate.|

Per informazioni dettagliate sulla procedura di installazione, vedere [procedura: configurare un computer per sviluppare soluzioni Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md).

## <a name="if-project-templates-dont-appear-or-they-dont-work-in-visual-studio"></a>Se i modelli di progetto non vengono visualizzati o non funzionano in Visual Studio

Se si installa una versione supportata di Visual Studio, il .NET Framework e Microsoft Office, ma i modelli di progetto di Office non vengono visualizzati nella finestra di dialogo **nuovo progetto** di Visual Studio oppure viene visualizzato un errore quando si tenta di utilizzarne uno, verificare quanto segue:

- Assicurarsi che nel computer siano installati gli strumenti di sviluppo di Microsoft Office.

     Gli strumenti di sviluppo di Office sono un componente facoltativo di Visual Studio, ma vengono installati automaticamente insieme a Visual Studio. Se si personalizza l'installazione di Visual Studio specificando i componenti da installare, selezionare **Microsoft Office Developer Tools** durante l'installazione per installare gli strumenti.

     Per assicurarsi che questi strumenti siano installati, avviare il programma di installazione di Visual Studio e scegliere il pulsante **modifica** . Selezionare la casella di controllo **Microsoft Office Developer Tools** , quindi scegliere il pulsante **Aggiorna** .

- Assicurarsi che non sia in esecuzione una versione di Office che è stata recapitata tramite clic per l'esecuzione. Vedere [procedura: verificare se Outlook è un'applicazione a cui è possibile fare clic in un computer](/previous-versions/office/developer/office-2010/ff864733(v=office.14)).

- Verificare che sia in esecuzione una sola versione di Microsoft Office.

Se continuano a verificarsi problemi, vedere [supporto aggiuntivo per gli errori nelle soluzioni Office](../vsto/additional-support-for-errors-in-office-solutions.md).

## <a name="see-also"></a>Vedere anche
- [Introduzione &#40;sviluppo per Office in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Procedura: configurare un computer per sviluppare soluzioni Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)
- [Procedura: installare la Strumenti di Visual Studio per Office Runtime Redistributable](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)
- [Procedura: installare assembly di interoperabilità primari di Office](../vsto/how-to-install-office-primary-interop-assemblies.md)
- [Funzionalità disponibili in base ai tipi di progetto e applicazioni di Office](../vsto/features-available-by-office-application-and-project-type.md)