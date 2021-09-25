---
title: Accesso alle sottoscrizioni Visual Studio con l'account GitHub | Microsoft Docs
author: evanwindom
ms.author: cabuschl
manager: cabuschl
ms.assetid: 1bdcb3c9-bba1-4e25-a609-9d7e539d78e0
ms.date: 03/08/2021
ms.topic: conceptual
description: Informazioni su come accedere alle sottoscrizioni di Visual Studio con l'account GitHub.
ms.openlocfilehash: d57eb9c68a21fd7e68eda23efa3b194f8f0fb203
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2021
ms.locfileid: "128428249"
---
# <a name="signing-in-to-visual-studio-subscriptions-with-your-github-account"></a>Accesso alle sottoscrizioni di Visual Studio con l'account GitHub 
La procedura per accedere alla sottoscrizione di Visual Studio dipende dal tipo di account usato. Ad esempio, si potrebbe usare un account Microsoft (MSA) o un indirizzo di posta elettronica fornito dal datore di lavoro o dell'istituto di istruzione. A partire da gennaio 2019 è possibile usare anche il proprio account GitHub per accedere ad alcune sottoscrizioni. 

Questo articolo illustra la procedura per l'accesso con l'account GitHub.

## <a name="signing-in-with-your-github-account"></a>Accesso con l'account GitHub

Il supporto delle identità GitHub consente di usare un account di GitHub esistente come credenziali per un account Microsoft nuovo o esistente, collegando l'account GitHub con l'account Microsoft. 

Quando si esegue l'accesso con GitHub, Microsoft verifica se un indirizzo e-mail associato all'account GitHub corrisponde a un account Microsoft personale o aziendale. Se l'indirizzo corrisponde all'account aziendale dell'utente, verrà richiesto di accedere a tale account. Se l'indirizzo corrisponde a un account personale, l'account GitHub verrà aggiunto come metodo di accesso all'account personale.

Dopo aver collegare le credenziali GitHub e account Microsoft, è possibile usare tale accesso Single Sign-In ovunque sia possibile usare un account Microsoft personale, ad esempio nei siti di Azure, nelle app Office e xbox. Questi account possono essere usati anche per gli Azure Active Directory guest come account Microsoft, presupponendo che l'indirizzo di posta elettronica corrisponda a quello dell'invito.

> [!NOTE]
> Il collegamento di un'identità di GitHub a un account Microsoft non consente a Microsoft nessun accesso al codice. Quando le app come Azure DevOps e Visual Studio richiedono l'accesso ai repository di codice, verrà richiesto all'utente il consenso specifico per tale accesso. 

### <a name="frequently-asked-questions"></a>Domande frequenti
Le domande frequenti che seguono riguardano aspetti relativi all'uso delle credenziali dell'account GitHub per l'accesso alle sottoscrizioni di Visual Studio.

#### <a name="q-i-forgot-my-github-password--how-can-i-access-my-account-now"></a>D: Ho dimenticato la password GitHub password.  Come posso accedere al mio account?
A: È possibile ripristinare l'account GitHub selezionando [Reimposta la password](https://github.com/password_reset). In alternativa è possibile recuperare l'account Microsoft collegato a GitHub immettendo l'indirizzo di posta elettronica dell'account GitHub in [Recupera il tuo account](https://account.live.com/password/reset).

#### <a name="q-i-deleted-my-github-account--how-can-i-access-my-microsoft-account-msa-now"></a>D: L'account GitHub è stato eliminato.  Come posso accedere al mio account Microsoft (account del servizio gestito)?
A: Se non si hanno altre credenziali nell'account del servizio app, ad esempio una password, un'app Authenticator o una chiave di sicurezza, è possibile recuperare il account Microsoft usando l'indirizzo di posta elettronica allegato. Per iniziare, passare a [Recupera il tuo account](https://account.live.com/password/reset). È necessario aggiungere una password per l'account, che potrà essere usata per gli accessi successivi. 

#### <a name="q-theres-no-sign-in-with-github-option-on-the-sign-in-page--how-can-i-use-my-github-credentials-to-sign-in"></a>D: Non è disponibile l'opzione "Accedi con GitHub" nella pagina di accesso.  Come è possibile usare le credenziali di GitHub per l'accesso?
A: Digitare l'GitHub di posta elettronica dell'account selezionato al momento della creazione GitHub collegata account Microsoft. Si verrà trasferiti a GitHub per l'accesso. In alternativa, se nella pagina è presente un collegamento Opzioni di accesso usare il pulsante **Accedi con GitHub** visualizzato dopo aver fatto clic su tale collegamento. 

#### <a name="q-i-cant-sign-in-to-some-of-my-apps-and-products-with-github--why"></a>D: Non è possibile accedere ad alcune app e prodotti con GitHub.  Perché?
A: Non tutti i prodotti Microsoft possono accedere a GitHub.com dalla pagina di accesso, ad esempio le console Xbox. Quando si digita l'indirizzo e-mail dell'account GitHub collegato, Microsoft invia un codice a tale indirizzo per verificare l'identità del mittente. L'utente continua ad accedere allo stesso account, ma con un altro metodo di accesso. 

#### <a name="q--ive-added-a-password-to-the-microsoft-account-i-have-linked-to-my-github-account--will-that-cause-a-problem"></a>D: È stata aggiunta una password al account Microsoft collegato all'account GitHub personale.  Può rappresentare un problema?
A: Per niente. Questo non modifica la password di GitHub, è semplicemente disponibile un altro modo per accedere all'account Microsoft. Ogni volta che si accede usando l'indirizzo e-mail, sarà possibile scegliere se accedere con la password dell'account Microsoft o andare a GitHub per l'accesso. Se è necessario aggiungere una password, è consigliabile che sia diversa dalla password per l'account GitHub.

#### <a name="q-i-want-to-add-the-authenticator-app-to-the-account-i-created-using-github--can-i-do-that"></a>D: Si vuole aggiungere l'app Authenticator all'account creato usando GitHub.  È possibile procedere in questo modo?
A: Nessun problema: è sufficiente scaricare l'app e accedere usando l'indirizzo di posta elettronica. Quando si accede con l'indirizzo di posta elettronica viene richiesto di scegliere come credenziali l'[app Authenticator](https://www.microsoft.com/p/microsoft-authenticator/9nblgggzmcj6) o GitHub.

#### <a name="q-ive-enabled-two-factor-authentication-on-both-my-github-and-microsoft-accounts-msa-but-when-i-sign-in-to-my-msa-im-still-asked-to-authenticate-twice--why"></a>D: L'autenticazione a due fattori è stata abilitata sia per gli account GitHub che per gli account Microsoft, ma quando si accede all'account msa, viene comunque richiesto di eseguire l'autenticazione due volte.  Perché?
A causa delle restrizioni di sicurezza, Microsoft conta l'accesso con GitHub come verifica a fattore singolo, anche se è abilitata la verifica in due passaggi. Pertanto, è necessario eseguire nuovamente l'autenticazione per l'account Microsoft. 

#### <a name="q--how-can-i-tell-if-my-microsoft-account-and-github-accounts-are-linked"></a>D: Come è possibile determinare se gli account account Microsoft e GitHub sono collegati?
A: Ogni volta che si effettua l'accesso usando l'alias dell'account (indirizzo di posta elettronica, numero di telefono, Skype nome), verranno visualizzati tutti i metodi di accesso per l'account. Se GitHub non è visualizzato fra tali metodi, non è stato ancora configurato.

#### <a name="q--how-can-i-unlink-my-microsoft-and-github-accounts"></a>D: Come è possibile scollegare gli account Microsoft e GitHub personali? 
A: Passare al scheda Sicurezza [di](https://account.microsoft.com/security) account.microsoft.com e fare clic su Opzioni di sicurezza **avanzate** per scollegare l'account GitHub locale. Quando viene scollegato, l'account GitHub viene rimosso come metodo di accesso e viene anche rimosso l'accesso a qualsiasi repository GitHub in Visual Studio. Altri prodotti Microsoft potrebbero avere richiesto l'accesso all'account GitHub separatamente. Pertanto la rimozione dell'accesso in questa posizione non rimuoverà l'accesso in tutti i prodotti. Andare alla pagina delle [autorizzazioni applicazione](https://github.com/settings/applications) del profilo GitHub per revocare il consenso alle app elencate in tale pagina.

#### <a name="q--i-try-to-use-my-github-account-to-sign-in-but-im-prompted-that-i-already-have-a-microsoft-identity-that-i-should-use-instead--whats-happening"></a>D: Si prova a usare l'account GitHub per accedere, ma viene richiesto di avere già un'identità Microsoft da usare.  Qual è il problema?
A: Se si ha un indirizzo Azure Active Directory di posta elettronica nell'account GitHub, è già presente un'identità Microsoft in grado di accedere ad Azure ed eseguire pipeline CI usando il codice GitHub codice. L'uso di tale account garantisce che le risorse di Azure e le pipeline di compilazione restino entro i limiti dell'organizzazione. Se tuttavia si stanno eseguendo attività a titolo personale, è consigliabile inserire un indirizzo di posta elettronica personale nell'account GitHub, in modo da potere sempre accedere all'account stesso. Dopo aver eseguito questa operazione, provare a eseguire nuovamente l'accesso e scegliere **Usa un indirizzo e-mail diverso** quando viene chiesto di accedere al proprio account aziendale o dell'istituto di istruzione. In questo modo è possibile creare un nuovo account Microsoft con tale indirizzo di posta elettronica personale.

## <a name="resources"></a>Risorse
- Per assistenza su vendite, sottoscrizioni, account e fatturazione per Sottoscrizioni di Visual Studio, vedere supporto Visual Studio [sottoscrizioni](https://aka.ms/vssubscriberhelp).

## <a name="see-also"></a>Vedi anche
- [Visual Studio documentazione](/visualstudio/)
- [Documentazione di Azure DevOps](/azure/devops/)
- [Documentazione di Azure](/azure/)
- [Microsoft 365 documentazione](/microsoft-365/)

## <a name="next-steps"></a>Passaggi successivi
Dopo aver eseguito l'accesso al portale delle sottoscrizioni, è consigliabile visitare la pagina relativa ai vantaggi all'indirizzo https://my.visualstudio.com/benefits per conoscere gli strumenti, i servizi e le offerte disponibili.