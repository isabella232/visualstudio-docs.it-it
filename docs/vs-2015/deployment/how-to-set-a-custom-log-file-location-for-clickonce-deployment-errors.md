---
title: 'Procedura: impostare un percorso di File di Log personalizzato per gli errori di distribuzione ClickOnce | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- troubleshooting ClickOnce deployments
- ClickOnce deployment, troubleshooting
- ClickOnce deployment, error logging
ms.assetid: 77424414-7f0e-4b99-94bb-ea130de92d09
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 9f061037b6349838b145627125527f64b68a2856
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47519686"
---
# <a name="how-to-set-a-custom-log-file-location-for-clickonce-deployment-errors"></a>Procedura: impostare un percorso personalizzato per il file di log degli errori della distribuzione ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [procedura: impostare un percorso di File di Log personalizzato per gli errori di distribuzione ClickOnce](https://docs.microsoft.com/visualstudio/deployment/how-to-set-a-custom-log-file-location-for-clickonce-deployment-errors).  
  
[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] mantiene i file di log di attivazione per tutte le distribuzioni. Questi log documentare eventuali errori di installazione e l'inizializzazione di un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] distribuzione. Per impostazione predefinita, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] crea un file di log per l'attivazione ogni distribuzione. Archivia questi file di log nella cartella dei file Internet temporanei. Il file di log per una distribuzione viene visualizzato all'utente quando si verifica un errore di attivazione, l'utente fa clic **dettagli** nella finestra di dialogo di errore risultante.  
  
 È possibile modificare questo comportamento per un client specifico utilizzando l'Editor del Registro di sistema (**regedit.exe**) per impostare un percorso di file di log personalizzato. In questo caso, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] i log di attivazione e non riusciti per tutte le distribuzioni in un singolo file.  
  
> [!CAUTION]
>  Se si usa in modo non corretto dell'Editor del Registro di sistema, si può causare gravi problemi che potrebbero richiedere la reinstallazione del sistema operativo. L'uso dell'editor del Registro di sistema è a rischio e pericolo dell'utente.  
  
> [!NOTE]
>  È necessario troncare o eliminare il file di log in alcuni casi per impedire che raggiunga dimensioni eccessivamente elevate.  
  
 La procedura seguente descrive come impostare un percorso di file di log personalizzato per un singolo client.  
  
### <a name="to-set-a-custom-log-file-location"></a>Per impostare un percorso di file di log personalizzato  
  
1.  Aprire **Regedit.exe**.  
  
2.  Passare al nodo `HKCU\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment`.  
  
3.  Impostare il valore stringa `LogFilePath` per il percorso completo e il nome della propria località preferita log personalizzato.  
  
     Questo percorso deve essere in una directory a cui l'utente ha accesso in scrittura. Ad esempio, in Windows Vista, creare la seguente struttura di cartelle e impostare `LogFilePath` a C:\Users\\< nome utente\>\Documents\Logs\ClickOnce\installation.log.  
  
## <a name="see-also"></a>Vedere anche  
 [Risoluzione dei problemi relativi alle distribuzioni ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)





