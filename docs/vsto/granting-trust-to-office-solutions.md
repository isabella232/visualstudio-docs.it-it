---
title: Concedere l'attendibilità alle soluzioni OfficeGrant trust to Office solutions
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
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/13/2020
ms.locfileid: "79303302"
---
# <a name="grant-trust-to-office-solutions"></a>Concedere l'attendibilità alle soluzioni OfficeGrant trust to Office solutions
  Concedere l'attendibilità alle soluzioni Office significa modificare i criteri di sicurezza di ogni computer di destinazione per considerare attendibili l'assembly della soluzione, il manifesto dell'applicazione, il manifesto di distribuzione e il documento. L'attendibilità può essere concessa alla soluzione Office dall'utente o dall'utente finale.

 È possibile concedere l'attendibilità totale alla soluzione Office firmando i manifesti dell'applicazione e di distribuzione.

 Gli utenti finali possono concedere l'attendibilità alla [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] soluzione Office prendendo una decisione di attendibilità nella richiesta di attendibilità.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="trust-the-solution-by-signing-the-application-and-deployment-manifests"></a><a name="Signing"></a>Considerare attendibile la soluzione firmando i manifesti dell'applicazione e di distribuzione
 Tutti i manifesti dell'applicazione e di distribuzione per le soluzioni Office devono essere firmati con un certificato che identifica l'autore. I certificati forniscono una base per prendere decisioni sull'attendibilità.

 Viene creato automaticamente un certificato temporaneo e viene concessa l'attendibilità in fase di compilazione in modo che la soluzione venga eseguita durante il debug. Se si pubblica una soluzione firmata con un certificato temporaneo, all'utente finale verrà richiesto di prendere una decisione sull'attendibilità.

 Se si firma la soluzione con un certificato noto e attendibile, la soluzione verrà installata automaticamente senza chiedere all'utente finale di prendere una decisione sull'attendibilità. Per ulteriori informazioni su come ottenere un certificato per la firma, vedere [ClickOnce e Authenticode](../deployment/clickonce-and-authenticode.md). Dopo aver ottenuto un certificato, il certificato deve essere considerato esplicitamente attendibile aggiungendolo all'elenco Autori attendibili. Per ulteriori informazioni, vedere [Procedura: aggiungere un autore attendibile a un computer client per](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)le applicazioni ClickOnce .

 Se uno sviluppatore firma la soluzione con un certificato temporaneo, un amministratore può firmare nuovamente la personalizzazione con un certificato noto e attendibile utilizzando lo strumento di generazione e modifica del manifesto (*mage.exe*), uno degli strumenti di Microsoft .NET Framework. Per ulteriori informazioni sulla firma di soluzioni, vedere [Procedura: firmare soluzioni Office](../vsto/how-to-sign-office-solutions.md) e [Procedura: firmare manifesti dell'applicazione e di distribuzione](../ide/how-to-sign-application-and-deployment-manifests.md).

## <a name="trust-the-solution-by-using-the-clickonce-trust-prompt"></a><a name="TrustPrompt"></a>Considerare attendibile la soluzione utilizzando la richiesta di attendibilità ClickOnce
 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]richiede all'utente finale di prendere la decisione di attendibilità se non esiste alcun criterio a livello di organizzazione che consideri attendibile il certificato della soluzione. Se l'utente finale concede l'attendibilità alla soluzione, viene creata una voce dell'elenco di inclusione contenente un URL e una chiave pubblica per archiviare questa decisione sull'attendibilità. Quando una personalizzazione attendibile viene eseguita in un secondo momento, l'utente finale non viene richiesto nuovamente.

 Gli amministratori [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] possono disabilitare la richiesta di attendibilità o richiedere che il prompt si verifichi solo per le soluzioni firmate con un certificato Authenticode. Per ulteriori informazioni su come modificare queste impostazioni per le aree MyComputer, LocalIntranet, Internet, TrustedSites e UntrustedSites, vedere [Procedura: configurare il comportamento del prompt di attendibilità ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md).

## <a name="see-also"></a>Vedere anche

- [Proteggere le soluzioni OfficeSecure Office solutions](../vsto/securing-office-solutions.md)
- [Concedere l'attendibilità ai documentiGrant trust to documents](../vsto/granting-trust-to-documents.md)
- [Risolvere i problemi di sicurezza delle soluzioni OfficeTroubleshoot Office solution security](../vsto/troubleshooting-office-solution-security.md)
- [Considerazioni specifiche sulla sicurezza per le soluzioni OfficeSpecific security considerations for Office solutions](../vsto/specific-security-considerations-for-office-solutions.md)