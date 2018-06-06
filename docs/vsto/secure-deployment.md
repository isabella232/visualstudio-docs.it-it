---
title: Distribuzione sicura
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deploying applications [Office development in Visual Studio], security
- Office development in Visual Studio, security
- Office applications [Office development in Visual Studio], security
- ClickOnce deployment [Office development in Visual Studio], security
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 47cecda571a6826c2d7e845945c05d0264971134
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34693331"
---
# <a name="secure-deployment"></a>Distribuzione sicura
  Quando si crea una soluzione Office, il computer di sviluppo viene aggiornato automaticamente per consentire al codice nel progetto per l'esecuzione. Tuttavia, quando si distribuisce la soluzione, è necessario fornire l'evidenza sulla quale basare una decisione di attendibilità della soluzione con un certificato di firma o utilizzando il [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] chiave di richiesta di attendibilità. Per altre informazioni, vedere [concedere l'attendibilità alle soluzioni Office](../vsto/granting-trust-to-office-solutions.md).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Per le personalizzazioni a livello di documento, se si distribuisce il documento in un percorso di rete, è necessario anche aggiungere il percorso del documento all'elenco di percorsi attendibili nel Centro protezione dell'applicazione di Office. Per ulteriori informazioni su come impostare le autorizzazioni di documento per utente finale computer, vedere [concedere l'attendibilità a documenti](../vsto/granting-trust-to-documents.md).  
  
## <a name="prevent-office-solutions-from-running-code"></a>Impedire l'esecuzione del codice di soluzioni Office  
 Gli amministratori possono utilizzare il Registro di sistema per impedire l'esecuzione in un computer di tutte le soluzioni Office. Quando una soluzione Office che Usa estensioni di codice gestito viene aperto, Visual Studio Tools per i controlli di runtime di Office se una voce con il nome `Disabled` esiste in una delle seguenti chiavi del Registro di sistema nel computer:  
  
-   **HKEY_CURRENT_USER\Software\Microsoft\VSTO**  
  
-   **HKEY_LOCAL_MACHINE\Software\Microsoft\VSTO**  
  
 Per impedire l'esecuzione del codice di soluzioni Office, creare un `Disabled` voce in una o entrambe queste chiavi del Registro di sistema e specificare uno dei seguenti tipi di dati e i valori per `Disabled`:  
  
-   REG_SZ o REG_EXPAND_SZ impostato su qualsiasi stringa diversa da "0" (zero).  
  
-   REG_DWORD che è impostato su qualsiasi valore diverso da 0 (zero).  
  
 Per abilitare l'esecuzione di codice delle soluzioni Office, impostare entrambe le `Disabled` voci su 0 (zero), o eliminare le voci del Registro di sistema.  
  
## <a name="see-also"></a>Vedere anche  
 [Distribuire una soluzione Office](../vsto/deploying-an-office-solution.md)   
 [Preparazione dei computer per eseguire o ospitare soluzioni Office](http://msdn.microsoft.com/en-us/be1b173f-7261-4d74-aa4e-94ccd43db8d8)   
 [Proteggere le soluzioni Office](../vsto/securing-office-solutions.md)  
  
  