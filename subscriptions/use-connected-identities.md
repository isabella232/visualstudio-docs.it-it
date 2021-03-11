---
title: Come usare le identità connesse nelle sottoscrizioni di Visual Studio | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: lank
ms.assetid: 50ce0445-ef1a-4e92-b9d0-aebb2155a111
ms.date: 02/19/2021
ms.topic: conceptual
robots: noindex, nofollow
description: Informazioni su come usare gli account Microsoft e le identità Azure Active Directory connesse
ms.openlocfilehash: 9625774cbf5338750034f1f288bd2ada0aa9fc33
ms.sourcegitcommit: f9ed9c4c6c166ef9826feb21dcb9c4d47ed14e1a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/10/2021
ms.locfileid: "102607119"
---
# <a name="how-to-use-connected-identities-in-visual-studio-subscriptions"></a>Come usare le identità connesse nelle sottoscrizioni di Visual Studio
Se si riceve una sottoscrizione di Visual Studio tramite l'azienda o l'Istituto di istruzione e si usa il account Microsoft (MSA) per eseguire l'accesso, l'amministratore delle sottoscrizioni può connettere il servizio MSA alla propria identità nell'Azure Active Directory (Azure AD) dell'organizzazione.  Verrà modificato il modo in cui è possibile accedere ad alcuni dei vantaggi inclusi nella sottoscrizione. 

## <a name="overview-of-connected-ids"></a>Panoramica degli ID connessi
Le organizzazioni si spostano sempre più in identità basate su Azure AD per offrire una migliore sicurezza e supporto per la gestione automatica delle sottoscrizioni.  Se la sottoscrizione usa un account del servizio gestito @outlook.com , ad esempio o un altro indirizzo di posta elettronica personale, l'amministratore può modificare il messaggio di posta elettronica di accesso all'identità del Azure ad.  In questo modo sarà possibile accedere al portale Sottoscrittore, https://my.visualstudio.com ma non modificare la modalità di accesso a tutti i vantaggi.  

Se l'amministratore connette le identità di MSA e Azure AD, si riceverà un messaggio di posta elettronica che informa di iniziare ad accedere alla sottoscrizione di Visual Studio con l'identità del Azure AD anziché il servizio MSA. 

## <a name="how-to-access-benefits-using-azure-ad-identities"></a>Come accedere ai vantaggi usando identità Azure AD
Dopo che l'amministratore ha connesso il servizio MSA alla propria identità di Azure AD, è necessario accedere al portale per gli abbonati all'indirizzo https://my.visualstudio.com con l'identità del Azure ad per accedere ai vantaggi che si basano su Azure ad.  Tra queste sono incluse:
- IDE di Visual Studio
- Azure DevOps
- Credito individuale per Azure DevTest

## <a name="how-to-access-benefits-using-your-msa"></a>Come accedere ai vantaggi usando MSA
Per molti dei vantaggi offerti nelle sottoscrizioni di Visual Studio, ad esempio Pluralsight, LinkedIn, CloudPilot e altri, si creano effettivamente account utente nei siti Web dei partner.  Per questi account, è necessario continuare a usare l'identità usata al momento della creazione dell'account.  Se, ad esempio, è stato attivato il vantaggio Pluralsight usando il servizio MSA, è necessario continuare a usare il servizio MSA durante l'esecuzione della formazione Pluralsight, indipendentemente dall'identità usata per accedere al portale per gli abbonati.  

## <a name="use-an-alternate-identity-to-access-your-subscription"></a>Usare un'identità alternativa per accedere alla sottoscrizione
L'aggiunta di un account alternativo alla sottoscrizione di Visual Studio consente di accedere ai vantaggi della sottoscrizione, tra cui Azure DevOps e Azure, con un'identità diversa rispetto a quella a cui è assegnata la sottoscrizione. In precedenza, questa funzionalità era disponibile solo se la sottoscrizione di Visual Studio (VS) era assegnata a un account Microsoft. Questa funzionalità è stata estesa agli account aziendali o di istituti di istruzione in Azure Active Directory (Azure AD).  Per altre informazioni sull'uso di account alternativi, vedere l'articolo [identità alternative](vs-alternate-identity.md) . 

## <a name="frequently-asked-questions"></a>Domande frequenti
### <a name="q-how-can-i-contact-my-admin-about-this"></a>D: in che modo è possibile contattare l'amministratore?
R: per informazioni su come contattare l'amministratore, vedere l'articolo [contattare l'amministratore delle sottoscrizioni](contact-my-admin.md) .  

### <a name="q-im-an-admin--how-do-i-use-this"></a>D: sono un amministratore.  Ricerca per categorie utilizzarlo?
R: l'implementazione di identità connesse è semplice.  Vedi [questo articolo](personal-email-sign-ins.md) per altre informazioni. 

## <a name="resources"></a>Risorse
- Per assistenza in merito a vendite, sottoscrizioni, account e fatturazione per le sottoscrizioni di Visual Studio, vedere [supporto delle sottoscrizioni](https://aka.ms/vssubscriberhelp)di Visual Studio.

## <a name="see-also"></a>Vedi anche
- [Documentazione di Visual Studio](/visualstudio/)
- [Documentazione di Azure DevOps](/azure/devops/)
- [Documentazione di Azure](/azure/)
- [Documentazione di Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Passaggi successivi
Quando l'amministratore connette gli account Azure AD e MSA, è consigliabile verificare che sia possibile accedere al portale per le [sottoscrizioni](https://my.visualstudio.com?wt.mc_id=o~msft~docs) e accedere a vantaggi come Azure DevOps, Visual Studio e il credito individuale Azure DevTest.