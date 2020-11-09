---
title: '&lt;&gt;elemento assemblyIdentity (distribuzione ClickOnce) | Microsoft Docs'
description: L'elemento assemblyIdentity è obbligatorio nella distribuzione ClickOnce. Non contiene elementi figlio e ha attributi descritti in questo articolo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assemblyIdentity
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assemblyIdentity> element [ClickOnce deployment manifest]
ms.assetid: f4a3bb83-c800-47d0-9905-9a5ae2486838
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5a692d37771070f1835fc791515d5dbc24ce6b1b
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2020
ms.locfileid: "94383183"
---
# <a name="ltassemblyidentitygt-element-clickonce-deployment"></a>&lt;&gt;elemento assemblyIdentity (distribuzione ClickOnce)
Identifica l'assembly primario dell' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione.

## <a name="syntax"></a>Sintassi

```xml

      <assemblyIdentity  
   name 
   version
   publicKeyToken
   processorArchitecture
    type
/>
```

## <a name="elements-and-attributes"></a>Elementi e attributi
 L' `assemblyIdentity` elemento è obbligatorio. Non contiene elementi figlio e ha gli attributi seguenti.

|Attributo|Descrizione|
|---------------|-----------------|
|`name`|Obbligatorio. Identifica il nome leggibile della distribuzione a scopo informativo.<br /><br /> Se `name` contiene caratteri speciali, ad esempio virgolette singole o doppie, l'attivazione dell'applicazione potrebbe non riuscire.|
|`version`|Obbligatorio. Specifica il numero di versione dell'assembly, nel formato seguente: `major.minor.build.revision` .<br /><br /> Questo valore deve essere incrementato in un manifesto aggiornato per attivare un aggiornamento dell'applicazione.|
|`publicKeyToken`|Obbligatorio. Specifica una stringa esadecimale di 16 caratteri che rappresenta gli ultimi 8 byte del valore hash SHA-1 della chiave pubblica in cui il manifesto di distribuzione è firmato. La chiave pubblica usata per firmare deve essere di 2048 bit o superiore.<br /><br /> Sebbene la firma di un assembly sia consigliata ma facoltativa, questo attributo è obbligatorio. Se un assembly non è firmato, è necessario copiare un valore da un assembly autofirmato oppure utilizzare un valore "fittizio" di tutti gli zeri.|
|`processorArchitecture`|Obbligatorio. Specifica il processore. I valori validi sono `msil` per tutti i processori, `x86` per windows a 32 bit, `IA64` per Windows a 64 bit e `Itanium` per processori Itanium Intel 64-bit.|
|`type`|Obbligatorio. Per la compatibilità con la tecnologia di installazione side-by-side di Windows. L'unico valore consentito è `win32` .|

## <a name="remarks"></a>Commenti

## <a name="example"></a>Esempio
 Nell'esempio di codice riportato di seguito viene illustrato un `assemblyIdentity` elemento in un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesto di distribuzione. Questo esempio di codice fa parte di un esempio più ampio fornito per l'argomento [manifesto della distribuzione ClickOnce](../deployment/clickonce-deployment-manifest.md) .

```xml
<!-- Identify the deployment. -->
<assemblyIdentity
  name="My Application Deployment.app"
  version="1.0.0.0"
  publicKeyToken="43cb1e8e7a352766"
  language="neutral"
  processorArchitecture="x86"
  xmlns="urn:schemas-microsoft-com:asm.v1" />
```

## <a name="see-also"></a>Vedere anche
- [Manifesto della distribuzione ClickOnce](../deployment/clickonce-deployment-manifest.md)
- [\<assemblyIdentity> elemento](../deployment/assemblyidentity-element-clickonce-application.md)