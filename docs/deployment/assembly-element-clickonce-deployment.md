---
title: '&lt;Elemento assembly &gt; (ClickOnce Deployment) | Microsoft Docs'
description: L'elemento assembly è l'elemento radice ed è necessario nella ClickOnce distribuzione. Il primo elemento contenuto deve essere un elemento assemblyIdentity.
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
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 54affc5f75a17fe93beac0ee62207f6c25a1c448
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122074033"
---
# <a name="ltassemblygt-element-clickonce-deployment"></a>&lt;Elemento assembly &gt; (distribuzione ClickOnce assembly)
Elemento di primo livello per il manifesto della distribuzione.

## <a name="syntax"></a>Sintassi

```xml

      <assembly  
   manifestVersion
/>
```

## <a name="elements-and-attributes"></a>Elementi e attributi
 `assembly`L'elemento è l'elemento radice ed è obbligatorio. Il primo elemento contenuto deve essere un `assemblyIdentity` elemento . Gli elementi del manifesto devono essere negli spazi dei nomi seguenti: `urn:schemas-microsoft-com:asm.v1` `urn:schemas-microsoft-com:asm.v2` , e `http://www.w3.org/2000/09/xmldsig#` . Anche gli elementi figlio dell'assembly devono essere presenti in questi spazi dei nomi, tramite ereditarietà o mediante l'assegnazione di tag.

 L'elemento `assembly` presenta l'attributo seguente:

|Attributo|Descrizione|
|---------------|-----------------|
|`manifestVersion`|Obbligatorio. Questo attributo deve essere impostato su `1.0` .|

## <a name="example"></a>Esempio
 Nell'esempio di codice seguente viene illustrato un `assembly` elemento in un manifesto della distribuzione per un'applicazione distribuita tramite [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . Questo esempio di codice fa parte di un esempio più ampio fornito per [l'ClickOnce manifesto della](../deployment/clickonce-deployment-manifest.md) distribuzione.

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

## <a name="see-also"></a>Vedi anche
- [ClickOnce di distribuzione](../deployment/clickonce-deployment-manifest.md)
- [\<assembly> Elemento](../deployment/assembly-element-clickonce-application.md)