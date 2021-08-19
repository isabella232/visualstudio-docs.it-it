---
title: Impostare il percorso del file di log personalizzato (ClickOnce errori di distribuzione)
description: Informazioni sui file di log di attivazione ClickOnce per tutte le distribuzioni, che documenta gli errori per l'installazione e l'inizializzazione di una ClickOnce distribuzione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 94786783ebc4ccf849af122b7c334f9543f72435
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122073825"
---
# <a name="how-to-set-a-custom-log-file-location-for-clickonce-deployment-errors"></a>Procedura: Impostare un percorso personalizzato per il file di log degli errori della distribuzione ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] gestisce i file di log di attivazione per tutte le distribuzioni. Questi log documentano eventuali errori relativi all'installazione e all'inizializzazione di una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione. Per impostazione predefinita, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] crea un file di log per ogni attivazione della distribuzione. Archivia questi file di log nella cartella Dei file temporanei Internet. Il file di log per una distribuzione viene visualizzato all'utente quando si verifica un errore di attivazione e l'utente fa clic su **Dettagli** nella finestra di dialogo di errore risultante.

 È possibile modificare questo comportamento per un client specifico usando l'editor del Registro di sistema (regedit.exe)**per impostare** un percorso di file di log personalizzato. In questo caso, registra le operazioni riuscite e gli errori di attivazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] per tutte le distribuzioni in un singolo file.

> [!CAUTION]
> L'errato utilizzo dell'Editor del Registro di sistema può causare gravi problemi che possono richiedere la reinstallazione del sistema operativo. L'uso dell'editor del Registro di sistema è a rischio e pericolo dell'utente.

> [!NOTE]
> È necessario troncare o eliminare occasionalmente il file di log per evitare che le dimensioni del file aumentano troppo.

 Nella procedura seguente viene descritto come impostare un percorso di file di log personalizzato per un singolo client.

### <a name="to-set-a-custom-log-file-location"></a>Per impostare un percorso del file di log personalizzato

1. Aprire **Regedit.exe**.

2. Passare al nodo `HKCU\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment` .

3. Impostare il valore stringa `LogFilePath` sul percorso completo e sul nome file del percorso del log personalizzato preferito.

     Questo percorso deve essere in una directory a cui l'utente ha accesso in scrittura. Ad esempio, in Windows Vista creare la struttura di cartelle seguente e impostare `LogFilePath` su *C:\Users \\ \<username> \Documents\Logs\ClickOnce\installation.log*.

## <a name="see-also"></a>Vedi anche
- [Risoluzione dei problemi relativi alle distribuzioni ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)