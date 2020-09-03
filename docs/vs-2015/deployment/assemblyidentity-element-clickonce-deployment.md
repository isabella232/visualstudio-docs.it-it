---
title: '&lt;&gt;elemento assemblyIdentity (distribuzione ClickOnce) | Microsoft Docs'
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
- <assemblyIdentity> element [ClickOnce deployment manifest]
ms.assetid: f4a3bb83-c800-47d0-9905-9a5ae2486838
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bfc2ff97a2eb465fe7306ebe368a20e2a7fd8638
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155717"
---
# <a name="ltassemblyidentitygt-element-clickonce-deployment"></a>&lt;&gt;elemento assemblyIdentity (distribuzione ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identifica l'assembly primario dell' [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applicazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
      <assemblyIdentity    
   name   
   version  
   publicKeyToken  
   processorArchitecture  
    type  
/>  
```  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 L' `assemblyIdentity` elemento è obbligatorio. Non contiene elementi figlio e ha gli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`name`|Obbligatorio. Identifica il nome leggibile della distribuzione a scopo informativo.<br /><br /> Se `name` contiene caratteri speciali, ad esempio virgolette singole o doppie, l'attivazione dell'applicazione potrebbe non riuscire.|  
|`version`|Obbligatorio. Specifica il numero di versione dell'assembly, nel formato seguente: `major.minor.build.revision` .<br /><br /> Questo valore deve essere incrementato in un manifesto aggiornato per attivare un aggiornamento dell'applicazione.|  
|`publicKeyToken`|Obbligatorio. Specifica una stringa esadecimale di 16 caratteri che rappresenta gli ultimi 8 byte del valore hash SHA-1 della chiave pubblica in cui il manifesto di distribuzione è firmato. La chiave pubblica usata per firmare deve essere di 2048 bit o superiore.<br /><br /> Sebbene la firma di un assembly sia consigliata ma facoltativa, questo attributo è obbligatorio. Se un assembly non è firmato, è necessario copiare un valore da un assembly autofirmato oppure utilizzare un valore "fittizio" di tutti gli zeri.|  
|`processorArchitecture`|Obbligatorio. Specifica il processore. I valori validi sono `msil` per tutti i processori, `x86` per windows a 32 bit, `IA64` per Windows a 64 bit e `Itanium` per processori Itanium Intel 64-bit.|  
|`type`|Obbligatorio. Per la compatibilità con la tecnologia di installazione side-by-side di Windows. L'unico valore consentito è `win32` .|  
  
## <a name="remarks"></a>Osservazioni  
  
## <a name="example"></a>Esempio  
 Nell'esempio di codice riportato di seguito viene illustrato un `assemblyIdentity` elemento in un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifesto di distribuzione. Questo esempio di codice fa parte di un esempio più ampio fornito per l'argomento [manifesto della distribuzione ClickOnce](../deployment/clickonce-deployment-manifest.md) .  
  
```  
<!-- Identify the deployment. -->  
<assemblyIdentity   
  name="My Application Deployment.app"  
  version="1.0.0.0"  
  publicKeyToken="43cb1e8e7a352766"  
  language="neutral"  
  processorArchitecture="x86"  
  xmlns="urn:schemas-microsoft-com:asm.v1" />  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Manifesto della distribuzione ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [\<assemblyIdentity> Elemento](../deployment/assemblyidentity-element-clickonce-application.md)
