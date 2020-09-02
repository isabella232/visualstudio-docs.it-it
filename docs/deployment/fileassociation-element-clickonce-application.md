---
title: '&lt;elemento fileAssociation &gt; (applicazione ClickOnce) | Microsoft Docs'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4d3a43af5b2c7d50034cbed9d7da16e65b402f70
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62928518"
---
# <a name="ltfileassociationgt-element-clickonce-application"></a>&lt;elemento fileAssociation &gt; (applicazione ClickOnce)
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

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] non sovrascrive le associazioni di file esistenti. Tuttavia, un'applicazione ClickOnce può eseguire l'override dell'estensione di file solo per l'utente corrente. Dopo la disinstallazione dell'applicazione ClickOnce, ClickOnce Elimina l'associazione di file per l'utente e l'associazione per computer è nuovamente attiva.

## <a name="example"></a>Esempio
 Nell'esempio di codice seguente vengono illustrati `fileAssociation` gli elementi in un manifesto dell'applicazione per un'applicazione editor di testo distribuita utilizzando [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . Questo esempio di codice include anche l' [ \<file> elemento](../deployment/file-element-clickonce-application.md) richiesto dall' `defaultIcon` attributo.

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
- [Manifesto dell'applicazione ClickOnce](../deployment/clickonce-application-manifest.md)