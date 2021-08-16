---
title: Distribuzione sicura
description: Informazioni su come fornire l'evidenza su cui basare una decisione di attendibilità firmando la soluzione con un certificato o usando la chiave ClickOnce di richiesta di attendibilità.
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 22efe77715cf157a7dba84cb9bd348c7e49859e1ce8e8b3ed113cca7e4a03e3e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121408110"
---
# <a name="secure-deployment"></a>Distribuzione sicura
  Quando si crea una soluzione Office, il computer di sviluppo viene aggiornato automaticamente per consentire l'esecuzione del codice nel progetto. Tuttavia, quando si distribuisce la soluzione, è necessario fornire l'evidenza su cui basare una decisione di attendibilità firmando la soluzione con un certificato o usando la chiave di richiesta [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] di attendibilità. Per altre informazioni, vedere [Concedere l'attendibilità Office soluzioni](../vsto/granting-trust-to-office-solutions.md).

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Per le personalizzazioni a livello di documento, se si distribuisce il documento in un percorso di rete, è necessario aggiungere anche il percorso del documento all'elenco di percorsi attendibili nel Centro protezione dell'applicazione Office documento. Per altre informazioni su come impostare le autorizzazioni per i documenti nei computer degli utenti finali, vedere [Concedere l'attendibilità ai documenti](../vsto/granting-trust-to-documents.md).

## <a name="prevent-office-solutions-from-running-code"></a>Impedire Office soluzioni di esecuzione del codice
 Gli amministratori possono usare il Registro di sistema per impedire Office tutte le soluzioni in esecuzione in un computer. Quando viene aperta una soluzione Office con estensioni di codice gestito, il runtime di Visual Studio Tools per Office verifica se una voce con il nome esiste in una delle chiavi del Registro di sistema `Disabled` seguenti nel computer:

- **HKEY_CURRENT_USER\Software\Microsoft\VSTO**

- **HKEY_LOCAL_MACHINE\Software\Microsoft\VSTO**

  Per impedire alle Office di eseguire codice, creare una voce in una o entrambe le chiavi del Registro di sistema e specificare uno dei tipi di dati e dei valori `Disabled` seguenti per `Disabled` :

- Oggetto REG_SZ o REG_EXPAND_SZ impostato su qualsiasi stringa diversa da "0" (zero).

- Oggetto REG_DWORD impostato su qualsiasi valore diverso da 0 (zero).

  Per consentire Office di eseguire codice, impostare entrambe le voci su `Disabled` 0 (zero) o eliminare le voci del Registro di sistema.

## <a name="see-also"></a>Vedi anche
- [Distribuire una soluzione Office distribuzione](../vsto/deploying-an-office-solution.md)
- [Preparare i computer per l'esecuzione o ospitare Office soluzioni](/previous-versions/bb772092(v=vs.110))
- [Soluzioni Office sicure](../vsto/securing-office-solutions.md)