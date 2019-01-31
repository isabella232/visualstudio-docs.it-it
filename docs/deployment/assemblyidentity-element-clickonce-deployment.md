---
title: '&lt;assemblyIdentity&gt; elemento (distribuzione ClickOnce) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assemblyIdentity
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assemblyIdentity> element [ClickOnce deployment manifest]
ms.assetid: f4a3bb83-c800-47d0-9905-9a5ae2486838
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2ebe08584e3be85b38778276c7876a6394d2cef1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55043154"
---
# <a name="ltassemblyidentitygt-element-clickonce-deployment"></a>&lt;assemblyIdentity&gt; elemento (distribuzione ClickOnce)
Identifica l'assembly principale del [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dell'applicazione.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
      <assemblyIdentity    
   name   
   version  
   publicKeyToken  
   processorArchitecture  
    type  
/>  
```  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 Il `assemblyIdentity` elemento è obbligatorio. Non contiene alcun elemento figlio e ha gli attributi seguenti.  
  
|Attributo|Description|  
|---------------|-----------------|  
|`name`|Obbligatorio. Identifica il nome leggibile dall'utente della distribuzione a scopo informativo.<br /><br /> Se `name` contiene caratteri speciali, ad esempio le virgolette singole o doppie, l'applicazione potrebbe non riuscire per l'attivazione.|  
|`version`|Obbligatorio. Specifica il numero di versione dell'assembly, nel formato seguente: `major.minor.build.revision`.<br /><br /> Questo valore deve essere incrementato in un manifesto aggiornato per attivare un aggiornamento dell'applicazione.|  
|`publicKeyToken`|Obbligatorio. Specifica una stringa esadecimale a 16 caratteri che rappresenta gli ultimi 8 byte del valore hash SHA-1 della chiave pubblica usata per firmare il manifesto di distribuzione. La chiave pubblica che viene usata per firmare deve essere 2048 bit o superiore.<br /><br /> Anche se la firma di un assembly è facoltativo ma consigliato, questo attributo è obbligatorio. Se un assembly è firmato, è necessario copiare un valore da un assembly autofirmato oppure utilizzare un valore "fittizio" di tutti gli zeri.|  
|`processorArchitecture`|Obbligatorio. Specifica il processore. I valori validi sono `msil` per tutti i processori `x86` per Windows, a 32 `IA64` per Windows a 64 bit, e `Itanium` per processori Itanium di Intel a 64 bit.|  
|`type`|Obbligatorio. Per garantire la compatibilità con la tecnologia di installazione side-by-side di Windows. L'unico valore consentito è `win32`.|  
  
## <a name="remarks"></a>Note  
  
## <a name="example"></a>Esempio  
 L'esempio di codice seguente illustra un' `assemblyIdentity` elemento in un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesto della distribuzione. Questo esempio di codice è parte di un esempio più esaustivo disponibile per il [manifesto della distribuzione ClickOnce](../deployment/clickonce-deployment-manifest.md) argomento.  
  
```xml  
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
 [Manifesto di distribuzione ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [\<assemblyIdentity > elemento](../deployment/assemblyidentity-element-clickonce-application.md)