---
title: Informazioni di riferimento sulle API non gestite ClickOnce | Microsoft Docs
description: Informazioni sulle API pubbliche ClickOnce non gestite da dfshim.dll, tra cui CleanOnlineAppCache, GetDeploymentDataFromManifest e LaunchApplication.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
api_name:
- CleanOnlineAppCache
- GetDeploymentDataFromManifest
- LaunchApplication
api_location:
- dfshim.dll
api_type:
- COM
topic_type:
- apiref
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- LaunchApplication [ClickOnce unmanaged]
- ClickOnce, unmanaged APIs
- CleanOnlineAppCache [ClickOnce unmanaged]
- CleanOnlineAppCacheW interface [ClickOnce unmanaged]
- GetDeploymentDataFromManifest [ClickOnce unmanaged]
ms.assetid: ec002138-4054-456d-bcc1-79ac2f4a4fd7
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: 88d8147dded05c6bec54682e76c6a8c1826b43e0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900795"
---
# <a name="clickonce-unmanaged-api-reference"></a>Riferimenti alle API non gestite ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] API pubbliche non gestite da dfshim.dll.

## <a name="cleanonlineappcache"></a>CleanOnlineAppCache
 Pulisce o disinstalla tutte le applicazioni online dalla [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] cache dell'applicazione.

### <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un valore HRESULT che rappresenta l'errore. Se si verifica un'eccezione gestita, restituisce 0x80020009 (DISP_E_EXCEPTION).

### <a name="remarks"></a>Commenti
 La chiamata di CleanOnlineAppCache avvierà il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] servizio se non è già in esecuzione.

## <a name="getdeploymentdatafrommanifest"></a>GetDeploymentDataFromManifest
 Recupera le informazioni di distribuzione dal manifesto e dall'URL di attivazione.

### <a name="parameters"></a>Parametri

|Parametro|Descrizione|Type|
|---------------|-----------------|----------|
|`pcwzActivationUrl`|Puntatore a `ActivationURL`.|LPCWSTR|
|`pcwzPathToDeploymentManifest`|Puntatore a `PathToDeploymentManifest`.|LPCWSTR|
|`pwzApplicationIdentity`|Puntatore a un buffer per ricevere una stringa con terminazione NULL che specifica l'identità dell'applicazione completa restituita.|LPWSTR|
|`pdwIdentityBufferLength`|Puntatore a un valore DWORD che corrisponde alla lunghezza del `pwzApplicationIdentity` buffer, in WCHAR. Include lo spazio per il carattere di terminazione NULL.|LPDWORD|
|`pwzProcessorArchitecture`|Puntatore a un buffer per ricevere una stringa con terminazione NULL che specifica l'architettura del processore della distribuzione dell'applicazione, dal manifesto.|LPWSTR|
|`pdwArchitectureBufferLength`|Puntatore a un valore DWORD che corrisponde alla lunghezza del `pwzProcessorArchitecture` buffer, in WCHAR.|LPDWORD|
|`pwzApplicationManifestCodebase`|Puntatore a un buffer per ricevere una stringa con terminazione NULL che specifica la codebase del manifesto dell'applicazione, dal manifesto.|LPWSTR|
|`pdwCodebaseBufferLength`|Puntatore a un valore DWORD che corrisponde alla lunghezza del `pwzApplicationManifestCodebase` buffer, in WCHAR.|LPDWORD|
|`pwzDeploymentProvider`|Puntatore a un buffer per ricevere una stringa con terminazione NULL che specifica il provider di distribuzione dal manifesto, se presente. In caso contrario, viene restituita una stringa vuota.|LPWSTR|
|`pdwProviderBufferLength`|Puntatore a un valore DWORD che rappresenta la lunghezza di `pwzProviderBufferLength` .|LPDWORD|

### <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un valore HRESULT che rappresenta l'errore. Restituisce HRESULTFROMWIN32 (ERROR_INSUFFICIENT_BUFFER) se un buffer è troppo piccolo.

### <a name="remarks"></a>Commenti
 I puntatori non devono essere null. `pcwzActivationUrl` e `pcwzPathToDeploymentManifest` non devono essere vuoti.

 È responsabilità del chiamante pulire l'URL di attivazione. Ad esempio, l'aggiunta di caratteri di escape dove sono necessari o la rimozione della stringa di query.

 È responsabilità del chiamante limitare la lunghezza di input. Ad esempio, la lunghezza massima dell'URL è 2 KB.

## <a name="launchapplication"></a>LaunchApplication
 Avvia o installa un'applicazione usando un URL di distribuzione.

### <a name="parameters"></a>Parametri

|Parametro|Descrizione|Type|
|---------------|-----------------|----------|
|`deploymentUrl`|Puntatore a una stringa con terminazione NULL che contiene l'URL del manifesto di distribuzione.|LPCWSTR|
|`data`|Riservato per utilizzi futuri. Deve essere NULL.|LPVOID|
|`flags`|Riservato per utilizzi futuri. Deve essere 0.|DWORD|

### <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un valore HRESULT che rappresenta l'errore. Se si verifica un'eccezione gestita, restituisce 0x80020009 (DISP_E_EXCEPTION).

## <a name="see-also"></a>Vedere anche
- <xref:System.Deployment.Application.DeploymentServiceCom.CleanOnlineAppCache%2A>