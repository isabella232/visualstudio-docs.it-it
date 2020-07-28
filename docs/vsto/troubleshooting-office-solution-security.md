---
title: Risolvere i problemi relativi alla sicurezza delle soluzioni Office
ms.date: 02/02/2017
ms.topic: troubleshooting
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], troubleshooting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8825f1f4393d93df6a621fd71b6782c6652a9c0c
ms.sourcegitcommit: 9a7fb8556a5f3dbb4459122fefc7e7a8dfda753a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234809"
---
# <a name="troubleshoot-office-solution-security"></a>Risolvere i problemi relativi alla sicurezza delle soluzioni Office
  Questo argomento contiene suggerimenti per la risoluzione di problemi comuni che possono verificarsi quando si lavora con la protezione delle soluzioni Office.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="trusted-solutions-cannot-be-installed-from-restricted-sites"></a>Non è possibile installare soluzioni attendibili da siti con restrizioni
 Gli utenti non possono installare una soluzione da un percorso Web se il sito Web è elencato nell'area siti con restrizioni di Internet Explorer. Questo vale anche se la soluzione è firmata con un certificato attendibile.

 L'URL del manifesto di distribuzione può essere categorizzato in una delle cinque zone seguenti:

- Risorse del computer

- Internet

- Intranet locale

- Siti attendibili

- Siti con restrizioni

  Se il percorso del manifesto di distribuzione è stato assegnato all'area siti con restrizioni, non [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] installa la soluzione. Se il percorso è noto e può essere considerato attendibile, l'utente può rimuovere il percorso dall'area siti con restrizioni e installare la soluzione. Per informazioni su come gestire le zone, vedere [configurazione di editori attendibili ClickOnce](/previous-versions/dotnet/articles/ms996418(v=msdn.10)).

## <a name="solutions-cannot-be-installed-from-network-file-shares-or-web-locations-when-internet-explorer-enhanced-security-configuration-or-internet-explorer-7-is-installed"></a>Non è possibile installare le soluzioni da condivisioni file di rete o da percorsi Web quando è installata la configurazione sicurezza avanzata di Internet Explorer o Internet Explorer 7
 Sicurezza avanzata di Internet Explorer (IEESC) in Windows Server 2003 e versioni successive e Internet Explorer 7 e versioni successive, limita in modo significativo la possibilità degli utenti di esplorare Internet. Quando gli utenti tentano di installare soluzioni Office da una condivisione file di rete o da un percorso Web, potrebbero ricevere il messaggio di errore seguente: "la funzionalità personalizzata in questa applicazione non funzionerà perché il certificato usato per firmare il manifesto di distribuzione per *SolutionName* non è attendibile. Per ulteriore assistenza, contattare l'amministratore. "

 Con IEESC e Internet Explorer 7 e versioni successive, se l'URL del manifesto di distribuzione è categorizzato nell'area Internet, è necessario che il manifesto disponga di un certificato di un autore attendibile oppure che la soluzione non sia installata. Senza IEESC, il comportamento predefinito è quello di richiedere all'utente finale di prendere una decisione di attendibilità.

 Per gestire l'effetto di IEESC e Internet Explorer 7 e versioni successive, identificare i siti Web e i percorsi UNC (Universal Naming Convention) attendibili e aggiungerli a una delle aree di sicurezza attendibili (Intranet locale o siti attendibili). Per informazioni su come gestire le zone, vedere [configurare gli autori attendibili ClickOnce](/previous-versions/dotnet/articles/ms996418(v=msdn.10)).

## <a name="see-also"></a>Vedere anche
- [Soluzioni Office sicure](../vsto/securing-office-solutions.md)
- [Risoluzione dei problemi di Visual Studio](/troubleshoot/visualstudio/welcome-visual-studio/)
