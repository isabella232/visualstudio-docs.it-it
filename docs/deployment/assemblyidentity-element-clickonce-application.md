---
title: '&lt;Elemento assemblyIdentity &gt; (ClickOnce Application) | Microsoft Docs'
description: L'elemento assemblyIdentity è obbligatorio nell ClickOnce appliazione. Non contiene elementi figlio e dispone di attributi descritti in questo articolo.
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
- <assemblyIdentity> element [ClickOnce application manifest]
ms.assetid: f48e9531-efac-4d11-8166-f63a5ece1ac5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: c70873e347999b7e7a8503febf78771ceeaad0d3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122090068"
---
# <a name="ltassemblyidentitygt-element-clickonce-application"></a>&lt;Elemento assemblyIdentity &gt; (applicazione ClickOnce)
Identifica l'applicazione distribuita in una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione.

## <a name="syntax"></a>Sintassi

```xml

      <assemblyIdentity
   name
   version
   publicKeyToken
   processorArchitecture
   language
/>
```

## <a name="elements-and-attributes"></a>Elementi e attributi
 `assemblyIdentity`L'elemento è obbligatorio. Non contiene elementi figlio e dispone degli attributi seguenti.

|Attributo|Descrizione|
|---------------|-----------------|
|`Name`|Obbligatorio. Identifica il nome dell'applicazione.<br /><br /> Se `Name` contiene caratteri speciali, ad esempio virgolette singole o doppie, l'applicazione potrebbe non essere attivata.|
|`Version`|Obbligatorio. Specifica il numero di versione dell'applicazione nel formato seguente: `major.minor.build.revision`|
|`publicKeyToken`|facoltativo. Specifica una stringa esadecimale di 16 caratteri che rappresenta gli ultimi 8 byte del valore hash della chiave pubblica con cui viene firmata l'applicazione o `SHA-1` l'assembly. La chiave pubblica usata per firmare il catalogo deve essere di 2048 bit o superiore.<br /><br /> Anche se la firma di un assembly è consigliata ma facoltativa, questo attributo è obbligatorio. Se un assembly non è firmato, è necessario copiare un valore da un assembly autofirmato o usare un valore "fittizio" di tutti gli zeri.|
|`processorArchitecture`|Obbligatorio. Specifica il processore. I valori validi sono per tutti i processori, per i Windows a 32 bit, per i Windows a 64 bit e per i processori `msil` `x86` Intel Itanium a `IA64` `Itanium` 64 bit.|
|`language`|Obbligatorio. Identifica i codici di lingua in due parti (ad esempio, `en-US` ) dell'assembly. Questo elemento si trova nello spazio `asmv2` dei nomi . Se non specificato, il valore predefinito è `neutral` .|

## <a name="examples"></a>Esempi

### <a name="description"></a>Descrizione
 L'esempio di codice seguente illustra un `assemblyIdentity` elemento in un manifesto [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dell'applicazione. Questo esempio di codice fa parte di un esempio più ampio fornito in [ClickOnce manifesto dell'applicazione](../deployment/clickonce-application-manifest.md).

### <a name="code"></a>Codice

```xml
<asmv1:assemblyIdentity
  name="My Application Deployment.exe"
  version="1.0.0.0"
  publicKeyToken="43cb1e8e7a352766"
  language="neutral"
  processorArchitecture="x86"
  type="win32" />
```

## <a name="see-also"></a>Vedi anche
- [ClickOnce manifesto dell'applicazione](../deployment/clickonce-application-manifest.md)
- [\<assemblyIdentity> Elemento](../deployment/assemblyidentity-element-clickonce-deployment.md)