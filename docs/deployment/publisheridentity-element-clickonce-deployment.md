---
title: '&lt;publisherIdentity&gt; elemento (distribuzione ClickOnce) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publisherIdentity Element [ClickOnce deployment manifest], introduction
- required element for signed manifests [ClickOnce], publisherIdentity Element
- publisherIdentity Element [ClickOnce deployment manifest], syntax, elements, and attributes
ms.assetid: 34c579db-d2f2-4b66-b9c8-47207f33d950
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d1fa91423a5c0ddf6b276095b53ae4461d7057c4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55005527"
---
# <a name="ltpublisheridentitygt-element-clickonce-deployment"></a>&lt;publisherIdentity&gt; elemento (distribuzione ClickOnce)
Contiene informazioni sull'editore che ha firmato questo manifesto della distribuzione.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
<publisherIdentity  
   name  
   issuerKeyHash  
/>  
```  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 Il `publisherIdentity` elemento è obbligatorio per manifesti firmati. La tabella seguente illustra gli attributi di `publisherIdentity` supportato dall'elemento.  
  
|Attributo|Description|  
|---------------|-----------------|  
|`name`|Obbligatorio. Descrive l'identità dell'entità pubblicata l'applicazione.|  
|`issuerKeyHash`|Obbligatorio. Contiene l'hash SHA-1 della chiave pubblica dell'autorità di certificazione.|  
  
#### <a name="parameters"></a>Parametri  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/valore restituito  
  
## <a name="exceptions"></a>Eccezioni  
  
## <a name="remarks"></a>Note  
  
## <a name="requirements"></a>Requisiti  
  
## <a name="subhead"></a>Sottotitolo