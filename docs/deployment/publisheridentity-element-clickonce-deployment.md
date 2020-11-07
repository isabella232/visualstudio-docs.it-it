---
title: '&lt;&gt;elemento publisherIdentity (distribuzione ClickOnce) | Microsoft Docs'
description: L'elemento publisherIdentity contiene informazioni sul server di pubblicazione che ha firmato un manifesto di distribuzione. L'elemento è obbligatorio per i manifesti firmati.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 1eb4b67bfdca13c63480f3dde82004d87cd4a12a
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2020
ms.locfileid: "94350686"
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