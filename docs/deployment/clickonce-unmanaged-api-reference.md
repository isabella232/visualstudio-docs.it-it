---
title: Riferimenti alle API non gestite ClickOnce | Microsoft Docs
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
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: ae06a978f1ce75ce174ea610453d8b9b7acc713a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54986670"
---
# <a name="clickonce-unmanaged-api-reference"></a>Riferimenti alle API non gestite ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pubbliche API non gestite da dfshim.  
  
## <a name="cleanonlineappcache"></a>CleanOnlineAppCache  
 Esegue la pulizia o disinstalla tutte le applicazioni online dal [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] cache dell'applicazione.  
  
### <a name="return-value"></a>Valore restituito  
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un HRESULT che rappresenta l'errore. Se si verifica un'eccezione gestita, restituisce 0x80020009 (DISP_E_EXCEPTION).  
  
### <a name="remarks"></a>Note  
 La chiamata a CleanOnlineAppCache avvierà il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] del servizio se non è già in esecuzione.  
  
## <a name="getdeploymentdatafrommanifest"></a>GetDeploymentDataFromManifest  
 Recupera le informazioni di distribuzione dall'URL del manifesto e l'attivazione.  
  
### <a name="parameters"></a>Parametri  
  
|Parametro|Descrizione|Tipo|  
|---------------|-----------------|----------|  
|`pcwzActivationUrl`|Un puntatore al `ActivationURL`.|LPCWSTR|  
|`pcwzPathToDeploymentManifest`|Un puntatore al `PathToDeploymentManifest`.|LPCWSTR|  
|`pwzApplicationIdentity`|Puntatore a un buffer per la ricezione di una stringa con terminazione NULL che specifica l'identità dell'applicazione completo restituito.|LPWSTR|  
|`pdwIdentityBufferLength`|Un puntatore a un valore DWORD che è la lunghezza del `pwzApplicationIdentity` buffer, in WCHAR. Ciò include lo spazio per il carattere di terminazione NULL.|LPDWORD|  
|`pwzProcessorArchitecture`|Puntatore a un buffer per la ricezione di una stringa con terminazione NULL che specifica l'architettura del processore di distribuzione dell'applicazione, dal manifesto.|LPWSTR|  
|`pdwArchitectureBufferLength`|Un puntatore a un valore DWORD che è la lunghezza del `pwzProcessorArchitecture` buffer, in WCHAR.|LPDWORD|  
|`pwzApplicationManifestCodebase`|Puntatore a un buffer per la ricezione di una stringa con terminazione NULL che specifica la codebase del manifesto dell'applicazione, dal manifesto.|LPWSTR|  
|`pdwCodebaseBufferLength`|Un puntatore a un valore DWORD che è la lunghezza del `pwzApplicationManifestCodebase` buffer, in WCHAR.|LPDWORD|  
|`pwzDeploymentProvider`|Un puntatore a un buffer per ricevere una stringa con terminazione NULL che specifica il provider di distribuzione dal manifesto, se presente. In caso contrario, viene restituita una stringa vuota.|LPWSTR|  
|`pdwProviderBufferLength`|Un puntatore a un valore DWORD che è la lunghezza del `pwzProviderBufferLength`.|LPDWORD|  
  
### <a name="return-value"></a>Valore restituito  
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un HRESULT che rappresenta l'errore. Restituisce HRESULTFROMWIN32 (ERROR_INSUFFICIENT_BUFFER) se un buffer è troppo piccolo.  
  
### <a name="remarks"></a>Note  
 I puntatori non devono essere null. `pcwzActivationUrl` e `pcwzPathToDeploymentManifest` non deve essere vuoto.  
  
 È responsabilità del chiamante per pulire l'URL di attivazione. Ad esempio, aggiungendo caratteri di escape in cui sono necessari o rimuovendo la stringa di query.  
  
 È responsabilità del chiamante per limitare la lunghezza di input. Ad esempio, la lunghezza URL massima è 2KB.  
  
## <a name="launchapplication"></a>LaunchApplication  
 Avvia o si installa un'applicazione usando un URL di distribuzione.  
  
### <a name="parameters"></a>Parametri  
  
|Parametro|Descrizione|Tipo|  
|---------------|-----------------|----------|  
|`deploymentUrl`|Un puntatore a una stringa con terminazione NULL che contiene l'URL del manifesto della distribuzione.|LPCWSTR|  
|`data`|Riservato per usi futuri. Deve essere NULL.|LPVOID|  
|`flags`|Riservato per usi futuri. Deve essere 0.|DWORD|  
  
### <a name="return-value"></a>Valore restituito  
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un HRESULT che rappresenta l'errore. Se si verifica un'eccezione gestita, restituisce 0x80020009 (DISP_E_EXCEPTION).  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Deployment.Application.DeploymentServiceCom.CleanOnlineAppCache%2A>