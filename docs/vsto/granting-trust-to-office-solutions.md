---
title: Concedere l'attendibilità alle soluzioni Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], trust
- inclusion lists [Office development in Visual Studio], about inclusion lists
- trust [Office development in Visual Studio], 2007 Office system
- granting trust [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1acc6f73dd52bacdfd62aff3b2da62e559c4fda6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53890469"
---
# <a name="grant-trust-to-office-solutions"></a>Concedere l'attendibilità alle soluzioni Office
  Concedere l'attendibilità Office solutions significa che modifica i criteri di sicurezza di ogni computer di destinazione per considerare attendibile l'assembly della soluzione, manifesto dell'applicazione, manifesto della distribuzione e documenti. È possibile concedere attendibilità alla soluzione Office per l'utente o l'utente finale.

 È possibile concedere l'attendibilità alla soluzione Office firmando i manifesti dell'applicazione e distribuzione.

 Gli utenti finali possono concedere l'attendibilità alla soluzione Office per prendere una decisione di attendibilità nel [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] richiesta di attendibilità.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

##  <a name="Signing"></a> Concedere l'attendibilità alla soluzione firmando i manifesti dell'applicazione e distribuzione
 Tutte le applicazioni e distribuzione manifests for Office solutions devono essere firmate con un certificato che identifica il server di pubblicazione. I certificati forniscono una base per prendere decisioni di attendibilità.

 Un certificato temporaneo viene creato e concessa l'attendibilità in fase di compilazione in modo che la soluzione verrà eseguita durante il debug. Se si pubblica una soluzione che viene firmata con un certificato temporaneo, all'utente finale verrà richiesto di prendere una decisione di attendibilità.

 Se si effettua la soluzione con un certificato noto e attendibile, la soluzione verrà automaticamente installata senza chiedere conferma all'utente finale di prendere una decisione di attendibilità. Per altre informazioni su come ottenere un certificato per la firma, vedere [ClickOnce e Authenticode](../deployment/clickonce-and-authenticode.md). Dopo aver ottenuto un certificato, il certificato deve essere attendibile in modo esplicito per aggiungerlo all'elenco degli autori attendibili. Per altre informazioni, vedere [Procedura: Aggiungere un autore attendibile a un computer client per applicazioni ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md).

 Se uno sviluppatore esegue la soluzione con un certificato temporaneo, un amministratore può firmare nuovamente la personalizzazione con un certificato attendibile e noto con il Manifest Generation and Editing Tool (*mage.exe*), ovvero una del Strumenti di Microsoft .NET Framework. Per altre informazioni sulla firma delle soluzioni, vedere [come: Firmare soluzioni Office](../vsto/how-to-sign-office-solutions.md) e [come: Firmare manifesti dell'applicazione e distribuzione](../ide/how-to-sign-application-and-deployment-manifests.md).

##  <a name="TrustPrompt"></a>Concedere l'attendibilità alla soluzione tramite la richiesta di attendibilità di ClickOnce
 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] chiede all'utente finale per prendere la decisione di attendibilità, se non sono presenti criteri a livello di organizzazione che considera attendibile il certificato della soluzione. Se l'utente concede l'attendibilità alla soluzione, viene creata una voce di elenco di inclusione che contiene un URL e una chiave pubblica per archiviare questa decisione di attendibilità. Quando una personalizzazione trusted viene eseguita in un secondo momento, è possibile che l'utente finale non viene richiesto anche in questo caso.

 Gli amministratori possono disabilitare la [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] richiesta di attendibilità o richiedono che il prompt dei comandi si verificano solo per le soluzioni che sono firmate con un certificato Authenticode. Per altre informazioni su come modificare queste impostazioni per le zone di siti non attendibili, siti attendibili, Internet, LocalIntranet e risorse del computer, vedere [come: Configurare il comportamento dei messaggi di richiesta di attendibilità di ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md).

## <a name="see-also"></a>Vedere anche

- [Proteggere le soluzioni Office](../vsto/securing-office-solutions.md)
- [Concedere l'attendibilità ai documenti](../vsto/granting-trust-to-documents.md)
- [Risolvere i problemi di sicurezza delle soluzioni Office](../vsto/troubleshooting-office-solution-security.md)
- [Considerazioni sulla sicurezza specifiche per le soluzioni Office](../vsto/specific-security-considerations-for-office-solutions.md)