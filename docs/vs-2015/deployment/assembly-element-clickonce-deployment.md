---
title: '&lt;&gt;elemento assembly (distribuzione ClickOnce) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assembly> element [ClickOnce deployment manifest]
ms.assetid: b8e3362a-f821-4696-b98d-571d4bbfe431
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3b77cfacf3dca2c2cc20d674f79929e9958a16d4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155731"
---
# <a name="ltassemblygt-element-clickonce-deployment"></a>&lt;&gt;elemento assembly (distribuzione ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Elemento di primo livello per il manifesto della distribuzione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
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
 Nell'esempio di codice seguente viene illustrato un `assembly` elemento in un manifesto di distribuzione per un'applicazione distribuita tramite [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . Questo esempio di codice fa parte di un esempio più ampio fornito per l'argomento [manifesto della distribuzione ClickOnce](../deployment/clickonce-deployment-manifest.md) .  
  
```  
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
 [Manifesto della distribuzione ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [\<assembly> Elemento](../deployment/assembly-element-clickonce-application.md)
