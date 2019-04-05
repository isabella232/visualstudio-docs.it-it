---
title: Panoramica della Cache di ClickOnce | Microsoft Docs
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
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58969321"
---
# <a name="clickonce-cache-overview"></a>Cenni preliminari sulla cache di ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tutti i [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] le applicazioni, se vengono installati in locale o ospitati online, vengono archiviate nel computer client in un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]application *cache*. Oggetto [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] cache è una famiglia di directory nascoste sotto la directory delle impostazioni locali della cartella documenti e le impostazioni dell'utente corrente. Questa cache contiene tutti i file dell'applicazione, tra cui l'assembly, i file di configurazione, applicazione e le impostazioni utente e directory dei dati. La cache è inoltre responsabile per la migrazione di directory dei dati dell'applicazione alla versione più recente. Per altre informazioni sulla migrazione dei dati, vedere [l'accesso ai dati locali e remoti in applicazioni ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).  
  
 Fornendo un'unica posizione per l'archiviazione dell'applicazione, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] subentra il compito di gestire l'installazione fisica di un'applicazione da parte dell'utente. La cache anche consente di isolare le applicazioni, mantenendo gli assembly e file di dati per tutte le applicazioni e le relative versioni separano uno da altro. Ad esempio, quando si aggiorna un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] un'applicazione, che vengono fornite versione e le relative risorse di dati con le proprie directory nella cache.  
  
## <a name="cache-storage-quota"></a>Quota di archiviazione della cache  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] le applicazioni ospitate in linea sono limitate nella quantità di spazio che possono occupare una quota che limita le dimensioni del [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] della cache. Le dimensioni della cache si applicano a tutte le applicazioni dell'utente online. una singola applicazione parzialmente attendibile, linea è limitata a che occupa la metà di questa quota. Le applicazioni installate non sono limitate dalla dimensione della cache e non vengono conteggiati rispetto al limite della cache. Per tutti i [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applicazioni, la cache mantiene solo la versione corrente e la versione precedentemente installata.  
  
 Per impostazione predefinita, i computer client sono pari a 250 MB di spazio di archiviazione online [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applicazioni. File di dati non vengono conteggiati per questo limite. Un amministratore di sistema è possibile ingrandire o ridurre la quota in un computer client specifico modificando la chiave del Registro di sistema, HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment\OnlineAppQuotaInKB, ovvero un valore DWORD che esprime la dimensione della cache in kilobyte. Ad esempio, per ridurre le dimensioni della cache a 50 MB, si sarebbe impostare questo valore su 51200.  
  
## <a name="see-also"></a>Vedere anche  
 [Accesso a dati locali e remoti in applicazioni ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)
