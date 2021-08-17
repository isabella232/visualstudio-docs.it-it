---
title: Concedere l'attendibilità ai documenti
description: Informazioni su come un progetto a livello di documento ha gli stessi requisiti di sicurezza dei progetti a livello di applicazione, ad esempio la firma dei manifesti con un certificato o la richiesta di attendibilità.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: d34e4a45deaf08b9e8ddfa51873305bc847133b4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122026408"
---
# <a name="grant-trust-to-documents"></a>Concedere l'attendibilità ai documenti
  Un progetto a livello di documento presenta gli stessi requisiti di sicurezza dei progetti a livello di applicazione, ovvero la firma dei manifesti con un certificato o la risposta, tramite clic, a una richiesta di attendibilità. Inoltre, il documento o la cartella di lavoro si deve trovare in una directory definita come percorso attendibile.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="trusted-locations"></a>Percorsi attendibili
 Le applicazioni in e Office 2010 hanno Centri protezione in cui gli utenti possono configurare le impostazioni di [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] sicurezza e privacy, ad esempio i percorsi attendibili. Per le soluzioni Office, il computer locale è considerato un percorso attendibile. Tuttavia, a causa del rischio più elevato, alcune directory non possono mai essere considerate attendibili, come le cartelle temporanee del sistema, per ciascun utente e per Internet Explorer.

 Per altre informazioni sul Centro protezione, vedere Sicurezza e criteri e impostazioni [in Office 2010.](/previous-versions/office/office-2010/cc178946(v=office.14)) Per altre informazioni su come creare, gestire, rimuovere e configurare cartelle attendibili, vedere Configurare i percorsi attendibili e le impostazioni degli editori attendibili nel sistema [Office 2007](/previous-versions/office/office-2007-resource-kit/cc178948(v=office.12)) e [Creare,](https://support.office.com/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62)rimuovere o modificare un percorso attendibile per i file .

## <a name="security-considerations-for-office-solutions"></a>Considerazioni sulla sicurezza per Office soluzioni
 Quando si determinano le cartelle da aggiungere ai percorsi attendibili, è necessario tenere in considerazione diversi aspetti relativi alla sicurezza:

- Le cartelle locali sono considerate più sicure e sono implicitamente attendibili. I percorsi remoti, ad esempio le condivisioni file, devono essere designati come percorsi attendibili.

- Quando si aggiunge una directory ai percorsi attendibili, questa azione concede l'attendibilità totale non solo alle soluzioni Office, ma anche al codice VBA e ActiveX. Per questo motivo, la directory radice e le Documenti *non* devono essere designate come attendibili.

- Anche se il documento stesso è designato come attendibile mediante l'uso di percorsi attendibili, per rendere attendibile la personalizzazione sono necessarie ulteriori autorizzazioni. È possibile concedere l'attendibilità totale alla personalizzazione usando la firma dei manifesti con un certificato, facendo clic sulla richiesta di attendibilità o installando la soluzione Office nella *directory* Programmi.

- È possibile archiviare il documento o la cartella di lavoro di una soluzione a livello di documento nella stessa directory dell'assembly o in una directory diversa. Ad esempio, il documento potrebbe trovarsi in un server SharePoint e l'assembly potrebbe essere in una condivisione file di rete. Per altre informazioni, vedere [Procedura: Pubblicare](/previous-versions/bb608595(v=vs.110))una soluzione Office a livello di documento in un server SharePoint usando ClickOnce .

## <a name="see-also"></a>Vedi anche
- [Concedere l'attendibilità Office soluzioni](../vsto/granting-trust-to-office-solutions.md)
- [Risolvere i Office della soluzione](../vsto/troubleshooting-office-solution-security.md)
- [Soluzioni Office sicure](../vsto/securing-office-solutions.md)