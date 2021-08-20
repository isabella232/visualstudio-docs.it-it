---
title: ClickOnce Informazioni di riferimento sulle API non gestite | Microsoft Docs
description: Informazioni sulle CLICKONCE pubbliche non gestite da dfshim.dll, tra cui CleanOnlineAppCache, GetDeploymentDataFromManifest e LaunchApplication.
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
ms.technology: vs-ide-deployment
ms.workload:
- cplusplus
ms.openlocfilehash: c78c5dc002caaa17569d3a71f01aa47e7ae901c1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122073864"
---
# <a name="clickonce-unmanaged-api-reference"></a>Riferimenti alle API non gestite ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] API pubbliche non gestite da dfshim.dll.

## <a name="cleanonlineappcache"></a>CleanOnlineAppCache
 Pulisce o disinstalla tutte le applicazioni online dalla [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] cache dell'applicazione.

### <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; In caso contrario, restituisce un HRESULT che rappresenta l'errore. Se si verifica un'eccezione gestita, restituisce 0x80020009 (DISP_E_EXCEPTION).

### <a name="remarks"></a>Commenti
 La chiamata a CleanOnlineAppCache avvia [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] il servizio se non è già in esecuzione.

## <a name="getdeploymentdatafrommanifest"></a>GetDeploymentDataFromManifest
 Recupera le informazioni sulla distribuzione dal manifesto e dall'URL di attivazione.

### <a name="parameters"></a>Parametri

|Parametro|Descrizione|Type|
|---------------|-----------------|----------|
|`pcwzActivationUrl`|Puntatore a `ActivationURL`.|LPCWSTR|
|`pcwzPathToDeploymentManifest`|Puntatore a `PathToDeploymentManifest`.|LPCWSTR|
|`pwzApplicationIdentity`|Puntatore a un buffer per ricevere una stringa con terminazione NULL che specifica l'identità dell'applicazione completa restituita.|LPWSTR|
|`pdwIdentityBufferLength`|Puntatore a un valore DWORD che rappresenta la lunghezza del `pwzApplicationIdentity` buffer, in WCHAR. Include lo spazio per il carattere di terminazione NULL.|LPDWORD|
|`pwzProcessorArchitecture`|Puntatore a un buffer per ricevere una stringa con terminazione NULL che specifica l'architettura del processore della distribuzione dell'applicazione, dal manifesto.|LPWSTR|
|`pdwArchitectureBufferLength`|Puntatore a un valore DWORD che rappresenta la lunghezza del `pwzProcessorArchitecture` buffer, in WCHAR.|LPDWORD|
|`pwzApplicationManifestCodebase`|Puntatore a un buffer per ricevere una stringa con terminazione NULL che specifica la codebase del manifesto dell'applicazione, dal manifesto.|LPWSTR|
|`pdwCodebaseBufferLength`|Puntatore a un valore DWORD che rappresenta la lunghezza del `pwzApplicationManifestCodebase` buffer, in WCHAR.|LPDWORD|
|`pwzDeploymentProvider`|Puntatore a un buffer per ricevere una stringa con terminazione NULL che specifica il provider di distribuzione dal manifesto, se presente. In caso contrario, viene restituita una stringa vuota.|LPWSTR|
|`pdwProviderBufferLength`|Puntatore a un valore DWORD che rappresenta la lunghezza di `pwzProviderBufferLength` .|LPDWORD|

### <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; In caso contrario, restituisce un HRESULT che rappresenta l'errore. Restituisce HRESULTFROMWIN32(ERROR_INSUFFICIENT_BUFFER) se un buffer è troppo piccolo.

### <a name="remarks"></a>Commenti
 I puntatori non devono essere Null. `pcwzActivationUrl` e `pcwzPathToDeploymentManifest` non devono essere vuoti.

 È responsabilità del chiamante pulire l'URL di attivazione. Ad esempio, l'aggiunta di caratteri di escape in cui sono necessari o la rimozione della stringa di query.

 È responsabilità del chiamante limitare la lunghezza dell'input. Ad esempio, la lunghezza massima dell'URL è 2 KB.

## <a name="launchapplication"></a>LaunchApplication
 Avvia o installa un'applicazione usando un URL di distribuzione.

### <a name="parameters"></a>Parametri

|Parametro|Descrizione|Type|
|---------------|-----------------|----------|
|`deploymentUrl`|Puntatore a una stringa con terminazione NULL che contiene l'URL del manifesto della distribuzione.|LPCWSTR|
|`data`|Riservato per utilizzi futuri. Deve essere NULL.|Lpvoid|
|`flags`|Riservato per utilizzi futuri. Deve essere 0.|DWORD|

### <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; In caso contrario, restituisce un HRESULT che rappresenta l'errore. Se si verifica un'eccezione gestita, restituisce 0x80020009 (DISP_E_EXCEPTION).

## <a name="see-also"></a>Vedere anche
- <xref:System.Deployment.Application.DeploymentServiceCom.CleanOnlineAppCache%2A>