---
title: 'Errore: controllo di sicurezza non riuscito perché il servizio di amministrazione IIS non ha risposto | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.iis_not_responding
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f668de3d7c7e9a8bd075beb972199cf849feea65
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72737882"
---
# <a name="error-a-security-check-failed-because-the-iis-admin-service-did-not-respond"></a>Errore: controllo di sicurezza non riuscito. Il servizio di amministrazione IIS non ha risposto
Questo errore si verifica quando il servizio di amministrazione IIS non risponde. In questo modo viene indicato che l'installazione di IIS presenta un problema. Verificare innanzitutto che il servizio sia in esecuzione tramite lo strumento **Servizi** in **Strumenti di amministrazione**.

### <a name="to-correct-this-error"></a>Per correggere l'errore

- Reinstallare IIS tramite il pannello di controllo **Installazione applicazioni**.

- oppure

- Disinstallare IIS dal computer mediante Installazione applicazioni in Pannello di controllo. Se è stato disinstallato IIS ma si verificano ancora problemi, controllare il Registro di sistema e accertarsi che questa chiave non esista più:

    `HKEY_CLASSES_ROOT\CLSID\{A9E69610-B80D-11D0-B9B9-00A0C922E750}`

     oppure

- Disabilitare il servizio di amministrazione IIS tramite il pannello di controllo Strumenti di amministrazione. In questo modo il servizio IIS verrà disabilitato sul proprio computer.

     Dopo aver eseguito uno di questi tre passaggi, riavviare il computer.

     Per ulteriori informazioni, vedere la documentazione relativa al servizio IIS.

## <a name="see-also"></a>Vedere anche
- [Debug di applicazioni Web: errori e risoluzione dei problemi](../debugger/debugging-web-applications-errors-and-troubleshooting.md)