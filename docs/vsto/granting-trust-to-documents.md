---
title: Concedi attendibilità ai documenti
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], trust
- inclusion lists [Office development in Visual Studio], about inclusion lists
- trust [Office development in Visual Studio], 2007 Office system
- granting trust [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9d245ddf00e4005b763bcd4437d3f8c18d05291e
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/28/2019
ms.locfileid: "72986034"
---
# <a name="grant-trust-to-documents"></a>Concedi attendibilità ai documenti
  Un progetto a livello di documento presenta gli stessi requisiti di sicurezza dei progetti a livello di applicazione, ovvero la firma dei manifesti con un certificato o la risposta, tramite clic, a una richiesta di attendibilità. Inoltre, il documento o la cartella di lavoro si deve trovare in una directory definita come percorso attendibile.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="trusted-locations"></a>Percorsi attendibili
 Le applicazioni in [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] e Office 2010 hanno centri di attendibilità in cui gli utenti possono configurare le impostazioni relative alla sicurezza e alla privacy, ad esempio posizioni attendibili. Per le soluzioni Office, il computer locale è considerato un percorso attendibile. Tuttavia, a causa del rischio più elevato, alcune directory non possono mai essere considerate attendibili, come le cartelle temporanee del sistema, per ciascun utente e per Internet Explorer.

 Per altre informazioni sul Centro protezione, vedere [sicurezza e criteri e impostazioni in Office 2010](/previous-versions/office/office-2010/cc178946(v=office.14)). Per ulteriori informazioni su come creare, gestire, rimuovere e configurare cartelle attendibili, vedere [configurare le impostazioni dei percorsi attendibili e degli autori attendibili nel sistema Office 2007](/previous-versions/office/office-2007-resource-kit/cc178948(v=office.12)) e [creare, rimuovere o modificare un percorso attendibile per i file](https://support.office.com/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).

## <a name="security-considerations-for-office-solutions"></a>Considerazioni sulla sicurezza per le soluzioni Office
 Quando si determinano le cartelle da aggiungere ai percorsi attendibili, è necessario tenere in considerazione diversi aspetti relativi alla sicurezza:

- Le cartelle locali sono considerate più sicure e sono implicitamente attendibili. I percorsi remoti, ad esempio le condivisioni file, devono essere designati come percorsi attendibili.

- Quando si aggiunge una directory ai percorsi attendibili, questa azione concede l'attendibilità totale non solo alle soluzioni Office, ma anche al codice VBA e ActiveX. Per questo motivo, la directory radice e le cartelle *documenti* non devono essere designate come attendibili.

- Anche se il documento stesso è designato come attendibile mediante l'uso di percorsi attendibili, per rendere attendibile la personalizzazione sono necessarie ulteriori autorizzazioni. È possibile concedere l'attendibilità totale alla personalizzazione usando la firma dei manifesti con un certificato, facendo clic sulla richiesta di attendibilità oppure installando la soluzione Office nella directory *programmi* .

- È possibile archiviare il documento o la cartella di lavoro di una soluzione a livello di documento nella stessa directory dell'assembly o in una directory diversa. Ad esempio, il documento potrebbe trovarsi in un server SharePoint e l'assembly potrebbe essere in una condivisione file di rete. Per altre informazioni, vedere [procedura: pubblicare una soluzione Office a livello di documento in un server SharePoint tramite ClickOnce](https://msdn.microsoft.com/2408e809-fb78-42a1-9152-00afa1522e58).

## <a name="see-also"></a>Vedere anche
- [Concedi attendibilità alle soluzioni Office](../vsto/granting-trust-to-office-solutions.md)
- [Risolvere i problemi relativi alla sicurezza delle soluzioni Office](../vsto/troubleshooting-office-solution-security.md)
- [Soluzioni Office sicure](../vsto/securing-office-solutions.md)
