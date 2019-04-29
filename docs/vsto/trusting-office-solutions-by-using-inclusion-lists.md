---
title: Trust di soluzioni Office mediante elenchi di inclusione
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio]
- inclusion lists [Office development in Visual Studio], about inclusion lists
- security [Office development in Visual Studio], inclusion lists
- inclusion lists [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 34b4ed5dbc0996239e73db38f1d6bea9e43d6de4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62978302"
---
# <a name="trust-office-solutions-by-using-inclusion-lists"></a>Trust di soluzioni Office mediante elenchi di inclusione
  Gli elenchi di inclusione consentono agli utenti di concedere l'attendibilità alle soluzioni Office firmate con un certificato che identifica l'editore. Gli elenchi di inclusione sono specifici dell'utente e possono essere usati per le personalizzazioni a livello di documento e per i componenti aggiuntivi VSTO.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Quando un utente avvia una soluzione Microsoft Office a cui non è stata concessa l'attendibilità per tale utente, verrà richiesto all'utente di prendere una decisione di sicurezza con una richiesta di attendibilità [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Se l'utente decide di concedere l'attendibilità alla soluzione, viene eseguita la personalizzazione e l'utente non riceverà più richieste successivamente.

## <a name="inclusion-list-and-windows-installer"></a>Elenco di inclusione e Windows Installer
 Installazione di soluzioni Office nel *Program Files* directory mediante Windows Installer richiede diritti di amministratore. Per le soluzioni Office nella *Program Files* directory, Visual Studio Tools per Office runtime non verifica più nell'elenco di inclusione perché alle soluzioni Office sono già state concesse autorizzazioni FullTrust.

## <a name="clickonce-trust-prompt"></a>Richiesta di attendibilità ClickOnce
 Con l'implementazione di [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] per le soluzioni Office, gli amministratori possono configurare il livello di richiesta di attendibilità. In particolare, è possibile abilitare o disabilitare la funzionalità di richiesta di attendibilità oppure richiedere un certificato attendibile. Questa configurazione viene eseguita usando una chiave del Registro di sistema che controlla l'accesso all'elenco di inclusione.

 Se la funzionalità di richiesta di attendibilità è disabilitata, il sistema consente di installare solo le soluzioni che dispongono di un certificato attendibile e noto. Se il livello di richiesta di attendibilità prevede la richiesta di un certificato Authenticode, la soluzione deve essere firmata con un certificato fornito da un'autorità nota, non necessariamente collegato con una catena di trust a un'autorità radice attendibile (cioè un certificato attendibile). Se la funzionalità di richiesta di attendibilità è attiva, la soluzione può essere firmata con un certificato con un'identità sconosciuta. In questo scenario, la decisione sull'attendibilità viene presa dall'utente finale e per installare una soluzione è sufficiente un certificato temporaneo.

 Per altre informazioni, vedere [Procedura: Configurare la sicurezza di elenco di inclusione](../vsto/how-to-configure-inclusion-list-security.md) e la tabella 2, intitolata che richiede a livello del Registro di sistema Key Value Launch Effects, in [editori attendibili ClickOnce configurare](http://go.microsoft.com/fwlink/?LinkId=94774).

## <a name="structure-of-the-inclusion-list"></a>Struttura dell'elenco di inclusione
 Una voce valida di un elenco di inclusione presenta due parti: un percorso al manifesto della distribuzione e la chiave pubblica usata per firmare la soluzione. Le soluzioni che vengono aggiunte all'elenco di inclusione vengono considerate attendibili. Quando la soluzione Office viene eseguita, l'applicazione di Office confronta la chiave pubblica contenuta nell'elenco di inclusione con la chiave di firma contenuta nel manifesto della distribuzione allo scopo di verificare se la soluzione in esecuzione corrisponde alla versione originale ritenuta attendibile.

## <a name="see-also"></a>Vedere anche
- [Concedere l'attendibilità alle soluzioni Office](../vsto/granting-trust-to-office-solutions.md)
- [Proteggere le soluzioni Office](../vsto/securing-office-solutions.md)
