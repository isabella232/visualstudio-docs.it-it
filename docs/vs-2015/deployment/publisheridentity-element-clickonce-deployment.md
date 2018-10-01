---
title: '&lt;publisherIdentity&gt; elemento (distribuzione ClickOnce) | Microsoft Docs'
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
- publisherIdentity Element [ClickOnce deployment manifest], introduction
- required element for signed manifests [ClickOnce], publisherIdentity Element
- publisherIdentity Element [ClickOnce deployment manifest], syntax, elements, and attributes
ms.assetid: 34c579db-d2f2-4b66-b9c8-47207f33d950
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 4c11e8ed9a3e0b4341708fc849462fbc476dc395
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47528727"
---
# <a name="ltpublisheridentitygt-element-clickonce-deployment"></a>&lt;publisherIdentity&gt; elemento (distribuzione ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [ &lt;publisherIdentity&gt; elemento (distribuzione ClickOnce)](https://docs.microsoft.com/visualstudio/deployment/publisheridentity-element-clickonce-deployment).  
  
Contiene informazioni sull'editore che ha firmato questo manifesto della distribuzione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<publisherIdentity  
   name  
   issuerKeyHash  
/>  
```  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 Il `publisherIdentity` elemento è obbligatorio per manifesti firmati. La tabella seguente illustra gli attributi di `publisherIdentity` supportato dall'elemento.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`name`|Obbligatorio. Descrive l'identità dell'entità pubblicata l'applicazione.|  
|`issuerKeyHash`|Obbligatorio. Contiene l'hash SHA-1 della chiave pubblica dell'autorità di certificazione.|  
  
#### <a name="parameters"></a>Parametri  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
  
## <a name="exceptions"></a>Eccezioni  
  
## <a name="remarks"></a>Note  
  
## <a name="requirements"></a>Requisiti  
  
## <a name="subhead"></a>Sottotitolo



