---
title: Anonimizzazione dei dati del sottoscrittore di Visual Studio | Microsoft Docs
author: evanwindom
ms.author: cabuschl
manager: cabuschl
ms.assetid: ce5fc8a4-484c-4df6-97c3-cb60174fb66b
ms.date: 03/11/2021
ms.topic: conceptual
description: Informazioni sull'anonimizzazione dei dati dei sottoscrittori quando viene perso l'accesso alle sottoscrizioni.
ms.openlocfilehash: 379875dbd7717d33f495f3d42a38facabdb11d81
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2021
ms.locfileid: "128428107"
---
# <a name="anonymization-of-visual-studio-subscriber-information"></a>Anonimizzazione dei dati del sottoscrittore di Visual Studio
Quando si verifica un evento che blocca l'uso di un sottoscrittore di una sottoscrizione, ad esempio la scadenza di una sottoscrizione o l'eliminazione dell'account di accesso di un sottoscrittore, le informazioni personali dell'utente, ad esempio il nome e l'account di accesso, vengono criptate per renderle inutilizzabili.  Questa operazione viene eseguita per proteggere le informazioni personali del sottoscrittore.

[!INCLUDE [GDPR-related guidance](includes/gdpr-intro-sentence.md)]

## <a name="when-does-anonymization-occur"></a>Quando si verifica l'anonimizzazione?
Gli eventi che rendono inutilizzabile una sottoscrizione per un sottoscrittore attivano l'anonimizzazione.  La rapidità con cui si verifica l'anonimizzazione dipende dal tipo di sottoscrizione e dall'evento di attivazione. Per altre informazioni, vedere la tabella seguente.

| Tipo di sottoscrizione                                                                                                                       | Evento di attivazione dell'anonimizzazione                                                                                                     | Quando si verifica l'anonimizzazione |
|-----------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|---------------------------|
| Visual Studio Dev Essentials                                                                                                            | Il sottoscrittore rifiuta esplicitamente il programma o non accetta le condizioni d'uso                                    | 30 giorni               |
| Sottoscrizioni di Visual Studio acquistate tramite Microsoft Store (retail)                                                                      | La sottoscrizione scade o non è attivata                                                                   | 360 giorni                  |
| Sottoscrizioni di Visual Studio acquistate tramite contratti multilicenza, Visual Studio Marketplace (sottoscrizioni cloud) o programmi, ad esempio MPN | La sottoscrizione scade o non è assegnata a un utente                                                          | 180 giorni                  |
| Tutte le sottoscrizioni                                                                                                                       | Un account di Azure Active Directory o un account Microsoft (MSA) usato per accedere alla sottoscrizione viene chiuso | Immediatamente               |
| Tutte le sottoscrizioni                                                                                                                       | Un sottoscrittore viene rimosso dal tenant associato all'account di Azure Active Directory                                | Immediatamente               |

## <a name="faq"></a>Domande frequenti
### <a name="q--does-the-anonymization-of-the-subscribers-personal-information-cause-them-to-lose-access-to-the-subscription"></a>D: L'anonimizzazione delle informazioni personali del sottoscrittore comporta la perdita dell'accesso alla sottoscrizione?
R: No.  L'anonimizzazione è la risposta a un evento che causa la perdita dell'accesso alla sottoscrizione ma non causa la mancanza di accesso.

### <a name="q--im-an-admin-for-my-organizations-subscriptions--if-one-of-my-subscribers-information-is-anonymized-can-that-subscription-be-reassigned-to-another-user"></a>D: Sono un amministratore per le sottoscrizioni dell'organizzazione.  Se le informazioni di un sottoscrittore vengono rese anonime, è possibile riassegnare la sottoscrizione a un altro utente?
R: sì.  È possibile riassegnare una sottoscrizione se vengono soddisfatti questi criteri:
- La sottoscrizione non è scaduta
- Sono trascorsi almeno 90 giorni dall'ultima assegnazione della sottoscrizione a un sottoscrittore.  Ad esempio, se una sottoscrizione è stata assegnata a un sottoscrittore il 1° giugno, non può essere riassegnato almeno fino al 30 agosto.

### <a name="q-how-can-i-prevent-anonymization-caused-by-deleting-a-sign-in-email-address"></a>D: Come è possibile impedire l'anonimizzazione causata dall'eliminazione di un indirizzo di posta elettronica di accesso?
A: Esistono due modi per evitare il problema:
- Distribuire un solo sistema di gestione delle identità, MSA o AAD, ma non entrambi.  
- Associare le identità AAD e MSA tramite il tenant. 

## <a name="support-resources"></a>Risorse di supporto
- Per assistenza su vendite, sottoscrizioni, account e fatturazione per Sottoscrizioni di Visual Studio, vedere supporto Visual Studio [sottoscrizioni](https://aka.ms/vssubscriberhelp).

## <a name="see-also"></a>Vedi anche
- [Visual Studio documentazione](/visualstudio/)
- [Documentazione di Azure DevOps](/azure/devops/)
- [Documentazione di Azure](/azure/)
- [Microsoft 365 documentazione](/microsoft-365/)

## <a name="next-steps"></a>Passaggi successivi
Informazioni su come impedire l'anonimizzazione associando le identità [msa e AAD.](/azure/active-directory/b2b/add-users-administrator)