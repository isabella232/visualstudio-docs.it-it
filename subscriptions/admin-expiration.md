---
title: Modifiche al portale di amministrazione per i contratti Visual Studio sottoscrizione scaduti | Microsoft Docs
author: evanwindom
ms.author: cabuschl
manager: cabuschl
ms.assetid: f38092ba-051c-4e58-97f5-4255dbe873ba
ms.date: 09/13/2021
ms.topic: conceptual
description: Informazioni su cosa accade agli amministratori alla scadenza di un contratto
ms.openlocfilehash: 719b05adb1c3aff4e981a051d547129f441e75c9
ms.sourcegitcommit: da19ed1e48259b219c61c4cb9e98b006004a5766
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/21/2021
ms.locfileid: "128053183"
---
# <a name="admin-portal-changes-for-expired-agreements"></a>Modifiche al portale di amministrazione per i contratti scaduti
Quando il contratto usato per acquistare Visual Studio scade, il contratto e le sottoscrizioni assegnate al suo interno rimarranno disponibili per un periodo di tempo limitato.  Questo periodo potrebbe non essere lo stesso per tutti i contratti e le informazioni più specifiche sulla durata di tale periodo verranno fornite nelle comunicazioni ricevute tramite posta elettronica e nel portale di amministrazione.  A seconda dei piani aziendali, potrebbe essere necessario intervenire per assistere i sottoscrittori o per evitare la perdita di informazioni importanti.

## <a name="expiration-timeline"></a>Sequenza temporale scadenza 
La sequenza temporale per la scadenza del contratto è costituita da tre fasi:
- [Prima della scadenza](#prior-to-expiration)
- [Scaduta](#expired)
- [Disabilitato](#disabled)

### <a name="prior-to-expiration"></a>Prima della scadenza
A partire da circa 120 giorni prima della scadenza del contratto, inizieremo a inviare notifiche agli amministratori e agli amministratori con privilegi di amministratore con privilegi aggiuntivi con informazioni sulla scadenza, nonché i passaggi che potrebbe essere necessario eseguire a seconda che l'azienda piani o meno di rinnovare il contratto. 

### <a name="expired"></a>Scaduto
Quando il contratto raggiunge la data di scadenza, gli amministratori e i sottoscrittori avranno comunque accesso per un periodo di tempo limitato.  Questa operazione viene eseguita per offrire all'azienda la possibilità di completare i processi di acquisto in corso e di fornire sia agli amministratori che ai sottoscrittori la possibilità di adottare le misure appropriate per conservare i dati importanti nel caso in cui l'azienda non rinnovi il contratto o sceva di acquistarne uno nuovo.  Gli amministratori continueranno a ricevere notifiche durante tale periodo con collegamenti a informazioni specifiche per conservare informazioni come gli elenchi di sottoscrittori per un uso futuro.  I sottoscrittori inizieranno anche a ricevere notifiche che forniscono indicazioni sulla conservazione delle informazioni, ad esempio eventuali asset creati nelle sottoscrizioni di Azure esistenti.  

Durante questa fase, sia gli amministratori che i sottoscrittori continueranno ad avere accesso ai rispettivi portali.  Gli amministratori potranno comunque eseguire l'intera gamma di attività di gestione delle sottoscrizioni.  I sottoscrittori continueranno ad avere accesso illimitato ai vantaggi della sottoscrizione.  

> [!IMPORTANT]
> Anche se gli amministratori e i sottoscrittori continueranno ad avere accesso alle rispettive risorse, è importante eseguire rapidamente un'azione in modo che i dati importanti siano preseved prima della scadenza di questo periodo e che l'accesso alle informazioni venga perso.

### <a name="disabled"></a>Disabled
Quando il contratto raggiunge la fine del periodo successivo alla scadenza:
- Gli amministratori e gli amministratori con privilegi super perderanno l'accesso ai contratti scaduti nel [portale di amministrazione.](https://manage.visualstudio.com)  Non saranno in grado di apportare modifiche alle sottoscrizioni all'interno del contratto.  L'accesso a qualsiasi altro contratto corrente nel portale di amministrazione rimarrà invariato.  Anche [l'accesso alla](https://manage.visualstudio.com.gethelp) pagina Ottieni guida continuerà a essere disponibile.
- I sottoscrittori perderanno l'accesso alla sottoscrizione scaduta nel portale [per i sottoscrittori.](https://my.visualstudio.com)  Se sono presenti altre sottoscrizioni assegnate come parte di un altro contratto, tali sottoscrizioni non saranno interessate. Dopo 30 giorni dalla disabilitazione di una sottoscrizione di Visual Studio, verranno rimosse anche tutte le sottoscrizioni di Azure che si basano sulla sottoscrizione Visual Studio, quindi è essenziale che i sottoscrittori spostino le risorse di Azure in un'altra sottoscrizione valida se vogliono conservarle.  Azure ha un proprio processo di notifica che consente di guidare i sottoscrittori in questo caso.  

## <a name="preserving-your-information"></a>Conservazione delle informazioni
Gli amministratori possono avere alcune informazioni che è possibile conservare se il contratto scade o si acquista un nuovo contratto. 
- Utilizzo massimo.  Conoscere il numero di sottoscrizioni assegnate durante la durata del contratto può aiutare l'organizzazione ad acquistare il numero giusto di sottoscrizioni per le proprie esigenze.  È possibile [visualizzare l'utilizzo ed esportare un report](maximum-usage.md) dal portale di amministrazione.  
- Elenco dei sottoscrittori.  [L'esportazione di un elenco dei sottoscrittori](exporting-subscriptions.md) nel contratto corrente consente di spostare rapidamente le sottoscrizioni in un nuovo contratto.  

## <a name="assisting-subscribers"></a>Assistenza ai sottoscrittori
Quando iniziano a ricevere notifiche sulla scadenza delle sottoscrizioni, i sottoscrittori possono contattare l'utente per domande.  Alcune delle risposte a queste domande dipenderanno naturalmente dal piano aziendale.  Se l'azienda prevede di rinnovare il contratto o di acquistarne uno nuovo, è possibile aiutare i sottoscrittori a capire dove si trova la società.  Se l'azienda non intende rinnovare, è possibile guidarli nel processo di salvataggio delle informazioni importanti.  Può risultare utile scoprire in che modo i singoli sottoscrittori saranno influenzati alla scadenza di un contratto. Per altre [informazioni, vedere l'articolo](subscription-expiration.md) Alla scadenza delle sottoscrizioni. 

## <a name="moving-to-a-new-agreement"></a>Passaggio a un nuovo contratto
Se l'azienda acquista un nuovo contratto, è possibile spostare i sottoscrittori [in](migrate-subscriptions.md) un nuovo contratto anziché ricrearli nel nuovo contratto.  

## <a name="next-steps"></a>Passaggi successivi
- Informazioni su [come i singoli sottoscrittori](subscription-expiration.md) sono influenzati dai contratti scaduti.
- Informazioni su come [esportare l'elenco di sottoscrittori](exporting-subscriptions.md).
- Informazioni su come [spostare le sottoscrizioni in un nuovo contratto](migrate-subscriptions.md)
- Informazioni su come [aggiungere sottoscrittori usando Azure Active Directory](assign-license-bulk.md#use-azure-active-directory-groups-to-assign-subscriptions) gruppi.