---
title: Come automatizzare l'Sottoscrizioni di Visual Studio usando Azure Active Directory gruppi
author: esteban-herrera
ms.author: esherrer
manager: shve
ms.date: 07/22/2021
ms.topic: how-to
description: Informazioni su come gli amministratori possono assegnare e le sottoscrizioni usando Azure Active Directory gruppi
ms.openlocfilehash: de485170185049270d4819a418ea7d027b1a9d4b
ms.sourcegitcommit: 2694ab246eb857a1c607738a67198c46f826f106
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/30/2021
ms.locfileid: "114995361"
---
# <a name="how-to-automate-your-visual-studio-subscriptions-using-azure-active-directory-groups"></a>Come automatizzare l'Sottoscrizioni di Visual Studio usando Azure Active Directory gruppi

Questa guida illustra come sfruttare i Azure Active Directory (Azure AD) per creare un processo semplice e pratico per automatizzare e gestire Visual Studio sottoscrizioni.
Dopo aver assegnato un livello di sottoscrizione a un gruppo di Azure Active Directory, gli utenti potranno richiedere di partecipare a un gruppo di Azure Active Directory in base al livello di sottoscrizione necessario. Dopo l'approvazione per l'aggiunta al gruppo, verrà assegnata automaticamente la sottoscrizione corrispondente. Se vengono rimossi dal gruppo o dall'Azure Active Directory la sottoscrizione verrà rimossa automaticamente.

## <a name="requirements"></a>Requisiti
- L'organizzazione deve usare un Azure Active Directory tenent per la gestione delle identità.
- È necessario disporre dei diritti di amministratore e dell'accesso al [portale di amministrazione.](https://manage.visualstudio.com)
- È necessario avere il ruolo Amministratore globale o Amministratore ruoli con privilegi per la directory nell'interfaccia [Azure Active Directory di amministrazione](https://aad.portal.azure.com/).

## <a name="how-to"></a>Procedure
1.  Creare un Azure Active Directory per ogni livello di sottoscrizione che si prevede di usare 
    > [!NOTE]
    > Alcuni suggerimenti per la creazione del gruppo di Azure Active Directory:
    > - Aggiungere almeno un membro al gruppo.
    > - I membri devono essere tutti al livello superiore (non annidare altri gruppi).
    > - Incorporare il livello di sottoscrizione Azure Active Directory nome del gruppo, in modo da indicare chiaramente per quale scopo verrà usato il gruppo. 
    > - Tutti i membri del gruppo riceveranno il messaggio di Sottoscrizioni di Visual Studio messaggio di posta elettronica nella stessa lingua. Usare un gruppo diverso per ogni area per assicurarsi che i sottoscrittori ricevano questo messaggio di posta elettronica nella lingua preferita.
    > - Tutti i membri devono avere un indirizzo di posta elettronica associato al Azure Active Directory account.

2.  (Facoltativo) Configurare un modo per consentire agli utenti di richiedere l'aggiunta a un gruppo Sono disponibili più opzioni per questo scopo:
    1.  Creare un portale interno che sfrutta [l'API Azure Active Directory Graph per](https://docs.microsoft.com/graph/api/resources/groups-overview?view=graph-rest-1.0) gestire le appartenenze ai gruppi.
    2.  Usare il [portale self-help](https://docs.microsoft.com/azure/active-directory/enterprise-users/groups-self-service-management) tramite Pannello di accesso 
3.  Passare al portale [di amministrazione.](https://manage.visualstudio.com)
4.  Selezionare **Aggiungi** e **Azure Active Directory gruppo**
    > [!div class="mx-imgBorder"]
    > ![Screenshot del pulsante Aggiungi Azure Active Directory gruppo.](media/add-azure-ad-group.png "Fare clic sul pulsante Aggiungi e quindi Azure Active Directory gruppo")

5.  Nella diapositiva **Aggiungi gruppo** individuare il gruppo Azure Active Directory cui si desidera assegnare le sottoscrizioni. Assicurarsi che il livello di sottoscrizione sia corretto e completare gli altri campi prima di fare clic sul pulsante "Aggiungi".
    a.  Se ai membri del Azure Active Directory è già stata assegnata una sottoscrizione, verranno aggiornati per essere gestiti dal gruppo in futuro.\*
    > [!div class="mx-imgBorder"]
    > ![Screenshot del riquadro Azure Active Directory dettagli del gruppo.](media/azure-ad-group-details.png "Selezionare il gruppo e il livello di sottoscrizione da assegnare a tale gruppo")

6.  Ripetere il processo per ogni livello di sottoscrizione, se necessario, ad esempio creare un Azure Active Directory per Visual Studio Professional utenti e uno per Visual Studio Enterprise.
7.  L'operazione è stata completata. Quando gli utenti vengono aggiunti o rimossi dai Azure Active Directory, verranno assegnati o non assegnati automaticamente a una sottoscrizione e riceveranno una notifica tramite posta elettronica.

\*Se si gestisce già Sottoscrizioni di Visual Studio per un po' di tempo, è probabile che siano già presenti assegnazioni che si desidera aggiornare per usare Azure Active Directory gruppi. Questa operazione è stata resa più semplice. se si aggiunge un Azure Active Directory contenente utenti che hanno già sottoscrizioni, queste verranno raggruppate automaticamente nel gruppo di Azure Active Directory appena aggiunto al termine della prima sincronizzazione. Il sottoscrittore manterrà l'ID sottoscrizione e non si renderà conto che sono state modificate modifiche. Se vengono rimossi dal gruppo Azure Active Directory in futuro, la sottoscrizione verrà rimossa automaticamente. 

> [!NOTE]
>Se la singola sottoscrizione è per un livello di sottoscrizione diverso, le verrà data una sottoscrizione aggiuntiva per il nuovo livello. Esempio: se un utente ha una singola sottoscrizione Visual Studio Professional e è membro di un gruppo a cui si assegnano Visual Studio Enterprise le sottoscrizioni che ora avranno entrambe. 
