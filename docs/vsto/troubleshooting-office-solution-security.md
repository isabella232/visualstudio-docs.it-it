---
title: Risoluzione dei problemi di sicurezza delle soluzioni Office | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], troubleshooting
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 547ba6d1e58376c50d0e01ab8fd3d55f62d5a935
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/01/2018
ms.locfileid: "34693318"
---
# <a name="troubleshooting-office-solution-security"></a>Risoluzione dei problemi relativi alla sicurezza delle soluzioni Office
  In questo argomento contiene suggerimenti per la risoluzione dei problemi comuni che possono verificarsi quando si lavora con sicurezza delle soluzioni Office.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="trusted-solutions-cannot-be-installed-from-restricted-sites"></a>Trusted soluzioni non possono essere installate da siti con restrizioni  
 Gli utenti non è possibile installare una soluzione da un percorso web se il sito Web è presente nell'area siti con restrizioni di Internet Explorer. Questo vale anche se la soluzione è firmata con un certificato attendibile.  
  
 L'URL del manifesto di distribuzione può essere suddivise in una delle cinque aree:  
  
-   Risorse del Computer  
  
-   Internet  
  
-   Intranet locale  
  
-   Siti attendibili  
  
-   Siti con restrizioni  
  
 Se il percorso del manifesto della distribuzione è stato assegnato all'area siti con restrizioni, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] non installare la soluzione. Se il percorso è noto e può essere considerato attendibile, l'utente può rimuovere il percorso dall'area siti con restrizioni e installare la soluzione. Per informazioni su come gestire le zone, vedere [di editori attendibili ClickOnce configurazione](http://go.microsoft.com/fwlink/?LinkId=94774).  
  
## <a name="solutions-cannot-be-installed-from-network-file-shares-or-web-locations-when-internet-explorer-enhanced-security-configuration-or-internet-explorer-7-is-installed"></a>Soluzioni non possono essere installate da condivisioni File di rete o indirizzi di siti Web quando sicurezza avanzata di Internet Explorer o sia installato Internet Explorer 7  
 Internet Explorer Enhanced Security Configuration (IEESC) in Windows Server 2003 e versioni successive e Internet Explorer 7 e versioni successive, in modo significativo limita la capacità degli utenti per accedere a Internet. Quando gli utenti tentano di installare soluzioni Office da un percorso web o condivisione di rete di file, è possibile che venga visualizzato il seguente messaggio di errore: "la funzionalità personalizzata in questa applicazione non funzionerà perché il certificato utilizzato per firmare il manifesto di distribuzione per *SolutionName* non è attendibile. Contattare l'amministratore per ulteriore assistenza."  
  
 Con IEESC e Internet Explorer 7 e versioni successive, se l'URL del manifesto della distribuzione è stato categorizzato nell'area Internet, il manifesto deve essere un certificato da un autore attendibile o non è possibile installare la soluzione. Senza IEESC, il comportamento predefinito è per richiedere all'utente finale per prendere una decisione di attendibilità.  
  
 Gestire l'effetto di IEESC e Internet Explorer 7 e versioni successive, identificare i siti Web e i percorsi UNC universal naming convention (UNC) che si considera attendibile e li aggiunge a una delle aree di sicurezza con attendibilità (intranet locale o siti attendibili). Per informazioni su come gestire le zone, vedere [configurazione di editori attendibili ClickOnce](http://go.microsoft.com/fwlink/?LinkId=94774).  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza delle soluzioni Office](../vsto/securing-office-solutions.md)  
  
  