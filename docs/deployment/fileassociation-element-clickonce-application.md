---
title: '&lt;fileAssociation&gt; elemento (applicazione ClickOnce) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <fileAssociation> element [ClickOnce application manifest]
- manifests [ClickOnce], fileAssociation element
ms.assetid: 8f951b4f-54f9-412e-a9e5-af4e379fcf08
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 62e099f949af3cc3ea336663224c1dd92726ac53
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2018
ms.locfileid: "39080025"
---
# <a name="ltfileassociationgt-element-clickonce-application"></a>&lt;fileAssociation&gt; elemento (applicazione ClickOnce)
Identifica un'estensione di file da associare all'applicazione.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
<fileAssociation  
    xmlns="urn:schemas-microsoft-com:clickonce.v1"  
    extension  
    description  
    progid  
    defaultIcon  
/>  
```  
  
## <a name="elements-and-attributes"></a>Gli elementi e attributi  
 L'elemento `fileAssociation` è facoltativo. L'elemento ha gli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`extension`|Obbligatorio. L'estensione di file da associare all'applicazione.|  
|`description`|Obbligatorio. Descrizione del tipo di file per l'utilizzo dalla shell.|  
|`progid`|Obbligatorio. Nome che identifica il tipo di file.|  
|`defaultIcon`|Obbligatorio. Specifica l'icona da utilizzare per i file con questa estensione. Il file di icona deve essere specificato utilizzando il [ \<file > elemento](../deployment/file-element-clickonce-application.md) all'interno di [ \<assembly > elemento](../deployment/assembly-element-clickonce-application.md) che contiene questo elemento.|  
  
## <a name="remarks"></a>Note  
 Questo elemento deve includere un riferimento XML dello spazio dei nomi "urn: schemas-microsoft-v1". Se il `<fileAssociation>` viene usato l'elemento, deve essere specificato dopo il `<application>` elemento nel relativo elemento padre [ \<assembly > elemento](../deployment/assembly-element-clickonce-application.md).  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] non sovrascrive le associazioni di file esistenti. Tuttavia, un'applicazione ClickOnce è possibile ignorare l'estensione di file per solo l'utente corrente. Dopo la disinstallazione di tale applicazione ClickOnce, ClickOnce consente di eliminare l'associazione di file per l'utente e l'associazione per ogni macchina è attiva anche in questo caso.  
  
## <a name="example"></a>Esempio  
 L'esempio di codice seguente illustra `fileAssociation` elementi in un'applicazione del manifesto per un'applicazione di editor di testo distribuita tramite [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Questo esempio di codice include anche il [ \<file > elemento](../deployment/file-element-clickonce-application.md) richiesto dal `defaultIcon` attributo.  
  
```xml  
<file name="text.ico" size="4286">  
  <hash>  
    <dsig:Transforms>  
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
    </dsig:Transforms>  
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
    <dsig:DigestValue>0joAqhmfeBb93ZneZv/oTMP2brY=</dsig:DigestValue>  
  </hash>  
</file>  
<file name="writing.ico" size="9662">  
  <hash>  
    <dsig:Transforms>  
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
    </dsig:Transforms>  
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
    <dsig:DigestValue>2cL2U7cm13nG40v9MQdxYKazIwI=</dsig:DigestValue>  
  </hash>  
</file>  
<fileAssociation xmlns="urn:schemas-microsoft-com:clickonce.v1" extension=".text" description="Text  Document (ClickOnce)" progid="Text.Document" defaultIcon="text.ico" />  
<fileAssociation xmlns="urn:schemas-microsoft-com:clickonce.v1" extension=".writing" description="Writings (ClickOnce)" progid="Writing.Document" defaultIcon="writing.ico" />  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Manifesto dell'applicazione ClickOnce](../deployment/clickonce-application-manifest.md)