---
title: Soluzioni Office attendibilità tramite elenchi di inclusione
description: Informazioni su come gli elenchi di inclusione consentono agli utenti di concedere l'attendibilità Office soluzioni firmate con un certificato che identifica l'editore.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: c651a3659d4165d359453df5f64080a2d57b229f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122046256"
---
# <a name="trust-office-solutions-by-using-inclusion-lists"></a>Soluzioni Office attendibilità tramite elenchi di inclusione
  Gli elenchi di inclusione consentono agli utenti di concedere l'attendibilità alle soluzioni Office firmate con un certificato che identifica l'editore. Gli elenchi di inclusione sono specifici dell'utente e possono essere usati per le personalizzazioni a livello di documento e per i componenti aggiuntivi VSTO.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Quando un utente avvia una soluzione Microsoft Office a cui non è stata concessa l'attendibilità per tale utente, verrà richiesto all'utente di prendere una decisione di sicurezza con una richiesta di attendibilità [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Se l'utente decide di concedere l'attendibilità alla soluzione, viene eseguita la personalizzazione e l'utente non riceverà più richieste successivamente.

## <a name="inclusion-list-and-windows-installer"></a>Elenco di inclusione e programma Windows di installazione
 L'installazione Office soluzioni nella directory *Programmi* usando il programma di Windows di installazione richiede diritti di amministratore. Per Office soluzioni nella *directory* Programmi, il runtime di Visual Studio Tools per Office non controlla più l'elenco di inclusione perché alle soluzioni Office è già stata concessa l'autorizzazione FullTrust.

## <a name="clickonce-trust-prompt"></a>Richiesta di attendibilità ClickOnce
 Con l'implementazione di [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] per le soluzioni Office, gli amministratori possono configurare il livello di richiesta di attendibilità. In particolare, è possibile abilitare o disabilitare la funzionalità di richiesta di attendibilità oppure richiedere un certificato attendibile. Questa configurazione viene eseguita usando una chiave del Registro di sistema che controlla l'accesso all'elenco di inclusione.

 Se la funzionalità di richiesta di attendibilità è disabilitata, il sistema consente di installare solo le soluzioni che dispongono di un certificato attendibile e noto. Se il livello di richiesta di attendibilità prevede la richiesta di un certificato Authenticode, la soluzione deve essere firmata con un certificato fornito da un'autorità nota, non necessariamente collegato con una catena di trust a un'autorità radice attendibile (cioè un certificato attendibile). Se la funzionalità di richiesta di attendibilità è attiva, la soluzione può essere firmata con un certificato con un'identità sconosciuta. In questo scenario, la decisione sull'attendibilità viene presa dall'utente finale e per installare una soluzione è sufficiente un certificato temporaneo.

 Per altre informazioni, vedere [Procedura:](../vsto/how-to-configure-inclusion-list-security.md) Configurare la sicurezza dell'elenco di inclusione e Tabella 2, intitolata Prompting Level Registry Key Value Launch Effects,in [Configure ClickOnce trusted publishers](/previous-versions/dotnet/articles/ms996418(v=msdn.10)).

## <a name="structure-of-the-inclusion-list"></a>Struttura dell'elenco di inclusione
 Una voce valida di un elenco di inclusione presenta due parti: un percorso al manifesto della distribuzione e la chiave pubblica usata per firmare la soluzione. Le soluzioni che vengono aggiunte all'elenco di inclusione vengono considerate attendibili. Quando la soluzione Office viene eseguita, l'applicazione di Office confronta la chiave pubblica contenuta nell'elenco di inclusione con la chiave di firma contenuta nel manifesto della distribuzione allo scopo di verificare se la soluzione in esecuzione corrisponde alla versione originale ritenuta attendibile.

## <a name="see-also"></a>Vedi anche
- [Concedere l'attendibilità Office soluzioni](../vsto/granting-trust-to-office-solutions.md)
- [Proteggere Office soluzioni](../vsto/securing-office-solutions.md)
