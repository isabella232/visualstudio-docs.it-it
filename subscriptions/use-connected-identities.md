---
title: Come usare l'account Microsoft connesso e le identità di Azure Active Directory Documenti Microsoft
author: evanwindom
ms.author: lank
manager: lank
ms.date: 03/11/2020
ms.topic: conceptual
robots: noindex, nofollow
description: Informazioni su come usare gli account Microsoft connessi e le identità di Azure Active Directory
ms.openlocfilehash: 3dcb41a26f27e5135962edf7ff933de40ccefe5e
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/21/2020
ms.locfileid: "79508979"
---
# <a name="how-to-use-connected-identities-in-visual-studio-subscriptions"></a>Come usare le identità connesse nelle sottoscrizioni di Visual StudioHow to use connected identities in Visual Studio subscriptions
Se si riceve una sottoscrizione di Visual Studio tramite l'organizzazione o l'istituto di istruzione e si usa l'account Microsoft (MSA) per accedere, l'amministratore delle sottoscrizioni può connettere l'ACCOUNT MSA all'identità in Azure Active Directory (Azure AD) dell'organizzazione.  Questo cambierà il modo in cui si accede ad alcuni dei vantaggi inclusi nella sottoscrizione. 

## <a name="overview-of-connected-ids"></a>Panoramica degli AVVISI connessi
Le organizzazioni stanno passando sempre più alle identità basate su Azure AD per fornire maggiore sicurezza e supporto per la gestione automatizzata delle sottoscrizioni.  Se la sottoscrizione usa un @outlook.com MESSAGGIO MSA, ad esempio un indirizzo di posta elettronica personale, l'amministratore può modificare la posta elettronica di accesso all'identità di Azure AD.  Questo cambierà il modo in cui https://my.visualstudio.com accedere al portale per gli abbonati, ma potrebbe non cambiare la modalità di accesso a tutti i vantaggi.  

Se l'amministratore connette le identità di MSA e Azure AD, si riceverà un messaggio di posta elettronica che informa di iniziare ad accedere alla sottoscrizione di Visual Studio con l'identità di Azure AD anziché con il messaggio MSA. 

## <a name="how-to-access-benefits-using-azure-ad-identities"></a>Come accedere ai vantaggi usando le identità di Azure ADHow to access benefits using Azure AD identities
Dopo che l'amministratore ha connesso l'account MSA all'identità di https://my.visualstudio.com Azure AD, è necessario accedere al portale per abbonati con l'identità di Azure AD per accedere ai vantaggi che si basano su Azure AD.  incluse le seguenti:
- IDE di Visual Studio
- Azure DevOps
- Credito individuale per Azure DevTest

## <a name="how-to-access-benefits-using-your-msa"></a>Come accedere ai vantaggi utilizzando l'MSA
Per molti dei vantaggi offerti nelle sottoscrizioni di Visual Studio, ad esempio Pluralsight, LinkedIn, CloudPilot e altri, si creano effettivamente account utente nei siti Web dei partner.  Per tali account, è necessario continuare a utilizzare l'identità utilizzata al momento della creazione dell'account.  Ad esempio, se hai attivato il vantaggio Pluralsight utilizzando il tuo MSA, dovresti continuare a utilizzare il tuo MSA quando esegui la formazione Pluralsight, indipendentemente dall'identità che usi per accedere al portale per gli abbonati.  

## <a name="use-an-alternate-identity-to-access-your-subscription"></a>Usare un'identità alternativa per accedere alla sottoscrizioneUse an alternate identity to access your subscription
L'aggiunta di un account alternativo alla sottoscrizione di Visual Studio consente di accedere ai vantaggi della sottoscrizione, tra cui Azure DevOps e Azure, con un'identità diversa rispetto a quella a cui è assegnata la sottoscrizione. In precedenza, questa funzionalità era disponibile solo se la sottoscrizione di Visual Studio (VS) era assegnata a un account Microsoft. Questa funzionalità è stata estesa agli account aziendali o di istituti di istruzione in Azure Active Directory (Azure AD).  Per ulteriori informazioni sull'utilizzo di account alternativi, consulta il nostro articolo [Identità alternative.](vs-alternate-identity.md) 

## <a name="frequently-asked-questions"></a>Domande frequenti
### <a name="q-how-can-i-contact-my-admin-about-this"></a>D: Come posso contattare il mio amministratore?
R: Per informazioni su come contattare l'amministratore, consulta l'articolo [Contattare l'amministratore](contact-my-admin.md) delle sottoscrizioni.  

## <a name="see-also"></a>Vedere anche
- [Documentazione di Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Documentazione di Azure DevOpsAzure DevOps documentation](https://docs.microsoft.com/azure/devops/)
- [Documentazione di Azure](https://docs.microsoft.com/azure/)
- [Documentazione di Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Passaggi successivi
Dopo che l'amministratore connette gli account Azure AD e MSA, è consigliabile verificare che sia possibile accedere correttamente al portale di sottoscrizione e accedere a vantaggi come DevOps di Azure, Visual Studio e il credito individuale di Azure DevTest.After your admin connects your Azure AD and MSA accounts, we recommend verifying that you can successfully sign in to the [subscription portal](https://my.visualstudio.com?wt.mc_id=o~msft~docs) and access benefits like Azure DevOps, Visual Studio, and your Azure DevTest individual credit. 