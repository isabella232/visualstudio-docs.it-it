---
title: 'Procedura: impostare un percorso di File di Log personalizzato per gli errori di distribuzione ClickOnce | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- troubleshooting ClickOnce deployments
- ClickOnce deployment, troubleshooting
- ClickOnce deployment, error logging
ms.assetid: 77424414-7f0e-4b99-94bb-ea130de92d09
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 986311cc4b56880c6ce98cb649d5f4afc1f80b34
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56636528"
---
# <a name="how-to-set-a-custom-log-file-location-for-clickonce-deployment-errors"></a>Procedura: Impostare un percorso personalizzato per il file di log degli errori della distribuzione ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] mantiene i file di log di attivazione per tutte le distribuzioni. Questi log documentare eventuali errori di installazione e l'inizializzazione di un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione. Per impostazione predefinita, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] crea un file di log per l'attivazione ogni distribuzione. Archivia questi file di log nella cartella dei file Internet temporanei. Il file di log per una distribuzione viene visualizzato all'utente quando si verifica un errore di attivazione, l'utente fa clic **dettagli** nella finestra di dialogo di errore risultante.

 È possibile modificare questo comportamento per un client specifico utilizzando l'Editor del Registro di sistema (**regedit.exe**) per impostare un percorso di file di log personalizzato. In questo caso, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] i log di attivazione e non riusciti per tutte le distribuzioni in un singolo file.

> [!CAUTION]
>  Se si usa in modo non corretto dell'Editor del Registro di sistema, si può causare gravi problemi che potrebbero richiedere la reinstallazione del sistema operativo. L'uso dell'editor del Registro di sistema è a rischio e pericolo dell'utente.

> [!NOTE]
>  È necessario troncare o eliminare il file di log in alcuni casi per impedire che raggiunga dimensioni eccessivamente elevate.

 La procedura seguente descrive come impostare un percorso di file di log personalizzato per un singolo client.

### <a name="to-set-a-custom-log-file-location"></a>Per impostare un percorso di file di log personalizzato

1.  Aprire **Regedit.exe**.

2.  Passare al nodo `HKCU\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment`.

3.  Impostare il valore stringa `LogFilePath` per il percorso completo e il nome della propria località preferita log personalizzato.

     Questo percorso deve essere in una directory a cui l'utente ha accesso in scrittura. Ad esempio, in Windows Vista, creare la seguente struttura di cartelle e impostare `LogFilePath` al *C:\Users\\\<username > \Documents\Logs\ClickOnce\installation.log*.

## <a name="see-also"></a>Vedere anche
- [Risoluzione dei problemi relativi alle distribuzioni ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)