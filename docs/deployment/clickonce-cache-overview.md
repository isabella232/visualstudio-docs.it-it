---
title: Panoramica della cache ClickOnce | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3d7abeeec4a640119e3089c795ac529a10f8dc09
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2020
ms.locfileid: "84182625"
---
# <a name="clickonce-cache-overview"></a>Panoramica della cache di ClickOnce
Tutte [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] le applicazioni, indipendentemente dal fatto che siano installate localmente o ospitate online, vengono archiviate nel computer client in una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] *cache*di applicazione. Una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] cache è una famiglia di directory nascoste nella directory impostazioni locali della cartella documenti e impostazioni dell'utente corrente. Questa cache include tutti i file dell'applicazione, inclusi gli assembly, i file di configurazione, le impostazioni dell'applicazione e dell'utente e la directory dei dati. La cache è anche responsabile della migrazione della directory dei dati dell'applicazione alla versione più recente. Per ulteriori informazioni sulla migrazione dei dati, vedere [accesso a dati locali e remoti in applicazioni ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).

 Fornendo un'unica posizione per l'archiviazione delle applicazioni, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] acquisisce l'attività di gestione dell'installazione fisica di un'applicazione da parte dell'utente. La cache consente inoltre di isolare le applicazioni mantenendo gli assembly e i file di dati per tutte le applicazioni e le relative versioni distinte separate l'una dall'altra. Ad esempio, quando si aggiorna un' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione, la versione e le relative risorse dati vengono fornite con le rispettive directory nella cache.

## <a name="cache-storage-quota"></a>Quota di archiviazione della cache
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]le applicazioni ospitate online sono limitate dalla quantità di spazio che possono essere occupate da una quota che vincola le dimensioni della [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] cache. Le dimensioni della cache si applicano a tutte le applicazioni online dell'utente; una singola applicazione online parzialmente attendibile è limitata a occupare metà dello spazio delle quote. Le applicazioni installate non sono limitate dalle dimensioni della cache e non vengono conteggiate rispetto al limite della cache. Per tutte le [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazioni, la cache mantiene solo la versione corrente e la versione installata in precedenza.

 Per impostazione predefinita, i computer client hanno 250 MB di spazio di archiviazione per [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] le applicazioni online. I file di dati non vengono conteggiati per questo limite. Un amministratore di sistema può ingrandire o ridurre la quota in un particolare computer client modificando la chiave del registro di sistema, **HKEY_CURRENT_USER \software\classes\software\microsoft\windows\currentversion\deployment\onlineappquotainkb**, che è un valore DWORD che esprime la dimensione della cache in kilobyte. Ad esempio, per ridurre le dimensioni della cache a 50 MB, è necessario impostare questo valore su 51200.

## <a name="see-also"></a>Vedere anche
- [Accedere a dati locali e remoti in applicazioni ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)