---
title: Sottoscrizioni di Visual Studio in MPSA | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: b331c837-3524-42b7-820e-b4fdd5e12793
ms.date: 03/21/2021
ms.topic: conceptual
description: Informazioni sulla gestione Visual Studio sottoscrizioni in un contratto MPSA (Microsoft Products and Services Agreement)
ms.openlocfilehash: 2cc01a90bbdaa1a627dc076593fad6756cb0b0c28a4a4b859883bff63f6f33d8
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121421547"
---
# <a name="visual-studio-subscriptions-in-a-microsoft-products-and-services-agreement-mpsa"></a>Sottoscrizioni di Visual Studio in un contratto MPSA (Microsoft Product and Services Agreement)
Se è stato acquistato Sottoscrizioni di Visual Studio tramite il programma MPSA, è necessario tenere presenti alcuni aspetti prima di poter diventare un amministratore delle sottoscrizioni Visual Studio e assegnare sottoscrizioni agli utenti. Se è già stato configurato come amministratore, è possibile passare direttamente al portale di amministrazione delle Visual Studio [sottoscrizioni.](https://manage.visualstudio.com/)

I clienti MPSA gestiscono gli asset acquistati tramite MPSA in un portale denominato [Business Center,](https://businessaccount.microsoft.com/Customer)che supporta funzionalità simili a Volume Licensing Service Center (VLSC). Ad esempio, visualizzare il riepilogo delle licenze, gli ordini, i download, le chiavi, gli utenti e così via. Tuttavia, Visual Studio sottoscrizioni in MPSA si comportano in modo molto simile a Servizi cloud. Il portale Business Center usa anche account aziendali per l'accesso invece di account Microsoft (MSA). Se l'organizzazione usa servizi cloud come Office 365 o Azure Active Directory e l'indirizzo di posta elettronica è incluso in uno di questi due servizi, l'account è già un account aziendale. Di conseguenza, è possibile eseguire la registrazione in Business Center con la password esistente. Se l'organizzazione non usa servizi cloud e l'indirizzo di posta elettronica non è un account aziendale, è possibile usarlo per eseguire la registrazione in Business Center.

Il portale di amministrazione delle [](https://manage.visualstudio.com/) Visual Studio è anche il portale di amministrazione in cui si assegnano le sottoscrizioni quando si diventa amministratore Visual Studio sottoscrizioni. In MPSA è Visual Studio il provisioning delle sottoscrizioni nel rispettivo portale di gestione, ovvero nel Sottoscrizioni di Visual Studio di amministrazione. A tale scopo, associare l'account di acquisto a un tenant, ad esempio contoso.onmicrosoft.com.

Si noti che esistono due tipi di tenant: tenant gestiti e tenant non gestiti. Un tenant gestito fa riferimento a un tenant già gestito dagli amministratori all'interno dell'organizzazione.

Un tenant non gestito è un tenant senza alcun amministratore assegnato e non può essere utilizzato per i Servizi online, ad esempio Office 365. I tenant non gestiti vengono creati anche quando si esegue la registrazione in Business Center con un indirizzo di posta elettronica che non è un account aziendale. Se viene chiesto di creare una password durante la registrazione in Business Center, significa che l'indirizzo di posta elettronica specificato non è un account aziendale e di conseguenza viene creato un tenant non gestito.

Di seguito sono riportati alcuni requisiti/passaggi per diventare un amministratore Sottoscrizioni di Visual Studio prima di completare l'associazione del tenant.

## <a name="pre-tenant-association-managed-tenant"></a>Associazione pre-tenant (tenant gestito)
- È necessario essere un utente registrato in Business Center.
- È necessario essere un amministratore utenti (requisito minimo) o un amministratore globale all'interno del tenant cui si appartiene. (Questo requisito si applica se la società usa già i Servizi cloud). Entrambi i ruoli devono essere un amministratore Visual Studio sottoscrizioni.
- È necessario essere un amministratore globale nel tenant cui si appartiene per poter associare l'account di acquisto al tenant.
- È necessario essere un amministratore account o un account manager in Business Center.
- Il campo "Paese o area geografica" all'interno del proprio profilo utente o di un altro utente in [Azure](https://portal.azure.com/) deve essere popolato correttamente in base all'area geografica (ad esempio US, CA e così via). 

> [!NOTE]
> Non è necessario che gli utenti Visual Studio amministratori delle sottoscrizioni siano utenti in Business Center, perché devono soddisfare solo i criteri 2 e 5.

Dopo aver soddisfatto i criteri precedenti, è possibile procedere con l'associazione dell'account di acquisto al tenant seguendo questa procedura.
1. Accedere a [Business Center](https://businessaccount.microsoft.com/Customer).
2. Fare clic sulla scheda **Account** e scegliere **Associa dominio**.
3. Selezionare l'**account di acquisto** se sono disponibili più account.
4. Selezionare il **tenant** (ad esempio: contoso.onmicrosoft.com).
5. Fare clic su **Associa dominio**.

Al momento dell'associazione, tutti gli utenti che soddisfano i criteri eseguiranno in genere il provisioning Visual Studio amministratori delle sottoscrizioni in pochi minuti. In alcuni casi, tuttavia, potrebbe essere necessario attendere fino a 24 ore. Dopo aver effettuato il provisioning del tenant, sarà possibile accedere al portale Sottoscrizioni di Visual Studio administration. Se l'operazione richiede più di 24 ore, contattare il [supporto tecnico di Business Center.](https://businessaccount.microsoft.com/Customer/ContactUs)

> [!NOTE]
> Se sono presenti nuovi utenti che dopo l'associazione soddisfano i criteri indicati nei passaggi 2 e 5, è necessario contattare il supporto MPSA. Il supporto MPSA fornirà assistenza per il provisioning dei nuovi Sottoscrizioni di Visual Studio amministratori.

## <a name="tenant-association-unmanaged"></a>Associazione del tenant (non gestito)
Se è stata eseguita la registrazione in Business Center con un indirizzo di posta elettronica che non è un account aziendale (non registrato in Azure Active Directory, "Azure AD"), come descritto sopra, l'associazione del tenant sarà leggermente diversa. Sarà necessario eseguire un "take-over del dominio". Durante questo processo sarà necessario configurare se stessi come amministratore globale e modificare il tenant da non gestito a gestito.

Per una descrizione più dettagliata di questo processo,vedere le [guide rapide](https://www.microsoft.com/Licensing/existing-customer/business-center-training-and-resources.aspx). Scaricare la guida *denominata "Setup and Use Your Online Services"* (Installazione e uso dei Servizi online) che guiderà l'utente nella procedura di take-over del dominio. Al termine, l'account di acquisto verrà associato anche al tenant.

> [!NOTE]
> Dopo aver completato il processo di take-over del dominio, è necessario rispettare i criteri dei cinque passaggi della sezione Associazione pre-tenant (gestita). Dopo aver soddisfatto i criteri, sarà necessario contattare il supporto MPSA solo per effettuare il provisioning di Visual Studio amministratori delle sottoscrizioni.

## <a name="support-resources"></a>Risorse di supporto
- Per assistenza per l'amministrazione di Sottoscrizioni di Visual Studio, contattare [Visual Studio supporto per le sottoscrizioni](https://aka.ms/vsadminhelp).

## <a name="see-also"></a>Vedi anche
- [Visual Studio documentazione](/visualstudio/)
- [Documentazione di Azure DevOps](/azure/devops/)
- [Documentazione di Azure](/azure/)
- [Microsoft 365 documentazione](/microsoft-365/)

## <a name="next-steps"></a>Passaggi successivi
Altre informazioni sulla gestione delle Visual Studio sottoscrizione.
- [Assegnare sottoscrizioni singole](assign-license.md)
- [Assegnare più sottoscrizioni](assign-license-bulk.md)
- [Modificare sottoscrizioni](edit-license.md)
- [Eliminare sottoscrizioni](delete-license.md)
- [Determinare l'utilizzo massimo](maximum-usage.md)