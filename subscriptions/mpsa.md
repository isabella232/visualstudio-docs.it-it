---
title: Sottoscrizioni di Visual Studio in un contratto MPSA (Microsoft Products and Services Agreement)| Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/23/2019
ms.topic: conceptual
description: Sottoscrizioni di Visual Studio in un contratto MPSA (Microsoft Product and Services Agreement)
ms.openlocfilehash: f87a77cdc19244ca24da1685c0b05372f6cc76d7
ms.sourcegitcommit: ce1ab8a25c66a83e60eab80ed8e1596fe66dd85c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/29/2019
ms.locfileid: "68605854"
---
# <a name="visual-studio-subscriptions-in-a-microsoft-products-and-services-agreement-mpsa"></a>Sottoscrizioni di Visual Studio in un contratto MPSA (Microsoft Product and Services Agreement)
Se sono state acquistate sottoscrizioni di Visual Studio tramite il programma MPSA, è necessario tenere presente alcuni aspetti prima di poter diventare un amministratore di sottoscrizioni di Visual Studio e assegnare le sottoscrizioni agli utenti. Se il proprio account è già stato configurato come amministratore, è possibile passare direttamente al [portale di amministrazione](https://manage.visualstudio.com/) delle sottoscrizioni di Visual Studio.

I clienti con contratto MPSA gestiscono ora le risorse acquistate tramite MPSA in un nuovo portale denominato [Business Center](https://businessaccount.microsoft.com/Customer), che supporta funzionalità simili a quelle di Volume Licensing Service Center (VLSC). Queste funzionalità includono la visualizzazione di Riepilogo licenze, Ordini, Download, Chiavi, Utenti e così via. Tuttavia, le sottoscrizioni di Visual Studio in MPSA sono simili ai Servizi cloud. Il portale Business Center usa anche account aziendali per l'accesso invece di account Microsoft (MSA). Se l'organizzazione usa servizi cloud come Office 365 o Azure Active Directory e l'indirizzo di posta elettronica è incluso in uno di questi due servizi, l'account è già un account aziendale. Di conseguenza, è possibile eseguire la registrazione in Business Center con la password esistente. Se l'organizzazione non usa servizi cloud e l'indirizzo di posta elettronica non è un account aziendale, è possibile usarlo per eseguire la registrazione in Business Center.

Inoltre, il [portale di amministrazione](https://manage.visualstudio.com/) delle sottoscrizioni di Visual Studio è il punto in cui vengono assegnate le sottoscrizioni ai sottoscrittori quando si diventa un amministratore delle sottoscrizioni di Visual Studio. In MPSA è necessario effettuare il provisioning delle sottoscrizioni di Visual Studio nel portale di gestione corrispondente, ovvero nel portale di amministrazione delle sottoscrizioni di Visual Studio. A tale scopo, associare l'account di acquisto a un tenant, ad esempio contoso.onmicrosoft.com.

Si noti che esistono due tipi di tenant: i tenant gestiti e i tenant non gestiti. Un tenant gestito è un tenant già gestito dagli amministratori all'interno dell'organizzazione.

Un tenant non gestito è un tenant senza alcun amministratore assegnato e non può essere usato per i servizi online come Office 365. I tenant non gestiti vengono creati anche quando si esegue la registrazione in Business Center con un indirizzo di posta elettronica che non è un account aziendale. Se viene chiesto di creare una password durante la registrazione in Business Center, significa che l'indirizzo di posta elettronica specificato non è un account aziendale e di conseguenza viene creato un tenant non gestito.

Ecco alcuni requisiti/passaggi necessari per diventare un amministratore delle sottoscrizioni di Visual Studio prima di completare l'associazione del tenant.

## <a name="pre-tenant-association-managed-tenant"></a>Associazione pre-tenant (tenant gestito)
- È necessario essere un utente registrato in Business Center.
- È necessario essere un amministratore utenti (requisito minimo) o un amministratore globale all'interno del tenant cui si appartiene. (Questo requisito si applica se la società usa già i Servizi cloud). Ogni ruolo deve essere un amministratore delle sottoscrizioni di Visual Studio.
- È necessario essere un amministratore globale nel tenant cui si appartiene per poter associare l'account di acquisto al tenant.
- È necessario essere un amministratore account o un account manager in Business Center.
- Il campo "Paese o area geografica" all'interno del proprio profilo utente o di un altro utente in [Azure](https://portal.azure.com/) deve essere popolato correttamente in base all'area geografica (ad esempio US, CA e così via). 

> [!NOTE]
> Gli utenti che si vuole configurare come amministratori delle sottoscrizioni di Visual Studio non devono essere utenti in Business Center, ma solo soddisfare i criteri indicati nei passaggi 2 e 5.

Dopo aver soddisfatto i criteri indicati sopra, è possibile procedere all'associazione dell'account di acquisto al tenant eseguendo la procedura seguente.
1. Accedere a [Business Center](https://businessaccount.microsoft.com/Customer).
2. Fare clic sulla scheda **Account** e scegliere **Associa dominio**.
3. Selezionare l'**account di acquisto** se sono disponibili più account.
4. Selezionare il **tenant**, ad esempio contoso.onmicrosoft.com.
5. Fare clic su **Associa dominio**.

Durante l'associazione, tutti gli utenti che soddisfano i criteri effettuano generalmente il provisioning come amministratori delle sottoscrizioni di Visual Studio entro pochi minuti. In alcuni casi, tuttavia, potrebbe essere necessario attendere fino a 24 ore. Al termine del provisioning del tenant, sarà possibile accedere al portale di amministrazione delle sottoscrizioni di Visual Studio. Se l'operazione richiede più di 24 ore, contattare il supporto MPSA.

> [!NOTE]
> Se sono presenti nuovi utenti che dopo l'associazione soddisfano i criteri indicati nei passaggi 2 e 5, è necessario contattare il supporto MPSA. Il supporto MPSA offrirà assistenza per eseguire il provisioning dei nuovi amministratori delle sottoscrizioni di Visual Studio.

## <a name="tenant-association-unmanaged"></a>Associazione del tenant (non gestito)
Se è stata eseguita la registrazione in Business Center con un indirizzo di posta elettronica che non è un account aziendale (non registrato in Azure Active Directory, "Azure AD"), come descritto sopra, l'associazione del tenant sarà leggermente diversa. Sarà necessario eseguire un "take-over del dominio". Durante questo processo sarà necessario configurare se stessi come amministratore globale e modificare il tenant da non gestito a gestito.

Per una descrizione più dettagliata di questo processo,vedere le [guide rapide](https://www.microsoft.com/en-us/Licensing/existing-customer/business-center-training-and-resources.aspx). Scaricare la guida denominata *"Setup and Use Your Online Services"* (Configurare e usare i servizi online) per istruzioni su come eseguire il take-over di un dominio. Al termine, anche l'account di acquisto risulterà associato al tenant.

> [!NOTE]
> Dopo aver completato il processo di take-over del dominio, è necessario soddisfare i criteri dei cinque passaggi della sezione Associazione pre-tenant (tenant gestito). Dopo aver soddisfatto i criteri, sarà necessario contattare il supporto MPSA per eseguire il provisioning di altri amministratori delle sottoscrizioni di Visual Studio.