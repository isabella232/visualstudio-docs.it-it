---
title: Risolvere i problemi di sicurezza delle soluzioni Office
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 921bef3514b802672296dda6d680b665f1f42482
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62978315"
---
# <a name="troubleshoot-office-solution-security"></a>Risolvere i problemi di sicurezza delle soluzioni Office
  In questo argomento contiene suggerimenti per la risoluzione di problemi comuni che possono verificarsi quando si lavora con sicurezza delle soluzioni Office.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="trusted-solutions-cannot-be-installed-from-restricted-sites"></a>Soluzioni attendibili non possono essere installate da siti con restrizioni
 Se il sito Web è contenuto nell'area siti con restrizioni di Internet Explorer, gli utenti non è possibile installare una soluzione da un percorso web. Questo vale anche se la soluzione è firmata con un certificato attendibile.

 L'URL del manifesto della distribuzione può essere classificata in base a una delle cinque aree:

- Risorse del Computer

- Internet

- Intranet locale

- Siti attendibili

- Siti con restrizioni

  Se il percorso del manifesto della distribuzione è stato assegnato all'area siti con restrizioni, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] non installa la soluzione. Se il percorso è noto e può essere considerato attendibile, l'utente può rimuovere il percorso dall'area siti con restrizioni e installare la soluzione. Per informazioni su come gestire le zone, vedere [configurazione di editori attendibili ClickOnce](http://go.microsoft.com/fwlink/?LinkId=94774).

## <a name="solutions-cannot-be-installed-from-network-file-shares-or-web-locations-when-internet-explorer-enhanced-security-configuration-or-internet-explorer-7-is-installed"></a>Le soluzioni non possono essere installate da condivisioni file di rete o percorsi web quando si installa la funzionalità sicurezza avanzata di Internet Explorer o Internet Explorer 7
 Internet Explorer Enhanced Security Configuration (IEESC) in Windows Server 2003 e versioni successive e Internet Explorer 7 e versioni successive, consente di limitare in modo significativo la capacità degli utenti per accedere a Internet. Quando gli utenti tentano di installare soluzioni Office da un file di rete condividono o percorso web, che venga visualizzato il messaggio di errore seguente: "Funzionalità personalizzate di questa applicazione non funzionerà perché il certificato usato per firmare il manifesto di distribuzione per *SolutionName* non è attendibile. Contattare l'amministratore per ottenere assistenza."

 Con IEESC e Internet Explorer 7 e versioni successive, se l'URL del manifesto della distribuzione è stato categorizzato nell'area Internet, il manifesto deve avere un certificato da un autore attendibile o non è possibile installare la soluzione. Senza IEESC, il comportamento predefinito è per richiedere all'utente finale per prendere una decisione di attendibilità.

 Per gestire l'effetto di IEESC e Internet Explorer 7 e versioni successive, identificare i siti Web e percorsi UNC universal naming convention (UNC) che si considera attendibile e aggiungerli a una delle aree di sicurezza attendibile (intranet locale o siti attendibili). Per informazioni su come gestire le zone, vedere [editori attendibili ClickOnce configurare](http://go.microsoft.com/fwlink/?LinkId=94774).

## <a name="see-also"></a>Vedere anche
- [Proteggere le soluzioni Office](../vsto/securing-office-solutions.md)
