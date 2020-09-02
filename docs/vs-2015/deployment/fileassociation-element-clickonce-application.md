---
title: '&lt;elemento fileAssociation &gt; (applicazione ClickOnce) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <fileAssociation> element [ClickOnce application manifest]
- manifests [ClickOnce], fileAssociation element
ms.assetid: 8f951b4f-54f9-412e-a9e5-af4e379fcf08
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4b31ac34627b244cb61b6fdb5c6ca214675ec045
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150848"
---
# <a name="ltfileassociationgt-element-clickonce-application"></a>&lt;elemento fileAssociation &gt; (applicazione ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identifica un'estensione di file da associare all'applicazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<fileAssociation  
    xmlns="urn:schemas-microsoft-com:clickonce.v1"  
    extension  
    description  
    progid  
    defaultIcon  
/>  
```  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 L'elemento `fileAssociation` è facoltativo. L'elemento presenta gli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`extension`|Obbligatorio. Estensione di file da associare all'applicazione.|  
|`description`|Obbligatorio. Descrizione del tipo di file per l'utilizzo da parte della shell.|  
|`progid`|Obbligatorio. Nome che identifica in modo univoco il tipo di file.|  
|`defaultIcon`|Obbligatorio. Specifica l'icona da usare per i file con questa estensione. Il file icona deve essere specificato usando l' [ \<file> elemento](../deployment/file-element-clickonce-application.md) all'interno dell' [ \<assembly> elemento](../deployment/assembly-element-clickonce-application.md) che contiene questo elemento.|  
  
## <a name="remarks"></a>Osservazioni  
 Questo elemento deve includere un riferimento allo spazio dei nomi XML a "urn: schemas-microsoft-com: ClickOnce. V1". Se l' `<fileAssociation>` elemento viene utilizzato, deve provenire dopo l' `<application>` elemento nel relativo [ \<assembly> elemento](../deployment/assembly-element-clickonce-application.md)padre.  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] non sovrascrive le associazioni di file esistenti. Tuttavia, un'applicazione ClickOnce può eseguire l'override dell'estensione di file solo per l'utente corrente. Dopo la disinstallazione dell'applicazione ClickOnce, ClickOnce Elimina l'associazione di file per l'utente e l'associazione per computer è nuovamente attiva.  
  
## <a name="example"></a>Esempio  
 Nell'esempio di codice seguente vengono illustrati `fileAssociation` gli elementi in un manifesto dell'applicazione per un'applicazione editor di testo distribuita utilizzando [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . Questo esempio di codice include anche l' [ \<file> elemento](../deployment/file-element-clickonce-application.md) richiesto dall' `defaultIcon` attributo.  
  
```  
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
