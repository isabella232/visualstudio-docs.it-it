---
title: '&lt;assembly&gt; elemento (applicazione ClickOnce) | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assembly> element [ClickOnce application manifest]
ms.assetid: 51410569-10f9-4c0a-96b5-d39185edbefc
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: edd968ffb6f2b0422e54bc6d456c1090d189fcc0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47529114"
---
# <a name="ltassemblygt-element-clickonce-application"></a>&lt;assembly&gt; elemento (applicazione ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [ &lt;assembly&gt; elemento (applicazione ClickOnce)](https://docs.microsoft.com/visualstudio/deployment/assembly-element-clickonce-application).  
  
L'elemento di primo livello per il manifesto dell'applicazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
      <assembly  
   manifestVersion  
/>  
```  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 Il `assembly` elemento è l'elemento radice ed è obbligatorio. Il primo elemento di contenuto deve essere un `assemblyIdentity` elemento. Gli elementi del manifesto devono essere in uno degli spazi dei nomi seguenti:  
  
 `urn:schemas-microsoft-com:asm.v1`  
  
 `urn:schemas-microsoft-com:asm.v2`  
  
 `http://www.w3.org/2000/09/xmldsig#`  
  
 Gli elementi figlio dell'assembly devono essere anche in questi spazi dei nomi, tramite ereditarietà o tramite l'assegnazione di tag.  
  
 Il `assembly` elemento ha l'attributo seguente.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`manifestVersion`|Obbligatorio. Il `manifestVersion` attributo deve essere impostato su `1.0`.|  
  
## <a name="example"></a>Esempio  
 L'esempio di codice seguente illustra un' `assembly` elemento in un manifesto dell'applicazione per un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dell'applicazione. Questo esempio di codice è parte di un esempio più esaustivo disponibile nel [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md).  
  
```  
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
  
## <a name="see-also"></a>Vedere anche  
 [Manifesto dell'applicazione ClickOnce](../deployment/clickonce-application-manifest.md)   
 [\<assembly > elemento](../deployment/assembly-element-clickonce-deployment.md)



