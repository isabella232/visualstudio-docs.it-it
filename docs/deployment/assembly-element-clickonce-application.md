---
title: '&lt;Elemento assembly &gt; (ClickOnce Application) | Microsoft Docs'
description: L'elemento assembly è l'elemento radice ed è obbligatorio in ClickOnce Application. Il primo elemento contenuto deve essere un elemento assemblyIdentity.
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
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: cc8fb424c3a6232f27737521604247cf55ebc20e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122090060"
---
# <a name="ltassemblygt-element-clickonce-application"></a>&lt;Elemento assembly &gt; (ClickOnce Application)
Elemento di primo livello per il manifesto dell'applicazione.

## <a name="syntax"></a>Sintassi

```xml

      <assembly
   manifestVersion
/>
```

## <a name="elements-and-attributes"></a>Elementi e attributi
 `assembly`L'elemento è l'elemento radice ed è obbligatorio. Il primo elemento contenuto deve essere un `assemblyIdentity` elemento . Gli elementi manifesto devono essere in uno degli spazi dei nomi seguenti:

 `urn:schemas-microsoft-com:asm.v1`

 `urn:schemas-microsoft-com:asm.v2`

 `http://www.w3.org/2000/09/xmldsig#`

 Anche gli elementi figlio dell'assembly devono essere presenti in questi spazi dei nomi, tramite ereditarietà o mediante l'assegnazione di tag.

 L'elemento `assembly` presenta l'attributo seguente:

|Attributo|Descrizione|
|---------------|-----------------|
|`manifestVersion`|Obbligatorio. `manifestVersion`L'attributo deve essere impostato su `1.0` .|

## <a name="example"></a>Esempio
 Nell'esempio di codice seguente viene illustrato un `assembly` elemento in un manifesto dell'applicazione per un'applicazione. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Questo esempio di codice fa parte di un esempio più ampio fornito in ClickOnce [dell'applicazione](../deployment/clickonce-application-manifest.md).

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
- [ClickOnce manifesto dell'applicazione](../deployment/clickonce-application-manifest.md)
- [\<assembly> Elemento](../deployment/assembly-element-clickonce-deployment.md)
