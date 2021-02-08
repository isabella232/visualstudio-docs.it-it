---
title: '&lt;&gt;elemento assembly (applicazione ClickOnce) | Microsoft Docs'
description: L'elemento assembly è l'elemento radice ed è obbligatorio nell'applicazione ClickOnce. Il primo elemento contenuto deve essere un elemento assemblyIdentity.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assembly> element [ClickOnce application manifest]
ms.assetid: 51410569-10f9-4c0a-96b5-d39185edbefc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f86ed604ae6b893f02da1d4f65a816bd05f34f94
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837788"
---
# <a name="ltassemblygt-element-clickonce-application"></a>&lt;&gt;elemento assembly (applicazione ClickOnce)
Elemento di primo livello per il manifesto dell'applicazione.

## <a name="syntax"></a>Sintassi

```xml

      <assembly
   manifestVersion
/>
```

## <a name="elements-and-attributes"></a>Elementi e attributi
 L' `assembly` elemento è l'elemento radice ed è obbligatorio. Il primo elemento contenuto deve essere un `assemblyIdentity` elemento. Gli elementi del manifesto devono trovarsi in uno degli spazi dei nomi seguenti:

 `urn:schemas-microsoft-com:asm.v1`

 `urn:schemas-microsoft-com:asm.v2`

 `http://www.w3.org/2000/09/xmldsig#`

 Gli elementi figlio dell'assembly devono essere presenti anche in questi spazi dei nomi, per ereditarietà o per contrassegno.

 L'elemento `assembly` presenta l'attributo seguente:

|Attributo|Descrizione|
|---------------|-----------------|
|`manifestVersion`|Obbligatorio. L' `manifestVersion` attributo deve essere impostato su `1.0` .|

## <a name="example"></a>Esempio
 Nell'esempio di codice seguente viene illustrato un `assembly` elemento in un manifesto dell'applicazione per un' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione. Questo esempio di codice fa parte di un esempio più ampio fornito nel [manifesto dell'applicazione ClickOnce](../deployment/clickonce-application-manifest.md).

```xml
<asmv1:assembly
  xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"
  manifestVersion="1.0"
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"
  xmlns:dsig=http://www.w3.org/2000/09/xmldsig#
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"
  xmlns="urn:schemas-microsoft-com:asm.v2"
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"
  xmlns:xsi=http://www.w3.org/2001/XMLSchema-instance
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1">
```

## <a name="see-also"></a>Vedi anche
- [Manifesto dell'applicazione ClickOnce](../deployment/clickonce-application-manifest.md)
- [\<assembly> elemento](../deployment/assembly-element-clickonce-deployment.md)
