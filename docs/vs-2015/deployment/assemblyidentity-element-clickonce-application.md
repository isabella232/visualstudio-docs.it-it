---
title: '&lt;&gt;elemento assemblyIdentity (applicazione ClickOnce) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assemblyIdentity
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assemblyIdentity> element [ClickOnce application manifest]
ms.assetid: f48e9531-efac-4d11-8166-f63a5ece1ac5
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5bde22809af69071f5484e25717a5aea7d78a603
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62428534"
---
# <a name="ltassemblyidentitygt-element-clickonce-application"></a>&lt;&gt;elemento assemblyIdentity (applicazione ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identifica l'applicazione distribuita in una [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] distribuzione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
      <assemblyIdentity   
   name  
   version  
   publicKeyToken  
   processorArchitecture  
   language  
/>  
```  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 L' `assemblyIdentity` elemento è obbligatorio. Non contiene elementi figlio e ha gli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Name`|Obbligatorio. Identifica il nome dell'applicazione.<br /><br /> Se `Name` contiene caratteri speciali, ad esempio virgolette singole o doppie, l'attivazione dell'applicazione potrebbe non riuscire.|  
|`Version`|Obbligatorio. Specifica il numero di versione dell'applicazione nel formato seguente: `major.minor.build.revision`|  
|`publicKeyToken`|facoltativo. Specifica una stringa esadecimale di 16 caratteri che rappresenta gli ultimi 8 byte del `SHA-1` valore hash della chiave pubblica in cui l'applicazione o l'assembly è firmato. La chiave pubblica usata per firmare il catalogo deve essere di 2048 bit o superiore.<br /><br /> Sebbene la firma di un assembly sia consigliata ma facoltativa, questo attributo è obbligatorio. Se un assembly non è firmato, è necessario copiare un valore da un assembly autofirmato oppure utilizzare un valore "fittizio" di tutti gli zeri.|  
|`processorArchitecture`|Obbligatorio. Specifica il processore. I valori validi sono `msil` per tutti i processori, `x86` per windows a 32 bit, `IA64` per Windows a 64 bit e `Itanium` per processori Itanium Intel 64-bit.|  
|`language`|Obbligatorio. Identifica i codici di lingua in due parti (ad esempio, `en-US` ) dell'assembly. Questo elemento si trova nello `asmv2` spazio dei nomi. Se non è specificato, il valore predefinito è `neutral` .|  
  
## <a name="examples"></a>Esempi  
  
### <a name="description"></a>Descrizione  
 Nell'esempio di codice riportato di seguito viene illustrato un `assemblyIdentity` elemento in un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifesto dell'applicazione. Questo esempio di codice fa parte di un esempio più ampio fornito nel [manifesto dell'applicazione ClickOnce](../deployment/clickonce-application-manifest.md).  
  
### <a name="code"></a>Codice  
  
```  
<asmv1:assemblyIdentity   
  name="My Application Deployment.exe"   
  version="1.0.0.0"   
  publicKeyToken="43cb1e8e7a352766"   
  language="neutral"   
  processorArchitecture="x86"   
  type="win32" />  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Manifesto dell'applicazione ClickOnce](../deployment/clickonce-application-manifest.md)   
 [\<assemblyIdentity> Elemento](../deployment/assemblyidentity-element-clickonce-deployment.md)
