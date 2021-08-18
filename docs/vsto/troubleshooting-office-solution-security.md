---
title: Risolvere i Office della soluzione
description: Suggerimenti per la risoluzione di problemi comuni che possono verificarsi quando si lavora con la protezione Microsoft Office soluzioni.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: troubleshooting
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], troubleshooting
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: b23dcf46853c2e8a236c4bf2db21911f3ad7708d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122032160"
---
# <a name="troubleshoot-office-solution-security"></a>Risolvere i Office della soluzione
  Questo argomento contiene suggerimenti per la risoluzione di problemi comuni che possono verificarsi quando si lavora con la protezione Office soluzioni.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="trusted-solutions-cannot-be-installed-from-restricted-sites"></a>Non è possibile installare soluzioni attendibili da siti con restrizioni
 Gli utenti non possono installare una soluzione da un percorso Web se il sito Web è elencato nell'Internet Explorer siti con restrizioni. Questo vale anche se la soluzione è firmata con un certificato attendibile.

 L'URL del manifesto della distribuzione può essere categorizzato in una delle cinque zone seguenti:

- Risorse del computer

- Internet

- Intranet locale

- Siti attendibili

- Siti con restrizioni

  Se il percorso del manifesto della distribuzione è stato assegnato all'area siti con restrizioni, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] non installa la soluzione. Se il percorso è noto e può essere considerato attendibile, l'utente può rimuovere il percorso dall'area siti con restrizioni e installare la soluzione. Per informazioni su come gestire le zone, vedere [Configuring ClickOnce Trusted Publishers](/previous-versions/dotnet/articles/ms996418(v=msdn.10)).

## <a name="solutions-cannot-be-installed-from-network-file-shares-or-web-locations-when-internet-explorer-enhanced-security-configuration-or-internet-explorer-7-is-installed"></a>Non è possibile installare soluzioni da condivisioni file di rete o percorsi Web quando Internet Explorer sicurezza avanzata o Internet Explorer 7
 Internet Explorer sicurezza avanzata (IEESC) in Windows Server 2003 e versioni successive e Internet Explorer 7 e versioni successive, limita significativamente la capacità degli utenti di esplorare Internet. Quando gli utenti tentano di installare soluzioni Office da una condivisione file di rete o da un percorso Web, è possibile che venga visualizzato il messaggio di errore seguente: "La funzionalità personalizzata in questa applicazione non funzionerà perché il certificato usato per firmare il manifesto della distribuzione per *SolutionName* non è attendibile. Contattare l'amministratore per ulteriore assistenza."

 Con IEESC e Internet Explorer 7 e versioni successive, se l'URL del manifesto della distribuzione è stato categorizzato nell'area Internet, il manifesto deve avere un certificato di un autore attendibile o la soluzione non può essere installata. Senza IEESC, il comportamento predefinito è richiedere all'utente finale di prendere una decisione di attendibilità.

 Per gestire l'effetto di IEESC e Internet Explorer 7 e versioni successive, identificare i siti Web e i percorsi UNC (Universal Naming Convention) considerati attendibili e aggiungerli a una delle aree di sicurezza attendibili (Intranet locale o Siti attendibili). Per informazioni su come gestire le zone, vedere [Configurare ClickOnce autori attendibili.](/previous-versions/dotnet/articles/ms996418(v=msdn.10))

## <a name="see-also"></a>Vedi anche
- [Soluzioni Office sicurezza](../vsto/securing-office-solutions.md)
- [Visual Studio risoluzione dei problemi](/troubleshoot/visualstudio/welcome-visual-studio/)
