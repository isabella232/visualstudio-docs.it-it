---
title: '&lt;&gt;elemento assembly (distribuzione ClickOnce) | Microsoft Docs'
description: L'elemento assembly è l'elemento radice ed è necessario nella distribuzione ClickOnce. Il primo elemento contenuto deve essere un elemento assemblyIdentity.
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
- <assembly> element [ClickOnce deployment manifest]
ms.assetid: b8e3362a-f821-4696-b98d-571d4bbfe431
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dde3bdb5fc0e9c6ea256aaa4368623a8e8af18d6
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2020
ms.locfileid: "94383235"
---
# <a name="ltassemblygt-element-clickonce-deployment"></a>&lt;&gt;elemento assembly (distribuzione ClickOnce)
Elemento di primo livello per il manifesto della distribuzione.

## <a name="syntax"></a>Sintassi

```xml

      <assembly  
   manifestVersion
/>
```

## <a name="elements-and-attributes"></a>Elementi e attributi
 L' `assembly` elemento è l'elemento radice ed è obbligatorio. Il primo elemento contenuto deve essere un `assemblyIdentity` elemento. Gli elementi del manifesto devono trovarsi negli spazi dei nomi seguenti: `urn:schemas-microsoft-com:asm.v1` , `urn:schemas-microsoft-com:asm.v2` e `http://www.w3.org/2000/09/xmldsig#` . Gli elementi figlio dell'assembly devono essere presenti anche in questi spazi dei nomi, per ereditarietà o per contrassegno.

 L'elemento `assembly` presenta l'attributo seguente:

|Attributo|Descrizione|
|---------------|-----------------|
|`manifestVersion`|Obbligatorio. Questo attributo deve essere impostato su `1.0` .|

## <a name="example"></a>Esempio
 Nell'esempio di codice seguente viene illustrato un `assembly` elemento in un manifesto di distribuzione per un'applicazione distribuita tramite [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . Questo esempio di codice fa parte di un esempio più ampio fornito per l'argomento [manifesto della distribuzione ClickOnce](../deployment/clickonce-deployment-manifest.md) .

```xml
<asmv1:assembly
  xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"
  manifestVersion="1.0"
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"
  xmlns:dsig=http://www.w3.org/2000/09/xmldsig#
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1"
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"
  xmlns="urn:schemas-microsoft-com:asm.v2"
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"
  xmlns:xrml="urn:mpeg:mpeg21:2003:01-REL-R-NS"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
```

## <a name="see-also"></a>Vedere anche
- [Manifesto della distribuzione ClickOnce](../deployment/clickonce-deployment-manifest.md)
- [\<assembly> elemento](../deployment/assembly-element-clickonce-application.md)