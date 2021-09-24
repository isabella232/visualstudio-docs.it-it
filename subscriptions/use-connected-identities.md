---
title: Come usare le identità connesse in Visual Studio sottoscrizioni | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 50ce0445-ef1a-4e92-b9d0-aebb2155a111
ms.date: 02/19/2021
ms.topic: conceptual
robots: noindex, nofollow
description: Informazioni su come usare account Microsoft connessi e Azure Active Directory identità
ms.openlocfilehash: 6c666f50fee33d4277b32cc70ea37db5115dcdf4
ms.sourcegitcommit: da5efd7698e357c59ba9b7dbbcaaceb5d1cfade2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/23/2021
ms.locfileid: "128329395"
---
# <a name="how-to-use-connected-identities-in-visual-studio-subscriptions"></a>Come usare le identità connesse nelle sottoscrizioni Visual Studio servizio
Se si riceve una sottoscrizione di Visual Studio tramite l'azienda o l'istituto di istruzione e si usa l'account account Microsoft (MSA) per accedere, l'amministratore delle sottoscrizioni può connettere l'account del servizio microsoft all'identità dell'utente nell'Azure Active Directory (Azure AD) dell'organizzazione.  In questo modo verrà modificato il modo in cui si accede ad alcuni dei vantaggi inclusi nella sottoscrizione. 

## <a name="overview-of-connected-ids"></a>Panoramica degli ID connessi
Le organizzazioni stanno passando sempre più Azure AD basate su criteri per offrire sicurezza e supporto migliori per la gestione automatizzata delle sottoscrizioni.  Se la sottoscrizione usa un account del servizio microsoft, ad esempio un indirizzo di posta elettronica personale o un altro indirizzo di posta elettronica, l'amministratore può modificare l'indirizzo di posta elettronica di accesso con @outlook.com l'Azure AD aziendale.  Ciò modificherà la modalità di accesso al portale per i sottoscrittori all'indirizzo , ma potrebbe non cambiare la modalità di accesso https://my.visualstudio.com a tutti i vantaggi.  

Se l'amministratore connette l'account del servizio microsoft e le identità Azure AD, si riceverà un messaggio di posta elettronica che informa di iniziare ad accedere alla sottoscrizione di Visual Studio con l'identità Azure AD anziché con l'account del servizio microsoft. 

## <a name="how-to-access-benefits-using-azure-ad-identities"></a>Come accedere ai vantaggi usando Azure AD identità
Dopo che l'amministratore ha connesso l'account microsoft all'identità di Azure AD, è necessario accedere al portale per i sottoscrittori all'indirizzo con l'identità di Azure AD per accedere ai vantaggi che si basano su https://my.visualstudio.com Azure AD.  Queste includono:
- IDE di Visual Studio
- Azure DevOps
- Credito individuale per Azure DevTest

## <a name="how-to-access-benefits-using-your-msa"></a>Come accedere ai vantaggi con l'account del servizio microsoft
Per molti dei vantaggi offerti nelle sottoscrizioni Visual Studio, ad esempio Pluralsight, LinkedIn, CloudPilot e altri, si creano effettivamente account utente nei siti Web dei partner.  Per questi account, è consigliabile continuare a usare l'identità usata durante la creazione dell'account.  Ad esempio, se il vantaggio Pluralsight è stato attivato usando l'account del servizio gestito, è consigliabile continuare a usare l'account del servizio gestito quando si esegue il training pluralsight, indipendentemente dall'identità che si usa per accedere al portale per i sottoscrittori.  

## <a name="use-an-alternate-identity-to-access-your-subscription"></a>Usare un'identità alternativa per accedere alla sottoscrizione
L'aggiunta di un account alternativo alla sottoscrizione di Visual Studio consente di accedere ai vantaggi della sottoscrizione, tra cui Azure DevOps e Azure, con un'identità diversa rispetto a quella a cui è assegnata la sottoscrizione. In precedenza, questa funzionalità era disponibile solo se la sottoscrizione di Visual Studio (VS) era assegnata a un account Microsoft. Questa funzionalità è stata estesa agli account aziendali o di istituti di istruzione in Azure Active Directory (Azure AD).  Per altre informazioni sull'uso di account alternativi, vedere [l'articolo Identità alternative.](vs-alternate-identity.md) 

## <a name="frequently-asked-questions"></a>Domande frequenti
### <a name="q-how-can-i-contact-my-admin-about-this"></a>D: Come è possibile contattare l'amministratore?
Per informazioni su come contattare [l'amministratore,](contact-my-admin.md) vedere l'articolo Contattare l'amministratore delle sottoscrizioni.  

### <a name="q-im-an-admin--how-do-i-use-this"></a>D: Sono un amministratore.  Ricerca per categorie usarlo?
A: L'implementazione delle identità connesse è semplice.  Vedi [questo articolo](personal-email-sign-ins.md) per altre informazioni. 

## <a name="resources"></a>Risorse
- Per assistenza su vendite, sottoscrizioni, account e fatturazione per Sottoscrizioni di Visual Studio, vedere Supporto Visual Studio [sottoscrizioni](https://aka.ms/vssubscriberhelp).

## <a name="see-also"></a>Vedi anche
- [Visual Studio documentazione](/visualstudio/)
- [Documentazione di Azure DevOps](/azure/devops/)
- [Documentazione di Azure](/azure/)
- [Microsoft 365 documentazione](/microsoft-365/)

## <a name="next-steps"></a>Passaggi successivi
Dopo che l'amministratore ha connesso gli account Azure AD e MSA, è consigliabile verificare che sia possibile accedere correttamente al portale delle sottoscrizioni e accedere a vantaggi come Azure DevOps, Visual Studio e il credito individuale di Azure DevTest. [](https://my.visualstudio.com?wt.mc_id=o~msft~docs)