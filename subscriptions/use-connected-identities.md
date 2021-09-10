---
title: Come usare le identità connesse nelle sottoscrizioni Visual Studio | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: lank
ms.assetid: 50ce0445-ef1a-4e92-b9d0-aebb2155a111
ms.date: 02/19/2021
ms.topic: conceptual
robots: noindex, nofollow
description: Informazioni su come usare account Microsoft connessi e Azure Active Directory identità
ms.openlocfilehash: 9625774cbf5338750034f1f288bd2ada0aa9fc33
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2021
ms.locfileid: "123965771"
---
# <a name="how-to-use-connected-identities-in-visual-studio-subscriptions"></a>Come usare le identità connesse nelle sottoscrizioni Visual Studio connessione
Se si riceve una sottoscrizione Visual Studio tramite l'azienda o l'istituto di istruzione e si usa l'account Microsoft (MSA) per accedere, l'amministratore delle sottoscrizioni può connettere l'amministratore delle sottoscrizioni all'identità nel Azure Active Directory (Azure AD) dell'organizzazione.  In questo modo verrà modificato il modo in cui si accede ad alcuni dei vantaggi inclusi nella sottoscrizione. 

## <a name="overview-of-connected-ids"></a>Panoramica degli ID connessi
Le organizzazioni stanno passando sempre più Azure AD basate su identità per offrire sicurezza e supporto migliorati per la gestione automatica delle sottoscrizioni.  Se la sottoscrizione usa un account microsoft, ad esempio un indirizzo di posta elettronica o un altro indirizzo di posta elettronica personale, l'amministratore può modificare il messaggio di posta elettronica di accesso con @outlook.com l'Azure AD identità.  Ciò modificherà la modalità di accesso al portale per i sottoscrittori all'indirizzo , ma potrebbe non cambiare il modo in cui https://my.visualstudio.com si accede a tutti i vantaggi.  

Se l'amministratore connette le identità dell'amministratore di sistema e Azure AD, si riceverà un messaggio di posta elettronica che informa di iniziare ad accedere alla sottoscrizione Visual Studio con l'identità Azure AD anziché con l'account del servizio. 

## <a name="how-to-access-benefits-using-azure-ad-identities"></a>Come accedere ai vantaggi usando Azure AD identità
Dopo che l'amministratore ha connesso l'account del servizio app all'identità Azure AD, è necessario accedere al portale per i sottoscrittori all'indirizzo con l'identità Azure AD per accedere ai vantaggi che si basano su https://my.visualstudio.com Azure AD.  Queste includono:
- IDE di Visual Studio
- Azure DevOps
- Credito individuale per Azure DevTest

## <a name="how-to-access-benefits-using-your-msa"></a>Come accedere ai vantaggi usando l'account del servizio di gestione delle risorse
Per molti dei vantaggi offerti nelle sottoscrizioni Visual Studio, ad esempio Pluralsight, LinkedIn, CloudPilot e altri, si creano effettivamente account utente nei siti Web dei partner.  Per questi account, è consigliabile continuare a usare l'identità usata al momento della creazione dell'account.  Ad esempio, se il vantaggio Pluralsight è stato attivato usando l'account del servizio gestito, è consigliabile continuare a usare l'account del servizio gestito quando si esegue il training pluralsight, indipendentemente dall'identità utilizzata per accedere al portale per i sottoscrittori.  

## <a name="use-an-alternate-identity-to-access-your-subscription"></a>Usare un'identità alternativa per accedere alla sottoscrizione
L'aggiunta di un account alternativo alla sottoscrizione di Visual Studio consente di accedere ai vantaggi della sottoscrizione, tra cui Azure DevOps e Azure, con un'identità diversa rispetto a quella a cui è assegnata la sottoscrizione. In precedenza, questa funzionalità era disponibile solo se la sottoscrizione di Visual Studio (VS) era assegnata a un account Microsoft. Questa funzionalità è stata estesa agli account aziendali o di istituti di istruzione in Azure Active Directory (Azure AD).  Per altre informazioni sull'uso di account alternativi, vedere [l'articolo Identità alternative.](vs-alternate-identity.md) 

## <a name="frequently-asked-questions"></a>Domande frequenti
### <a name="q-how-can-i-contact-my-admin-about-this"></a>D: Come è possibile contattare l'amministratore?
Per informazioni su [](contact-my-admin.md) come contattare l'amministratore, vedere l'articolo Contattare l'amministratore delle sottoscrizioni.  

### <a name="q-im-an-admin--how-do-i-use-this"></a>D: Sono un amministratore.  Ricerca per categorie usare questo?
A: L'implementazione di identità connesse è semplice.  Vedi [questo articolo](personal-email-sign-ins.md) per altre informazioni. 

## <a name="resources"></a>Risorse
- Per assistenza su vendite, sottoscrizioni, account e fatturazione per Sottoscrizioni di Visual Studio, vedere supporto Visual Studio [sottoscrizioni](https://aka.ms/vssubscriberhelp).

## <a name="see-also"></a>Vedi anche
- [Visual Studio documentazione](/visualstudio/)
- [Documentazione di Azure DevOps](/azure/devops/)
- [Documentazione di Azure](/azure/)
- [Microsoft 365 documentazione](/microsoft-365/)

## <a name="next-steps"></a>Passaggi successivi
Dopo che l'amministratore ha connesso gli account Azure AD e MSA, è consigliabile verificare che sia possibile accedere correttamente al portale delle sottoscrizioni e accedere ai vantaggi come Azure DevOps, Visual Studio e il credito individuale di Azure DevTest. [](https://my.visualstudio.com?wt.mc_id=o~msft~docs)