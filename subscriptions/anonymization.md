---
title: Anonimizzazione dei dati del sottoscrittore di Visual Studio | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 10/31/2018
ms.topic: conceptual
description: Informazioni sull'anonimizzazione dei dati dei sottoscrittori quando viene perso l'accesso alle sottoscrizioni.
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: 4570ff43f946c25c50d298e22de3b0c8a261f870
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51811251"
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

## <a name="next-steps"></a>Passaggi successivi

Scoprire come impedire l'anonimizzazione [collegando le identità MSA e AAD](/azure/active-directory/b2b/add-users-administrator).