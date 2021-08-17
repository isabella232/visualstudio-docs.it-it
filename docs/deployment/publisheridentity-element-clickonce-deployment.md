---
title: '&lt;Elemento publisherIdentity &gt; (ClickOnce Deployment) | Microsoft Docs'
description: L'elemento publisherIdentity contiene informazioni sul server di pubblicazione che ha firmato un manifesto della distribuzione. L'elemento è obbligatorio per i manifesti firmati.
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
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: a0421172d9f97fde3fcf558214b7325152e3c15373a70d242f9b68c013a5cc42
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121343416"
---
# <a name="ltpublisheridentitygt-element-clickonce-deployment"></a>&lt;Elemento publisherIdentity &gt; (distribuzione ClickOnce)
Contiene informazioni sull'editore che ha firmato questo manifesto della distribuzione.

## <a name="syntax"></a>Sintassi

```xml
<publisherIdentity
   name
   issuerKeyHash
/>
```

## <a name="elements-and-attributes"></a>Elementi e attributi
 `publisherIdentity`L'elemento è obbligatorio per i manifesti firmati. Nella tabella seguente vengono illustrati gli attributi supportati `publisherIdentity` dall'elemento .

|Attributo|Descrizione|
|---------------|-----------------|
|`name`|Obbligatorio. Descrive l'identità dell'entità che ha pubblicato l'applicazione.|
|`issuerKeyHash`|Obbligatorio. Contiene l'hash SHA-1 della chiave pubblica dell'autorità di certificazione.|

#### <a name="parameters"></a>Parametri

## <a name="property-valuereturn-value"></a>Valore proprietà/valore restituito

## <a name="exceptions"></a>Eccezioni

## <a name="remarks"></a>Osservazioni

## <a name="requirements"></a>Requisiti

## <a name="subhead"></a>Sottotitolo