---
title: ClickOnce Panoramica della cache | Microsoft Docs
description: Informazioni sulla cache ClickOnce applicazione, che include le directory nascoste in un computer client in cui ClickOnce sono archiviate le applicazioni.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows applications, ClickOnce deployemtn
- ClickOnce applications, cache
- ClickOnce deployment, cache
ms.assetid: e379921e-9ef1-4326-bbf3-53ba67925526
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: c88c3e641869e9f58111fee28742d0ebeaafd9ab
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122051677"
---
# <a name="clickonce-cache-overview"></a>Panoramica della cache di ClickOnce
Tutte le applicazioni, indipendentemente dal fatto che siano installate in locale o ospitate online, vengono archiviate [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nel computer client in una cache [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] *dell'applicazione.* Una cache è una famiglia di directory nascoste nella directory Impostazioni locale della cartella Documents e Impostazioni [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dell'utente corrente. Questa cache contiene tutti i file dell'applicazione, inclusi gli assembly, i file di configurazione, le impostazioni dell'applicazione e dell'utente e la directory dei dati. La cache è anche responsabile della migrazione della directory dei dati dell'applicazione alla versione più recente. Per altre informazioni sulla migrazione dei dati, vedere [Accessing Local and Remote Data in ClickOnce Applications](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).

 Fornendo un'unica posizione per l'archiviazione delle applicazioni, assume l'attività di gestione dell'installazione fisica [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] di un'applicazione dall'utente. La cache consente anche di isolare le applicazioni mantenendo gli assembly e i file di dati per tutte le applicazioni e le relative versioni distinte separate l'una dall'altra. Ad esempio, quando si aggiorna un'applicazione, tale versione e le relative risorse dati vengono fornite con le [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] proprie directory nella cache.

## <a name="cache-storage-quota"></a>Quota di archiviazione nella cache
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Le applicazioni ospitate online sono limitate nella quantità di spazio che possono occupare da una quota che vincola le dimensioni della [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] cache. Le dimensioni della cache si applicano a tutte le applicazioni online dell'utente. Una singola applicazione online parzialmente attendibile è limitata a occupare metà dello spazio di quota. Le applicazioni installate non sono limitate dalle dimensioni della cache e non vengono conteggiati rispetto al limite della cache. Per tutte [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] le applicazioni, la cache mantiene solo la versione corrente e la versione installata in precedenza.

 Per impostazione predefinita, i computer client hanno 250 MB di spazio di archiviazione per le applicazioni [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] online. I file di dati non vengono conteggiati per questo limite. Un amministratore di sistema può ingrandire o ridurre questa quota in un determinato computer client modificando la chiave del Registro di sistemaHKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment\OnlineAppQuotaInKB, **ovvero** un valore DWORD che esprime le dimensioni della cache in kilobyte. Ad esempio, per ridurre le dimensioni della cache a 50 MB, modificare questo valore in 51200.

## <a name="see-also"></a>Vedi anche
- [Accedere a dati locali e remoti in applicazioni ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)