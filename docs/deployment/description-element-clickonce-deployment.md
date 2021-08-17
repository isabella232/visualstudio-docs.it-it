---
title: '&lt;Elemento description &gt; (ClickOnce Deployment) | Microsoft Docs'
description: L'elemento description identifica le informazioni sull'applicazione usate per creare una presenza della shell e un elemento Installazione applicazioni in Pannello di controllo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#description
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <description> element [ClickOnce deployment manifest]
ms.assetid: 18f6919e-a3ab-4942-a57d-167fabfac44e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: fabce5e8d6f7b6bf59f1a62346c8d9b5927e2cae
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122080650"
---
# <a name="ltdescriptiongt-element-clickonce-deployment"></a>&lt;elemento &gt; description (distribuzione ClickOnce)
Identifica le informazioni sull'applicazione utilizzate per creare una presenza della shell **e** un elemento Installazione applicazioni in Pannello di controllo.

## <a name="syntax"></a>Sintassi

```xml

      <description 
   publisher 
   product
   suiteName
   supportUrl
/>
```

## <a name="elements-and-attributes"></a>Elementi e attributi
 L'elemento `description` è obbligatorio e si trova nello spazio dei nomi `urn:schemas-microsoft-com:asm.v1` . Non contiene elementi figlio e ha gli attributi seguenti.

|Attributo|Descrizione|
|---------------|-----------------|
|`publisher`|Obbligatorio. Identifica il nome della società usato per il posizionamento  delle icone nel menu **Start** di Windows e nell'elemento Installazione applicazioni in Pannello di controllo, quando la distribuzione è configurata per l'installazione.|
|`product`|Obbligatorio. Identifica il nome completo del prodotto. Usato come titolo per l'icona installata nel **menu** Windows Start.|
|`suiteName`|facoltativo. Identifica una sottocartella `publisher` all'interno della cartella Windows menu **Start.**|
|`supportUrl`|facoltativo. Specifica un URL di supporto visualizzato **nell'elemento** Installazione applicazioni in Pannello di controllo. Un collegamento a questo URL viene creato anche per il supporto dell'applicazione nel menu **Start** di Windows, quando la distribuzione è configurata per l'installazione.|

## <a name="remarks"></a>Commenti
 L'elemento description è obbligatorio in tutte le configurazioni di distribuzione.

## <a name="example"></a>Esempio
 Nell'esempio di codice seguente viene illustrato un `description` elemento in un manifesto della [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione. Questo esempio di codice fa parte di un esempio più ampio fornito per [l'ClickOnce manifesto della](../deployment/clickonce-deployment-manifest.md) distribuzione.

```xml
<description
  asmv2:publisher="My Company Name"
  asmv2:product="My Application"
  xmlns="urn:schemas-microsoft-com:asm.v1" />
```

## <a name="see-also"></a>Vedi anche
- [ClickOnce di distribuzione](../deployment/clickonce-deployment-manifest.md)