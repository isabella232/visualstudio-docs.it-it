---
title: Concedere l'attendibilità Office soluzioni
description: Concedere l'attendibilità Office soluzioni significa modificare i criteri di sicurezza di ogni computer di destinazione in modo da considerare attendibili l'assembly della soluzione, il manifesto di distribuzione e il documento.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: cdf67b8a5cfda899607f0fdca511c78548eb319d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122139842"
---
# <a name="grant-trust-to-office-solutions"></a>Concedere l'attendibilità Office soluzioni
  Concedere l'attendibilità Office soluzioni significa modificare i criteri di sicurezza di ogni computer di destinazione in modo da considerare attendibili l'assembly della soluzione, il manifesto dell'applicazione, il manifesto della distribuzione e il documento. L'attendibilità può essere concessa alla Office dall'utente finale o dall'utente finale.

 È possibile concedere l'attendibilità totale alla soluzione Office firmando i manifesti dell'applicazione e della distribuzione.

 Gli utenti finali possono concedere l'attendibilità alla soluzione Office prendendo una decisione di attendibilità nella richiesta [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] di attendibilità.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="trust-the-solution-by-signing-the-application-and-deployment-manifests"></a><a name="Signing"></a> Considerare attendibile la soluzione firmando i manifesti dell'applicazione e della distribuzione
 Tutti i manifesti dell'applicazione e della distribuzione Office soluzioni devono essere firmati con un certificato che identifica l'autore. I certificati consentono di prendere decisioni di attendibilità.

 Viene creato un certificato temporaneo e viene concessa l'attendibilità in fase di compilazione in modo che la soluzione verrà eseguita durante il debug. Se si pubblica una soluzione firmata con un certificato temporaneo, all'utente finale verrà richiesto di prendere una decisione di attendibilità.

 Se si firma la soluzione con un certificato noto e attendibile, la soluzione verrà installata automaticamente senza chiedere all'utente finale di prendere una decisione di attendibilità. Per altre informazioni su come ottenere un certificato per la firma, vedere ClickOnce [e Authenticode](../deployment/clickonce-and-authenticode.md). Dopo aver ottenuto un certificato, il certificato deve essere considerato attendibile in modo esplicito aggiungendolo all'elenco Autori attendibili. Per altre informazioni, vedere [Procedura: Aggiungere un](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)autore attendibile a un computer client per ClickOnce applicazioni .

 Se uno sviluppatore firma la soluzione con un certificato temporaneo, un amministratore può firmare nuovamente la personalizzazione con un certificato noto e attendibile usando il Strumento per la generazione e la modifica di manifesti (*mage.exe*), che è uno degli strumenti microsoft .NET Framework. Per altre informazioni sulla firma di soluzioni, vedere [Procedura:](../vsto/how-to-sign-office-solutions.md) Firmare Office soluzioni e [Procedura: Firmare](../ide/how-to-sign-application-and-deployment-manifests.md)manifesti dell'applicazione e della distribuzione .

## <a name="trust-the-solution-by-using-the-clickonce-trust-prompt"></a><a name="TrustPrompt"></a>Considerare attendibile la soluzione usando la richiesta ClickOnce attendibilità
 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] richiede all'utente finale di prendere la decisione di attendibilità se non sono presenti criteri a livello di organizzazione che considera attendibili il certificato della soluzione. Se l'utente finale concede l'attendibilità alla soluzione, viene creata una voce dell'elenco di inclusione contenente un URL e una chiave pubblica per archiviare questa decisione di attendibilità. Quando una personalizzazione attendibile viene eseguita in un secondo momento, l'utente finale non viene richiesto di nuovo.

 Gli amministratori possono disabilitare la richiesta di attendibilità o richiedere che la richiesta venga eseguita solo per le soluzioni [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] firmate con un certificato Authenticode. Per altre informazioni su come modificare queste impostazioni per le zone MyComputer, LocalIntranet, Internet, TrustedSites e UntrustedSites, vedere [Procedura: Configurare](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)il comportamento della richiesta di attendibilità ClickOnce .

## <a name="see-also"></a>Vedi anche

- [Soluzioni Office sicure](../vsto/securing-office-solutions.md)
- [Concedere l'attendibilità ai documenti](../vsto/granting-trust-to-documents.md)
- [Risolvere i Office della soluzione](../vsto/troubleshooting-office-solution-security.md)
- [Considerazioni specifiche sulla sicurezza per Office soluzioni](../vsto/specific-security-considerations-for-office-solutions.md)