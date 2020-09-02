---
title: Panoramica della cache ClickOnce | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
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
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 58ea758ea10e2c58ff123a2bc991f14191db0aa1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68151658"
---
# <a name="clickonce-cache-overview"></a>Cenni preliminari sulla cache di ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tutte [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] le applicazioni, indipendentemente dal fatto che siano installate localmente o ospitate online, vengono archiviate nel computer client in una [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] *cache*di applicazione. Una [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] cache è una famiglia di directory nascoste nella directory impostazioni locali della cartella documenti e impostazioni dell'utente corrente. Questa cache include tutti i file dell'applicazione, inclusi gli assembly, i file di configurazione, le impostazioni dell'applicazione e dell'utente e la directory dei dati. La cache è anche responsabile della migrazione della directory dei dati dell'applicazione alla versione più recente. Per ulteriori informazioni sulla migrazione dei dati, vedere [accesso a dati locali e remoti in applicazioni ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).  
  
 Fornendo un'unica posizione per l'archiviazione delle applicazioni, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] acquisisce l'attività di gestione dell'installazione fisica di un'applicazione da parte dell'utente. La cache consente inoltre di isolare le applicazioni mantenendo gli assembly e i file di dati per tutte le applicazioni e le relative versioni distinte separate l'una dall'altra. Ad esempio, quando si aggiorna un' [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applicazione, la versione e le relative risorse dati vengono fornite con le rispettive directory nella cache.  
  
## <a name="cache-storage-quota"></a>Quota di archiviazione della cache  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] le applicazioni ospitate online sono limitate dalla quantità di spazio che possono essere occupate da una quota che vincola le dimensioni della [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] cache. Le dimensioni della cache si applicano a tutte le applicazioni online dell'utente; una singola applicazione online parzialmente attendibile è limitata a occupare metà dello spazio delle quote. Le applicazioni installate non sono limitate dalle dimensioni della cache e non vengono conteggiate rispetto al limite della cache. Per tutte le [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applicazioni, la cache mantiene solo la versione corrente e la versione installata in precedenza.  
  
 Per impostazione predefinita, i computer client hanno 250 MB di spazio di archiviazione per [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] le applicazioni online. I file di dati non vengono conteggiati per questo limite. Un amministratore di sistema può ingrandire o ridurre la quota in un particolare computer client modificando la chiave del registro di sistema, HKEY_CURRENT_USER \Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment\OnlineAppQuotaInKB, che è un valore DWORD che esprime la dimensione della cache in kilobyte. Ad esempio, per ridurre le dimensioni della cache a 50 MB, è necessario impostare questo valore su 51200.  
  
## <a name="see-also"></a>Vedere anche  
 [Accesso a dati locali e remoti in applicazioni ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)
