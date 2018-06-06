---
title: Trust di soluzioni Office mediante gli elenchi di inclusione
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio]
- inclusion lists [Office development in Visual Studio], about inclusion lists
- security [Office development in Visual Studio], inclusion lists
- inclusion lists [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6fb44e7927136ba02d04f4b57f38ae52cc76c9fd
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767884"
---
# <a name="trust-office-solutions-by-using-inclusion-lists"></a>Trust di soluzioni Office mediante gli elenchi di inclusione
  Gli elenchi di inclusione consentono agli utenti di concedere l'attendibilità alle soluzioni Office firmate con un certificato che identifica l'editore. Gli elenchi di inclusione sono specifici dell'utente e possono essere usati per le personalizzazioni a livello di documento e per i componenti aggiuntivi VSTO.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Quando un utente avvia una soluzione Microsoft Office a cui non è stata concessa l'attendibilità per tale utente, verrà richiesto all'utente di prendere una decisione di sicurezza con una richiesta di attendibilità [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Se l'utente decide di concedere l'attendibilità alla soluzione, viene eseguita la personalizzazione e l'utente non riceverà più richieste successivamente.  
  
## <a name="inclusion-list-and-windows-installer"></a>Elenco di inclusione e Windows Installer  
 L'installazione di soluzioni Office nella directory Programmi con Windows Installer richiede diritti di amministratore. Per le soluzioni Office nella directory Programmi, Visual Studio Tools per Office runtime non controlla più l'elenco di inclusione perché alle soluzioni Office sono già state concesse le autorizzazioni FullTrust.  
  
## <a name="clickonce-trust-prompt"></a>Richiesta di attendibilità di ClickOnce  
 Con l'implementazione di [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] per le soluzioni Office, gli amministratori possono configurare il livello di richiesta di attendibilità. In particolare, è possibile abilitare o disabilitare la funzionalità di richiesta di attendibilità oppure richiedere un certificato attendibile. Questa configurazione viene eseguita usando una chiave del Registro di sistema che controlla l'accesso all'elenco di inclusione.  
  
 Se la funzionalità di richiesta di attendibilità è disabilitata, il sistema consente di installare solo le soluzioni che dispongono di un certificato attendibile e noto. Se il livello di richiesta di attendibilità prevede la richiesta di un certificato Authenticode, la soluzione deve essere firmata con un certificato fornito da un'autorità nota, non necessariamente collegato con una catena di trust a un'autorità radice attendibile (cioè un certificato attendibile). Se la funzionalità di richiesta di attendibilità è attiva, la soluzione può essere firmata con un certificato con un'identità sconosciuta. In questo scenario, la decisione sull'attendibilità viene presa dall'utente finale e per installare una soluzione è sufficiente un certificato temporaneo.  
  
 Per altre informazioni, vedere [procedura: configurare la protezione di elenco di inclusione](../vsto/how-to-configure-inclusion-list-security.md) e la tabella 2, intitolata chiedere conferma livello del Registro di sistema Key Value Launch Effects, in [editori attendibili ClickOnce configurare](http://go.microsoft.com/fwlink/?LinkId=94774).  
  
## <a name="structure-of-the-inclusion-list"></a>Struttura dell'elenco di inclusione  
 Una voce valida di un elenco di inclusione presenta due parti: un percorso al manifesto della distribuzione e la chiave pubblica usata per firmare la soluzione. Le soluzioni che vengono aggiunte all'elenco di inclusione vengono considerate attendibili. Quando la soluzione Office viene eseguita, l'applicazione di Office confronta la chiave pubblica contenuta nell'elenco di inclusione con la chiave di firma contenuta nel manifesto della distribuzione allo scopo di verificare se la soluzione in esecuzione corrisponde alla versione originale ritenuta attendibile.  
  
## <a name="see-also"></a>Vedere anche  
 [Concedere l'attendibilità alle soluzioni Office](../vsto/granting-trust-to-office-solutions.md)   
 [Proteggere le soluzioni Office](../vsto/securing-office-solutions.md)  
  
  