---
title: Concedi attendibilità alle soluzioni Office
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cf7a68d5d3567305e4f70049d76a1c260ddecf25
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "89315239"
---
# <a name="grant-trust-to-office-solutions"></a>Concedi attendibilità alle soluzioni Office
  Concedi attendibilità alle soluzioni Office significa modificare i criteri di sicurezza di ogni computer di destinazione in modo da considerare attendibile l'assembly della soluzione, il manifesto dell'applicazione, il manifesto di distribuzione e il documento. È possibile concedere l'attendibilità alla soluzione Office da parte dell'utente o dell'utente finale.

 Per concedere l'attendibilità totale alla soluzione Office, è possibile firmare i manifesti dell'applicazione e della distribuzione.

 Gli utenti finali possono concedere l'attendibilità alla soluzione Office prendendo una decisione di attendibilità nella [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] richiesta di attendibilità.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="trust-the-solution-by-signing-the-application-and-deployment-manifests"></a><a name="Signing"></a> Attendibilità della soluzione mediante la firma dei manifesti dell'applicazione e della distribuzione
 Tutti i manifesti dell'applicazione e della distribuzione per le soluzioni Office devono essere firmati con un certificato che identifica il server di pubblicazione. I certificati costituiscono una base per prendere decisioni di attendibilità.

 Viene creato automaticamente un certificato temporaneo e viene concessa la relazione di trust in fase di compilazione, in modo che la soluzione venga eseguita mentre viene eseguito il debug. Se si pubblica una soluzione firmata con un certificato temporaneo, all'utente finale verrà richiesto di prendere una decisione di attendibilità.

 Se si firma la soluzione con un certificato noto e attendibile, la soluzione verrà installata automaticamente senza richiedere all'utente finale di prendere una decisione di attendibilità. Per ulteriori informazioni su come ottenere un certificato per la firma, vedere [ClickOnce e Authenticode](../deployment/clickonce-and-authenticode.md). Una volta ottenuto un certificato, il certificato deve essere considerato attendibile in modo esplicito aggiungendolo all'elenco Autori attendibili. Per ulteriori informazioni, vedere [procedura: aggiungere un autore attendibile a un computer client per applicazioni ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md).

 Se uno sviluppatore firma la soluzione con un certificato temporaneo, un amministratore può firmare nuovamente la personalizzazione con un certificato noto e attendibile usando il Strumento per la generazione e la modifica di manifesti (*mage.exe*), che è uno degli strumenti di Microsoft .NET Framework. Per altre informazioni sulla firma di soluzioni, vedere [procedura: firmare soluzioni Office](../vsto/how-to-sign-office-solutions.md) e [procedura: firmare manifesti dell'applicazione e di distribuzione](../ide/how-to-sign-application-and-deployment-manifests.md).

## <a name="trust-the-solution-by-using-the-clickonce-trust-prompt"></a><a name="TrustPrompt"></a>Attendibilità della soluzione tramite la richiesta di attendibilità ClickOnce
 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] richiede all'utente finale di prendere la decisione di attendibilità se non sono presenti criteri a livello di organizzazione che considerano attendibile il certificato della soluzione. Se l'utente finale concede l'attendibilità alla soluzione, viene creata una voce dell'elenco di inclusione contenente un URL e una chiave pubblica per archiviare questa decisione di attendibilità. Quando una personalizzazione attendibile viene eseguita in un secondo momento, l'utente finale non viene più richiesto.

 Gli amministratori possono disabilitare la [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] richiesta di attendibilità o richiedere che la richiesta venga eseguita solo per le soluzioni firmate con un certificato Authenticode. Per ulteriori informazioni su come modificare queste impostazioni per le zone computer, LocalIntranet, Internet, TrustedSites e UntrustedSites, vedere [procedura: configurare il comportamento della richiesta di attendibilità ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md).

## <a name="see-also"></a>Vedere anche

- [Soluzioni Office sicure](../vsto/securing-office-solutions.md)
- [Concedi attendibilità ai documenti](../vsto/granting-trust-to-documents.md)
- [Risolvere i problemi relativi alla sicurezza delle soluzioni Office](../vsto/troubleshooting-office-solution-security.md)
- [Considerazioni specifiche sulla sicurezza per le soluzioni Office](../vsto/specific-security-considerations-for-office-solutions.md)