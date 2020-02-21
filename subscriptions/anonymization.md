---
title: Anonimizzazione dei dati del sottoscrittore di Visual Studio | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 02/20/2020
ms.topic: conceptual
description: Informazioni sull'anonimizzazione dei dati dei sottoscrittori quando viene perso l'accesso alle sottoscrizioni.
ms.openlocfilehash: f3a35448dd0befbbb91f1657dd62b2b99ff37a2a
ms.sourcegitcommit: 3c105990656cd509062ce60e52e776c794f6305d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2020
ms.locfileid: "77520839"
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
R: no.  L'anonimizzazione è la risposta a un evento che causa la perdita dell'accesso alla sottoscrizione ma non causa la mancanza di accesso.

### <a name="q--im-an-administrator-for-my-organizations-subscriptions--if-one-of-my-subscribers-information-is-anonymized-can-that-subscription-be-reassigned-to-another-user"></a>Q: Sono amministratore delle sottoscrizioni dell'organizzazione.  Se le informazioni di un sottoscrittore vengono rese anonime, è possibile riassegnare la sottoscrizione a un altro utente?
A: Sì, a condizione che la sottoscrizione non sia scaduta, è possibile riassegnarla a un altro sottoscrittore.

### <a name="q-how-can-i-prevent-anonymization-caused-by-deleting-a-sign-in-email-address"></a>D: in che modo è possibile impedire la anonimato dei causata dall'eliminazione di un indirizzo di posta elettronica di accesso?
R: è possibile evitare il problema in due modi:
- Distribuire un solo sistema di gestione delle identità, MSA o AAD, ma non entrambi.  
- Associare le identità AAD e MSA tramite il tenant. 

## <a name="next-steps"></a>Passaggi successivi
Informazioni su come impedire anonimato dei [associando le identità di MSA e AAD](https://docs.microsoft.com/azure/active-directory/b2b/add-users-administrator).

## <a name="see-also"></a>Vedere anche
- [Documentazione di Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Documentazione di Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Documentazione di Azure](https://docs.microsoft.com/azure/)
- [Documentazione di Microsoft 365](https://docs.microsoft.com/microsoft-365/)
