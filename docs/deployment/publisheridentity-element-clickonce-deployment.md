---
title: '&lt;&gt;elemento publisherIdentity (distribuzione ClickOnce) | Microsoft Docs'
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
ms.openlocfilehash: 995b002784c1e76ceed36e51edb1ae893448f448
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62927539"
---
# <a name="ltpublisheridentitygt-element-clickonce-deployment"></a>&lt;&gt;elemento publisherIdentity (distribuzione ClickOnce)
Contiene informazioni sull'editore che ha firmato questo manifesto della distribuzione.

## <a name="syntax"></a>Sintassi

```xml
<publisherIdentity
   name
   issuerKeyHash
/>
```

## <a name="elements-and-attributes"></a>Elementi e attributi
 L' `publisherIdentity` elemento è obbligatorio per i manifesti firmati. La tabella seguente illustra gli attributi supportati dall' `publisherIdentity` elemento.

|Attributo|Descrizione|
|---------------|-----------------|
|`name`|Obbligatorio. Descrive l'identità della parte che ha pubblicato l'applicazione.|
|`issuerKeyHash`|Obbligatorio. Contiene l'hash SHA-1 della chiave pubblica dell'autorità emittente del certificato.|

#### <a name="parameters"></a>Parametri

## <a name="property-valuereturn-value"></a>Valore proprietà/valore restituito

## <a name="exceptions"></a>Eccezioni

## <a name="remarks"></a>Osservazioni

## <a name="requirements"></a>Requisiti

## <a name="subhead"></a>Sottotitolo