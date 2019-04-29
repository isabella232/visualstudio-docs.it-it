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
ms.openlocfilehash: 995b002784c1e76ceed36e51edb1ae893448f448
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62927539"
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

|Attributo|Descrizione|
|---------------|-----------------|
|`name`|Obbligatorio. Descrive l'identità dell'entità pubblicata l'applicazione.|
|`issuerKeyHash`|Obbligatorio. Contiene l'hash SHA-1 della chiave pubblica dell'autorità di certificazione.|

#### <a name="parameters"></a>Parametri

## <a name="property-valuereturn-value"></a>Valore proprietà/valore restituito

## <a name="exceptions"></a>Eccezioni

## <a name="remarks"></a>Note

## <a name="requirements"></a>Requisiti

## <a name="subhead"></a>Sottotitolo