---
title: '&lt;Elemento assemblyIdentity &gt; (ClickOnce Deployment) | Microsoft Docs'
description: L'elemento assemblyIdentity è obbligatorio ClickOnce distribuzione. Non contiene elementi figlio e dispone degli attributi descritti in questo articolo.
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
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: e4633b5ed024b1e43134b33827a5614bfa5f8d17
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122146498"
---
# <a name="ltassemblyidentitygt-element-clickonce-deployment"></a>&lt;Elemento assemblyIdentity &gt; (distribuzione ClickOnce)
Identifica l'assembly primario [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dell'applicazione.

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
 `assemblyIdentity`L'elemento è obbligatorio. Non contiene elementi figlio e ha gli attributi seguenti.

|Attributo|Descrizione|
|---------------|-----------------|
|`name`|Obbligatorio. Identifica il nome leggibile della distribuzione a scopo informativo.<br /><br /> Se `name` contiene caratteri speciali, ad esempio virgolette singole o doppie, l'attivazione dell'applicazione potrebbe non riuscire.|
|`version`|Obbligatorio. Specifica il numero di versione dell'assembly, nel formato seguente: `major.minor.build.revision` .<br /><br /> Questo valore deve essere incrementato in un manifesto aggiornato per attivare un aggiornamento dell'applicazione.|
|`publicKeyToken`|Obbligatorio. Specifica una stringa esadecimale di 16 caratteri che rappresenta gli ultimi 8 byte del valore hash SHA-1 della chiave pubblica con cui viene firmato il manifesto della distribuzione. La chiave pubblica usata per firmare deve essere di 2048 bit o superiore.<br /><br /> Sebbene la firma di un assembly sia consigliata ma facoltativa, questo attributo è obbligatorio. Se un assembly non è firmato, è necessario copiare un valore da un assembly autofirmato o usare un valore "fittizio" di tutti gli zeri.|
|`processorArchitecture`|Obbligatorio. Specifica il processore. I valori validi sono per tutti i processori, per i Windows a 32 bit, per i Windows a 64 bit e per i processori `msil` `x86` Intel Itanium a `IA64` `Itanium` 64 bit.|
|`type`|Obbligatorio. Per la compatibilità Windows tecnologia di installazione side-by-side. L'unico valore consentito è `win32` .|

## <a name="remarks"></a>Commenti

## <a name="example"></a>Esempio
 Nell'esempio di codice seguente viene illustrato un `assemblyIdentity` elemento in un manifesto della [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione. Questo esempio di codice fa parte di un esempio più ampio fornito per [l'argomento ClickOnce manifesto della](../deployment/clickonce-deployment-manifest.md) distribuzione.

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

## <a name="see-also"></a>Vedi anche
- [ClickOnce di distribuzione](../deployment/clickonce-deployment-manifest.md)
- [\<assemblyIdentity> Elemento](../deployment/assemblyidentity-element-clickonce-application.md)