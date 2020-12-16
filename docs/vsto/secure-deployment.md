---
title: Distribuzione sicura
description: Viene illustrato come è necessario fornire l'evidenza su cui basare una decisione di attendibilità firmando la soluzione con un certificato o utilizzando la chiave di richiesta di attendibilità ClickOnce.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deploying applications [Office development in Visual Studio], security
- Office development in Visual Studio, security
- Office applications [Office development in Visual Studio], security
- ClickOnce deployment [Office development in Visual Studio], security
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b47a18aa3e791d446abc2a57b6aad1f139924ebf
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528473"
---
# <a name="secure-deployment"></a>Distribuzione sicura
  Quando si crea una soluzione Office, il computer di sviluppo viene aggiornato automaticamente per consentire l'esecuzione del codice nel progetto. Tuttavia, quando si distribuisce la soluzione, è necessario fornire l'evidenza su quale basare una decisione di attendibilità firmando la soluzione con un certificato o usando la [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] chiave della richiesta di attendibilità. Per altre informazioni, vedere [concedere l'attendibilità alle soluzioni Office](../vsto/granting-trust-to-office-solutions.md).

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Per le personalizzazioni a livello di documento, se si distribuisce il documento in un percorso di rete, è necessario aggiungere anche il percorso del documento all'elenco di percorsi attendibili nel centro protezione dell'applicazione di Office. Per ulteriori informazioni sull'impostazione delle autorizzazioni per i documenti nei computer degli utenti finali, vedere [Grant trust to Documents](../vsto/granting-trust-to-documents.md).

## <a name="prevent-office-solutions-from-running-code"></a>Impedisci alle soluzioni Office di eseguire codice
 Gli amministratori possono usare il registro di sistema per impedire l'esecuzione di tutte le soluzioni Office in un computer. Quando viene aperta una soluzione Office con estensioni di codice gestito, il Strumenti di Visual Studio per Office Runtime controlla se esiste una voce con il nome `Disabled` in una delle seguenti chiavi del registro di sistema nel computer:

- **HKEY_CURRENT_USER\Software\Microsoft\VSTO**

- **HKEY_LOCAL_MACHINE\Software\Microsoft\VSTO**

  Per impedire l'esecuzione di codice per le soluzioni Office, creare una `Disabled` voce in una o entrambe le chiavi del registro di sistema e specificare uno dei tipi di dati e i valori seguenti per `Disabled` :

- REG_SZ o REG_EXPAND_SZ impostato su una stringa diversa da "0" (zero).

- REG_DWORD impostato su un valore diverso da 0 (zero).

  Per consentire alle soluzioni Office di eseguire codice, impostare entrambe le `Disabled` voci su 0 (zero) o eliminare le voci del registro di sistema.

## <a name="see-also"></a>Vedere anche
- [Distribuire una soluzione Office](../vsto/deploying-an-office-solution.md)
- [Preparare i computer per l'esecuzione o l'hosting di soluzioni Office](/previous-versions/bb772092(v=vs.110))
- [Soluzioni Office sicure](../vsto/securing-office-solutions.md)