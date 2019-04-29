---
title: '&lt;assembly&gt; elemento (distribuzione ClickOnce) | Microsoft Docs'
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
ms.openlocfilehash: 3b639a7f95cfb59844fa37963730e22ead450482
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62929082"
---
# <a name="ltassemblygt-element-clickonce-deployment"></a>&lt;assembly&gt; elemento (distribuzione ClickOnce)
L'elemento di primo livello per il manifesto di distribuzione.

## <a name="syntax"></a>Sintassi

```xml

      <assembly  
   manifestVersion
/>
```

## <a name="elements-and-attributes"></a>Elementi e attributi
 Il `assembly` elemento è l'elemento radice ed è obbligatorio. Il primo elemento di contenuto deve essere un `assemblyIdentity` elemento. Gli elementi del manifesto devono essere in spazi dei nomi seguenti: `urn:schemas-microsoft-com:asm.v1`, `urn:schemas-microsoft-com:asm.v2`, e `http://www.w3.org/2000/09/xmldsig#`. Gli elementi figlio dell'assembly devono essere anche in questi spazi dei nomi, tramite ereditarietà o tramite l'assegnazione di tag.

 L'elemento `assembly` presenta l'attributo seguente:

|Attributo|Descrizione|
|---------------|-----------------|
|`manifestVersion`|Obbligatorio. Questo attributo deve essere impostato su `1.0`.|

## <a name="example"></a>Esempio
 L'esempio di codice seguente illustra un' `assembly` elemento in un manifesto di distribuzione per un'applicazione distribuita usando [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Questo esempio di codice è parte di un esempio più esaustivo disponibile per il [del manifesto della distribuzione ClickOnce](../deployment/clickonce-deployment-manifest.md) argomento.

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
- [Manifesto di distribuzione ClickOnce](../deployment/clickonce-deployment-manifest.md)
- [\<assembly > elemento](../deployment/assembly-element-clickonce-application.md)