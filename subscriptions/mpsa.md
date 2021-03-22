---
title: Sottoscrizioni di Visual Studio in MPSA | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: b331c837-3524-42b7-820e-b4fdd5e12793
ms.date: 03/21/2021
ms.topic: conceptual
description: Informazioni sulla gestione delle sottoscrizioni di Visual Studio in un contratto per prodotti e servizi Microsoft (MPSA)
ms.openlocfilehash: 63124e8853184fde04db7bc202e5acea3cfbe89f
ms.sourcegitcommit: d7d9fb79448b3534923cc95071d1f91eabde88e8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104776532"
---
# <a name="visual-studio-subscriptions-in-a-microsoft-products-and-services-agreement-mpsa"></a>Sottoscrizioni di Visual Studio in un contratto MPSA (Microsoft Product and Services Agreement)
Se sono state acquistate sottoscrizioni di Visual Studio tramite il programma MPSA, è necessario tenere presenti alcune considerazioni prima di poter diventare un amministratore delle sottoscrizioni di Visual Studio e assegnare le sottoscrizioni agli utenti. Se si è già stati configurati come amministratore, è possibile passare direttamente al [portale di amministrazione](https://manage.visualstudio.com/)delle sottoscrizioni di Visual Studio.

I clienti di MPSA gestiscono le risorse acquistate tramite MPSA in un portale denominato [Business Center](https://businessaccount.microsoft.com/Customer), che supporta funzionalità simili a Volume Licensing Service Center (VLSC). Sono incluse la visualizzazione del riepilogo delle licenze, degli ordini, dei download, delle chiavi, degli utenti e così via. Tuttavia, le sottoscrizioni di Visual Studio in MPSA si comportano in modo simile ai servizi cloud. Il portale Business Center usa anche account aziendali per l'accesso invece di account Microsoft (MSA). Se l'organizzazione usa servizi cloud come Office 365 o Azure Active Directory e l'indirizzo di posta elettronica è incluso in uno di questi due servizi, l'account è già un account aziendale. Di conseguenza, è possibile eseguire la registrazione in Business Center con la password esistente. Se l'organizzazione non usa servizi cloud e l'indirizzo di posta elettronica non è un account aziendale, è possibile usarlo per eseguire la registrazione in Business Center.

Inoltre, il [portale di amministrazione](https://manage.visualstudio.com/) delle sottoscrizioni di Visual Studio è il punto in cui verranno assegnate le sottoscrizioni dopo essere diventati un amministratore delle sottoscrizioni di Visual Studio In MPSA è necessario eseguire il provisioning delle sottoscrizioni di Visual Studio nel rispettivo portale di gestione, ovvero il portale di amministrazione delle sottoscrizioni di Visual Studio. A tale scopo, associare l'account di acquisto a un tenant, ad esempio contoso.onmicrosoft.com.

Si noti che esistono due tipi di tenant gestiti da tenant e tenant non gestiti. Un tenant gestito fa riferimento a un tenant già gestito dagli amministratori all'interno dell'organizzazione.

Un tenant non gestito è un tenant senza amministratori assegnati e non è utilizzabile per i servizi online come Office 365. I tenant non gestiti vengono creati anche quando si esegue la registrazione in Business Center con un indirizzo di posta elettronica che non è un account aziendale. Se viene chiesto di creare una password durante la registrazione in Business Center, significa che l'indirizzo di posta elettronica specificato non è un account aziendale e di conseguenza viene creato un tenant non gestito.

Ecco alcuni requisiti/passaggi per diventare un amministratore delle sottoscrizioni di Visual Studio prima di completare l'associazione del tenant.

## <a name="pre-tenant-association-managed-tenant"></a>Associazione pre-tenant (tenant gestito)
- È necessario essere un utente registrato in Business Center.
- È necessario essere un amministratore utenti (requisito minimo) o un amministratore globale all'interno del tenant cui si appartiene. (Questo requisito si applica se la società usa già i Servizi cloud). Entrambi i ruoli sono necessari per essere un amministratore delle sottoscrizioni di Visual Studio.
- È necessario essere un amministratore globale nel tenant cui si appartiene per poter associare l'account di acquisto al tenant.
- È necessario essere un amministratore account o un account manager in Business Center.
- Il campo "Paese o area geografica" all'interno del proprio profilo utente o di un altro utente in [Azure](https://portal.azure.com/) deve essere popolato correttamente in base all'area geografica (ad esempio US, CA e così via). 

> [!NOTE]
> Tutti gli utenti per i quali si vuole rendere amministratori delle sottoscrizioni di Visual Studio non devono essere utenti di business center, perché devono soddisfare solo i criteri 2 e 5.

Dopo aver soddisfatto i criteri descritti in precedenza, è possibile associare l'account di acquisto al tenant attenendosi alla procedura riportata di seguito.
1. Accedere a [Business Center](https://businessaccount.microsoft.com/Customer).
2. Fare clic sulla scheda **Account** e scegliere **Associa dominio**.
3. Selezionare l'**account di acquisto** se sono disponibili più account.
4. Selezionare il **tenant** (ad esempio: contoso.onmicrosoft.com).
5. Fare clic su **Associa dominio**.

Al momento dell'associazione, tutti gli utenti che soddisfano i criteri vengono in genere provisioning come amministratori delle sottoscrizioni di Visual Studio in pochi minuti In alcuni casi, tuttavia, potrebbe essere necessario attendere fino a 24 ore. Al termine del provisioning del tenant, sarà possibile accedere al portale di amministrazione delle sottoscrizioni di Visual Studio. Se l'operazione richiede più di 24 ore, contattare il [supporto tecnico di business center](https://businessaccount.microsoft.com/Customer/ContactUs).

> [!NOTE]
> Se sono presenti nuovi utenti che dopo l'associazione soddisfano i criteri indicati nei passaggi 2 e 5, è necessario contattare il supporto MPSA. Il supporto di MPSA fornirà assistenza per il provisioning dei nuovi amministratori delle sottoscrizioni di Visual Studio.

## <a name="tenant-association-unmanaged"></a>Associazione del tenant (non gestito)
Se è stata eseguita la registrazione in Business Center con un indirizzo di posta elettronica che non è un account aziendale (non registrato in Azure Active Directory, "Azure AD"), come descritto sopra, l'associazione del tenant sarà leggermente diversa. Sarà necessario eseguire un "take-over del dominio". Durante questo processo sarà necessario configurare se stessi come amministratore globale e modificare il tenant da non gestito a gestito.

Per una descrizione più dettagliata di questo processo,vedere le [guide rapide](https://www.microsoft.com/Licensing/existing-customer/business-center-training-and-resources.aspx). Scaricare la guida denominata *"installazione e uso dei servizi online"* che guiderà l'utente attraverso il passaggio a un dominio. Al termine dell'operazione, anche l'account di acquisto verrà associato al tenant.

> [!NOTE]
> Quando si completa il processo di completamento del dominio, è necessario rispettare i criteri dei cinque passaggi della sezione per l'associazione pre-tenant (gestita). Una volta soddisfatti i criteri, sarà necessario contattare il supporto MPSA per eseguire il provisioning di altri amministratori delle sottoscrizioni di Visual Studio.

## <a name="support-resources"></a>Risorse di supporto
- Per assistenza sull'amministrazione delle sottoscrizioni di Visual Studio, contattare il [supporto delle sottoscrizioni di Visual Studio](https://aka.ms/vsadminhelp).

## <a name="see-also"></a>Vedi anche
- [Documentazione di Visual Studio](/visualstudio/)
- [Documentazione di Azure DevOps](/azure/devops/)
- [Documentazione di Azure](/azure/)
- [Documentazione di Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Passaggi successivi
Altre informazioni sulla gestione delle sottoscrizioni di Visual Studio.
- [Assegna singole sottoscrizioni](assign-license.md)
- [Assegna più sottoscrizioni](assign-license-bulk.md)
- [Modificare sottoscrizioni](edit-license.md)
- [Eliminare sottoscrizioni](delete-license.md)
- [Determinare l'utilizzo massimo](maximum-usage.md)