---
title: Concedere l'attendibilità ai documenti
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
ms.openlocfilehash: aba47e277b1c109bf4b0d03efb5694733f45760c
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "54871884"
---
# <a name="grant-trust-to-documents"></a>Concedere l'attendibilità ai documenti
  Un progetto a livello di documento presenta gli stessi requisiti di sicurezza dei progetti a livello di applicazione, ovvero la firma dei manifesti con un certificato o la risposta, tramite clic, a una richiesta di attendibilità. Inoltre, il documento o la cartella di lavoro si deve trovare in una directory definita come percorso attendibile.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="trusted-locations"></a>Percorsi attendibili  
 Le applicazioni in [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] e Office 2010 hanno il Centro protezione in cui gli utenti possono configurare le impostazioni di sicurezza e privacy, come i percorsi attendibili. Per le soluzioni Office, il computer locale è considerato un percorso attendibile. Tuttavia, a causa del rischio più elevato, alcune directory non possono mai essere considerate attendibili, come le cartelle temporanee del sistema, per ciascun utente e per Internet Explorer.  
  
 Per altre informazioni sul Centro protezione, vedere [sicurezza e criteri e impostazioni di Office 2010](http://go.microsoft.com/fwlink/?LinkId=89202). Per altre informazioni su come creare, gestire, rimuovere e configurare cartelle attendibili, vedere [configurare percorsi attendibili ed editori attendibili in Office system 2007](http://go.microsoft.com/fwlink/?LinkId=89203) e [creazione, rimozione o modifica un percorso per i file attendibile](https://support.office.com/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).  
  
## <a name="security-considerations-for-office-solutions"></a>Considerazioni sulla sicurezza per le soluzioni Office  
 Quando si determinano le cartelle da aggiungere ai percorsi attendibili, è necessario tenere in considerazione diversi aspetti relativi alla sicurezza:  
  
-   Le cartelle locali sono considerate più sicure e sono implicitamente attendibili. I percorsi remoti, ad esempio le condivisioni file, devono essere designati come percorsi attendibili.  
  
-   Quando si aggiunge una directory ai percorsi attendibili, questa azione concede l'attendibilità totale non solo alle soluzioni Office, ma anche al codice VBA e ActiveX. Per questo motivo, la directory radice e il *documenti* cartelle non devono essere designate come attendibili.  
  
-   Anche se il documento stesso è designato come attendibile mediante l'uso di percorsi attendibili, per rendere attendibile la personalizzazione sono necessarie ulteriori autorizzazioni. È possibile concedere attendibilità totale per la personalizzazione tramite i manifesti con un certificato di firma, la richiesta di attendibilità o installando la soluzione Office per i *Program Files* directory.  
  
-   È possibile archiviare il documento o la cartella di lavoro di una soluzione a livello di documento nella stessa directory dell'assembly o in una directory diversa. Ad esempio, il documento potrebbe trovarsi in un server SharePoint e l'assembly potrebbe essere in una condivisione file di rete. Per altre informazioni, vedere [Procedura: Pubblicare una soluzione Office a livello di documento in un server SharePoint tramite ClickOnce](https://msdn.microsoft.com/2408e809-fb78-42a1-9152-00afa1522e58).  
  
## <a name="see-also"></a>Vedere anche  
 [Concedere l'attendibilità alle soluzioni Office](../vsto/granting-trust-to-office-solutions.md)   
 [Risolvere i problemi di sicurezza delle soluzioni Office](../vsto/troubleshooting-office-solution-security.md)   
 [Proteggere le soluzioni Office](../vsto/securing-office-solutions.md)  
