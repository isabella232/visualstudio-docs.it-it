---
title: Come usare account Microsoft connesse e identità Azure Active Directory | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 09/27/2019
ms.topic: conceptual
robots: noindex, nofollow
description: Informazioni su come usare gli account Microsoft e le identità Azure Active Directory connesse
ms.openlocfilehash: d0d30092f34a3cb17b41455612cd336af3e58d30
ms.sourcegitcommit: 13decf878b33fc0c5d665a88067170c2861b261b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/30/2019
ms.locfileid: "71682158"
---
# <a name="how-to-use-connected-identities-in-visual-studio-subscriptions"></a>Come usare le identità connesse nelle sottoscrizioni di Visual Studio
Se si riceve una sottoscrizione di Visual Studio tramite l'azienda o l'Istituto di istruzione e si usa il account Microsoft (MSA) per eseguire l'accesso, l'amministratore delle sottoscrizioni può connettere il servizio MSA alla propria identità nell'Azure Active Directory (Azure AD) dell'organizzazione.  Verrà modificato il modo in cui è possibile accedere ad alcuni dei vantaggi inclusi nella sottoscrizione. 

## <a name="overview-of-connected-ids"></a>Panoramica degli ID connessi
Le organizzazioni si spostano sempre più in identità basate su Azure AD per offrire una migliore sicurezza e supporto per la gestione automatica delle sottoscrizioni.  Se la sottoscrizione usa un account del servizio gestito, ad esempio un @no__t 0 o un altro indirizzo di posta elettronica personale, l'amministratore può modificare il messaggio di posta elettronica di accesso all'identità del Azure AD.  In questo modo sarà possibile accedere al portale per gli abbonati a https://my.visualstudio.com, ma potrebbe non modificare la modalità di accesso a tutti i vantaggi.  

Se l'amministratore connette le identità di MSA e Azure AD, si riceverà un messaggio di posta elettronica che informa di iniziare ad accedere alla sottoscrizione di Visual Studio con l'identità del Azure AD anziché il servizio MSA. 

## <a name="how-to-access-benefits-using-azure-ad-identities"></a>Come accedere ai vantaggi usando identità Azure AD
Dopo che l'amministratore ha connesso il servizio MSA alla propria identità di Azure AD, sarà necessario accedere al portale per gli abbonati con https://my.visualstudio.com con l'identità del Azure AD per accedere ai vantaggi che si basano Azure AD.  Sono inclusi:
- IDE di Visual Studio
- Azure DevOps
- Crediti di Azure

## <a name="how-to-access-benefits-using-your-msa"></a>Come accedere ai vantaggi usando MSA
Per molti dei vantaggi offerti nelle sottoscrizioni di Visual Studio, ad esempio Pluralsight, LinkedIn, CloudPilot e altri, si creano effettivamente account utente nei siti Web dei partner.  Per questi account, è necessario continuare a usare l'identità usata al momento della creazione dell'account.  Se, ad esempio, è stato attivato il vantaggio Pluralsight usando il servizio MSA, è necessario continuare a usare il servizio MSA durante l'esecuzione della formazione Pluralsight, indipendentemente dall'identità usata per accedere al portale per gli abbonati.  

## <a name="use-an-alternate-identity-to-access-your-subscription"></a>Usare un'identità alternativa per accedere alla sottoscrizione
L'aggiunta di un account alternativo alla sottoscrizione di Visual Studio consente di accedere ai vantaggi della sottoscrizione, tra cui Azure DevOps e Azure, con un'identità diversa rispetto a quella a cui è assegnata la sottoscrizione. In precedenza, questa funzionalità era disponibile solo se la sottoscrizione di Visual Studio (VS) era assegnata a un account Microsoft. Questa funzionalità è stata estesa agli account aziendali o di istituti di istruzione in Azure Active Directory (Azure AD).  Per altre informazioni sull'uso di account alternativi, vedere l'articolo [identità alternative](vs-alternate-identity.md) . 

## <a name="frequently-asked-questions"></a>Domande frequenti
### <a name="q-how-can-i-contact-my-admin-about-this"></a>D: Come è possibile contattare l'amministratore?
R:  Per informazioni su come contattare l'amministratore, vedere l'articolo [contattare l'amministratore delle sottoscrizioni](contact-my-admin.md) .  

## <a name="next-steps"></a>Passaggi successivi
Dopo che l'amministratore ha connesso gli account Azure AD e MSA, è consigliabile verificare che sia possibile accedere al portale di [sottoscrizione](https://my.visualstudio.com?wt.mc_id=o~msft~docs) e accedere a vantaggi come Azure DevOps, Visual Studio e i crediti di Azure. 